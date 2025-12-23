# Relatório de Segurança de LLMs
## Caso Samsung/ChatGPT - Vazamento de Dados Corporativos (2023)

> **Classificação**: Confidencial
> **Data**: Janeiro 2025
> **Versão**: 1.0

---

# PARTE I: RESUMO EXECUTIVO

## Destinatários
- CEO, CFO, COO
- Conselho de Administração
- Comitê de Riscos e Compliance
- Diretores de Tecnologia

---

## 1. O Incidente em Contexto

### 1.1 O Que Aconteceu

Em março/abril de 2023, a **Samsung Semiconductor** liberou o uso do ChatGPT para seus engenheiros. Em menos de **20 dias**, três incidentes separados resultaram no vazamento de dados altamente confidenciais para os servidores da OpenAI.

### 1.2 Visão para o Board

```
╔════════════════════════════════════════════════════════════════════════════╗
║                    O INCIDENTE SAMSUNG EM PERSPECTIVA                      ║
╠════════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║   O QUE FOI VAZADO                                                         ║
║   ┌─────────────────────────────────────────────────────────────────────┐ ║
║   │                                                                      │ ║
║   │   1. CÓDIGO FONTE PROPRIETÁRIO                                      │ ║
║   │      Engenheiro pediu ao ChatGPT para corrigir bugs                 │ ║
║   │      → Propriedade intelectual de semicondutores exposta            │ ║
║   │                                                                      │ ║
║   │   2. SEQUÊNCIAS DE TESTES DE CHIPS                                   │ ║
║   │      Funcionário enviou padrões de teste para otimização            │ ║
║   │      → Segredos comerciais de detecção de defeitos vazados          │ ║
║   │                                                                      │ ║
║   │   3. NOTAS DE REUNIÃO CONFIDENCIAL                                   │ ║
║   │      Funcionário pediu para converter reunião em apresentação       │ ║
║   │      → Estratégias internas expostas                                │ ║
║   │                                                                      │ ║
║   └─────────────────────────────────────────────────────────────────────┘ ║
║                                                                            ║
║   POR QUE É IRREVERSÍVEL                                                   ║
║   ┌─────────────────────────────────────────────────────────────────────┐ ║
║   │                                                                      │ ║
║   │   • Dados enviados eram usados para TREINAR o modelo                │ ║
║   │   • Informações tornaram-se parte do "cérebro" do ChatGPT          │ ║
║   │   • NÃO HÁ COMO REMOVER dados de um modelo já treinado              │ ║
║   │   • Propriedade intelectual perdida PERMANENTEMENTE                 │ ║
║   │                                                                      │ ║
║   └─────────────────────────────────────────────────────────────────────┘ ║
║                                                                            ║
╚════════════════════════════════════════════════════════════════════════════╝
```

### 1.3 Números do Incidente

| Métrica | Valor | Implicação |
|---------|-------|------------|
| **Tempo até os vazamentos** | <20 dias | Velocidade alarmante de exposição |
| **Incidentes separados** | 3 | Problema sistêmico, não individual |
| **Funcionários envolvidos** | 3+ | Falta de conscientização generalizada |
| **Controles de segurança ativos** | 0 | Zero proteção implementada |
| **Dados recuperáveis** | 0% | Perda permanente |

---

## 2. Por Que Isso Importa para Sua Empresa

### 2.1 Riscos de Negócio

