# Módulo 5: Desenvolvimento de Agentes de IA para Cibersegurança

## Informações Gerais

| Item | Descrição |
|------|-----------|
| **Módulo** | 5 |
| **Trilha** | IA para Cibersegurança |
| **Disciplina** | Desenvolvimento de Agentes de IA para Cibersegurança |
| **Carga Horária** | 40 horas |
| **Teoria/Prática** | 12h teóricas (30%) / 28h práticas (70%) |
| **Número de Aulas** | 8 aulas de 5 horas |
| **Pré-requisitos** | Módulos 1-4 |

## Contexto de Mercado

> "Em 2025, a Deloitte prevê que 40% das grandes empresas terão agentes de IA implantados em seus SOCs. A Gartner destaca AI SOC Agents como 'Innovation Trigger' no Hype Cycle de Security Operations." - Pesquisa de mercado 2025

### Por que Agentes de IA em Cibersegurança?

- **Alert Overload**: SOCs enfrentam milhares de alertas diários, maioria falsos positivos
- **Escassez de Talentos**: Brasil precisa de 232.000+ profissionais de cibersegurança
- **Velocidade de Resposta**: Ataques modernos requerem resposta em minutos, não horas
- **Machine-Speed Warfare**: Adversários usam IA; defensores precisam de IA

## Ementa

Introdução a Agentes de IA: conceitos, arquiteturas e frameworks. LangChain, LangGraph e CrewAI para segurança. Desenvolvimento de agentes autônomos para SOC. Agentes de triagem de alertas. Agentes de threat hunting. Agentes de resposta a incidentes. Agentes multi-modelo e orquestração. Integração de agentes com ferramentas de segurança (APIs, SIEM, SOAR). Segurança de agentes: controle de permissões, human-in-the-loop. Vibe Coding para desenvolvimento acelerado de agentes. Casos de uso: Dropzone AI, Google Gemini Security Agents, IBM ATOM.

## Objetivos de Aprendizagem

Ao final deste módulo, o aluno será capaz de:

1. Compreender arquiteturas de agentes de IA (ReAct, Plan-and-Execute, MRKL)
2. Desenvolver agentes de segurança com LangChain e CrewAI
3. Criar agentes de triagem automática de alertas de SOC
4. Implementar agentes de threat hunting baseados em MITRE ATT&CK
5. Construir agentes de resposta automatizada a incidentes
6. Integrar agentes com APIs de ferramentas de segurança (SIEM, SOAR, EDR)
7. Aplicar controles de segurança em agentes (permissões, auditoria, guardrails)
8. Usar Vibe Coding para acelerar desenvolvimento de agentes

## Competências Desenvolvidas

| Competência | Nível | Indicadores |
|-------------|-------|-------------|
| Desenvolvimento de Agentes | Avançado | Cria agentes funcionais com LangChain/CrewAI |
| Integração de APIs | Avançado | Conecta agentes a múltiplas ferramentas |
| Prompt Engineering | Avançado | Projeta prompts eficazes para agentes |
| Vibe Coding | Intermediário-Avançado | Desenvolve rapidamente com assistência de IA |
| Segurança de Agentes | Intermediário | Implementa controles e guardrails |

---

# PLANOS DE AULA DETALHADOS

---

## AULA 1: Introdução a Agentes de IA - Conceitos e Arquiteturas

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 1 de 8 |
| **Tema** | Fundamentos de Agentes de IA |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2.5h / 2.5h |

### Objetivos
1. Definir o que são agentes de IA e como diferem de chatbots
2. Compreender arquiteturas de agentes (ReAct, Plan-and-Execute)
3. Conhecer o ecossistema de ferramentas e frameworks
4. Entender casos de uso em cibersegurança
5. Configurar ambiente de desenvolvimento

### Estrutura da Aula

| Tempo | Atividade | Tipo |
|-------|-----------|------|
| 0:00-0:45 | O que são Agentes de IA? | Expositiva |
| 0:45-1:30 | Arquiteturas de Agentes | Expositiva-dialogada |
| 1:30-2:00 | Casos de Uso em Segurança | Demonstração |
| 2:00-2:15 | Intervalo | - |
| 2:15-3:30 | **Lab 1.1**: Setup do Ambiente | Prática |
| 3:30-4:45 | **Lab 1.2**: Primeiro Agente | Prática |
| 4:45-5:00 | Encerramento | Discussão |

### Conteúdo Programático

#### 1. O que são Agentes de IA? (45 min)

