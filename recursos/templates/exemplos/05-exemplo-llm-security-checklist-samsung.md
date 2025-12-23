# LLM Security Checklist - Caso Samsung/ChatGPT
## Avaliação de Segurança para Uso Corporativo de LLMs (Exemplo Baseado em Caso Real)

> **Nota**: Este documento é um exemplo educacional baseado em informações públicas sobre o vazamento de dados da Samsung através do ChatGPT em 2023. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## Informações do Projeto

| Campo | Valor |
|-------|-------|
| **Nome do Projeto/Aplicação** | Implementação de ChatGPT para Engenharia - Samsung Semiconductor |
| **Modelo(s) Utilizado(s)** | OpenAI ChatGPT (GPT-3.5/GPT-4) |
| **Responsável pela Avaliação** | CISO Office - Avaliação Pós-Incidente |
| **Data da Avaliação** | Abril 2023 (Pós-Incidente) |
| **Versão do Checklist** | 1.0 |

---

## Contexto do Incidente Samsung

### O Que Aconteceu

Em março/abril de 2023, a Samsung Semiconductor permitiu que seus engenheiros usassem o ChatGPT para auxiliar em tarefas de desenvolvimento. Em menos de 20 dias, ocorreram **três incidentes separados de vazamento de dados confidenciais**:

| Incidente | Descrição | Dados Vazados |
|-----------|-----------|---------------|
| **#1** | Engenheiro colou código-fonte com bugs para o ChatGPT corrigir | Código proprietário de semicondutores |
| **#2** | Funcionário enviou sequências de testes para otimização | Padrões de teste para detecção de chips defeituosos (confidencial) |
| **#3** | Funcionário transcreveu reunião e pediu para gerar apresentação | Notas de reunião interna confidencial |

### Por Que Foi Um Problema

- **Dados enviados ao ChatGPT são usados para treinar o modelo** (na época)
- **Informações proprietárias tornaram-se parte do dataset de treinamento da OpenAI**
- **Dados são irrecuperáveis** - não há como "deletar" do modelo
- **Violação de propriedade intelectual** e possivelmente segredos comerciais

### Resposta da Samsung

1. Investigação disciplinar dos funcionários envolvidos
2. Limite de caracteres para entradas no ChatGPT (1KB)
3. Banimento temporário de ferramentas de IA generativa
4. Desenvolvimento de solução interna de IA
5. Em 2024-2025: Retorno controlado ao uso de ChatGPT com novos protocolos

---

## Avaliação de Segurança (Pré-Incidente Hipotética)

> Esta avaliação demonstra como o checklist deveria ter sido aplicado ANTES de permitir o uso do ChatGPT.

---

## 1. Prompt Injection (LLM01) - OWASP

### 1.1 Direct Prompt Injection
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 1.1.1 | Input sanitization implementado antes do prompt | ☐ N/A ☒ Não | Engenheiros copiavam código diretamente |
| 1.1.2 | Delimitadores claros entre system prompt e user input | ☐ N/A ☒ Não | Uso direto do ChatGPT sem wrapper |
| 1.1.3 | Validação de formato/tipo de input | ☐ N/A ☒ Não | Qualquer conteúdo aceito |
| 1.1.4 | Limite de caracteres no input do usuário | ☐ N/A ☒ Não | Sem limites (implementado pós-incidente: 1KB) |
| 1.1.5 | Testes com payloads de prompt injection realizados | ☐ N/A ☒ Não | Nenhum teste de segurança |
| 1.1.6 | Detecção de tentativas de jailbreak | ☐ N/A ☒ Não | N/A para este caso |

**Score Seção 1.1: 0/6 (0%)**

### 1.2 Indirect Prompt Injection
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 1.2.1 | Dados externos são sanitizados antes de entrar no contexto | ☐ N/A ☒ Não | Código fonte inserido diretamente |
| 1.2.2 | URLs/sites acessados pelo modelo são validados | ☒ N/A | ChatGPT não acessava URLs na época |
| 1.2.3 | Documentos importados são verificados | ☐ N/A ☒ Não | Documentos confidenciais copiados |
| 1.2.4 | Outputs de outros modelos são tratados como untrusted | ☒ N/A | Não aplicável |
| 1.2.5 | RAG sources são validadas e confiáveis | ☒ N/A | Não utilizava RAG |