```
IMPACTO POTENCIAL DE VAZAMENTOS VIA IA GENERATIVA

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   PROPRIEDADE INTELECTUAL                                               │
│   ══════════════════════                                                │
│   • Patentes podem ser invalidadas se informação torna-se "pública"    │
│   • Vantagem competitiva perdida                                        │
│   • Anos de P&D desperdiçados                                           │
│   Valor em risco: BILHÕES                                               │
│                                                                         │
│   SEGREDOS COMERCIAIS                                                   │
│   ════════════════════                                                  │
│   • Processos de fabricação                                             │
│   • Algoritmos proprietários                                            │
│   • Estratégias de negócio                                              │
│   Uma vez perdidos: IRRECUPERÁVEIS                                      │
│                                                                         │
│   COMPLIANCE E REGULAMENTAÇÃO                                           │
│   ════════════════════════════                                          │
│   • Violação de LGPD (dados pessoais)                                  │
│   • Violação de contratos de confidencialidade                         │
│   • Multas potenciais: ATÉ 2% DO FATURAMENTO                           │
│                                                                         │
│   REPUTAÇÃO                                                             │
│   ══════════                                                            │
│   • Perda de confiança de clientes                                     │
│   • Cobertura negativa na mídia                                        │
│   • Dificuldade em atrair talentos                                     │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2.2 Comparação: Samsung vs. Sua Empresa

| Aspecto | Samsung | Empresa Típica |
|---------|---------|----------------|
| Política de IA antes do uso | ❌ Não existia | ❓ Provavelmente não |
| DLP para detectar vazamentos | ❌ Não existia | ❓ Pode não cobrir IA |
| Treinamento sobre riscos de IA | ❌ Nenhum | ❓ Provavelmente limitado |
| Versão Enterprise vs. Consumer | ❌ Consumer (gratuito) | ❓ Funcionários podem usar pessoal |
| Visibilidade de uso de IA | ❌ Zero | ❓ Provavelmente limitada |

**A Samsung é uma empresa Fortune 500 com recursos ilimitados. Se aconteceu com eles, pode acontecer com qualquer organização.**

---

## 3. O Que a Samsung Fez (E O Que Sua Empresa Deve Fazer)

### 3.1 Resposta da Samsung

| Ação | Efetividade | Observação |
|------|-------------|------------|
| Investigação disciplinar | ⚠️ Parcial | Trata sintoma, não causa |
| Limite de 1KB no input | ✅ Efetivo | Reduz risco mas não elimina |
| Banimento temporário de IA | ✅ Efetivo | Solução de curto prazo |
| Desenvolvimento de IA interna | ✅ Estratégico | Solução de longo prazo |
| Retorno controlado (2024) | ✅ Maduro | Com controles adequados |

### 3.2 Recomendações para Sua Empresa

```
┌─────────────────────────────────────────────────────────────────────────┐
│              PLANO DE AÇÃO PARA LIDERANÇA EXECUTIVA                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   IMEDIATO (Esta Semana)                                                │
│   ──────────────────────                                                │
│   ☐ Descobrir: Quem está usando ChatGPT/IA generativa hoje?            │
│   ☐ Comunicar: "Não envie dados confidenciais para IA pública"         │
│   ☐ Bloquear: Considerar bloqueio temporário até ter controles         │
│                                                                         │
│   CURTO PRAZO (30 dias)                                                 │
│   ─────────────────────                                                 │
│   ☐ Política: Criar política de uso de IA generativa                   │
│   ☐ Classificação: Definir que dados NUNCA podem ir para IA            │
│   ☐ Treinamento: Sessão obrigatória sobre riscos                       │
│                                                                         │
│   MÉDIO PRAZO (90 dias)                                                 │
│   ──────────────────────                                                │
│   ☐ Ferramenta: Avaliar ChatGPT Enterprise ou Azure OpenAI             │
│   ☐ DLP: Implementar detecção de dados sensíveis em prompts            │
│   ☐ Monitoramento: Dashboard de uso corporativo de IA                  │
│                                                                         │
│   LONGO PRAZO (6 meses)                                                 │
│   ─────────────────────                                                 │
│   ☐ Governança: Comitê de ética e segurança de IA                      │
│   ☐ Auditoria: Processo de aprovação para novos casos de uso           │
│   ☐ Métricas: KPIs de uso seguro de IA                                 │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Investimento vs. Risco

### 4.1 Custo de Prevenção vs. Custo de Incidente

```
ANÁLISE DE CUSTO-BENEFÍCIO

CUSTO DE PREVENÇÃO (Anual)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

┌────────────────────────────────────────────────────────────┐
│ ChatGPT Enterprise (500 usuários)      ~$150,000/ano      │
│ DLP para IA (proxy/gateway)            ~$50,000/ano       │
│ Treinamento e conscientização          ~$20,000/ano       │
│ Consultoria de política                ~$30,000 (único)   │
│ ──────────────────────────────────────────────────────────│
│ TOTAL PRIMEIRO ANO                     ~$250,000          │
│ ANOS SUBSEQUENTES                      ~$220,000/ano      │
└────────────────────────────────────────────────────────────┘

CUSTO DE INCIDENTE (Estimado)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

┌────────────────────────────────────────────────────────────┐
│ Perda de propriedade intelectual       INCALCULÁVEL       │
│ Multas LGPD (até 2% faturamento)       $X milhões         │
│ Investigação forense                   ~$200,000          │
│ Assessoria jurídica                    ~$500,000          │
│ Comunicação de crise                   ~$100,000          │
│ Dano reputacional                      INCALCULÁVEL       │
│ Perda de contratos                     VARIÁVEL           │
│ ──────────────────────────────────────────────────────────│
│ TOTAL ESTIMADO                         $1-50 MILHÕES+     │
└────────────────────────────────────────────────────────────┘

ROI DE PREVENÇÃO: 400% - 20.000%+
```

