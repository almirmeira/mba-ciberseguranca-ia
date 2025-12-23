# Incident Response Playbook - Caso Colonial Pipeline
## Documentação de Resposta a Incidente de Ransomware (Exemplo Baseado em Caso Real)

> **Nota**: Este documento é um exemplo educacional baseado em informações públicas sobre o ataque ransomware à Colonial Pipeline em maio de 2021. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## 1. Informações do Incidente

| Campo | Valor |
|-------|-------|
| **ID do Incidente** | INC-2021-0507-001 |
| **Organização Afetada** | Colonial Pipeline Company |
| **Setor** | Infraestrutura Crítica - Energia (Petróleo/Gás) |
| **Tipo de Incidente** | Ransomware (DarkSide) |
| **Severidade** | **P1 - CRÍTICO** |
| **Data de Detecção** | 7 de Maio de 2021 |
| **Data de Resolução** | 12-15 de Maio de 2021 |
| **Impacto** | Interrupção de 45% do fornecimento de combustível da Costa Leste dos EUA |

---

## 2. Resumo Executivo

### 2.1 O Que Aconteceu

Em 7 de maio de 2021, a Colonial Pipeline, operadora do maior sistema de oleodutos de combustível dos Estados Unidos (5.500 milhas, transportando 2,5 milhões de barris/dia), sofreu um ataque de ransomware conduzido pelo grupo criminoso DarkSide.

**Vetor de Ataque**: Os atacantes ganharam acesso através de uma **senha comprometida de uma conta VPN inativa** que não possuía autenticação multifator (MFA).

**Impacto**: A empresa desligou proativamente suas operações de oleoduto por 6 dias, causando escassez de combustível em toda a Costa Leste dos EUA.

### 2.2 Números do Incidente

| Métrica | Valor |
|---------|-------|
| **Duração do Ataque** | ~2 horas (exfiltração inicial) |
| **Dados Exfiltrados** | ~100 GB |
| **Tempo de Detecção** | Desconhecido (detectado ao ver nota de resgate) |
| **Tempo de Parada Operacional** | 6 dias |
| **Resgate Pago** | 75 Bitcoin (~$4,4 milhões) |
| **Resgate Recuperado** | 63.7 Bitcoin (~$2,3 milhões) |
| **Postos sem Combustível** | ~10.600 (pico) |
| **Aumento no Preço da Gasolina** | $3.04/galão (maior em 6 anos) |

---

