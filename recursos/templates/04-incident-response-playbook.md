# Incident Response Playbook
## Manual de Resposta a Incidentes de Segurança

---

## 1. Informações do Documento

| Campo | Valor |
|-------|-------|
| **Organização** | |
| **Versão** | 1.0 |
| **Data de Criação** | |
| **Última Atualização** | |
| **Proprietário** | CISO / Security Operations |
| **Classificação** | Confidencial |
| **Próxima Revisão** | |

---

## 2. Objetivos e Escopo

### 2.1 Objetivos
- Minimizar o impacto de incidentes de segurança
- Garantir resposta rápida e coordenada
- Preservar evidências para análise forense
- Restaurar operações normais com segurança
- Aprender e melhorar continuamente

### 2.2 Escopo
Este playbook cobre incidentes de segurança cibernética incluindo:
- [x] Malware e Ransomware
- [x] Phishing e Engenharia Social
- [x] Vazamento de Dados
- [x] Acesso Não Autorizado
- [x] Ataques DDoS
- [x] Comprometimento de Sistemas de IA/ML
- [x] Insider Threats

---

## 3. Equipe de Resposta a Incidentes (CSIRT)

### 3.1 Estrutura da Equipe

```
                    ┌─────────────────┐
                    │   Incident      │
                    │   Commander     │
                    │   (CISO)        │
                    └────────┬────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
        ▼                    ▼                    ▼
┌───────────────┐   ┌───────────────┐   ┌───────────────┐
│   Technical   │   │  Communications│   │   Legal/      │
│   Lead        │   │   Lead        │   │   Compliance  │
└───────┬───────┘   └───────────────┘   └───────────────┘
        │
        ├─── Security Analyst(s)
        ├─── Forensics Specialist
        ├─── System Admin(s)
        └─── Network Engineer(s)
```

### 3.2 Contatos de Emergência

| Papel | Nome | Telefone | Email | Backup |
|-------|------|----------|-------|--------|
| Incident Commander | | | | |
| Technical Lead | | | | |
| Security Analyst | | | | |
| Legal Counsel | | | | |
| Communications | | | | |
| HR Representative | | | | |
| Fornecedor SOC (se terceirizado) | | | | |

### 3.3 Contatos Externos

| Entidade | Contato | Quando Acionar |
|----------|---------|----------------|
| Polícia Civil/Federal | | Crime cibernético |
| CERT.br | cert@cert.br | Incidentes graves |
| ANPD | | Vazamento de dados pessoais |
| Seguradora Cyber | | Acionamento de apólice |
| Fornecedor de IR | | Suporte especializado |

---

## 4. Classificação de Incidentes

### 4.1 Níveis de Severidade

| Severidade | Critérios | Resposta | SLA |
|------------|-----------|----------|-----|
| **P1 - Crítico** | Sistemas críticos indisponíveis; Vazamento massivo de dados; Ransomware ativo; Comprometimento de IA em produção | Resposta imediata 24/7; War room ativado | Contenção: 1h; Resolução: 4h |
| **P2 - Alto** | Sistemas importantes afetados; Vazamento de dados limitado; Malware detectado; Acesso não autorizado confirmado | Resposta em até 1h; Equipe dedicada | Contenção: 4h; Resolução: 24h |
| **P3 - Médio** | Sistemas não-críticos afetados; Tentativa de ataque bloqueada; Política violada; Anomalia em modelo ML | Resposta em horário comercial | Contenção: 8h; Resolução: 72h |
| **P4 - Baixo** | Eventos de segurança informativos; Vulnerabilidade identificada; Falso positivo confirmado | Próximo dia útil | Resolução: 1 semana |

### 4.2 Categorias de Incidentes

| Código | Categoria | Exemplos |
|--------|-----------|----------|
| MAL | Malware | Ransomware, Trojan, Worm, Cryptominer |
| PHI | Phishing | Spear phishing, BEC, Credential harvesting |
| UAC | Acesso Não Autorizado | Brute force, Credential stuffing, Privilege escalation |
| DLP | Vazamento de Dados | Exfiltração, Exposição acidental, Insider leak |
| DOS | Negação de Serviço | DDoS, Application DoS, Resource exhaustion |
| AIM | IA/ML Compromise | Adversarial attack, Model poisoning, Prompt injection |
| INS | Insider Threat | Sabotagem, Roubo de dados, Abuso de privilégio |
| VUL | Vulnerabilidade | Zero-day exploitado, CVE crítico |