**Score Seção 1.2: 0/2 aplicáveis (0%)**

---

## 2. Sensitive Information Disclosure (LLM02) - CRÍTICO

### 2.1 Proteção de Dados em Runtime
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 2.1.1 | Output filtering para PII/dados sensíveis | ☐ N/A ☒ **Não** | **FALHA CRÍTICA** - Dados confidenciais enviados |
| 2.1.2 | System prompt não é revelado ao usuário | ☒ N/A | Sem system prompt customizado |
| 2.1.3 | Logs não armazenam dados sensíveis em claro | ☐ N/A ☒ **Não** | OpenAI armazenava todas as conversas |
| 2.1.4 | Respostas não incluem informações de infraestrutura | ☒ Sim | N/A |
| 2.1.5 | Rate limiting para prevenir extraction attacks | ☐ N/A ☒ Não | Uso ilimitado permitido |
| 2.1.6 | Detecção de membership inference attacks | ☒ N/A | N/A para este cenário |

**Score Seção 2.1: 0/4 aplicáveis (0%) - CRÍTICO**

### 2.2 Classificação de Dados Enviados (Análise dos Incidentes)

| Incidente | Tipo de Dado | Classificação | Deveria ser Enviado? |
|-----------|--------------|---------------|---------------------|
| #1 | Código fonte proprietário | **RESTRITO** | **NÃO** |
| #2 | Sequências de teste de chips | **CONFIDENCIAL** | **NÃO** |
| #3 | Notas de reunião interna | **INTERNO** | **NÃO** |

### 2.3 Conformidade com Políticas de Dados
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 2.3.1 | Política de uso de IA generativa documentada | ☐ N/A ☒ **Não** | Nenhuma política existia |
| 2.3.2 | Treinamento sobre dados permitidos/proibidos | ☐ N/A ☒ **Não** | Funcionários não treinados |
| 2.3.3 | DLP para detectar dados sensíveis em prompts | ☐ N/A ☒ **Não** | Nenhum controle DLP |
| 2.3.4 | Aprovação para uso de ferramentas externas de IA | ☐ N/A ☒ **Não** | Liberação sem avaliação de segurança |

**Score Seção 2.3: 0/4 (0%) - CRÍTICO**

---

## 3. Supply Chain Vulnerabilities (LLM03)

### 3.1 Due Diligence do Fornecedor (OpenAI)
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 3.1.1 | Termos de serviço revisados por Legal | ☐ N/A ☒ **Não** | ToS permitiam uso para treinamento |
| 3.1.2 | Data Processing Agreement (DPA) negociado | ☐ N/A ☒ **Não** | Uso de versão consumer, não enterprise |
| 3.1.3 | Política de retenção de dados do fornecedor verificada | ☐ N/A ☒ **Não** | OpenAI retinha dados por 30 dias |
| 3.1.4 | Opção de opt-out de treinamento ativada | ☐ N/A ☒ **Não** | Não disponível/não configurado |
| 3.1.5 | Versão Enterprise/API com controles avaliada | ☐ N/A ☒ **Não** | Uso de versão gratuita/consumer |

**Score Seção 3.1: 0/5 (0%) - FALHA TOTAL**

### 3.2 Análise de Termos de Serviço (Na Época)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║              ALERTA: TERMOS DE SERVIÇO DO CHATGPT (2023)                         ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  ⚠️  "We may use Content you provide us to improve our Services"                 ║
║                                                                                   ║
║  IMPLICAÇÕES:                                                                     ║
║  • Todo conteúdo enviado PODERIA ser usado para treinar o modelo                 ║
║  • Dados confidenciais poderiam aparecer em outputs para outros usuários         ║
║  • Não havia garantia de confidencialidade                                       ║
║  • Dados eram armazenados nos servidores da OpenAI                               ║
║                                                                                   ║
║  OPÇÕES IGNORADAS:                                                                ║
║  • ChatGPT API com opt-out de treinamento                                        ║
║  • ChatGPT Enterprise (ainda não disponível na época)                            ║
║  • Azure OpenAI Service (dados não usados para treinar)                          ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## 4. Data and Model Poisoning (LLM04)