## 3. Timeline Detalhada do Incidente

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    TIMELINE DO INCIDENTE COLONIAL PIPELINE                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  FASE 1: COMPROMETIMENTO INICIAL (Semanas/Meses antes)                          │
│  ───────────────────────────────────────────────────────                         │
│                                                                                  │
│  [Data Desconhecida]                                                             │
│     │                                                                            │
│     ├── Credencial VPN comprometida (possivelmente via breach anterior)         │
│     │   • Conta VPN inativa (legacy)                                            │
│     │   • Sem MFA habilitado                                                    │
│     │   • Senha possivelmente reutilizada de outro breach                       │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 2: ATAQUE ATIVO (6-7 de Maio de 2021)                                     │
│  ───────────────────────────────────────────                                     │
│                                                                                  │
│  6 Mai (Estimado)                                                                │
│     │                                                                            │
│     ├── Atacantes acessam rede via VPN comprometida                             │
│     ├── Movimentação lateral na rede corporativa (IT)                           │
│     ├── Reconhecimento e mapeamento de sistemas                                 │
│     │                                                                            │
│  7 Mai - Madrugada                                                               │
│     │                                                                            │
│     ├── 05:30 EDT - Exfiltração de ~100GB de dados (em ~2 horas)               │
│     ├── Deployment do ransomware DarkSide                                       │
│     ├── Criptografia de sistemas na rede corporativa (billing)                  │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 3: DETECÇÃO E RESPOSTA INICIAL (7 de Maio)                                │
│  ───────────────────────────────────────────────                                 │
│                                                                                  │
│  7 Mai - Manhã                                                                   │
│     │                                                                            │
│     ├── Funcionário descobre nota de resgate                                    │
│     ├── Alerta disparado para equipe de TI/Segurança                            │
│     ├── Acionamento da liderança executiva                                      │
│     │                                                                            │
│  7 Mai - 12:30 EDT                                                               │
│     │                                                                            │
│     ├── DECISÃO CRÍTICA: Desligar operações do oleoduto                         │
│     │   Motivo: Incerteza sobre comprometimento de sistemas OT                  │
│     │   Motivo secundário: Sistema de billing comprometido                      │
│     │                                                                            │
│     ├── Mandiant contratada para investigação                                   │
│     ├── FBI notificado                                                          │
│     ├── CISA notificada                                                         │
│     ├── DOE notificado                                                          │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 4: CONTENÇÃO E INVESTIGAÇÃO (7-9 de Maio)                                 │
│  ───────────────────────────────────────────────                                 │
│                                                                                  │
│  7-8 Mai                                                                         │
│     │                                                                            │
│     ├── Isolamento de sistemas comprometidos                                    │
│     ├── Análise forense iniciada (Mandiant)                                     │
│     ├── Identificação do vetor de entrada (VPN)                                 │
│     ├── Confirmação: sistemas OT NÃO comprometidos                              │
│     │                                                                            │
│  9 Mai                                                                           │
│     │                                                                            │
│     ├── FBI confirma atribuição ao grupo DarkSide                               │
│     ├── Presidente Biden declara estado de emergência                           │
│     ├── DOT emite isenção de horas de serviço para caminhoneiros               │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 5: DECISÃO DE PAGAMENTO E RECUPERAÇÃO (9-12 de Maio)                      │
│  ─────────────────────────────────────────────────────────                       │
│                                                                                  │
│  9-10 Mai                                                                        │
│     │                                                                            │
│     ├── Negociações com DarkSide iniciadas                                      │
│     ├── Avaliação de opções de recuperação                                      │
│     ├── Decisão de pagar resgate tomada pelo CEO                                │
│     │   Justificativa: "Era a coisa certa a fazer pelo país"                   │
│     │                                                                            │
│  10 Mai                                                                          │
│     │                                                                            │
│     ├── Governador da Geórgia declara estado de emergência                      │
│     ├── Jones Act waiver aprovado (transporte marítimo)                         │
│     │                                                                            │
│  11 Mai                                                                          │
│     │                                                                            │
│     ├── CISA + FBI emitem Joint Advisory sobre DarkSide                         │
│     ├── Pagamento de 75 BTC (~$4.4M) efetuado                                   │
│     ├── Chave de decriptação recebida                                           │
│     │   NOTA: Decriptador "muito lento" - restauração via backup preferida      │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 6: RESTAURAÇÃO (12-15 de Maio)                                            │
│  ────────────────────────────────────                                            │
│                                                                                  │
│  12 Mai                                                                          │
│     │                                                                            │
│     ├── 17:00 EDT - Reinício das operações do oleoduto                         │
│     ├── Executive Order 14028 assinado por Biden                                │
│     │   (Melhorias em segurança cibernética federal)                            │
│     │                                                                            │
│  13-14 Mai                                                                       │
│     │                                                                            │
│     ├── Operações gradualmente normalizando                                     │
│     ├── Filas em postos de gasolina persistem                                   │
│     │                                                                            │
│  15 Mai                                                                          │
│     │                                                                            │
│     ├── Colonial anuncia operações normais restauradas                          │
│     │                                                                            │
│  ─────────────────────────────────────────────────────────────────────────────  │
│                                                                                  │
│  FASE 7: PÓS-INCIDENTE (Junho 2021+)                                            │
│  ────────────────────────────────────                                            │
│                                                                                  │
│  7 Jun 2021                                                                      │
│     │                                                                            │
│     ├── DOJ recupera 63.7 BTC (~$2.3M) do resgate                               │
│     │                                                                            │
│  8 Jun 2021                                                                      │
│     │                                                                            │
│     ├── CEO Joseph Blount testemunha perante Congresso                          │
│     │                                                                            │
│  2021-2023                                                                       │
│     │                                                                            │
│     └── Múltiplas iniciativas de segurança para infraestrutura crítica          │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Análise Técnica do Ataque