---

## 5. Processo de Resposta (PICERL)

### 5.1 Visão Geral do Processo

```
┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐
│Preparation│──▶│ Identifi-│──▶│Containment│──▶│Eradication│──▶│ Recovery │──▶│ Lessons  │
│          │   │ cation   │   │          │   │          │   │          │   │ Learned  │
└──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘   └──────────┘
     │              │              │              │              │              │
     ▼              ▼              ▼              ▼              ▼              ▼
  Playbooks     Detecção       Isolamento     Remoção       Restauração    Melhoria
  Treinamento   Triagem        Preservação    Limpeza       Validação      Documentação
  Ferramentas   Análise        Comunicação    Hardening     Monitoramento  Atualização
```

---

## 6. Playbooks por Tipo de Incidente

### 6.1 PLAYBOOK: Ransomware (MAL-RANSOM)

#### Identificação
| Passo | Ação | Responsável | Ferramenta |
|-------|------|-------------|------------|
| 1 | Confirmar sintomas (arquivos criptografados, nota de resgate) | Analyst | EDR, Logs |
| 2 | Identificar variante do ransomware | Analyst | VirusTotal, ID Ransomware |
| 3 | Determinar vetor de entrada | Analyst | SIEM, Email Gateway |
| 4 | Mapear sistemas afetados | Analyst | EDR, Asset Inventory |
| 5 | Avaliar impacto e classificar severidade | Tech Lead | Risk Matrix |

#### Contenção
| Passo | Ação | Responsável | Observação |
|-------|------|-------------|------------|
| 1 | **NÃO desligar sistemas** (preservar memória) | All | Crítico para forense |
| 2 | Isolar sistemas afetados da rede | NetEng | Desconectar cabo/VLAN |
| 3 | Bloquear IOCs no firewall/proxy | NetEng | IPs, Domínios, Hashes |
| 4 | Desabilitar contas comprometidas | SysAdmin | Active Directory |
| 5 | Interromper sincronização de backups | SysAdmin | Prevenir criptografia |
| 6 | Preservar logs e snapshots | Analyst | Chain of custody |

#### Erradicação
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Identificar e remover persistence mechanisms | Analyst |
| 2 | Limpar sistemas afetados ou reimaginar | SysAdmin |
| 3 | Resetar credenciais comprometidas | SysAdmin |
| 4 | Patch vulnerabilidade explorada | SysAdmin |
| 5 | Validar integridade de backups | SysAdmin |

#### Recuperação
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Restaurar de backup limpo (mais recente antes do incidente) | SysAdmin |
| 2 | Reimaginar workstations afetadas | SysAdmin |
| 3 | Restaurar conectividade gradualmente | NetEng |
| 4 | Monitoramento intensivo por 72h | Analyst |
| 5 | Validar funcionamento de sistemas | Business Owner |

#### Decisões Críticas
```
⚠️  PAGAR O RESGATE?

    NÃO RECOMENDADO porque:
    - Não garante recuperação dos dados
    - Financia atividades criminosas
    - Pode violar sanções internacionais
    - Marca a organização como alvo

    CONSIDERAR APENAS SE:
    - Não há backup viável
    - Dados são críticos para vida/segurança
    - Aprovação legal e executiva
    - Engajar negociador profissional
```

---

### 6.2 PLAYBOOK: Vazamento de Dados (DLP-BREACH)

#### Identificação
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Confirmar que vazamento ocorreu | Analyst |
| 2 | Identificar tipo de dados afetados | Analyst |
| 3 | Quantificar registros/titulares afetados | Analyst |
| 4 | Determinar causa (ataque, erro, insider) | Analyst |
| 5 | Identificar destino dos dados | Analyst |

#### Classificação de Dados Vazados
| Tipo | Exemplos | LGPD | Ações Adicionais |
|------|----------|------|------------------|
| Dados Pessoais | Nome, Email, Telefone | Art. 48 | Notificar ANPD em 72h |
| Dados Sensíveis | Saúde, Biometria, Religião | Art. 11 | Notificação prioritária |
| Dados Financeiros | Cartão, Conta Bancária | PCI-DSS | Notificar bandeiras |
| Propriedade Intelectual | Código, Modelos ML | N/A | Ação legal |
| Credenciais | Senhas, Tokens, API Keys | N/A | Reset imediato |