### 4.2 Decisão para o Board

| Opção | Investimento | Risco Residual | Recomendação |
|-------|--------------|----------------|--------------|
| **A: Bloquear todo uso de IA** | $0 | Zero | ❌ Perda de produtividade |
| **B: Manter status quo** | $0 | Muito Alto | ❌ Inaceitável |
| **C: Implementar controles** | ~$250K/ano | Baixo | ✅ **Recomendado** |

---

## 5. O Que Dizer aos Funcionários

### 5.1 Comunicação Recomendada

```
╔════════════════════════════════════════════════════════════════════════════╗
║                    COMUNICADO INTERNO SUGERIDO                             ║
╠════════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║   ASSUNTO: Uso de Ferramentas de IA Generativa (ChatGPT, etc.)            ║
║                                                                            ║
║   Caros colaboradores,                                                     ║
║                                                                            ║
║   Ferramentas de IA como ChatGPT podem aumentar produtividade, mas        ║
║   apresentam riscos significativos se usadas incorretamente.               ║
║                                                                            ║
║   ❌ NÃO ENVIE para ChatGPT ou similar:                                    ║
║      • Código fonte da empresa                                             ║
║      • Dados de clientes                                                   ║
║      • Informações financeiras                                             ║
║      • Estratégias de negócio                                              ║
║      • Conteúdo de reuniões confidenciais                                  ║
║      • Qualquer dado classificado como Confidencial ou Restrito           ║
║                                                                            ║
║   ✅ PODE usar para:                                                        ║
║      • Aprender sobre tecnologias públicas                                 ║
║      • Ajudar com redação de texto genérico                                ║
║      • Brainstorming de ideias não confidenciais                           ║
║                                                                            ║
║   ⚠️  Lembre-se: Tudo que você envia pode ser visto por terceiros e       ║
║      usado para treinar o modelo. Trate como informação PÚBLICA.           ║
║                                                                            ║
║   Em caso de dúvida, consulte o time de Segurança da Informação.          ║
║                                                                            ║
╚════════════════════════════════════════════════════════════════════════════╝
```

---

## 6. Métricas para Monitoramento pelo Board

### 6.1 KPIs de Segurança de IA

| KPI | Meta | Frequência | Responsável |
|-----|------|------------|-------------|
| % funcionários treinados em riscos de IA | 100% | Mensal | RH + CISO |
| Incidentes de vazamento via IA | 0 | Mensal | CISO |
| % uso de versão Enterprise vs Consumer | >95% | Mensal | TI |
| Alertas DLP relacionados a IA | Monitorar tendência | Semanal | SOC |
| Score de compliance da política de IA | >90% | Trimestral | Compliance |

---

# PARTE II: RELATÓRIO TÉCNICO

## Destinatários
- CISO (Chief Information Security Officer)
- Gerente de Segurança da Informação
- Arquitetos de Segurança
- Time de DLP/Data Protection
- DevSecOps

---

## 1. Análise Técnica do Incidente