### 4.1 Vetor de Ataque

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         KILL CHAIN DO ATAQUE                                     │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  1. INITIAL ACCESS                                                               │
│     ┌──────────────────────────────────────────────────────────────────────┐    │
│     │  Técnica: T1078 - Valid Accounts (VPN)                               │    │
│     │  • Conta VPN legada/inativa comprometida                             │    │
│     │  • Sem MFA configurado                                               │    │
│     │  • Possível origem: credential stuffing, dark web, phishing anterior │    │
│     └──────────────────────────────────────────────────────────────────────┘    │
│                              │                                                   │
│                              ▼                                                   │
│  2. DISCOVERY & LATERAL MOVEMENT                                                 │
│     ┌──────────────────────────────────────────────────────────────────────┐    │
│     │  Técnicas: T1087 (Account Discovery), T1021 (Remote Services)        │    │
│     │  • Reconhecimento da rede corporativa                                │    │
│     │  • Identificação de sistemas de alto valor                           │    │
│     │  • Movimentação lateral usando credenciais válidas                   │    │
│     │  • Rede IT e OT possivelmente não segmentadas adequadamente          │    │
│     └──────────────────────────────────────────────────────────────────────┘    │
│                              │                                                   │
│                              ▼                                                   │
│  3. COLLECTION & EXFILTRATION                                                    │
│     ┌──────────────────────────────────────────────────────────────────────┐    │
│     │  Técnicas: T1005 (Data from Local System), T1041 (Exfiltration)      │    │
│     │  • ~100 GB de dados exfiltrados                                      │    │
│     │  • Tempo de exfiltração: ~2 horas                                    │    │
│     │  • Dados incluíam informações corporativas sensíveis                 │    │
│     │  • Técnica de double extortion (roubo + criptografia)                │    │
│     └──────────────────────────────────────────────────────────────────────┘    │
│                              │                                                   │
│                              ▼                                                   │
│  4. IMPACT                                                                       │
│     ┌──────────────────────────────────────────────────────────────────────┐    │
│     │  Técnica: T1486 (Data Encrypted for Impact)                          │    │
│     │  • Ransomware DarkSide deployado                                     │    │
│     │  • Sistemas de billing criptografados                                │    │
│     │  • Nota de resgate deixada                                           │    │
│     │  • Demanda: ~$4.4 milhões em Bitcoin                                 │    │
│     └──────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Indicadores de Comprometimento (IOCs)

| Tipo | Indicador | Descrição |
|------|-----------|-----------|
| Malware | DarkSide Ransomware | RaaS (Ransomware-as-a-Service) |
| Extensão | .darkside, .dark | Arquivos criptografados |
| Nota de Resgate | README.[victim_id].txt | Instruções de pagamento |
| TTP | Exfiltração pré-criptografia | Double extortion |
| Grupo | DarkSide / UNC2465 | Afiliados do RaaS |

### 4.3 Vulnerabilidades Exploradas

| Vulnerabilidade | Descrição | Controle Ausente |
|-----------------|-----------|------------------|
| Conta VPN inativa | Conta legacy não desativada | Gestão de ciclo de vida de identidades |
| Ausência de MFA | VPN sem autenticação multifator | MFA obrigatório |
| Credential reuse | Senha possivelmente vazada em outro breach | Monitoramento de credenciais vazadas |
| Segmentação insuficiente | IT/OT não adequadamente separados | Microsegmentação |
| Detecção inadequada | Exfiltração não detectada | DLP, NDR, UEBA |

---

## 5. Ações de Resposta Executadas

### 5.1 Resposta Imediata (Primeiras 24 horas)

