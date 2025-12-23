# AI Governance Policy - TechCorp Brasil
## Política de Governança de Inteligência Artificial (Exemplo Baseado em Melhores Práticas)

> **Nota**: Este documento é um exemplo educacional baseado em frameworks públicos de IA responsável (Microsoft, Google, NIST) e requisitos regulatórios brasileiros. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## Informações do Documento

| Campo | Valor |
|-------|-------|
| **Organização** | TechCorp Brasil S.A. (Exemplo Fictício) |
| **Versão** | 1.0 |
| **Data de Aprovação** | Janeiro 2025 |
| **Próxima Revisão** | Janeiro 2026 |
| **Proprietário** | Chief AI Officer (CAIO) |
| **Classificação** | Interno |

---

## 1. Introdução

### 1.1 Propósito

Esta política estabelece os princípios, diretrizes e controles para o desenvolvimento, implantação e uso responsável de sistemas de Inteligência Artificial (IA) na TechCorp Brasil, garantindo que tais sistemas sejam seguros, éticos, transparentes e alinhados com:

- Valores organizacionais
- Legislação brasileira (LGPD, Marco Civil, futuro Marco Legal de IA)
- Regulamentações setoriais aplicáveis
- Melhores práticas internacionais (NIST AI RMF, ISO 42001)

### 1.2 Escopo

Esta política se aplica a:

| Categoria | Incluído |
|-----------|----------|
| Sistemas de IA desenvolvidos internamente | ✅ |
| Sistemas de IA adquiridos de terceiros | ✅ |
| APIs e serviços de IA externos (OpenAI, Azure, Google) | ✅ |
| Large Language Models (LLMs) | ✅ |
| Modelos de Machine Learning (ML) | ✅ |
| Automações baseadas em regras (não-IA) | ❌ |
| Analytics tradicional | ❌ |

**Audiência**: Todos os colaboradores, contratados e terceiros que desenvolvem, implementam ou utilizam sistemas de IA.

### 1.3 Definições

| Termo | Definição |
|-------|-----------|
| **Inteligência Artificial (IA)** | Sistemas computacionais capazes de realizar tarefas que tipicamente requerem inteligência humana, incluindo aprendizado, raciocínio e tomada de decisão |
| **Machine Learning (ML)** | Subconjunto de IA onde sistemas aprendem padrões a partir de dados |
| **Large Language Model (LLM)** | Modelos de IA treinados em grandes volumes de texto para gerar linguagem natural |
| **Sistema de IA de Alto Risco** | Sistema cujo uso pode impactar significativamente direitos fundamentais, saúde, segurança ou bem-estar de indivíduos |
| **Explicabilidade (XAI)** | Capacidade de explicar como um sistema de IA chegou a uma decisão ou output |
| **Viés (Bias)** | Padrões sistemáticos nos dados ou algoritmos que geram resultados injustos ou discriminatórios |
| **Data Poisoning** | Ataque onde dados maliciosos são inseridos no treinamento para comprometer o modelo |
| **Prompt Injection** | Ataque onde inputs maliciosos manipulam o comportamento de um LLM |

---

## 2. Princípios Fundamentais

### 2.1 Os Seis Princípios de IA Responsável da TechCorp

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    PRINCÍPIOS DE IA RESPONSÁVEL - TECHCORP                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│         ┌─────────────┐         ┌─────────────┐         ┌─────────────┐         │
│         │  SEGURANÇA  │         │TRANSPARÊNCIA│         │   JUSTIÇA   │         │
│         │  & PROTEÇÃO │         │& EXPLICABIL.│         │ & EQUIDADE  │         │
│         │             │         │             │         │             │         │
│         │ Sistemas    │         │ Decisões    │         │ IA não deve │         │
│         │ seguros,    │         │ compreensí- │         │ discriminar │         │
│         │ resilientes │         │ veis        │         │ ou perpetuar│         │
│         │ e protegidos│         │ e auditáveis│         │ vieses      │         │
│         └─────────────┘         └─────────────┘         └─────────────┘         │
│                                                                                  │
│         ┌─────────────┐         ┌─────────────┐         ┌─────────────┐         │
│         │ PRIVACIDADE │         │ACCOUNTABILITY│        │ BENEFICÊNCIA│         │
│         │  & DADOS    │         │& GOVERNANÇA │         │  & IMPACTO  │         │
│         │             │         │             │         │             │         │
│         │ Proteção de │         │ Responsabi- │         │ IA deve     │         │
│         │ dados       │         │ lidades     │         │ gerar valor │         │
│         │ pessoais e  │         │ claramente  │         │ positivo    │         │
│         │ conformidade│         │ definidas   │         │ para todos  │         │
│         └─────────────┘         └─────────────┘         └─────────────┘         │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │              SUPERVISÃO HUMANA (Human-in-the-Loop)                         │  │
│  │                                                                            │  │
│  │   Humanos mantêm controle e capacidade de override sobre decisões         │  │
│  │   críticas de IA. Nenhuma decisão que afete significativamente            │  │
│  │   indivíduos é totalmente automatizada sem revisão humana.                │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 2.2 Detalhamento dos Princípios