**Definição:**
Agentes de IA são sistemas autônomos que:
- Recebem uma tarefa/objetivo em linguagem natural
- Planejam como atingir o objetivo
- Executam ações usando ferramentas
- Observam resultados e ajustam plano
- Iteram até completar a tarefa

**Diferença de Chatbots:**

| Aspecto | Chatbot | Agente de IA |
|---------|---------|--------------|
| Autonomia | Responde perguntas | Executa tarefas |
| Planejamento | Nenhum | Multi-step |
| Ferramentas | Nenhuma | Múltiplas |
| Persistência | Sem memória | Com memória |
| Ações | Apenas texto | Ações no mundo real |

**Componentes de um Agente:**
```
┌─────────────────────────────────────────────┐
│                  AGENTE                      │
├─────────────────────────────────────────────┤
│  ┌─────────┐  ┌─────────┐  ┌─────────────┐ │
│  │   LLM   │  │ Memória │  │ Ferramentas │ │
│  │ (Cérebro)│  │(Contexto)│  │   (Ações)   │ │
│  └─────────┘  └─────────┘  └─────────────┘ │
│        │           │              │         │
│        └───────────┼──────────────┘         │
│                    │                        │
│             ┌──────┴──────┐                 │
│             │ Orquestrador │                 │
│             │   (Loop)     │                 │
│             └──────────────┘                 │
└─────────────────────────────────────────────┘
```

#### 2. Arquiteturas de Agentes (45 min)

**ReAct (Reason + Act):**
```
Thought: Preciso analisar este alerta de segurança
Action: query_siem(alert_id="12345")
Observation: Alerta de conexão suspeita para IP externo
Thought: Devo verificar a reputação deste IP
Action: check_virustotal(ip="203.0.113.50")
Observation: IP associado a C&C de botnet
Thought: Devo isolar o host afetado
Action: isolate_host(hostname="WORKSTATION-042")
Observation: Host isolado com sucesso
Final Answer: Alerta investigado e host comprometido isolado.
```

**Plan-and-Execute:**
```
Plano:
1. Coletar informações do alerta
2. Enriquecer com threat intelligence
3. Determinar severidade
4. Executar ação de contenção
5. Documentar incidente

Execução: [executa cada passo sequencialmente]
```

**MRKL (Modular Reasoning, Knowledge and Language):**
- Combina LLM com módulos especializados
- Cada módulo é um "expert" em uma área
- LLM decide qual módulo usar

#### 3. Agentes em Cibersegurança (30 min)

**Casos de Uso:**

| Caso de Uso | Descrição | Redução de Trabalho |
|-------------|-----------|---------------------|
| Triagem de Alertas | Classificar e priorizar alertas | 70-90% do tempo |
| Threat Hunting | Buscar ameaças proativamente | Horas → Minutos |
| Resposta a Incidentes | Contenção automatizada | 80% mais rápido |
| Threat Intel | Coletar e correlacionar IOCs | Automático |
| Relatórios | Documentação automática | 90% do tempo |

**Casos Reais:**
- **Dropzone AI**: Agente de triagem autônomo
- **Google Gemini Security Agents**: Triagem em Google Security Operations
- **IBM ATOM**: Autonomous Threat Operations Machine
- **Microsoft Copilot for Security**: Assistente de segurança

### Atividades Práticas

#### Lab 1.1: Setup do Ambiente (75 min)

**Objetivo:** Configurar ambiente de desenvolvimento para agentes

**Tarefas:**
```bash
# 1. Criar ambiente virtual
python -m venv agent-env
source agent-env/bin/activate  # Linux/Mac
# agent-env\Scripts\activate   # Windows

# 2. Instalar dependências
pip install langchain langchain-openai langchain-anthropic
pip install langgraph crewai
pip install python-dotenv requests

# 3. Configurar API keys
cat > .env << EOF
OPENAI_API_KEY=your-key-here
ANTHROPIC_API_KEY=your-key-here
EOF

# 4. Testar instalação
python -c "from langchain_anthropic import ChatAnthropic; print('OK')"
```

**Entregável:** Ambiente funcionando

#### Lab 1.2: Primeiro Agente Simples (75 min)

**Objetivo:** Criar primeiro agente de segurança básico