| Hora | Ação | Responsável | Resultado |
|------|------|-------------|-----------|
| T+0h | Detecção da nota de resgate | Funcionário | Alerta iniciado |
| T+0.5h | Acionamento do time de IR | IT Security | Equipe mobilizada |
| T+1h | Notificação à liderança executiva | CISO | Decisão de desligamento |
| T+2h | **Desligamento do oleoduto** | Operations | 5.500 milhas offline |
| T+3h | Contratação de Mandiant | CEO | Investigação forense |
| T+4h | Notificação ao FBI | Legal | Investigação federal |
| T+5h | Notificação à CISA | CISO | Suporte governamental |
| T+6h | Isolamento de sistemas afetados | IT Security | Contenção |
| T+24h | Análise inicial completa | Mandiant | Vetor identificado |

### 5.2 Decisões Críticas

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║                    DECISÃO 1: DESLIGAR O OLEODUTO                                 ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  CONTEXTO:                                                                        ║
║  • Ransomware detectado na rede IT (corporativa)                                 ║
║  • Incerteza sobre comprometimento de sistemas OT (operacionais)                 ║
║  • Sistema de billing comprometido (não podiam cobrar clientes)                  ║
║                                                                                   ║
║  OPÇÕES CONSIDERADAS:                                                             ║
║  1. Manter operações e investigar em paralelo                                    ║
║  2. Desligar operações até confirmar segurança dos sistemas OT                   ║
║                                                                                   ║
║  DECISÃO: Opção 2 - Desligamento preventivo                                      ║
║                                                                                   ║
║  JUSTIFICATIVA:                                                                   ║
║  • Risco de dano físico/ambiental se OT comprometido                             ║
║  • Responsabilidade com segurança pública                                        ║
║  • Incapacidade de faturar clientes de qualquer forma                            ║
║                                                                                   ║
║  IMPACTO:                                                                         ║
║  • 45% do combustível da Costa Leste interrompido                                ║
║  • Pânico em postos de gasolina                                                  ║
║  • Declaração de estado de emergência                                            ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝

╔══════════════════════════════════════════════════════════════════════════════════╗
║                    DECISÃO 2: PAGAR O RESGATE                                     ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  CONTEXTO:                                                                        ║
║  • 6 dias de oleoduto parado                                                     ║
║  • Crise nacional de combustível                                                 ║
║  • Backups disponíveis mas recuperação levaria tempo                             ║
║  • Pressão pública e governamental intensa                                       ║
║                                                                                   ║
║  OPÇÕES CONSIDERADAS:                                                             ║
║  1. Não pagar e restaurar via backups                                            ║
║  2. Pagar e obter chave de decriptação                                           ║
║                                                                                   ║
║  DECISÃO: Opção 2 - Pagar $4.4 milhões em Bitcoin                                ║
║                                                                                   ║
║  JUSTIFICATIVA (CEO Joseph Blount):                                               ║
║  "Era a coisa certa a fazer pelo país"                                           ║
║  • Incerteza sobre extensão total dos danos                                      ║
║  • Pressão para restaurar fornecimento rapidamente                               ║
║  • Chave de decriptação como "seguro" adicional                                  ║
║                                                                                   ║
║  RESULTADO:                                                                       ║
║  • Chave recebida, mas decriptador muito lento                                   ║
║  • Restauração final feita principalmente via backups                            ║
║  • DOJ recuperou 63.7 BTC (~$2.3M) posteriormente                                ║
║                                                                                   ║
║  LIÇÃO APRENDIDA:                                                                 ║
║  • Pagar não garante recuperação rápida                                          ║
║  • Backups testados são essenciais                                               ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## 6. Resposta Governamental

### 6.1 Ações de Agências Federais

| Data | Agência | Ação |
|------|---------|------|
| 9 Mai | **Presidente Biden** | Declaração de estado de emergência |
| 9 Mai | DOT/FMCSA | Isenção de horas de serviço para caminhoneiros |
| 10 Mai | FBI | Confirmação de atribuição ao DarkSide |
| 10 Mai | Gov. Georgia | Estado de emergência estadual |
| 11 Mai | CISA + FBI | Joint Cybersecurity Advisory sobre DarkSide |
| 11 Mai | DOT | Flexibilização adicional de regras de transporte |
| 12 Mai | DHS | Jones Act waiver para transporte marítimo |
| 12 Mai | **Presidente Biden** | Executive Order 14028 (Cybersecurity) |
| 7 Jun | DOJ | Recuperação de 63.7 BTC do resgate |
| 8 Jun | Congresso | Audiência com CEO da Colonial |