| Princípio | Compromissos | Métricas |
|-----------|--------------|----------|
| **Segurança** | Testes rigorosos, monitoramento contínuo, resposta a incidentes, proteção contra ataques adversariais | Zero incidentes críticos de segurança de IA |
| **Transparência** | Documentação completa (Model Cards), explicabilidade, comunicação clara aos usuários | 100% dos modelos com Model Card |
| **Justiça** | Testes de fairness, auditorias de viés, correção proativa | Disparidade < 5% entre grupos demográficos |
| **Privacidade** | LGPD compliance, minimização de dados, privacy by design | 100% conformidade LGPD |
| **Accountability** | Papéis claros, trilhas de auditoria, governança robusta | Rastreabilidade completa de decisões |
| **Beneficência** | Avaliação de impacto, alinhamento com valores, benefício social | Net positive impact assessment |

---

## 3. Estrutura de Governança

### 3.1 Organograma de Governança de IA

```
                        ┌─────────────────────────┐
                        │    Conselho de Admin.   │
                        │  (Supervisão Executiva) │
                        └───────────┬─────────────┘
                                    │
                        ┌───────────▼─────────────┐
                        │    Comitê de Ética      │
                        │    e IA Responsável     │
                        │    (AI Ethics Board)    │
                        └───────────┬─────────────┘
                                    │
         ┌──────────────────────────┼──────────────────────────┐
         │                          │                          │
         ▼                          ▼                          ▼
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│      CAIO       │      │      CISO       │      │       DPO       │
│  (AI Officer)   │      │   (Segurança)   │      │  (Privacidade)  │
│                 │      │                 │      │                 │
│ • Estratégia IA │      │ • Segurança IA  │      │ • LGPD/DPIA     │
│ • Governança    │      │ • Red Team IA   │      │ • Direitos      │
│ • Ética         │      │ • Incidentes    │      │ • Consentimento │
└────────┬────────┘      └────────┬────────┘      └────────┬────────┘
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│   AI/ML Team    │      │  Security Team  │      │   Legal Team    │
│                 │      │                 │      │                 │
│ • Data Science  │      │ • AppSec        │      │ • Contratos     │
│ • MLOps         │      │ • MLSecOps      │      │ • Regulatório   │
│ • AI Engineers  │      │ • SOC           │      │ • Compliance    │
└─────────────────┘      └─────────────────┘      └─────────────────┘
```

### 3.2 Comitê de Ética e IA Responsável

| Responsabilidade | Frequência |
|-----------------|------------|
| Revisar e aprovar projetos de IA de alto risco | Por projeto |
| Avaliar conformidade com princípios éticos | Trimestral |
| Revisar incidentes relacionados a IA | Conforme necessário |
| Atualizar políticas e diretrizes | Anual |
| Acompanhar evolução regulatória | Contínuo |
| Aprovar uso de LLMs externos | Por solicitação |

**Composição**:
- CAIO (Presidente)
- CISO
- DPO
- Head of Engineering
- Head of Legal
- Representante de RH
- Representante de Compliance
- Especialista externo em ética (consultivo)

### 3.3 Matriz RACI para Governança de IA

| Atividade | CAIO | CISO | DPO | AI Team | Business |
|-----------|------|------|-----|---------|----------|
| Definir estratégia de IA | **A** | C | C | R | C |
| Aprovar projetos alto risco | **A** | R | R | I | C |
| Avaliar segurança de IA | C | **A** | I | R | I |
| Conduzir DPIA | C | C | **A** | R | C |
| Desenvolver modelos | C | C | I | **A/R** | C |
| Monitorar modelos em produção | C | R | I | **A** | I |
| Responder a incidentes de IA | R | **A** | C | R | I |
| Treinar funcionários | R | R | R | C | **A** |