### 4.1 Risco Reverso - Samsung como "Poisoner" Involuntário
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 4.1.1 | Dados enviados podem contaminar modelo público | ☐ N/A ☒ **Sim** | Código Samsung agora parte do GPT |
| 4.1.2 | Propriedade intelectual pode aparecer para outros | ☐ N/A ☒ **Sim** | Risco de exposição |
| 4.1.3 | Segredos comerciais comprometidos | ☐ N/A ☒ **Sim** | Padrões de teste de chips |

**Este não é um risco de receber dados envenenados, mas de ENVIAR dados que contaminam o modelo para outros.**

---

## 5. Improper Output Handling (LLM05)

### 5.1 Validação de Output
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 5.1.1 | Outputs são revisados antes de uso em produção | ☐ N/A ☒ Não | Código gerado usado diretamente |
| 5.1.2 | Code review de código gerado por IA | ☐ N/A ☒ Não | Sem processo definido |
| 5.1.3 | Testes de segurança em código gerado | ☐ N/A ☒ Não | Sem SAST/DAST |

**Score Seção 5.1: 0/3 (0%)**

---

## 6. Excessive Agency (LLM06)

### 6.1 Princípio do Menor Privilégio
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 6.1.1 | Usuários têm apenas acesso necessário ao LLM | ☐ N/A ☒ Não | Todos os engenheiros tinham acesso irrestrito |
| 6.1.2 | Tipos de dados permitidos são limitados | ☐ N/A ☒ **Não** | Nenhuma restrição |
| 6.1.3 | Casos de uso aprovados são definidos | ☐ N/A ☒ **Não** | "Use para o que quiser" |

**Score Seção 6.1: 0/3 (0%)**

---

## 7. System Prompt Leakage (LLM07)

| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 7.1.1 | System prompt não contém dados da empresa | ☒ N/A | Uso direto sem customização |

**N/A - Samsung usava ChatGPT vanilla sem system prompts customizados**

---

## 8. Vector and Embedding Weaknesses (LLM08)

| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 8.1.1 | RAG não utilizado | ☒ N/A | Uso direto do ChatGPT |

**N/A - Não aplicável para este caso de uso**

---

## 9. Misinformation (LLM09)

### 9.1 Prevenção de Alucinações em Código
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 9.1.1 | Código gerado é testado antes de uso | ☐ N/A ☒ Não | Confiança excessiva no output |
| 9.1.2 | Funcionários treinados sobre limitações | ☐ N/A ☒ Não | Sem treinamento |
| 9.1.3 | Processo de revisão de código IA existe | ☐ N/A ☒ Não | Sem processo |

**Score Seção 9.1: 0/3 (0%)**

---

## 10. Unbounded Consumption (LLM10)

### 10.1 Rate Limiting e Quotas
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 10.1.1 | Limite de uso por funcionário | ☐ N/A ☒ Não | Uso ilimitado |
| 10.1.2 | Monitoramento de volume de dados enviados | ☐ N/A ☒ **Não** | 100GB+ poderiam ser enviados sem detecção |
| 10.1.3 | Alertas para uso anômalo | ☐ N/A ☒ **Não** | Nenhum monitoramento |

**Score Seção 10.1: 0/3 (0%) - Implementado pós-incidente (limite 1KB)**

---

## 11. Infraestrutura e Acesso

### 11.1 Controles de Acesso
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 11.1.1 | Acesso ao ChatGPT via SSO corporativo | ☐ N/A ☒ Não | Contas pessoais usadas |
| 11.1.2 | Logs de uso centralizados | ☐ N/A ☒ Não | Sem visibilidade |
| 11.1.3 | Política de uso aceitável assinada | ☐ N/A ☒ **Não** | Nenhuma política |
| 11.1.4 | Treinamento obrigatório antes do uso | ☐ N/A ☒ **Não** | Zero treinamento |

**Score Seção 11.1: 0/4 (0%)**