#### Contenção
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Interromper vazamento ativo | Analyst/NetEng |
| 2 | Revogar acessos suspeitos | SysAdmin |
| 3 | Bloquear endpoint/conta origem | SysAdmin |
| 4 | Solicitar remoção de dados (se publicados) | Legal |
| 5 | Preservar evidências | Analyst |

#### Notificações Obrigatórias (LGPD)

```
┌─────────────────────────────────────────────────────────────────┐
│                    TIMELINE DE NOTIFICAÇÃO                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  T+0h ─────────── Incidente Detectado                           │
│       │                                                          │
│  T+2h ─────────── Comunicação Interna (CISO, Legal, DPO)        │
│       │                                                          │
│  T+24h ────────── Avaliação de Risco aos Titulares              │
│       │                                                          │
│  T+48h ────────── Preparar Comunicação para ANPD                │
│       │                                                          │
│  T+72h ────────── NOTIFICAR ANPD (Prazo Legal)                  │
│       │           Notificar Titulares (se risco relevante)      │
│       │                                                          │
│  T+5d ─────────── Follow-up com medidas adotadas                │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

#### Template de Notificação ANPD
```
COMUNICAÇÃO DE INCIDENTE DE SEGURANÇA - ANPD

1. Identificação do Controlador: [Nome, CNPJ, Contato DPO]
2. Data/Hora do Incidente: [DD/MM/AAAA HH:MM]
3. Data da Ciência: [DD/MM/AAAA]
4. Descrição do Incidente: [Resumo]
5. Dados Pessoais Afetados: [Tipos]
6. Titulares Afetados: [Quantidade estimada]
7. Medidas de Segurança Existentes: [Controles]
8. Medidas Adotadas: [Contenção, Mitigação]
9. Riscos aos Titulares: [Avaliação]
10. Medidas para Mitigar Danos: [Ações]
```

---

### 6.3 PLAYBOOK: Comprometimento de Sistema de IA/ML (AIM-COMP)

#### Identificação
| Passo | Ação | Indicadores | Ferramenta |
|-------|------|-------------|------------|
| 1 | Detectar anomalia em outputs do modelo | Respostas inesperadas, drift súbito | Model Monitoring |
| 2 | Verificar integridade do modelo | Hash diferente, versão alterada | Model Registry |
| 3 | Analisar inputs recentes | Padrões adversariais, prompt injection | Input Logs |
| 4 | Verificar dados de treinamento | Alterações não autorizadas | Data Versioning |
| 5 | Revisar acessos ao pipeline ML | Logins suspeitos | IAM Logs |

#### Tipos de Ataque a IA/ML
| Tipo | Descrição | Indicadores |
|------|-----------|-------------|
| Data Poisoning | Dados maliciosos no treinamento | Degradação gradual, bias |
| Model Extraction | Roubo do modelo via queries | Alto volume de requests |
| Adversarial Input | Inputs crafted para enganar | Classificações erradas |
| Prompt Injection | Manipulação de LLM | Outputs não autorizados |
| Model Tampering | Modificação direta do modelo | Checksum alterado |
| Inference Attack | Extração de dados de treino | Queries específicas |

#### Contenção
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Colocar modelo em modo read-only | ML Engineer |
| 2 | Ativar modelo de fallback/anterior | ML Engineer |
| 3 | Rate limit agressivo na API | DevOps |
| 4 | Bloquear IPs/usuários suspeitos | NetEng |
| 5 | Pausar pipeline de retraining | ML Engineer |
| 6 | Isolar ambiente de treinamento | SysAdmin |

#### Erradicação
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Identificar e remover dados envenenados | Data Engineer |
| 2 | Restaurar modelo de versão confiável | ML Engineer |
| 3 | Validar integridade do pipeline | ML Engineer |
| 4 | Retreinar modelo se necessário | ML Engineer |
| 5 | Implementar validações adicionais | ML Engineer |

#### Recuperação
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Deploy de modelo limpo | ML Engineer |
| 2 | Validar outputs contra ground truth | Data Scientist |
| 3 | Monitoramento intensivo de drift | ML Engineer |
| 4 | Testes adversariais antes de produção | Security |
| 5 | Comunicar stakeholders sobre status | Comms |

#### Checklist Específico para LLMs
- [ ] Verificar guardrails de prompt injection
- [ ] Revisar system prompts para vazamentos
- [ ] Validar rate limits de API
- [ ] Checar logs de outputs sensíveis
- [ ] Verificar jailbreak attempts
- [ ] Analisar padrões de prompt engineering malicioso

---

### 6.4 PLAYBOOK: Phishing/BEC (PHI-BEC)

#### Identificação
| Passo | Ação |
|-------|------|
| 1 | Confirmar email/mensagem maliciosa |
| 2 | Identificar todos os destinatários |
| 3 | Determinar quantos interagiram (clicaram, responderam) |
| 4 | Identificar se credenciais foram comprometidas |
| 5 | Verificar se houve transferência financeira (BEC) |

#### Contenção Imediata
| Passo | Ação | Responsável |
|-------|------|-------------|
| 1 | Remover email das caixas (Message Trace) | Email Admin |
| 2 | Bloquear remetente/domínio | Email Admin |
| 3 | Bloquear URLs maliciosas no proxy | NetEng |
| 4 | Reset de senha para quem interagiu | SysAdmin |
| 5 | Revogar sessões ativas | SysAdmin |
| 6 | Se BEC: Contatar banco IMEDIATAMENTE | Finance + Legal |

#### Timeline BEC (Transferência Fraudulenta)
```
⚠️  URGENTE - CADA MINUTO CONTA