```python
from langchain_anthropic import ChatAnthropic
from langchain.agents import create_react_agent, AgentExecutor
from langchain.tools import Tool
from langchain import hub

# Ferramenta simples de lookup de IP
def check_ip_reputation(ip: str) -> str:
    """Verifica reputação de um IP."""
    # Simulação - em produção usaria API real
    malicious_ips = ["203.0.113.50", "198.51.100.23"]
    if ip in malicious_ips:
        return f"IP {ip}: MALICIOSO - Associado a atividade de botnet"
    return f"IP {ip}: Limpo - Nenhuma atividade maliciosa detectada"

# Definir ferramenta
tools = [
    Tool(
        name="check_ip_reputation",
        func=check_ip_reputation,
        description="Verifica se um IP é malicioso. Input: endereço IP"
    )
]

# Criar agente
llm = ChatAnthropic(model="claude-3-5-sonnet-20241022")
prompt = hub.pull("hwchase17/react")

agent = create_react_agent(llm, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)

# Executar
result = agent_executor.invoke({
    "input": "Verifique se o IP 203.0.113.50 é malicioso"
})
print(result["output"])
```

**Entregável:** Agente básico funcionando

### Materiais e Recursos

**Leitura Obrigatória:**
- LangChain Documentation: Agents Overview
- Google Cloud Blog: "The Dawn of Agentic AI in Security Operations"

**Ferramentas:**
- Claude Code para desenvolvimento assistido
- VS Code ou Cursor
- Python 3.10+

### Abordagem Metodológica

- **Expositiva dialogada:** Conceitos de agentes
- **Demonstração:** Casos de uso reais
- **Vibe Coding:** Desenvolvimento assistido por Claude Code
- **Hands-on:** Labs práticos

### Avaliação
| Instrumento | Peso |
|-------------|------|
| Lab 1.1 | 40% |
| Lab 1.2 | 60% |

### Referências

1. LangChain. **Agents Documentation**. 2025. https://python.langchain.com/docs/concepts/agents/
2. YAO, Shunyu et al. "ReAct: Synergizing Reasoning and Acting in Language Models". 2022.
3. Google Cloud. **The Dawn of Agentic AI in Security Operations**. 2025.

---

## AULA 2: Frameworks - LangChain, LangGraph e CrewAI

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 2 de 8 |
| **Tema** | Frameworks de Desenvolvimento de Agentes |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Dominar LangChain para criação de agentes
2. Entender LangGraph para workflows complexos
3. Usar CrewAI para agentes colaborativos
4. Comparar frameworks e escolher adequadamente
5. Aplicar Vibe Coding com Claude Code

### Conteúdo Programático

#### 1. LangChain Agents (45 min)

**Componentes:**
- **LLM**: O "cérebro" do agente (Claude, GPT-4, etc.)
- **Tools**: Ações que o agente pode executar
- **Prompt**: Instruções de como o agente deve se comportar
- **Memory**: Contexto de conversações anteriores

```python
from langchain_anthropic import ChatAnthropic
from langchain.agents import AgentExecutor, create_tool_calling_agent
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.tools import tool

@tool
def search_logs(query: str) -> str:
    """Busca logs no SIEM com a query fornecida."""
    # Implementação real conectaria ao SIEM
    return f"Encontrados 15 eventos para: {query}"

@tool
def get_host_info(hostname: str) -> str:
    """Obtém informações sobre um host."""
    return f"Host {hostname}: Windows 11, IP 192.168.1.100, User: john.doe"

# Prompt do agente
prompt = ChatPromptTemplate.from_messages([
    ("system", """Você é um analista de SOC experiente.
    Analise alertas de segurança de forma metódica:
    1. Colete informações relevantes
    2. Correlacione eventos
    3. Determine a severidade
    4. Recomende ações

    Sempre justifique suas conclusões."""),
    ("human", "{input}"),
    ("placeholder", "{agent_scratchpad}")
])

# Criar e executar agente
llm = ChatAnthropic(model="claude-3-5-sonnet-20241022")
tools = [search_logs, get_host_info]
agent = create_tool_calling_agent(llm, tools, prompt)
executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
```

#### 2. LangGraph (30 min)

**Para que serve:**
- Workflows complexos com múltiplos passos
- Controle fino sobre o fluxo
- Loops condicionais
- Persistência de estado