---

## 12. Monitoramento e Logging

### 12.1 Observabilidade
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 12.1.1 | Logs de todas as interações com LLM | ☐ N/A ☒ **Não** | Nenhum log corporativo |
| 12.1.2 | DLP integrado para detectar dados sensíveis | ☐ N/A ☒ **Não** | **FALHA CRÍTICA** |
| 12.1.3 | Alertas de dados confidenciais | ☐ N/A ☒ **Não** | Código fonte enviado sem alerta |
| 12.1.4 | Dashboard de uso de IA | ☐ N/A ☒ Não | Visibilidade zero |

**Score Seção 12.1: 0/4 (0%) - CRÍTICO**

---

## 13. Resumo e Scoring

### 13.1 Resumo por Categoria

| Categoria | Total Items | Sim | Não | N/A | Score |
|-----------|-------------|-----|-----|-----|-------|
| 1. Prompt Injection | 11 | 0 | 8 | 3 | **0/100** |
| 2. Sensitive Info Disclosure | 10 | 0 | 8 | 2 | **0/100** |
| 3. Supply Chain | 5 | 0 | 5 | 0 | **0/100** |
| 4. Data/Model Poisoning | 3 | 0 | 3 | 0 | **0/100** |
| 5. Output Handling | 3 | 0 | 3 | 0 | **0/100** |
| 6. Excessive Agency | 3 | 0 | 3 | 0 | **0/100** |
| 7. System Prompt Leakage | 1 | 0 | 0 | 1 | **N/A** |
| 8. Vector/Embedding | 1 | 0 | 0 | 1 | **N/A** |
| 9. Misinformation | 3 | 0 | 3 | 0 | **0/100** |
| 10. Unbounded Consumption | 3 | 0 | 3 | 0 | **0/100** |
| 11. Infraestrutura | 4 | 0 | 4 | 0 | **0/100** |
| 12. Monitoramento | 4 | 0 | 4 | 0 | **0/100** |
| **TOTAL** | **51** | **0** | **44** | **7** | **0/100** |

### 13.2 Risk Rating

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║                           RESULTADO DA AVALIAÇÃO                                  ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                   ║
║  SCORE FINAL: 0/100                                                               ║
║                                                                                   ║
║  ██████████████████████████████████████████████████████████████████████████████  ║
║  ████████████████████ RISCO CRÍTICO - USO NÃO AUTORIZADO █████████████████████  ║
║  ██████████████████████████████████████████████████████████████████████████████  ║
║                                                                                   ║
║  RECOMENDAÇÃO: USO DO CHATGPT DEVERIA TER SIDO BLOQUEADO                         ║
║                até implementação de controles adequados                          ║
║                                                                                   ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## 14. Plano de Remediação (Implementado pela Samsung)

### 14.1 Ações Imediatas (Implementadas)

| Ação | Descrição | Status |
|------|-----------|--------|
| Investigação disciplinar | Funcionários envolvidos investigados | ✅ Completo |
| Limite de caracteres | Input limitado a 1KB | ✅ Implementado |
| Banimento temporário | IA generativa bloqueada | ✅ Implementado (2023) |
| Comunicado interno | Alerta sobre riscos de IA | ✅ Enviado |

### 14.2 Ações de Médio Prazo (Recomendadas)

| Ação | Descrição | Responsável | Prioridade |
|------|-----------|-------------|------------|
| Desenvolver IA interna | Solução proprietária para código | R&D | Alta |
| Implementar DLP | Detectar dados sensíveis em prompts | Security | **Crítica** |
| Política de IA | Documentar uso permitido/proibido | Legal + CISO | **Crítica** |
| Treinamento obrigatório | Conscientização sobre riscos de IA | HR + Security | Alta |
| Avaliar Enterprise options | ChatGPT Enterprise, Azure OpenAI | IT + Security | Alta |