*R=Responsible, A=Accountable, C=Consulted, I=Informed*

---

## 4. Classificação de Risco de Sistemas de IA

### 4.1 Matriz de Classificação

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    CLASSIFICAÇÃO DE RISCO DE SISTEMAS DE IA                      │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  Impacto em Indivíduos                                                           │
│        │                                                                         │
│  Alto  │   MÉDIO    │    ALTO     │   CRÍTICO                                   │
│        │            │             │                                              │
│  Médio │   BAIXO    │    MÉDIO    │    ALTO                                     │
│        │            │             │                                              │
│  Baixo │   BAIXO    │    BAIXO    │    MÉDIO                                    │
│        │            │             │                                              │
│        └────────────┴─────────────┴────────────▶                                │
│              Baixa       Média        Alta                                       │
│                    Escala de Uso/Automação                                       │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Níveis de Risco e Exemplos

| Nível | Descrição | Exemplos na TechCorp | Controles Obrigatórios |
|-------|-----------|---------------------|----------------------|
| **Crítico** | Decisões automatizadas que afetam significativamente direitos ou bem-estar | Scoring de crédito, triagem de RH, detecção de fraude com bloqueio automático | DPIA, Comitê, Explicabilidade, Human Override, Auditoria Externa |
| **Alto** | Impacto significativo em operações ou clientes | Recomendações de produtos, chatbots de atendimento, precificação dinâmica | DPIA, Model Card, Fairness Testing, Monitoramento |
| **Médio** | Impacto moderado, decisões assistivas | Classificação de tickets, summarização, detecção de anomalias | Model Card, Testes, Monitoramento |
| **Baixo** | Impacto mínimo, uso interno | Automação de tarefas internas, PoCs, experimentos | Documentação básica |

### 4.3 Uso Proibido de IA

É **expressamente proibido** usar IA para:

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║                           USO PROIBIDO DE IA                                      ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  ❌ Decisões automatizadas sobre indivíduos sem possibilidade de revisão humana  ║
║                                                                                   ║
║  ❌ Vigilância ou monitoramento invasivo de funcionários                         ║
║                                                                                   ║
║  ❌ Geração de deepfakes, desinformação ou conteúdo enganoso                     ║
║                                                                                   ║
║  ❌ Discriminação baseada em atributos protegidos (raça, gênero, religião, etc.) ║
║                                                                                   ║
║  ❌ Manipulação psicológica ou exploração de vulnerabilidades                    ║
║                                                                                   ║
║  ❌ Sistemas de pontuação social ou citizen scoring                              ║
║                                                                                   ║
║  ❌ Reconhecimento facial para vigilância em massa                               ║
║                                                                                   ║
║  ❌ Armas autônomas ou sistemas letais                                           ║
║                                                                                   ║
║  ❌ Qualquer atividade ilegal ou antiética                                       ║
║                                                                                   ║
║  ❌ Contornar controles de segurança                                             ║
║                                                                                   ║
║  Violações resultarão em medidas disciplinares, incluindo demissão.              ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## 5. Ciclo de Vida de Sistemas de IA