```python
from langgraph.graph import StateGraph, END
from typing import TypedDict, Annotated
import operator

class AgentState(TypedDict):
    alert: str
    enrichment: str
    severity: str
    action: str
    messages: Annotated[list, operator.add]

def enrich_alert(state: AgentState) -> AgentState:
    """Enriquecer alerta com contexto adicional."""
    # Lógica de enriquecimento
    state["enrichment"] = "IP associado a APT29"
    return state

def classify_severity(state: AgentState) -> AgentState:
    """Classificar severidade do alerta."""
    if "APT" in state["enrichment"]:
        state["severity"] = "CRITICAL"
    else:
        state["severity"] = "LOW"
    return state

def decide_action(state: AgentState) -> str:
    """Decidir próxima ação baseado na severidade."""
    if state["severity"] == "CRITICAL":
        return "escalate"
    return "close"

# Construir grafo
workflow = StateGraph(AgentState)
workflow.add_node("enrich", enrich_alert)
workflow.add_node("classify", classify_severity)
workflow.add_node("escalate", lambda s: {...})
workflow.add_node("close", lambda s: {...})

workflow.set_entry_point("enrich")
workflow.add_edge("enrich", "classify")
workflow.add_conditional_edges("classify", decide_action)
workflow.add_edge("escalate", END)
workflow.add_edge("close", END)

app = workflow.compile()
```

#### 3. CrewAI (30 min)

**Para que serve:**
- Múltiplos agentes colaborando
- Divisão de trabalho por especialidade
- Simulação de equipe

```python
from crewai import Agent, Task, Crew, Process

# Definir agentes especializados
analyst = Agent(
    role="SOC Analyst",
    goal="Analisar alertas de segurança e determinar severidade",
    backstory="Analista de SOC com 5 anos de experiência",
    verbose=True,
    llm="anthropic/claude-3-5-sonnet"
)

threat_intel = Agent(
    role="Threat Intelligence Analyst",
    goal="Enriquecer alertas com inteligência de ameaças",
    backstory="Especialista em CTI com foco em APTs",
    verbose=True,
    llm="anthropic/claude-3-5-sonnet"
)

responder = Agent(
    role="Incident Responder",
    goal="Executar ações de contenção quando necessário",
    backstory="Especialista em resposta a incidentes",
    verbose=True,
    llm="anthropic/claude-3-5-sonnet"
)

# Definir tarefas
analyze_task = Task(
    description="Analisar o alerta: {alert}",
    expected_output="Análise detalhada com recomendações",
    agent=analyst
)

enrich_task = Task(
    description="Enriquecer análise com threat intel",
    expected_output="IOCs e contexto de ameaças",
    agent=threat_intel
)

respond_task = Task(
    description="Determinar e executar ações de resposta",
    expected_output="Ações executadas e status",
    agent=responder
)

# Criar e executar crew
crew = Crew(
    agents=[analyst, threat_intel, responder],
    tasks=[analyze_task, enrich_task, respond_task],
    process=Process.sequential,
    verbose=True
)

result = crew.kickoff(inputs={"alert": "Conexão suspeita detectada"})
```

### Atividades Práticas

#### Lab 2.1: Agente LangChain para SIEM (90 min)

**Tarefas:**
1. Criar agente com 3+ ferramentas de segurança
2. Implementar prompt de analista de SOC
3. Testar com cenários reais
4. Usar Claude Code para acelerar desenvolvimento

#### Lab 2.2: Crew de Segurança com CrewAI (120 min)

**Tarefas:**
1. Definir 3 agentes especializados
2. Criar pipeline de análise
3. Executar com alerta simulado
4. Analisar colaboração entre agentes

**Entregável:** Notebooks com ambas implementações

### Avaliação
| Instrumento | Peso |
|-------------|------|
| Lab 2.1 | 50% |
| Lab 2.2 | 50% |

### Referências

1. LangChain. **LangGraph Documentation**. 2025.
2. CrewAI. **Getting Started Guide**. 2025. https://docs.crewai.com/

---

## AULA 3: Desenvolvimento de Agente de Triagem de Alertas

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 3 de 8 |
| **Tema** | Agente de Triagem de Alertas de SOC |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h / 4h |

### Objetivos
1. Projetar agente de triagem de alertas
2. Implementar lógica de priorização
3. Integrar com fontes de dados
4. Reduzir falsos positivos automaticamente
5. Gerar recomendações de ação

### Conteúdo Programático

#### Arquitetura do Agente de Triagem

```
┌──────────────────────────────────────────────────────────────┐
│                    AGENTE DE TRIAGEM                          │
├──────────────────────────────────────────────────────────────┤
│                                                               │
│  [Alerta SIEM] ──▶ [Extração de IOCs]                        │
│                           │                                   │
│                           ▼                                   │
│                   [Enriquecimento]                           │
│                    ├── VirusTotal                            │
│                    ├── AbuseIPDB                             │
│                    ├── Shodan                                │
│                    └── MISP                                  │
│                           │                                   │
│                           ▼                                   │
│                   [Análise de Contexto]                      │
│                    ├── Histórico do host                     │
│                    ├── Comportamento do usuário              │
│                    └── Baseline de rede                      │
│                           │                                   │
│                           ▼                                   │
│                   [Classificação]                            │
│                    ├── True Positive                         │
│                    ├── False Positive                        │
│                    └── Needs Review                          │
│                           │                                   │
│                           ▼                                   │
│                   [Ação Recomendada]                         │
│                                                               │
└──────────────────────────────────────────────────────────────┘
```