### 6.2 Executive Order 14028 (12 Mai 2021)

A ordem executiva assinada em resposta ao incidente incluiu:

- Padrões de segurança mais rígidos para software vendido ao governo
- Melhoria na detecção e segurança de sistemas existentes
- Melhoria no compartilhamento de informações
- Estabelecimento do Cyber Safety Review Board
- Melhorias na resposta a incidentes

---

## 7. Lições Aprendidas

### 7.1 O Que Deu Errado

| Falha | Descrição | Controle que Preveniria |
|-------|-----------|------------------------|
| **Conta VPN legada ativa** | Conta não utilizada permaneceu ativa | Revisão periódica de contas, auto-desativação |
| **Ausência de MFA** | VPN acessível apenas com senha | MFA obrigatório para todos os acessos remotos |
| **Credential hygiene** | Senha possivelmente reutilizada | Monitoramento de credenciais vazadas, políticas de senha |
| **Detecção de exfiltração** | 100GB exfiltrados sem detecção | DLP, NDR, monitoramento de egress |
| **Segmentação IT/OT** | Incerteza sobre alcance do ataque | Segmentação rigorosa, air gap onde possível |
| **Plano de continuidade** | Decisão de shutdown total | BCP testado, cenários de ransomware |

### 7.2 O Que Deu Certo

| Ação | Descrição | Resultado |
|------|-----------|-----------|
| **Notificação rápida** | FBI e CISA notificados no mesmo dia | Suporte federal mobilizado |
| **Decisão de shutdown** | Priorização de segurança sobre operações | Sistemas OT protegidos |
| **Contratação de especialistas** | Mandiant para investigação | Análise forense profissional |
| **Comunicação transparente** | CEO assumiu responsabilidade | Gestão de crise efetiva |
| **Cooperação com autoridades** | Trabalho conjunto com DOJ | Recuperação de parte do resgate |

### 7.3 Recomendações Pós-Incidente

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│              RECOMENDAÇÕES PARA INFRAESTRUTURA CRÍTICA                           │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  1. IDENTIDADE E ACESSO                                                          │
│     ├── MFA obrigatório para TODOS os acessos remotos (VPN, RDP, SSH)           │
│     ├── Revisão trimestral de contas (desativar inativas em 30 dias)            │
│     ├── Monitoramento de credenciais em dark web                                 │
│     ├── Privileged Access Management (PAM) para contas admin                    │
│     └── Zero Trust Architecture                                                  │
│                                                                                  │
│  2. SEGMENTAÇÃO DE REDE                                                          │
│     ├── Separação rígida IT/OT (air gap ou diodo de dados)                      │
│     ├── Microsegmentação dentro de cada zona                                    │
│     ├── Monitoramento de tráfego lateral                                        │
│     └── Jump servers para acesso a sistemas críticos                            │
│                                                                                  │
│  3. DETECÇÃO E RESPOSTA                                                          │
│     ├── EDR em todos os endpoints                                               │
│     ├── NDR para detecção de exfiltração                                        │
│     ├── SIEM com correlação e UEBA                                              │
│     ├── Threat hunting proativo                                                 │
│     └── SOC 24/7 para infraestrutura crítica                                    │
│                                                                                  │
│  4. BACKUP E RECUPERAÇÃO                                                         │
│     ├── Backups imutáveis (air-gapped ou WORM)                                  │
│     ├── Teste de restauração mensal                                             │
│     ├── Múltiplas cópias em locais diferentes                                   │
│     ├── RTO/RPO definidos e testados                                            │
│     └── Playbook específico para ransomware                                     │
│                                                                                  │
│  5. GOVERNANÇA                                                                   │
│     ├── Exercícios de tabletop trimestrais                                      │
│     ├── Red team/Purple team anual                                              │
│     ├── Relacionamento pré-estabelecido com FBI/CISA                            │
│     ├── Seguro cyber adequado                                                   │
│     └── Plano de comunicação de crise                                           │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Impacto e Consequências