### 5.1 Framework de Desenvolvimento Seguro (AI-DevSecOps)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    CICLO DE VIDA AI-DEVSECOPS                                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   IDEAÇÃO         DESIGN          BUILD           DEPLOY         OPERATE        │
│   ────────        ──────          ─────           ──────         ───────        │
│                                                                                  │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐       │
│  │Business │    │Risk     │    │Secure   │    │Approval │    │Monitor  │       │
│  │Case     │───▶│Assess   │───▶│Develop  │───▶│Gate     │───▶│& Improve│       │
│  │         │    │         │    │         │    │         │    │         │       │
│  └────┬────┘    └────┬────┘    └────┬────┘    └────┬────┘    └────┬────┘       │
│       │              │              │              │              │             │
│       ▼              ▼              ▼              ▼              ▼             │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐       │
│  │• Use    │    │• DPIA   │    │• Data   │    │• Model  │    │• Drift  │       │
│  │  Case   │    │• Ethics │    │  Valid. │    │  Card   │    │  Detect │       │
│  │• Risk   │    │  Review │    │• Fair-  │    │• Comitê │    │• Fairness│      │
│  │  Class  │    │• Archi- │    │  ness   │    │  (se    │    │• Retrain│       │
│  │• Sponsor│    │  tecture│    │• Security│   │  crítico│    │• Audit  │       │
│  │• Approve│    │• Data   │    │  Tests  │    │• Deploy │    │• Incident│      │
│  └─────────┘    │  Require│    │• Explain│    └─────────┘    └─────────┘       │
│                 └─────────┘    └─────────┘                                       │
│                                                                                  │
│  GATE 1         GATE 2         GATE 3          GATE 4         CONTÍNUO          │
│  Aprovação      DPIA +         Security +      Produção       Monitoramento     │
│  Inicial        Ethics         Fairness        Release        & Melhoria        │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 5.2 Requisitos por Gate

#### Gate 1: Ideação → Design
| Requisito | Baixo | Médio | Alto | Crítico |
|-----------|-------|-------|------|---------|
| Business case documentado | ✅ | ✅ | ✅ | ✅ |
| Classificação de risco | ✅ | ✅ | ✅ | ✅ |
| Sponsor definido | ✅ | ✅ | ✅ | ✅ |
| Aprovação CAIO | ❌ | ❌ | ✅ | ✅ |
| Aprovação Comitê | ❌ | ❌ | ❌ | ✅ |

#### Gate 2: Design → Build
| Requisito | Baixo | Médio | Alto | Crítico |
|-----------|-------|-------|------|---------|
| Arquitetura documentada | ✅ | ✅ | ✅ | ✅ |
| Requisitos de dados | ✅ | ✅ | ✅ | ✅ |
| DPIA | ❌ | ❌ | ✅ | ✅ |
| Revisão ética | ❌ | ❌ | ✅ | ✅ |
| Security architecture | ❌ | ✅ | ✅ | ✅ |

#### Gate 3: Build → Deploy
| Requisito | Baixo | Médio | Alto | Crítico |
|-----------|-------|-------|------|---------|
| Testes funcionais | ✅ | ✅ | ✅ | ✅ |
| Testes de segurança | ❌ | ✅ | ✅ | ✅ |
| Testes de fairness | ❌ | ❌ | ✅ | ✅ |
| Adversarial testing | ❌ | ❌ | ✅ | ✅ |
| Model Card | ❌ | ✅ | ✅ | ✅ |
| Explicabilidade validada | ❌ | ❌ | ✅ | ✅ |

#### Gate 4: Deploy → Operate
| Requisito | Baixo | Médio | Alto | Crítico |
|-----------|-------|-------|------|---------|
| Monitoramento configurado | ✅ | ✅ | ✅ | ✅ |
| Plano de rollback | ❌ | ✅ | ✅ | ✅ |
| Treinamento de usuários | ❌ | ❌ | ✅ | ✅ |
| Aprovação final Comitê | ❌ | ❌ | ❌ | ✅ |
| Human override configurado | ❌ | ❌ | ✅ | ✅ |

---

## 6. Uso de LLMs e IA Generativa

### 6.1 Ferramentas Aprovadas

| Ferramenta | Status | Uso Permitido | Restrições |
|------------|--------|---------------|------------|
| **Azure OpenAI Service** | ✅ Aprovado | Desenvolvimento, produção | Dados confidenciais permitidos com controles |
| **GitHub Copilot Enterprise** | ✅ Aprovado | Desenvolvimento de código | Não usar para código de segurança crítica |
| **ChatGPT Enterprise** | ✅ Aprovado | Produtividade geral | Sem dados de clientes ou PII |
| **ChatGPT (consumer)** | ⚠️ Restrito | Pesquisa pessoal apenas | **PROIBIDO dados corporativos** |
| **Claude (API)** | ✅ Aprovado | Desenvolvimento | Via API com controles |
| **Midjourney/DALL-E** | ⚠️ Restrito | Marketing apenas | Aprovação prévia necessária |
| **Modelos open source** | 📋 Caso a caso | Desenvolvimento | Avaliação de segurança obrigatória |

### 6.2 Política de Dados para LLMs

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║                    CLASSIFICAÇÃO DE DADOS PARA USO EM LLMs                        ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  ✅ PERMITIDO (com ferramentas aprovadas):                                        ║
║     • Informações públicas                                                        ║
║     • Documentação técnica genérica                                               ║
║     • Código não-proprietário                                                     ║
║     • Dados de teste sintéticos                                                   ║
║                                                                                   ║
║  ⚠️  REQUER APROVAÇÃO:                                                            ║
║     • Código proprietário                                                         ║
║     • Documentos internos                                                         ║
║     • Informações de projetos                                                     ║
║                                                                                   ║
║  ❌ PROIBIDO (mesmo em ferramentas aprovadas):                                    ║
║     • PII de clientes (CPF, cartão, biometria)                                   ║
║     • Dados financeiros de clientes                                               ║
║     • Credenciais, senhas, API keys                                              ║
║     • Segredos comerciais                                                         ║
║     • Informações de M&A não públicas                                            ║
║     • Dados de saúde                                                              ║
║     • Comunicações privilegiadas (legal)                                          ║
║                                                                                   ║
║  LEMBRE-SE: Quando em dúvida, NÃO envie. Consulte o time de segurança.           ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

### 6.3 Controles Técnicos para LLMs

| Controle | Implementação | Status |
|----------|---------------|--------|
| **DLP Gateway** | Proxy que analisa todos os prompts antes de enviar | ✅ Produção |
| **Classificação automática** | ML que detecta dados sensíveis em prompts | ✅ Produção |
| **Logging centralizado** | Todas as interações logadas (sem PII) | ✅ Produção |
| **Limite de tokens** | Máximo 8K tokens por request | ✅ Configurado |
| **Guardrails** | Filtros de input/output | ✅ Azure, em progresso para outros |
| **Monitoramento de uso** | Dashboard de uso por usuário/departamento | ✅ Produção |

---

## 7. Fairness e Não-Discriminação

### 7.1 Atributos Protegidos (Brasil)

De acordo com a legislação brasileira (Constituição, CLT, LGPD), os seguintes atributos requerem atenção especial:

| Atributo | Base Legal | Monitoramento |
|----------|------------|---------------|
| Raça e cor | CF Art. 5º, Lei 7.716/89 | Obrigatório |
| Gênero | CF Art. 5º, CLT | Obrigatório |
| Idade | CF Art. 7º, Estatuto do Idoso | Obrigatório |
| Deficiência | Lei 13.146/2015 | Obrigatório |
| Religião | CF Art. 5º | Recomendado |
| Orientação sexual | STF ADO 26 | Recomendado |
| Origem geográfica | CF Art. 5º | Recomendado |
| Situação familiar | CLT Art. 391 | Recomendado |

### 7.2 Métricas de Fairness Obrigatórias

Para sistemas de Alto Risco e Críticos:

| Métrica | Definição | Threshold |
|---------|-----------|-----------|
| **Demographic Parity** | Taxa de resultado positivo igual entre grupos | Diferença < 5% |
| **Equalized Odds** | TPR e FPR similares entre grupos | Diferença < 5% |
| **Disparate Impact Ratio** | Ratio de taxas de seleção | Entre 0.8 e 1.25 |

### 7.3 Processo de Auditoria de Fairness

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    PROCESSO DE AUDITORIA DE FAIRNESS                             │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  1. PRÉ-DEPLOY                                                                   │
│     ├── Definir grupos demográficos relevantes                                  │
│     ├── Escolher métricas de fairness apropriadas                               │
│     ├── Estabelecer thresholds aceitáveis                                       │
│     └── Executar testes em dataset de validação                                 │
│                                                                                  │
│  2. DEPLOY                                                                       │
│     ├── Verificar fairness metrics nos primeiros 30 dias                        │
│     ├── Comparar com baseline pré-deploy                                        │
│     └── Documentar resultados                                                   │
│                                                                                  │
│  3. MONITORAMENTO CONTÍNUO                                                       │
│     ├── Dashboard de fairness atualizado diariamente                            │
│     ├── Alertas automáticos se threshold violado                                │
│     └── Revisão mensal de métricas                                              │
│                                                                                  │
│  4. AUDITORIA PERIÓDICA                                                          │
│     ├── Trimestral: Revisão interna                                             │
│     ├── Anual: Auditoria externa (para críticos)                                │
│     └── Documentação para compliance                                            │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Segurança de IA

### 8.1 Ameaças Específicas de IA

| Ameaça | Descrição | Controle |
|--------|-----------|----------|
| **Data Poisoning** | Corromper dados de treinamento | Validação de dados, proveniência |
| **Model Extraction** | Roubar modelo via API | Rate limiting, watermarking |
| **Adversarial Attacks** | Inputs crafted para enganar modelo | Adversarial training, input validation |
| **Prompt Injection** | Manipular LLMs via prompts maliciosos | Guardrails, input sanitization |
| **Model Inversion** | Extrair dados de treino do modelo | Differential privacy, output limiting |
| **Membership Inference** | Descobrir se dados específicos foram usados | DP-SGD, federated learning |

### 8.2 Requisitos de Segurança por Classificação

| Controle | Baixo | Médio | Alto | Crítico |
|----------|-------|-------|------|---------|
| Criptografia em repouso | ✅ | ✅ | ✅ | ✅ |
| Criptografia em trânsito | ✅ | ✅ | ✅ | ✅ |
| Rate Limiting | ❌ | ✅ | ✅ | ✅ |
| Input Validation | ❌ | ✅ | ✅ | ✅ |
| Output Filtering | ❌ | ❌ | ✅ | ✅ |
| Adversarial Testing | ❌ | ❌ | ✅ | ✅ |
| Red Team | ❌ | ❌ | ❌ | ✅ |
| Model Signing | ❌ | ✅ | ✅ | ✅ |
| Monitoramento de Drift | ❌ | ✅ | ✅ | ✅ |
| Audit Logging | Básico | Detalhado | Completo | Completo + Imutável |

---

## 9. Transparência e Explicabilidade

### 9.1 Requisitos de Transparência

| Requisito | Descrição | Obrigatório para |
|-----------|-----------|------------------|
| **Model Card** | Documentação padronizada do modelo | Médio+ |
| **Aviso de uso de IA** | Informar usuários quando interagem com IA | Alto/Crítico |
| **Explicação de decisões** | Capacidade de explicar outputs | Crítico |
| **Direito de contestação** | Processo para questionar decisões | Crítico |
| **Recurso humano** | Opção de revisão por humano | Alto/Crítico |

### 9.2 Template de Model Card (Resumido)

Todo modelo de classificação Média ou superior deve ter um Model Card contendo:

1. **Informações básicas**: Nome, versão, data, proprietário
2. **Uso pretendido**: Casos de uso aprovados e não aprovados
3. **Dados de treinamento**: Descrição (sem expor dados sensíveis)
4. **Métricas de performance**: Accuracy, precision, recall, etc.
5. **Métricas de fairness**: Demographic parity, equalized odds
6. **Limitações conhecidas**: Quando o modelo pode falhar
7. **Considerações éticas**: Riscos identificados e mitigações

---

## 10. Conformidade Regulatória

### 10.1 Mapeamento Regulatório

| Regulamentação | Jurisdição | Status | Requisitos Chave |
|----------------|------------|--------|------------------|
| **LGPD** | Brasil | Em vigor | Consentimento, DPIA, direitos do titular, Art. 20 (decisões automatizadas) |
| **PL 2338/2023 (Marco IA)** | Brasil | Em tramitação | Classificação de risco, transparência, direitos |
| **Resolução 4.893 BACEN** | Brasil (Financeiro) | Em vigor | Segurança cibernética em sistemas críticos |
| **GDPR Art. 22** | UE | Em vigor | Direito de não estar sujeito a decisão automatizada |
| **AI Act** | UE | Em vigor | Classificação de risco, proibições, requisitos |

### 10.2 LGPD Art. 20 - Decisões Automatizadas

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║              LGPD ART. 20 - DIREITO DE REVISÃO DE DECISÕES AUTOMATIZADAS         ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  "O titular dos dados tem direito a solicitar a revisão de decisões tomadas      ║
║   unicamente com base em tratamento automatizado de dados pessoais que           ║
║   afetem seus interesses, incluídas as decisões destinadas a definir o seu       ║
║   perfil pessoal, profissional, de consumo e de crédito ou os aspectos           ║
║   de sua personalidade."                                                         ║
║                                                                                   ║
║  OBRIGAÇÕES DA TECHCORP:                                                          ║
║                                                                                   ║
║  1. Informar quando decisões são automatizadas                                   ║
║  2. Fornecer informações claras sobre lógica utilizada                          ║
║  3. Permitir revisão humana quando solicitado                                    ║
║  4. Responder em 15 dias                                                         ║
║  5. Documentar todas as solicitações e respostas                                ║
║                                                                                   ║
║  PROCESSO DE REVISÃO:                                                             ║
║  • Canal: privacidade@techcorp.com.br                                            ║
║  • SLA: 15 dias corridos                                                         ║
║  • Responsável: DPO                                                              ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## 11. Treinamento e Conscientização

### 11.1 Programa de Treinamento

| Público | Treinamento | Frequência | Duração |
|---------|-------------|------------|---------|
| Todos os funcionários | Fundamentos de IA Responsável | Onboarding + Anual | 2h |
| Desenvolvedores | AI-DevSecOps, Segurança de ML | Onboarding + Anual | 8h |
| Data Scientists | MLSecOps, Fairness, Privacy | Onboarding + Anual | 16h |
| Gestores | Governança de IA, Riscos | Onboarding + Anual | 4h |
| Liderança | Estratégia e Ética de IA | Anual | 2h |

### 11.2 Conteúdo Obrigatório

- [ ] Princípios de IA responsável da TechCorp
- [ ] Esta política de governança de IA
- [ ] Uso permitido e proibido de ferramentas de IA
- [ ] Caso Samsung: o que NÃO fazer com LLMs
- [ ] Como reportar preocupações éticas
- [ ] Processo de aprovação de projetos de IA

---

## 12. Monitoramento e Métricas

### 12.1 KPIs de Governança de IA

| Métrica | Meta | Frequência |
|---------|------|------------|
| % de sistemas de IA inventariados | 100% | Mensal |
| % de sistemas com Model Card | 100% (Médio+) | Mensal |
| Incidentes de IA | 0 críticos | Mensal |
| Tempo médio de aprovação de projetos | < 10 dias | Mensal |
| Treinamento completado | > 95% | Trimestral |
| Auditorias de fairness realizadas | 100% (Alto/Crítico) | Trimestral |
| Reclamações LGPD Art. 20 | < 5/mês | Mensal |

---

## 13. Exceções e Violações

### 13.1 Processo de Exceção

Exceções a esta política devem:
1. Ser solicitadas formalmente ao CAIO
2. Incluir justificativa de negócio
3. Identificar riscos e mitigações alternativas
4. Ser aprovadas pelo Comitê de IA (para Alto/Crítico)
5. Ter prazo definido (máximo 6 meses)
6. Ser documentadas e revisadas

### 13.2 Consequências de Violações

| Gravidade | Exemplos | Consequências |
|-----------|----------|---------------|
| Leve | Uso de ferramenta não aprovada para tarefas de baixo risco | Advertência verbal, treinamento |
| Moderada | Envio de dados internos para LLM público | Advertência formal, suspensão de acesso |
| Grave | Envio de dados de clientes para LLM público, discriminação por IA | Demissão, possível ação legal |
| Crítica | Vazamento massivo de dados, dano a clientes | Demissão por justa causa, ação legal |

---

## 14. Revisão e Atualização

Esta política será revisada:
- **Anualmente** em condições normais
- **Imediatamente** se houver:
  - Nova regulamentação aplicável
  - Incidente significativo de IA
  - Mudança material na estratégia de IA
  - Aquisição de nova tecnologia de IA

---

## 15. Aprovações

| Papel | Nome | Data | Assinatura |
|-------|------|------|------------|
| CAIO | [Nome] | Jan 2025 | [Assinatura] |
| CISO | [Nome] | Jan 2025 | [Assinatura] |
| DPO | [Nome] | Jan 2025 | [Assinatura] |
| CLO (Jurídico) | [Nome] | Jan 2025 | [Assinatura] |
| CEO | [Nome] | Jan 2025 | [Assinatura] |

---

## 16. Referências

### Frameworks Utilizados

- [Microsoft Responsible AI Standard](https://www.microsoft.com/en-us/ai/responsible-ai)
- [Google AI Principles](https://ai.google/principles/)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [ISO/IEC 42001:2023 - AI Management System](https://www.iso.org/standard/81230.html)
- [OECD AI Principles](https://oecd.ai/en/ai-principles)
- [LGPD - Lei 13.709/2018](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/L13709.htm)
- [EU AI Act](https://artificialintelligenceact.eu/)

---

*Exemplo educacional baseado em melhores práticas de IA responsável - MBA Cibersegurança & IA*