#### Implementação Completa

```python
from langchain_anthropic import ChatAnthropic
from langchain_core.tools import tool
from langchain.agents import create_tool_calling_agent, AgentExecutor
from langchain_core.prompts import ChatPromptTemplate
import requests
from typing import Dict, Any

# === FERRAMENTAS DO AGENTE ===

@tool
def get_alert_details(alert_id: str) -> Dict[str, Any]:
    """Obtém detalhes completos de um alerta do SIEM.

    Args:
        alert_id: ID do alerta no SIEM

    Returns:
        Dicionário com detalhes do alerta
    """
    # Simulação - em produção conectaria ao SIEM real
    return {
        "id": alert_id,
        "type": "Suspicious Outbound Connection",
        "source_ip": "192.168.1.100",
        "dest_ip": "203.0.113.50",
        "dest_port": 443,
        "hostname": "WORKSTATION-042",
        "user": "john.doe",
        "timestamp": "2025-01-15T14:30:00Z",
        "bytes_sent": 15000,
        "process": "chrome.exe"
    }

@tool
def check_virustotal(ioc: str, ioc_type: str = "ip") -> Dict[str, Any]:
    """Consulta VirusTotal para verificar reputação de IOC.

    Args:
        ioc: O indicador de comprometimento (IP, hash, domínio)
        ioc_type: Tipo do IOC (ip, hash, domain)

    Returns:
        Resultado da análise do VirusTotal
    """
    # Simulação
    malicious_iocs = ["203.0.113.50", "evil.com"]
    if ioc in malicious_iocs:
        return {
            "ioc": ioc,
            "malicious": True,
            "detections": 45,
            "total_engines": 70,
            "categories": ["botnet", "c2"],
            "first_seen": "2024-06-15"
        }
    return {
        "ioc": ioc,
        "malicious": False,
        "detections": 0,
        "total_engines": 70
    }

@tool
def get_host_history(hostname: str) -> Dict[str, Any]:
    """Obtém histórico de alertas e atividade do host.

    Args:
        hostname: Nome do host

    Returns:
        Histórico de atividades e alertas
    """
    return {
        "hostname": hostname,
        "os": "Windows 11 Pro",
        "last_patch": "2025-01-10",
        "alerts_30d": 2,
        "previous_incidents": 0,
        "risk_score": 25,
        "installed_security": ["CrowdStrike", "Zscaler"]
    }

@tool
def get_user_behavior(username: str) -> Dict[str, Any]:
    """Analisa comportamento recente do usuário.

    Args:
        username: Nome do usuário

    Returns:
        Análise comportamental
    """
    return {
        "username": username,
        "department": "Engineering",
        "location": "São Paulo",
        "login_anomalies": False,
        "after_hours_activity": False,
        "data_exfiltration_risk": "low",
        "travel_status": "no_travel"
    }

@tool
def check_network_baseline(dest_ip: str, dest_port: int) -> Dict[str, Any]:
    """Verifica se destino está no baseline de rede.

    Args:
        dest_ip: IP de destino
        dest_port: Porta de destino

    Returns:
        Informação de baseline
    """
    known_destinations = ["8.8.8.8", "1.1.1.1"]
    return {
        "dest_ip": dest_ip,
        "in_baseline": dest_ip in known_destinations,
        "first_connection": "2025-01-15" if dest_ip not in known_destinations else "2024-01-01",
        "connection_frequency": "rare" if dest_ip not in known_destinations else "common"
    }

# === AGENTE DE TRIAGEM ===

TRIAGE_PROMPT = ChatPromptTemplate.from_messages([
    ("system", """Você é um analista de SOC Nível 2 experiente especializado em triagem de alertas.

Seu objetivo é analisar alertas de segurança e determinar:
1. Se é um True Positive, False Positive ou requer revisão humana
2. A severidade (Critical, High, Medium, Low, Informational)
3. Ações recomendadas

Processo de análise:
1. Primeiro, obtenha os detalhes completos do alerta
2. Extraia IOCs (IPs, hashes, domínios) e verifique reputação
3. Analise o contexto do host e usuário
4. Verifique se o destino está no baseline
5. Correlacione todas as informações
6. Faça sua classificação final

Seja metódico e justifique cada conclusão.
Priorize reduzir falsos positivos sem deixar escapar ameaças reais."""),
    ("human", "Analise o alerta: {alert_id}"),
    ("placeholder", "{agent_scratchpad}")
])

# Criar agente
llm = ChatAnthropic(model="claude-3-5-sonnet-20241022", temperature=0)
tools = [
    get_alert_details,
    check_virustotal,
    get_host_history,
    get_user_behavior,
    check_network_baseline
]

agent = create_tool_calling_agent(llm, tools, TRIAGE_PROMPT)
triage_agent = AgentExecutor(
    agent=agent,
    tools=tools,
    verbose=True,
    max_iterations=10,
    return_intermediate_steps=True
)

# Executar triagem
result = triage_agent.invoke({"alert_id": "ALERT-2025-001234"})
print("\n=== RESULTADO DA TRIAGEM ===")
print(result["output"])
```