### 14.3 Controles Recomendados para Uso Futuro

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│           FRAMEWORK DE CONTROLES PARA USO CORPORATIVO DE LLMs                    │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  1. POLÍTICA E GOVERNANÇA                                                        │
│     ├── Política de uso de IA generativa documentada e assinada                 │
│     ├── Classificação clara de dados permitidos/proibidos                       │
│     ├── Processo de aprovação para novos casos de uso                           │
│     └── Comitê de ética/segurança de IA                                         │
│                                                                                  │
│  2. CONTROLES TÉCNICOS                                                           │
│     ├── DLP integrado para detectar código, PII, segredos                       │
│     ├── Proxy/Gateway para todas as interações com LLMs                         │
│     ├── Logging centralizado de todas as conversas                              │
│     ├── Limite de tamanho de input (1-2KB para uso geral)                       │
│     ├── Bloqueio de upload de arquivos                                          │
│     └── Alertas para detecção de dados sensíveis                                │
│                                                                                  │
│  3. ESCOLHA DE FORNECEDOR                                                        │
│     ├── Preferência por soluções Enterprise (não consumer)                      │
│     ├── DPA (Data Processing Agreement) obrigatório                             │
│     ├── Opt-out de treinamento configurado                                      │
│     ├── Residência de dados na região adequada                                  │
│     └── Auditoria de segurança do fornecedor                                    │
│                                                                                  │
│  4. TREINAMENTO E CONSCIENTIZAÇÃO                                                │
│     ├── Treinamento obrigatório antes do acesso                                 │
│     ├── Exemplos de uso proibido (como o caso Samsung)                          │
│     ├── Recertificação anual                                                    │
│     └── Canais de reporte de incidentes                                         │
│                                                                                  │
│  5. MONITORAMENTO E RESPOSTA                                                     │
│     ├── Dashboard de uso de IA corporativa                                      │
│     ├── Alertas de uso anômalo                                                  │
│     ├── Processo de resposta a vazamentos de dados                              │
│     └── Métricas de conformidade                                                │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 15. Lições Aprendidas

### 15.1 Para Organizações

| Lição | Descrição |
|-------|-----------|
| **Política antes da tecnologia** | Definir regras ANTES de liberar ferramentas de IA |
| **DLP é essencial** | Detectar dados sensíveis antes que saiam da organização |
| **Consumer ≠ Enterprise** | Versões gratuitas não têm controles adequados |
| **Treinamento é obrigatório** | Funcionários precisam entender os riscos |
| **Dados são irrecuperáveis** | Uma vez enviados, não há como "voltar atrás" |

### 15.2 Para Funcionários

| Lição | Descrição |
|-------|-----------|
| **Nunca envie código proprietário** | LLMs públicos podem usar para treinamento |
| **Nunca envie dados confidenciais** | Reuniões, estratégias, dados de clientes |
| **Trate LLMs como público** | Assuma que tudo pode ser visto por terceiros |
| **Quando em dúvida, não envie** | Pergunte ao time de segurança primeiro |

---

## 16. Referências

### Fontes Utilizadas

- [CyberNews - ChatGPT Samsung Leak Explained](https://cybernews.com/security/chatgpt-samsung-leak-explained-lessons/)
- [Dark Reading - Samsung Engineers Sensitive Data ChatGPT](https://www.darkreading.com/vulnerabilities-threats/samsung-engineers-sensitive-data-chatgpt-warnings-ai-use-workplace)
- [TechRadar - Samsung Workers Leaked Company Secrets](https://www.techradar.com/news/samsung-workers-leaked-company-secrets-by-using-chatgpt)
- [AI Incident Database - Incident 768](https://incidentdatabase.ai/cite/768/)
- [SamMobile - Samsung Lets Employees Use ChatGPT Again](https://www.sammobile.com/news/samsung-lets-employees-use-chatgpt-again-after-secret-data-leak-in-2023/)
- [OWASP Top 10 for LLM Applications 2025](https://genai.owasp.org/llm-top-10/)

### Frameworks de Referência
- OWASP Top 10 for LLM Applications
- NIST AI Risk Management Framework
- ISO/IEC 42001 (AI Management System)

---

*Exemplo educacional baseado no caso Samsung/ChatGPT 2023 - MBA Cibersegurança & IA*
*Este documento demonstra a importância de avaliar segurança ANTES de implementar ferramentas de IA generativa.*