### 1.1 Anatomia do Vazamento

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    FLUXO DO VAZAMENTO DE DADOS                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   AMBIENTE SAMSUNG                        AMBIENTE OPENAI                   │
│   ─────────────────                        ───────────────                   │
│                                                                             │
│   ┌─────────────────┐                     ┌─────────────────┐              │
│   │ Engenheiro      │                     │                 │              │
│   │ Samsung         │ ──── HTTPS ────────▶│   ChatGPT API   │              │
│   │                 │ (Código fonte)      │                 │              │
│   └─────────────────┘                     └────────┬────────┘              │
│                                                    │                        │
│   NENHUM CONTROLE:                                 │                        │
│   • Sem DLP                                        ▼                        │
│   • Sem proxy                           ┌─────────────────┐                │
│   • Sem logging                         │   OpenAI        │                │
│   • Sem classificação                   │   Training      │                │
│                                         │   Pipeline      │                │
│                                         └────────┬────────┘                │
│                                                  │                          │
│                                                  ▼                          │
│                                         ┌─────────────────┐                │
│   DADOS AGORA:                          │   Modelo GPT    │                │
│   • Parte do modelo                     │   (Futuro)      │                │
│   • Irrecuperáveis                      │                 │                │
│   • Potencialmente                      │   Código Samsung│                │
│     expostos a outros                   │   agora parte   │                │
│     usuários                            │   do "cérebro"  │                │
│                                         └─────────────────┘                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 1.2 Avaliação OWASP Top 10 for LLM Applications

O checklist completo demonstrou **0% de conformidade** com as melhores práticas:

| Categoria OWASP | Status | Criticidade | Gap |
|-----------------|--------|-------------|-----|
| **LLM01: Prompt Injection** | ❌ 0/8 | Alta | Sem sanitização de input |
| **LLM02: Sensitive Info Disclosure** | ❌ 0/8 | **Crítica** | Sem filtro de dados sensíveis |
| **LLM03: Supply Chain** | ❌ 0/5 | **Crítica** | Sem due diligence do fornecedor |
| **LLM04: Data Poisoning** | ⚠️ Reverso | Alta | Samsung "envenenou" o modelo |
| **LLM05: Output Handling** | ❌ 0/3 | Média | Sem revisão de código gerado |
| **LLM06: Excessive Agency** | ❌ 0/3 | Alta | Acesso irrestrito |
| **LLM09: Misinformation** | ❌ 0/3 | Média | Confiança excessiva no output |
| **LLM10: Unbounded Consumption** | ❌ 0/3 | Média | Sem limites de uso |

### 1.3 Falhas de Controle Identificadas

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    MATRIZ DE FALHAS DE CONTROLE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  CATEGORIA           CONTROLE ESPERADO              STATUS                  │
│  ═══════════════════════════════════════════════════════════════════════   │
│                                                                             │
│  GOVERNANÇA                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Política de uso de IA generativa                    ❌ AUSENTE      │   │
│  │ Processo de aprovação para ferramentas externas     ❌ AUSENTE      │   │
│  │ Classificação de dados para contexto de IA          ❌ AUSENTE      │   │
│  │ Treinamento obrigatório sobre riscos                ❌ AUSENTE      │   │
│  │ Termos de serviço revisados por Legal               ❌ NÃO FEITO    │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  TÉCNICOS                                                                   │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ DLP para detectar código/dados sensíveis            ❌ AUSENTE      │   │
│  │ Proxy/Gateway para LLMs com logging                 ❌ AUSENTE      │   │
│  │ Limite de tamanho de input                          ❌ AUSENTE      │   │
│  │ Alertas de dados confidenciais                      ❌ AUSENTE      │   │
│  │ Bloqueio de upload de arquivos                      ❌ AUSENTE      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  FORNECEDOR                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Versão Enterprise com controles                     ❌ NÃO USADO    │   │
│  │ Data Processing Agreement (DPA)                     ❌ AUSENTE      │   │
│  │ Opt-out de uso para treinamento                     ❌ NÃO CONFIG   │   │
│  │ Residência de dados adequada                        ❌ NÃO AVALIADO │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  MONITORAMENTO                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ Logs de interações com LLMs                         ❌ AUSENTE      │   │
│  │ Dashboard de uso de IA                              ❌ AUSENTE      │   │
│  │ Alertas de uso anômalo                              ❌ AUSENTE      │   │
│  │ Métricas de conformidade                            ❌ AUSENTE      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Arquitetura de Proteção para LLMs

### 2.1 Arquitetura Atual (Samsung Pré-Incidente)

```
                    ARQUITETURA INSEGURA (O QUE SAMSUNG TINHA)

┌─────────────────┐                           ┌─────────────────┐
│    Usuário      │ ────── DIRETO ──────────▶│   ChatGPT       │
│    (Engenheiro) │                           │   (OpenAI)      │
│                 │                           │                 │
│  • Sem controle │                           │ • Retém dados   │
│  • Sem logging  │                           │ • Usa p/ treino │
│  • Sem filtro   │                           │ • Sem garantias │
└─────────────────┘                           └─────────────────┘

                        ⚠️ NENHUMA CAMADA DE PROTEÇÃO
```