### Atividades Práticas

#### Lab 3: Agente de Triagem Completo (4h)

**Objetivo:** Desenvolver agente de triagem funcional

**Fases:**

1. **Fase 1 - Ferramentas (60 min):**
   - Implementar 5+ ferramentas de enriquecimento
   - Usar Claude Code para acelerar

2. **Fase 2 - Agente (90 min):**
   - Criar prompt otimizado
   - Configurar agente com ferramentas
   - Testar com alertas simulados

3. **Fase 3 - Avaliação (60 min):**
   - Testar com 10 alertas (5 TP, 5 FP)
   - Medir precisão de classificação
   - Identificar melhorias

4. **Fase 4 - Refinamento (30 min):**
   - Ajustar prompt baseado em erros
   - Re-testar

**Entregável:** Agente de triagem funcional + relatório de avaliação

### Avaliação
| Instrumento | Peso |
|-------------|------|
| Lab completo | 80% |
| Relatório de avaliação | 20% |

---

## AULA 4: Agente de Threat Hunting Automatizado

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 4 de 8 |
| **Tema** | Agente de Threat Hunting com MITRE ATT&CK |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h / 4h |

### Objetivos
1. Criar agente de hunting baseado em hipóteses
2. Integrar com MITRE ATT&CK
3. Desenvolver queries de hunting automatizadas
4. Correlacionar achados com técnicas de adversários

### Implementação

```python
from langchain_anthropic import ChatAnthropic
from langchain_core.tools import tool
from typing import List, Dict

@tool
def get_mitre_technique(technique_id: str) -> Dict:
    """Obtém detalhes de uma técnica MITRE ATT&CK.

    Args:
        technique_id: ID da técnica (ex: T1059.001)
    """
    techniques = {
        "T1059.001": {
            "name": "PowerShell",
            "tactic": "Execution",
            "description": "Adversários usam PowerShell para execução",
            "detection": "Monitorar logs de PowerShell, block encoding",
            "hunting_queries": [
                "process.name:powershell.exe AND command_line:*-enc*",
                "process.name:powershell.exe AND command_line:*bypass*"
            ]
        }
    }
    return techniques.get(technique_id, {"error": "Técnica não encontrada"})

@tool
def execute_hunting_query(query: str) -> List[Dict]:
    """Executa query de hunting no SIEM.

    Args:
        query: Query em formato Lucene/KQL
    """
    # Simulação de resultados
    return [
        {
            "timestamp": "2025-01-15T10:30:00Z",
            "hostname": "WORKSTATION-042",
            "command_line": "powershell.exe -enc SQBFAFgAIAAoAE...",
            "user": "john.doe",
            "parent_process": "outlook.exe"
        }
    ]

@tool
def get_related_events(hostname: str, time_window: str = "1h") -> List[Dict]:
    """Busca eventos relacionados em um host.

    Args:
        hostname: Nome do host
        time_window: Janela de tempo
    """
    return [
        {"event": "Network connection to 203.0.113.50:443"},
        {"event": "File created: C:\\Users\\john.doe\\AppData\\Local\\Temp\\update.exe"},
        {"event": "Registry modification: HKCU\\Run\\Updater"}
    ]

HUNTING_PROMPT = """Você é um Threat Hunter experiente.

Sua missão é buscar proativamente ameaças que podem ter escapado das detecções automáticas.

Metodologia:
1. Formule uma hipótese de hunting baseada em técnicas MITRE ATT&CK
2. Desenvolva queries para testar a hipótese
3. Execute as queries e analise resultados
4. Correlacione achados com outras evidências
5. Documente findings com evidências

Hipótese atual: {hypothesis}

Seja metódico e documente todo o processo."""
```