T+0min: Fraude detectada
        │
        └──▶ Contatar banco IMEDIATAMENTE
             Solicitar bloqueio/reversão
             Documentar tudo

T+30min: Contatar banco do beneficiário
         (se conhecido)

T+1h: Registrar B.O.
      Acionar seguradora

T+24h: Avaliar se notificar ANPD
       (se dados pessoais envolvidos)
```

---

## 7. Templates e Formulários

### 7.1 Ticket de Incidente

```
═══════════════════════════════════════════════════════════════
                    REGISTRO DE INCIDENTE
═══════════════════════════════════════════════════════════════

ID do Incidente: INC-YYYY-NNNN
Data/Hora de Detecção:
Data/Hora do Incidente (se diferente):
Reportado por:
Severidade: [ ] P1  [ ] P2  [ ] P3  [ ] P4
Categoria:

───────────────────────────────────────────────────────────────
DESCRIÇÃO DO INCIDENTE
───────────────────────────────────────────────────────────────
[Descreva o que aconteceu, como foi detectado, impacto observado]




───────────────────────────────────────────────────────────────
SISTEMAS AFETADOS
───────────────────────────────────────────────────────────────
| Sistema | IP/Hostname | Criticidade | Status |
|---------|-------------|-------------|--------|
|         |             |             |        |

───────────────────────────────────────────────────────────────
INDICADORES DE COMPROMETIMENTO (IOCs)
───────────────────────────────────────────────────────────────
IPs:
Domínios:
Hashes:
URLs:
Emails:
Outros:

───────────────────────────────────────────────────────────────
AÇÕES TOMADAS
───────────────────────────────────────────────────────────────
| Data/Hora | Ação | Responsável | Resultado |
|-----------|------|-------------|-----------|
|           |      |             |           |

───────────────────────────────────────────────────────────────
EVIDÊNCIAS COLETADAS
───────────────────────────────────────────────────────────────
| Tipo | Localização | Hash | Coletado por | Data |
|------|-------------|------|--------------|------|
|      |             |      |              |      |

───────────────────────────────────────────────────────────────
STATUS E PRÓXIMOS PASSOS
───────────────────────────────────────────────────────────────
Status Atual: [ ] Aberto  [ ] Em Análise  [ ] Contido
              [ ] Erradicado  [ ] Recuperado  [ ] Fechado

Próximos Passos:
1.
2.
3.

═══════════════════════════════════════════════════════════════
```

### 7.2 Checklist de Preservação de Evidências

```
CHAIN OF CUSTODY - EVIDÊNCIAS DIGITAIS