### 2.2 Arquitetura Recomendada

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ARQUITETURA DE LLM SEGURO                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐                                                           │
│   │   Usuário   │                                                           │
│   │  Corporativo│                                                           │
│   └──────┬──────┘                                                           │
│          │                                                                  │
│          │ 1. Autenticação SSO                                             │
│          ▼                                                                  │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │                         AI GATEWAY                                   │  │
│   │  ┌───────────────────────────────────────────────────────────────┐  │  │
│   │  │ CAMADA DE SEGURANÇA                                            │  │  │
│   │  │                                                                │  │  │
│   │  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐           │  │  │
│   │  │  │    DLP      │  │   Input     │  │   Rate      │           │  │  │
│   │  │  │  Scanner    │  │  Validator  │  │   Limiter   │           │  │  │
│   │  │  │             │  │             │  │             │           │  │  │
│   │  │  │ • Código    │  │ • Tamanho   │  │ • Por user  │           │  │  │
│   │  │  │ • PII       │  │ • Formato   │  │ • Por dept  │           │  │  │
│   │  │  │ • Segredos  │  │ • Tipo      │  │ • Global    │           │  │  │
│   │  │  └─────────────┘  └─────────────┘  └─────────────┘           │  │  │
│   │  │                                                                │  │  │
│   │  │  2. BLOQUEIA ou ALERTA se dados sensíveis detectados          │  │  │
│   │  └───────────────────────────────────────────────────────────────┘  │  │
│   │                                                                      │  │
│   │  ┌───────────────────────────────────────────────────────────────┐  │  │
│   │  │ LOGGING E AUDITORIA                                            │  │  │
│   │  │                                                                │  │  │
│   │  │  • Usuário      • Timestamp     • Prompt (redacted)           │  │  │
│   │  │  • Departamento • Modelo usado  • Response (redacted)         │  │  │
│   │  │  • Alertas DLP  • Tokens usados • Classificação               │  │  │
│   │  │                                                                │  │  │
│   │  │  3. LOGS enviados para SIEM                                    │  │  │
│   │  └───────────────────────────────────────────────────────────────┘  │  │
│   └──────────────────────────────┬──────────────────────────────────────┘  │
│                                  │                                         │
│                                  │ 4. Request sanitizado                   │
│                                  ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │                    LLM PROVIDER (Enterprise)                         │  │
│   │                                                                      │  │
│   │  OPÇÕES RECOMENDADAS:                                                │  │
│   │                                                                      │  │
│   │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐     │  │
│   │  │ Azure OpenAI    │  │ ChatGPT         │  │ AWS Bedrock     │     │  │
│   │  │                 │  │ Enterprise      │  │                 │     │  │
│   │  │ • Dados não     │  │ • Opt-out de    │  │ • Dados na AWS  │     │  │
│   │  │   usados p/     │  │   treinamento   │  │ • Controles IAM │     │  │
│   │  │   treinamento   │  │ • SSO/SCIM      │  │ • VPC endpoint  │     │  │
│   │  │ • Region BR     │  │ • Admin console │  │ • Logging       │     │  │
│   │  │ • Compliance    │  │ • DPA incluso   │  │                 │     │  │
│   │  └─────────────────┘  └─────────────────┘  └─────────────────┘     │  │
│   │                                                                      │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Implementação de Controles

### 3.1 DLP para IA Generativa

```yaml
# Exemplo: Configuração de DLP para detectar código fonte
dlp_rules:
  - name: "Source Code Detection"
    description: "Bloqueia envio de código proprietário para LLMs"
    enabled: true
    priority: 1
    action: block_and_alert

    patterns:
      # Detectar código Samsung-específico
      - type: regex
        pattern: "(samsung|semiconductor|chip_test|fab_process)"
        case_insensitive: true

      # Detectar estruturas de código
      - type: regex
        pattern: "(class\s+\w+|def\s+\w+|function\s+\w+|#include|import\s+\w+)"

      # Detectar arquivos de código colados
      - type: file_extension
        extensions: [".c", ".cpp", ".h", ".py", ".java", ".js", ".ts"]

      # Detectar comentários de copyright
      - type: regex
        pattern: "(Copyright|Proprietary|Confidential|Trade Secret)"
        case_insensitive: true

    alert:
      severity: critical
      notify:
        - security-team@company.com
        - user-manager

    log:
      include_content: false  # Não logar o conteúdo sensível
      include_metadata: true

  - name: "PII Detection"
    description: "Detecta dados pessoais"
    enabled: true
    priority: 2
    action: warn_and_log

    patterns:
      - type: pii
        categories: [cpf, email, phone, credit_card, address]
```