### Atividade Prática

#### Lab 4: Agente de Hunting (4h)

**Cenário:** Buscar atividade de PowerShell suspeita

**Tarefas:**
1. Criar ferramentas de hunting
2. Integrar com MITRE ATT&CK
3. Desenvolver agente de hunting
4. Executar hunting session
5. Documentar findings

**Entregável:** Agente de hunting + relatório de hunting

---

## AULA 5: Agente de Resposta a Incidentes

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 5 de 8 |
| **Tema** | Agente de Resposta Automatizada |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h / 4h |

### Objetivos
1. Criar agente de resposta a incidentes
2. Implementar ações de contenção
3. Aplicar human-in-the-loop para ações críticas
4. Documentar automaticamente

### Implementação

```python
@tool
def isolate_host(hostname: str, reason: str) -> Dict:
    """Isola um host da rede (requer aprovação).

    Args:
        hostname: Host a ser isolado
        reason: Justificativa para isolamento
    """
    # Em produção: chamaria API do EDR
    return {
        "action": "isolate",
        "hostname": hostname,
        "status": "pending_approval",
        "requires_approval": True
    }

@tool
def block_ip_firewall(ip: str, direction: str = "outbound") -> Dict:
    """Bloqueia IP no firewall.

    Args:
        ip: IP a ser bloqueado
        direction: Direção do bloqueio
    """
    return {
        "action": "block_ip",
        "ip": ip,
        "status": "success"
    }

@tool
def disable_user_account(username: str, reason: str) -> Dict:
    """Desabilita conta de usuário (requer aprovação).

    Args:
        username: Usuário a ser desabilitado
        reason: Justificativa
    """
    return {
        "action": "disable_account",
        "username": username,
        "status": "pending_approval",
        "requires_approval": True
    }

@tool
def create_incident_ticket(title: str, description: str, severity: str) -> Dict:
    """Cria ticket de incidente.

    Args:
        title: Título do incidente
        description: Descrição detalhada
        severity: Severidade
    """
    return {
        "ticket_id": "INC-2025-001234",
        "status": "created"
    }

# Agente com controle de ações
class ControlledResponseAgent:
    def __init__(self):
        self.pending_approvals = []
        self.executed_actions = []

    def request_approval(self, action: Dict) -> bool:
        """Solicita aprovação humana para ação crítica."""
        print(f"\n⚠️  APROVAÇÃO REQUERIDA:")
        print(f"   Ação: {action['action']}")
        print(f"   Alvo: {action.get('hostname') or action.get('username')}")
        print(f"   Justificativa: {action.get('reason', 'N/A')}")

        response = input("Aprovar? (s/n): ")
        return response.lower() == 's'
```

### Atividade Prática

#### Lab 5: Agente de Resposta (4h)

**Cenário:** Responder a incidente de ransomware

**Tarefas:**
1. Implementar ferramentas de resposta
2. Criar agente com human-in-the-loop
3. Executar playbook de contenção
4. Documentar incidente automaticamente

---

## AULA 6: Integração com APIs e Ferramentas de Segurança

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 6 de 8 |
| **Tema** | Integração de Agentes com Ecossistema de Segurança |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h / 4h |

### Objetivos
1. Integrar agentes com APIs reais
2. Conectar a SIEM, SOAR, EDR
3. Implementar autenticação segura
4. Tratar erros e timeouts

### APIs Comuns

```python
# VirusTotal
import requests

def query_virustotal(api_key: str, ip: str) -> Dict:
    url = f"https://www.virustotal.com/api/v3/ip_addresses/{ip}"
    headers = {"x-apikey": api_key}
    response = requests.get(url, headers=headers)
    return response.json()

# Shodan
def query_shodan(api_key: str, ip: str) -> Dict:
    url = f"https://api.shodan.io/shodan/host/{ip}?key={api_key}"
    response = requests.get(url)
    return response.json()

# Elastic SIEM
from elasticsearch import Elasticsearch

def query_elastic(es_client: Elasticsearch, query: str) -> List:
    result = es_client.search(
        index="logs-*",
        body={"query": {"query_string": {"query": query}}},
        size=100
    )
    return result["hits"]["hits"]
```

### Atividade Prática

#### Lab 6: Integração Multi-Ferramenta (4h)

**Tarefas:**
1. Integrar com 3+ APIs reais
2. Implementar tratamento de erros
3. Criar agente que usa todas as integrações
4. Testar fluxo end-to-end

---

## AULA 7: Segurança de Agentes - Permissões, Auditoria e Human-in-the-Loop

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 7 de 8 |
| **Tema** | Segurança e Governança de Agentes |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h / 3h |