Incidente: INC-YYYY-NNNN
Data:

ANTES DE COLETAR:
[ ] Fotografar estado atual da tela
[ ] Documentar data/hora do sistema
[ ] Identificar timezone
[ ] Preparar mídia de destino (sanitizada)

COLETA DE MEMÓRIA (se sistema ligado):
[ ] Executar dump de memória RAM
[ ] Ferramenta utilizada: ___________
[ ] Hash da imagem: _______________
[ ] Armazenamento: ________________

COLETA DE DISCO:
[ ] Realizar imagem forense bit-a-bit
[ ] Ferramenta: [ ] dd  [ ] FTK  [ ] EnCase  [ ] Outro: _____
[ ] Hash MD5: _______________________
[ ] Hash SHA256: ____________________
[ ] Armazenamento: __________________

COLETA DE LOGS:
[ ] Logs de sistema operacional
[ ] Logs de aplicação
[ ] Logs de firewall/IDS
[ ] Logs de autenticação
[ ] Logs de email
[ ] Logs de proxy/web

DOCUMENTAÇÃO:
[ ] Formulário de chain of custody preenchido
[ ] Evidências em local seguro (acesso restrito)
[ ] Backup das evidências realizado

Coletado por: _________________ Data: _________
Testemunha: __________________ Data: _________
```

---

## 8. Comunicação Durante Incidentes

### 8.1 Matriz de Comunicação

| Audiência | Quando | Canal | Responsável | Template |
|-----------|--------|-------|-------------|----------|
| CSIRT | Imediato | War Room / Slack | Tech Lead | Técnico |
| Executivos | P1: 1h, P2: 4h | Email / Reunião | IC | Executivo |
| Jurídico | Se vazamento/crime | Email / Reunião | IC | Jurídico |
| RH | Se insider | Email / Reunião | IC | Confidencial |
| Clientes | Se impactados | Email / Portal | Comms | Cliente |
| Imprensa | Se público | Press Release | Comms + PR | Público |
| Reguladores | Conforme lei | Oficial | Legal + DPO | Regulatório |

### 8.2 Template de Comunicação Executiva

```
ATUALIZAÇÃO DE INCIDENTE DE SEGURANÇA

Para: [C-Level]
De: [CISO/Incident Commander]
Data: [DD/MM/AAAA HH:MM]
Incidente: INC-YYYY-NNNN
Severidade: [P1/P2/P3/P4]

RESUMO EXECUTIVO
[2-3 frases descrevendo o incidente e status atual]

IMPACTO NO NEGÓCIO
• Sistemas afetados: [lista]
• Usuários/Clientes impactados: [número]
• Risco financeiro estimado: [R$]
• Risco reputacional: [Baixo/Médio/Alto]

STATUS ATUAL
• Fase: [Identificação/Contenção/Erradicação/Recuperação]
• Contenção: [Sim/Não/Parcial]
• ETA para resolução: [estimativa]

AÇÕES EM ANDAMENTO
1. [Ação]
2. [Ação]
3. [Ação]

DECISÕES NECESSÁRIAS
• [Se houver decisão que precisa de aprovação executiva]

PRÓXIMA ATUALIZAÇÃO
[Data/Hora]
```

---

## 9. Métricas e KPIs

### 9.1 Métricas de Resposta a Incidentes

| Métrica | Definição | Meta | Atual |
|---------|-----------|------|-------|
| MTTD (Mean Time to Detect) | Tempo médio de detecção | < 24h | |
| MTTR (Mean Time to Respond) | Tempo médio de resposta inicial | P1: < 15min | |
| MTTC (Mean Time to Contain) | Tempo médio de contenção | P1: < 4h | |
| MTTR (Mean Time to Recover) | Tempo médio de recuperação | P1: < 24h | |
| Incidentes por mês | Volume mensal | Baseline | |
| % Incidentes com Root Cause | Análise completa | > 90% | |
| Recorrência | Mesmo tipo em 90 dias | < 10% | |

### 9.2 Dashboard de Incidentes

```
┌────────────────────────────────────────────────────────────────┐
│                  DASHBOARD DE INCIDENTES                        │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│  INCIDENTES ATIVOS          ÚLTIMOS 30 DIAS                    │
│  ┌─────┐                    ┌─────────────────────────────┐    │
│  │  3  │                    │ Total: 45                    │    │
│  └─────┘                    │ P1: 2  P2: 8  P3: 20  P4: 15│    │
│  P1:1 P2:1 P3:1             └─────────────────────────────┘    │
│                                                                 │
│  MTTD        MTTR        TOP CATEGORIAS                        │
│  ┌─────┐     ┌─────┐     ┌─────────────────────────────┐       │
│  │ 4.2h│     │ 6.1h│     │ PHI: ████████░░ 40%        │       │
│  └─────┘     └─────┘     │ MAL: █████░░░░░ 25%        │       │
│  Meta: 24h   Meta: 8h    │ UAC: ████░░░░░░ 20%        │       │
│                          │ DLP: ███░░░░░░░ 15%        │       │
│                          └─────────────────────────────┘       │
│                                                                 │
└────────────────────────────────────────────────────────────────┘
```

---

## 10. Lições Aprendidas

### 10.1 Template de Post-Mortem

```
═══════════════════════════════════════════════════════════════
              POST-MORTEM / LIÇÕES APRENDIDAS