### 3.2 Proxy/Gateway para LLMs

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    CONFIGURAÇÃO DO AI GATEWAY                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  COMPONENTES NECESSÁRIOS:                                                   │
│                                                                             │
│  1. PROXY REVERSO                                                           │
│     ┌─────────────────────────────────────────────────────────────────┐    │
│     │ Opções:                                                          │    │
│     │ • Kong Gateway + AI Plugin                                       │    │
│     │ • AWS API Gateway + Lambda                                       │    │
│     │ • Azure API Management                                           │    │
│     │ • Cloudflare AI Gateway                                          │    │
│     │ • Portkey.ai / LiteLLM / Helicone (especializados)              │    │
│     └─────────────────────────────────────────────────────────────────┘    │
│                                                                             │
│  2. MOTOR DE DLP                                                            │
│     ┌─────────────────────────────────────────────────────────────────┐    │
│     │ Opções:                                                          │    │
│     │ • Microsoft Purview (integração nativa)                          │    │
│     │ • Google Cloud DLP API                                           │    │
│     │ • Symantec DLP                                                   │    │
│     │ • Custom ML classifier para código                               │    │
│     └─────────────────────────────────────────────────────────────────┘    │
│                                                                             │
│  3. LOGGING E SIEM                                                          │
│     ┌─────────────────────────────────────────────────────────────────┐    │
│     │ Dados a capturar:                                                │    │
│     │ • user_id, department, timestamp                                 │    │
│     │ • model_used, tokens_in, tokens_out                              │    │
│     │ • dlp_alerts, classification                                     │    │
│     │ • prompt_hash (não o conteúdo)                                   │    │
│     │                                                                  │    │
│     │ Enviar para: Splunk, ELK, Datadog, etc.                         │    │
│     └─────────────────────────────────────────────────────────────────┘    │
│                                                                             │
│  4. RATE LIMITING                                                           │
│     ┌─────────────────────────────────────────────────────────────────┐    │
│     │ Limites recomendados:                                            │    │
│     │ • Por usuário: 100 requests/hora                                 │    │
│     │ • Por departamento: 1000 requests/hora                           │    │
│     │ • Tamanho de input: 2KB (ajustar conforme uso)                   │    │
│     │ • Tamanho de output: 4KB                                         │    │
│     └─────────────────────────────────────────────────────────────────┘    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 3.3 Classificação de Dados para Contexto de IA

| Classificação | Pode Enviar para LLM Público? | Pode Enviar para LLM Enterprise? | Exemplos |
|---------------|-------------------------------|----------------------------------|----------|
| **Público** | ✅ Sim | ✅ Sim | Documentação pública, tutoriais |
| **Interno** | ⚠️ Com cuidado | ✅ Sim | Processos internos genéricos |
| **Confidencial** | ❌ **NÃO** | ⚠️ Com aprovação | Estratégias, roadmaps |
| **Restrito** | ❌ **NUNCA** | ❌ **NÃO** | Código fonte, segredos, PII |
| **PII/Regulado** | ❌ **NUNCA** | ❌ Requer DPA | Dados de clientes, LGPD |

---

## 4. Comparativo de Soluções Enterprise

### 4.1 ChatGPT Consumer vs Enterprise vs Azure OpenAI