### Objetivos
1. Implementar controle de permissões em agentes
2. Criar sistema de auditoria
3. Aplicar guardrails
4. Proteger contra prompt injection em agentes
5. Implementar human-in-the-loop efetivo

### Conteúdo

#### Modelo de Permissões

```python
from enum import Enum
from dataclasses import dataclass
from typing import List, Callable

class ActionSeverity(Enum):
    READ_ONLY = 1      # Consultas, leituras
    LOW_IMPACT = 2     # Ações reversíveis
    MEDIUM_IMPACT = 3  # Ações que afetam sistemas
    HIGH_IMPACT = 4    # Isolamento, bloqueio
    CRITICAL = 5       # Desabilitar usuários, wipe

@dataclass
class Permission:
    action: str
    severity: ActionSeverity
    requires_approval: bool
    approvers: List[str]

class AgentPermissionManager:
    def __init__(self):
        self.permissions = {
            "query_siem": Permission("query_siem", ActionSeverity.READ_ONLY, False, []),
            "check_virustotal": Permission("check_virustotal", ActionSeverity.READ_ONLY, False, []),
            "isolate_host": Permission("isolate_host", ActionSeverity.HIGH_IMPACT, True, ["soc_lead"]),
            "disable_user": Permission("disable_user", ActionSeverity.CRITICAL, True, ["security_manager"]),
        }

    def can_execute(self, action: str, user_role: str) -> bool:
        perm = self.permissions.get(action)
        if not perm:
            return False
        if perm.requires_approval:
            return self.request_approval(action, perm.approvers)
        return True
```

#### Sistema de Auditoria

```python
import json
from datetime import datetime

class AgentAuditLog:
    def __init__(self, log_file: str = "agent_audit.jsonl"):
        self.log_file = log_file

    def log_action(self, agent_id: str, action: str, inputs: Dict,
                   outputs: Dict, user: str):
        entry = {
            "timestamp": datetime.utcnow().isoformat(),
            "agent_id": agent_id,
            "action": action,
            "inputs": inputs,
            "outputs": outputs,
            "user": user,
            "status": "success"
        }
        with open(self.log_file, "a") as f:
            f.write(json.dumps(entry) + "\n")
```

### Atividade Prática

#### Lab 7: Agente Seguro (3h)

**Tarefas:**
1. Implementar sistema de permissões
2. Adicionar auditoria completa
3. Implementar guardrails com NeMo
4. Testar contra prompt injection

---

## AULA 8: Projeto Final - Construindo um AI SOC Agent

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 8 de 8 |
| **Tema** | Projeto Integrador e CTF |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 0.5h / 4.5h |

### Objetivos
1. Desenvolver agente SOC completo
2. Integrar todas as capacidades aprendidas
3. Demonstrar em cenário realista
4. Competir em CTF de agentes

### Projeto: AI SOC Agent

**Requisitos:**
- Triagem automática de alertas
- Enriquecimento com threat intel
- Hunting baseado em MITRE ATT&CK
- Resposta automatizada com aprovações
- Documentação automática
- Auditoria completa

### CTF do Módulo (3h)

**Categorias:**

1. **Agent Development (4 desafios)**
   - Corrigir agente quebrado
   - Adicionar ferramenta
   - Otimizar prompt
   - Implementar memória

2. **Agent Security (4 desafios)**
   - Bypass de permissões
   - Prompt injection em agente
   - Exfiltrar dados via agente
   - Implementar defesas

3. **Integration (4 desafios)**
   - Conectar a API
   - Parsear resposta
   - Tratar erros
   - Orquestrar múltiplas ferramentas

---

## Bibliografia Completa do Módulo

### Referências Básicas
1. LangChain. **LangChain Documentation**. 2025.
2. CrewAI. **CrewAI Documentation**. 2025.
3. Google Cloud. **The Dawn of Agentic AI in Security Operations**. 2025.

### Referências Complementares
4. IBM. **Agentic AI Enables an Autonomous SOC**. 2025.
5. Radiant Security. **AI Agents in the SOC**. 2025.
6. OWASP. **Top 10 for Agentic Applications**. 2026.
7. YAO, Shunyu et al. "ReAct: Synergizing Reasoning and Acting". 2022.

### Ferramentas
- LangChain: https://python.langchain.com/
- LangGraph: https://langchain-ai.github.io/langgraph/
- CrewAI: https://docs.crewai.com/
- Claude Code: Para desenvolvimento assistido

---

*CECyber - Academia de Cibersegurança*