### 8.1 Impacto Imediato

| Categoria | Impacto |
|-----------|---------|
| **Operacional** | 6 dias de parada, 5.500 milhas de oleoduto offline |
| **Econômico** | Preço da gasolina mais alto em 6 anos ($3.04/galão) |
| **Social** | Pânico, filas em postos, 10.600 postos sem combustível |
| **Financeiro** | $4.4M pagos em resgate (≈$2.1M perda líquida) |
| **Reputacional** | Exposição pública significativa |

### 8.2 Impacto de Longo Prazo

| Categoria | Impacto |
|-----------|---------|
| **Regulatório** | TSA emitiu diretivas de segurança para oleodutos |
| **Legislativo** | Executive Order 14028, novas leis de reporte |
| **Indústria** | Aumento de investimentos em segurança em infraestrutura crítica |
| **Governamental** | Criação do Cyber Safety Review Board |
| **Conscientização** | Ransomware reconhecido como ameaça à segurança nacional |

---

## 9. Aplicação para Organizações

### 9.1 Checklist de Prevenção de Ransomware

#### Antes do Incidente
- [ ] MFA habilitado para todos os acessos remotos
- [ ] Contas VPN inativas desabilitadas
- [ ] Monitoramento de credenciais vazadas implementado
- [ ] Segmentação de rede IT/OT implementada
- [ ] EDR deployed em todos os endpoints
- [ ] NDR para detecção de exfiltração
- [ ] Backups imutáveis e testados
- [ ] Plano de IR para ransomware documentado e testado
- [ ] Seguro cyber contratado
- [ ] Contato pré-estabelecido com IR firm

#### Durante o Incidente
- [ ] **NÃO desligar sistemas** (preservar memória para forense)
- [ ] Isolar sistemas afetados da rede
- [ ] Ativar equipe de IR
- [ ] Notificar liderança executiva
- [ ] Engajar firma de IR especializada
- [ ] Notificar autoridades (FBI, CISA no Brasil: CERT.br, Polícia Federal)
- [ ] Preservar evidências
- [ ] Avaliar opções de recuperação
- [ ] Comunicar stakeholders conforme plano

#### Depois do Incidente
- [ ] Conduzir análise de causa raiz
- [ ] Documentar lições aprendidas
- [ ] Implementar melhorias identificadas
- [ ] Atualizar planos e playbooks
- [ ] Conduzir treinamento adicional
- [ ] Comunicar melhorias para stakeholders

---

## 10. Referências

### Fontes Utilizadas

- [CISA - Attack on Colonial Pipeline: What We've Learned](https://www.cisa.gov/news-events/news/attack-colonial-pipeline-what-weve-learned-what-weve-done-over-past-two-years)
- [Wikipedia - Colonial Pipeline Ransomware Attack](https://en.wikipedia.org/wiki/Colonial_Pipeline_ransomware_attack)
- [Department of Energy - Colonial Pipeline Cyber Incident](https://www.energy.gov/ceser/colonial-pipeline-cyber-incident)
- [MSSP Alert - Colonial Pipeline Investigation](https://www.msspalert.com/news/colonial-pipeline-investigation)
- [TechTarget - Colonial Pipeline Hack Explained](https://www.techtarget.com/whatis/feature/Colonial-Pipeline-hack-explained-Everything-you-need-to-know)
- [Harvard Business School - Ransomware Attack at Colonial Pipeline Company](https://www.hbs.edu/faculty/Pages/item.aspx?num=63756)
- [Cyber Defense Review - Lessons Learned](https://cyberdefensereview.army.mil/Portals/6/Documents/2021_summer_cdr/02_ReederHall_CDR_V6N3_2021.pdf)

### Frameworks de Referência
- NIST Cybersecurity Framework
- MITRE ATT&CK
- CISA Ransomware Guide

---

*Exemplo educacional baseado no caso Colonial Pipeline 2021 - MBA Cibersegurança & IA*
*Este documento demonstra como documentar e aprender com um incidente de ransomware em infraestrutura crítica.*