| Aspecto | ChatGPT Free/Plus | ChatGPT Enterprise | Azure OpenAI |
|---------|-------------------|-------------------|--------------|
| **Uso para treinamento** | ⚠️ Sim (opt-out disponível) | ❌ Não | ❌ Não |
| **SSO/SAML** | ❌ Não | ✅ Sim | ✅ Sim (Azure AD) |
| **DPA incluso** | ❌ Não | ✅ Sim | ✅ Sim |
| **Admin console** | ❌ Não | ✅ Sim | ✅ Sim |
| **Region BR disponível** | ❌ Não | ❌ Não | ✅ Sim |
| **SOC 2 Type II** | ❌ Não | ✅ Sim | ✅ Sim |
| **HIPAA disponível** | ❌ Não | ✅ BAA disponível | ✅ BAA disponível |
| **Controle de retenção** | ❌ 30 dias | ✅ Customizável | ✅ Customizável |
| **API para integração** | ⚠️ Limitada | ✅ Full API | ✅ Full API |
| **Preço** | $0-20/mês/user | ~$60/mês/user | Pay-as-you-go |

### 4.2 Recomendação

```
╔════════════════════════════════════════════════════════════════════════════╗
║                    RECOMENDAÇÃO DE SOLUÇÃO                                 ║
╠════════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  PARA EMPRESAS COM DADOS SENSÍVEIS:                                        ║
║                                                                            ║
║  🥇 PRIMEIRA OPÇÃO: Azure OpenAI Service                                   ║
║     • Dados ficam na sua subscription Azure                                ║
║     • Não usados para treinamento                                          ║
║     • Região Brasil disponível (baixa latência, residência de dados)       ║
║     • Integração com Azure AD, Purview DLP, Defender                       ║
║     • Compliance: SOC 2, ISO 27001, LGPD                                   ║
║                                                                            ║
║  🥈 SEGUNDA OPÇÃO: ChatGPT Enterprise                                       ║
║     • Dados não usados para treinamento                                    ║
║     • Interface familiar para usuários                                     ║
║     • Admin console para gerenciamento                                     ║
║     • SSO/SAML suportado                                                   ║
║                                                                            ║
║  🥉 TERCEIRA OPÇÃO: AWS Bedrock                                             ║
║     • Multi-model (Claude, Llama, Titan)                                   ║
║     • Dados na sua conta AWS                                               ║
║     • VPC endpoint disponível                                              ║
║     • Pay-as-you-go                                                        ║
║                                                                            ║
║  ❌ NÃO RECOMENDADO: ChatGPT Free/Plus para uso corporativo                ║
║     • Dados podem ser usados para treinamento                              ║
║     • Sem controles administrativos                                        ║
║     • Sem garantias de confidencialidade                                   ║
║                                                                            ║
╚════════════════════════════════════════════════════════════════════════════╝
```

---

## 5. Política de Uso de IA Generativa

### 5.1 Template de Política