═══════════════════════════════════════════════════════════════

Incidente: INC-YYYY-NNNN
Data do Incidente:
Data do Post-Mortem:
Facilitador:
Participantes:

───────────────────────────────────────────────────────────────
1. RESUMO DO INCIDENTE
───────────────────────────────────────────────────────────────
[Descrição factual do que aconteceu]

───────────────────────────────────────────────────────────────
2. TIMELINE DETALHADA
───────────────────────────────────────────────────────────────
| Data/Hora | Evento |
|-----------|--------|
|           |        |

───────────────────────────────────────────────────────────────
3. CAUSA RAIZ (5 Porquês)
───────────────────────────────────────────────────────────────
Por que 1:
Por que 2:
Por que 3:
Por que 4:
Por que 5 (Causa Raiz):

───────────────────────────────────────────────────────────────
4. O QUE FUNCIONOU BEM
───────────────────────────────────────────────────────────────
•
•
•

───────────────────────────────────────────────────────────────
5. O QUE PODE MELHORAR
───────────────────────────────────────────────────────────────
•
•
•

───────────────────────────────────────────────────────────────
6. AÇÕES CORRETIVAS
───────────────────────────────────────────────────────────────
| Ação | Responsável | Prazo | Status |
|------|-------------|-------|--------|
|      |             |       |        |

───────────────────────────────────────────────────────────────
7. MÉTRICAS DO INCIDENTE
───────────────────────────────────────────────────────────────
MTTD:
MTTC:
MTTR:
Custo estimado:
Horas-pessoa:

═══════════════════════════════════════════════════════════════
```

---

## 11. Anexos

### 11.1 Referências Rápidas

**MITRE ATT&CK Tactics**
- Initial Access → Execution → Persistence → Privilege Escalation
- Defense Evasion → Credential Access → Discovery → Lateral Movement
- Collection → Command and Control → Exfiltration → Impact

**Portas Comuns de Ameaças**
- 3389: RDP (Ransomware)
- 445: SMB (Worms)
- 22: SSH (Brute Force)
- 4444/5555: Metasploit default

**Ferramentas de IR**
- Volatility: Análise de memória
- Autopsy: Forense de disco
- Wireshark: Análise de rede
- YARA: Detecção de malware

### 11.2 Exercícios de Simulação (Tabletop)

| Cenário | Frequência | Participantes |
|---------|------------|---------------|
| Ransomware em sistemas críticos | Trimestral | CSIRT + Executivos |
| Vazamento de dados de clientes | Semestral | CSIRT + Legal + DPO |
| Comprometimento de modelo de IA | Anual | CSIRT + ML Team |
| BEC / Fraude financeira | Trimestral | Finance + CSIRT |

---

## 12. Aprovações e Controle de Versões

| Versão | Data | Autor | Alterações |
|--------|------|-------|------------|
| 1.0 | | | Criação inicial |
| | | | |

| Papel | Nome | Assinatura | Data |
|-------|------|------------|------|
| CISO | | | |
| CIO | | | |
| Legal | | | |
| DPO | | | |

---

*Template versão 1.0 - MBA Cibersegurança & IA*