```
┌─────────────────────────────────────────────────────────────────────────────┐
│            POLÍTICA DE USO DE INTELIGÊNCIA ARTIFICIAL GENERATIVA            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  1. ESCOPO                                                                  │
│     Esta política aplica-se a todos os colaboradores que utilizem           │
│     ferramentas de IA generativa (ChatGPT, Claude, Gemini, Copilot, etc.)  │
│     para atividades relacionadas ao trabalho.                               │
│                                                                             │
│  2. FERRAMENTAS APROVADAS                                                   │
│     ☐ [Ferramenta Enterprise aprovada]                                     │
│     ☐ Microsoft Copilot (se licenciado)                                    │
│     ☐ GitHub Copilot (para desenvolvedores, se aprovado)                   │
│                                                                             │
│  3. FERRAMENTAS PROIBIDAS                                                   │
│     ☒ ChatGPT Free/Plus (versão consumer)                                  │
│     ☒ Qualquer LLM público sem aprovação de Segurança                      │
│     ☒ LLMs locais/open source sem avaliação                                │
│                                                                             │
│  4. DADOS PROIBIDOS (NUNCA ENVIAR)                                          │
│     ☒ Código fonte proprietário                                            │
│     ☒ Dados de clientes (PII)                                              │
│     ☒ Informações financeiras confidenciais                                │
│     ☒ Estratégias de negócio                                               │
│     ☒ Segredos comerciais                                                  │
│     ☒ Credenciais (senhas, tokens, chaves)                                 │
│     ☒ Conteúdo de reuniões confidenciais                                   │
│     ☒ Qualquer dado classificado como Confidencial ou Restrito             │
│                                                                             │
│  5. DADOS PERMITIDOS                                                        │
│     ☐ Informações públicas                                                 │
│     ☐ Perguntas técnicas genéricas                                         │
│     ☐ Ajuda com redação de texto não confidencial                          │
│     ☐ Aprendizado sobre tecnologias públicas                               │
│                                                                             │
│  6. OBRIGAÇÕES DO COLABORADOR                                               │
│     • Completar treinamento obrigatório antes do uso                       │
│     • Revisar todo output antes de usar em produção                        │
│     • Reportar incidentes de vazamento imediatamente                       │
│     • Não usar contas pessoais para trabalho                               │
│                                                                             │
│  7. CONSEQUÊNCIAS                                                           │
│     Violações podem resultar em:                                            │
│     • Advertência formal                                                   │
│     • Suspensão de acesso                                                  │
│     • Medidas disciplinares                                                │
│     • Demissão por justa causa (casos graves)                              │
│                                                                             │
│  8. REVISÃO                                                                 │
│     Esta política será revisada trimestralmente pelo Comitê de IA.         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 6. Métricas e Monitoramento

### 6.1 Dashboard de Uso de IA

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    DASHBOARD DE SEGURANÇA DE IA                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   USO POR DEPARTAMENTO (Últimos 30 dias)                                   │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │ Engenharia     ████████████████████████████████████  45%           │  │
│   │ Marketing      ██████████████████                    25%           │  │
│   │ Vendas         ████████████                          15%           │  │
│   │ RH             ██████                                 8%           │  │
│   │ Outros         ████                                   7%           │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│   ALERTAS DLP (Últimos 30 dias)                                            │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │ Código fonte detectado      ████████  12 alertas     ⚠️ ATENÇÃO    │  │
│   │ PII detectado               ████       5 alertas     🟡 MODERADO   │  │
│   │ Dados financeiros           ██         3 alertas     🟡 MODERADO   │  │
│   │ Credenciais                 █          1 alerta      🔴 CRÍTICO    │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│   COMPLIANCE                                                                │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │ Treinamento completo        ████████████████████████  92%          │  │
│   │ Política assinada           █████████████████████████ 98%          │  │
│   │ Uso de ferramenta aprovada  ███████████████████████   88%  ⚠️     │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│   VOLUME DE USO                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │ Total de requests:          125,000                                │  │
│   │ Tokens consumidos:          45M                                    │  │
│   │ Usuários ativos:            450                                    │  │
│   │ Requests bloqueados:        21 (0.02%)                             │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 6.2 Alertas Recomendados

| Alerta | Trigger | Severidade | Resposta |
|--------|---------|------------|----------|
| Código fonte detectado | DLP pattern match | Crítica | Bloquear + investigar |
| PII em prompt | DLP pattern match | Alta | Bloquear + notificar |
| Credencial detectada | Regex match | Crítica | Bloquear + rotacionar |
| Uso de ferramenta não aprovada | URL/app detection | Média | Alertar usuário + manager |
| Volume anômalo | >3x baseline | Média | Investigar |
| Usuário sem treinamento | IAM check | Baixa | Bloquear até completar |

---

## 7. Conclusão e Próximos Passos

### 7.1 Lições do Caso Samsung

1. **Política ANTES da tecnologia**: Nunca libere ferramentas de IA sem controles
2. **DLP é essencial**: Detectar dados sensíveis antes que saiam
3. **Consumer ≠ Enterprise**: Versões gratuitas não têm proteções adequadas
4. **Treinamento obrigatório**: Funcionários precisam entender os riscos
5. **Dados são irrecuperáveis**: Uma vez enviados, não há como voltar

### 7.2 Checklist de Implementação

| Fase | Ação | Prazo | Status |
|------|------|-------|--------|
| **Emergência** | Comunicar riscos aos funcionários | Imediato | ☐ |
| **Emergência** | Identificar uso atual de IA | 1 semana | ☐ |
| **Curto Prazo** | Criar política de uso de IA | 2 semanas | ☐ |
| **Curto Prazo** | Avaliar soluções Enterprise | 3 semanas | ☐ |
| **Médio Prazo** | Implementar AI Gateway + DLP | 6 semanas | ☐ |
| **Médio Prazo** | Treinamento obrigatório | 8 semanas | ☐ |
| **Longo Prazo** | Dashboard de monitoramento | 12 semanas | ☐ |
| **Longo Prazo** | Comitê de governança de IA | 16 semanas | ☐ |

---

*Relatório elaborado para fins educacionais - MBA Cibersegurança & IA*
