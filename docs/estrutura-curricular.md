# Estrutura Curricular Completa

## MBA em Cibersegurança e Inteligência Artificial

---

## Visão Geral da Matriz Curricular

| # | Trilha | Módulo | Disciplina | CH |
|---|--------|--------|------------|-----|
| 1 | Fundamentos | 1 | Fundamentos de Segurança da Informação | 40h |
| 2 | Fundamentos | 2 | Fundamentos de Inteligência Artificial e Vibe Coding | 40h |
| 3 | IA para Cyber | 3 | Machine Learning para Detecção de Ameaças | 40h |
| 4 | IA para Cyber | 4 | Automação de SOC com IA | 30h |
| 5 | IA para Cyber | 5 | **Desenvolvimento de Agentes de IA para Cibersegurança** | 40h |
| 6 | IA para Cyber | 6 | Threat Intelligence, Hunting e Resposta a Incidentes | 30h |
| 7 | Segurança de IA | 7 | Segurança de LLMs e Modelos Generativos | 40h |
| 8 | Segurança de IA | 8 | OWASP Top 10 para IA/LLM | 40h |
| 9 | Segurança de IA | 9 | Governança e Ética em IA | 30h |
| 10 | Segurança de IA | 10 | Proteção de Dados e Privacidade em IA | 30h |
| 11 | Liderança | 11 | GRC para Ambientes de IA | 30h |
| 12 | Liderança | 12 | Projeto Aplicado - CTF Final | 30h |
| | | | **TOTAL** | **420h** |

---

## COMPETÊNCIA TRANSVERSAL: VIBE CODING

### O que é Vibe Coding?

**Vibe Coding** é uma abordagem de desenvolvimento onde o profissional expressa suas intenções em linguagem natural e a IA transforma esse pensamento em código executável. Termo cunhado por Andrej Karpathy em 2025, representa uma mudança fundamental na forma como profissionais de segurança interagem com código.

### Por que Vibe Coding no MBA?

Em 2025, o mercado reporta que:
- 25% das startups do YC têm codebases 95% gerados por IA
- Ciclos de desenvolvimento reduziram de 12 para 7 semanas
- Profissionais de segurança precisam criar ferramentas rapidamente

### Ferramentas de Vibe Coding no Curso

| Ferramenta | Uso Principal | Módulos |
|------------|---------------|---------|
| **Claude Code** | Desenvolvimento de agentes e automações | 2, 5, 7 |
| **GitHub Copilot** | Assistência em código de segurança | Todos |
| **Cursor** | IDE com IA integrada | 3, 4, 5 |

### Competências de Vibe Coding

Ao longo do MBA, o aluno desenvolverá:

1. **Prompting Efetivo para Código**
   - Escrever prompts claros para geração de código
   - Iterar e refinar outputs
   - Identificar e corrigir erros

2. **Revisão Crítica de Código Gerado**
   - Avaliar segurança de código gerado por IA
   - Identificar vulnerabilidades introduzidas
   - Validar lógica e correção

3. **Integração em Workflows de Segurança**
   - Automatizar tarefas repetitivas
   - Criar scripts de análise rapidamente
   - Desenvolver PoCs de ferramentas

### Aplicação por Módulo

| Módulo | Aplicação de Vibe Coding |
|--------|--------------------------|
| 2 | Introdução a ferramentas, setup de ambiente |
| 3 | Criação rápida de modelos de ML |
| 4 | Desenvolvimento de playbooks e automações |
| 5 | Construção de agentes de segurança |
| 6 | Scripts de hunting e análise |
| 7 | Ferramentas de teste de LLMs |
| 8 | Exploits e mitigações |
| 12 | Projeto final com suporte de IA |

---

## TRILHA 1: FUNDAMENTOS (80h)

### Módulo 1: Fundamentos de Segurança da Informação

**Carga Horária:** 40 horas (16h teóricas + 24h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
Princípios fundamentais de segurança da informação: confidencialidade, integridade e disponibilidade. Gestão de riscos em segurança da informação. Controles de segurança: preventivos, detectivos e corretivos. Arquitetura de redes seguras. Fundamentos de criptografia. Autenticação e controle de acesso. Segurança em sistemas operacionais. Frameworks de segurança: NIST CSF, ISO 27001/27002, CIS Controls. Ameaças e vulnerabilidades contemporâneas. Preparatório CompTIA Security+.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Aplicar os princípios de CIA em cenários corporativos
2. Conduzir análise de riscos básica em sistemas de informação
3. Implementar controles de segurança apropriados
4. Configurar elementos de segurança em redes e sistemas
5. Utilizar técnicas criptográficas adequadas
6. Preparar-se para o exame CompTIA Security+

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Princípios de Segurança: CIA, AAA, Defesa em Profundidade | 5h |
| 2 | Gestão de Riscos e Frameworks (NIST, ISO 27001) | 5h |
| 3 | Arquitetura de Redes Seguras | 5h |
| 4 | Fundamentos de Criptografia | 5h |
| 5 | Autenticação, Autorização e IAM | 5h |
| 6 | Segurança de Sistemas Operacionais | 5h |
| 7 | Ameaças, Vulnerabilidades e Ataques | 5h |
| 8 | Revisão Security+ e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- STALLINGS, William; BROWN, Lawrie. **Segurança de Computadores: Princípios e Práticas**. 2ª ed. Elsevier, 2014.
- CompTIA. **CompTIA Security+ Study Guide (SY0-701)**. Sybex, 2024.
- NIST. **Cybersecurity Framework 2.0**. 2024.

**Complementar:**
- ISO/IEC 27001:2022 - Information Security Management Systems
- HARRIS, Shon. **CISSP All-in-One Exam Guide**. 9th ed. McGraw-Hill, 2024.
- MITNICK, Kevin. **A Arte de Enganar**. Pearson, 2003.

---

### Módulo 2: Fundamentos de Inteligência Artificial e Vibe Coding

**Carga Horária:** 40 horas (16h teóricas + 24h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
Introdução à Inteligência Artificial: histórico, conceitos e aplicações. Machine Learning: aprendizado supervisionado, não supervisionado e por reforço. Redes neurais e Deep Learning. Processamento de Linguagem Natural (NLP). Large Language Models (LLMs): arquitetura, funcionamento e aplicações. **Vibe Coding: desenvolvimento assistido por IA com Claude Code, Cursor e GitHub Copilot.** Introdução ao Python para IA. Bibliotecas fundamentais: NumPy, Pandas, Scikit-learn. Ética e vieses em IA.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Compreender os fundamentos teóricos de IA e ML
2. Diferenciar tipos de aprendizado de máquina
3. Implementar modelos básicos de ML em Python
4. Entender a arquitetura e funcionamento de LLMs
5. **Utilizar ferramentas de Vibe Coding para desenvolvimento acelerado**
6. **Avaliar criticamente código gerado por IA**
7. Reconhecer questões éticas em IA

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Introdução à IA: História, Conceitos e Aplicações | 5h |
| 2 | Python para IA: NumPy, Pandas, Visualização | 5h |
| 3 | Machine Learning Supervisionado | 5h |
| 4 | Machine Learning Não Supervisionado | 5h |
| 5 | Redes Neurais e Deep Learning | 5h |
| 6 | Large Language Models (LLMs) e Prompting | 5h |
| 7 | **Vibe Coding: Claude Code, Cursor e GitHub Copilot** | 5h |
| 8 | Ética em IA e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- GÉRON, Aurélien. **Mãos à Obra: Aprendizado de Máquina com Scikit-Learn, Keras e TensorFlow**. 3ª ed. Alta Books, 2023.
- CHOLLET, François. **Deep Learning with Python**. 2nd ed. Manning, 2021.
- Anthropic. **Claude Code Documentation**. 2025.

**Complementar:**
- GOODFELLOW, Ian et al. **Deep Learning**. MIT Press, 2016.
- GitHub. **GitHub Copilot Documentation**. 2025.
- IBM. **What is Vibe Coding?**. 2025.

---

## TRILHA 2: IA PARA CIBERSEGURANÇA (140h)

### Módulo 3: Machine Learning para Detecção de Ameaças

**Carga Horária:** 40 horas (12h teóricas + 28h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
Aplicação de Machine Learning em cibersegurança. Detecção de anomalias com algoritmos de clustering. Classificação de malware com técnicas supervisionadas. Análise comportamental com séries temporais. Feature engineering para dados de segurança. Detecção de intrusão com ML: IDS/IPS inteligentes. Análise de tráfego de rede com Deep Learning. User and Entity Behavior Analytics (UEBA). Detecção de phishing com NLP. Uso de Vibe Coding para prototipagem rápida de modelos. Desafios: adversarial attacks em modelos de segurança.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Desenvolver modelos de ML para detecção de anomalias
2. Implementar classificadores de malware
3. Criar sistemas de detecção de intrusão baseados em ML
4. Aplicar UEBA para identificação de ameaças internas
5. Construir detectores de phishing com NLP
6. **Usar Vibe Coding para acelerar desenvolvimento de modelos**
7. Compreender e mitigar ataques adversariais

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | ML para Segurança: Visão Geral e Datasets | 5h |
| 2 | Detecção de Anomalias e Clustering | 5h |
| 3 | Classificação de Malware | 5h |
| 4 | Detecção de Intrusão com ML (IDS/IPS) | 5h |
| 5 | Análise de Tráfego de Rede | 5h |
| 6 | User and Entity Behavior Analytics (UEBA) | 5h |
| 7 | Detecção de Phishing e Spam com NLP | 5h |
| 8 | Adversarial ML e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- STAMP, Mark. **Introduction to Machine Learning with Applications in Information Security**. 2nd ed. CRC Press, 2022.
- SAXE, Joshua; SANDERS, Hillary. **Malware Data Science**. No Starch Press, 2018.

**Complementar:**
- APRUZZESE, Giovanni et al. **The Role of Machine Learning in Cybersecurity**. ACM Computing Surveys, 2023.
- BUCZAK, Anna L.; GUVEN, Erhan. **A Survey of Data Mining and Machine Learning Methods for Cyber Security Intrusion Detection**. IEEE Communications Surveys, 2016.

---

### Módulo 4: Automação de SOC com IA

**Carga Horária:** 30 horas (10h teóricas + 20h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Arquitetura de SOC moderno e o Agentic SOC. SIEM e correlação de eventos com ML. SOAR: Security Orchestration, Automation and Response. Playbooks automatizados com IA. Priorização de alertas com ML. Redução de falsos positivos com IA. Métricas e KPIs de SOC. Introdução a agentes de IA no SOC. Ferramentas: Splunk, Elastic SIEM, Microsoft Sentinel.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Projetar arquitetura de SOC moderno com componentes de IA
2. Configurar SIEM com regras de ML
3. Desenvolver playbooks automatizados em SOAR
4. Implementar priorização inteligente de alertas
5. Medir e otimizar performance de SOC
6. Compreender o papel de agentes de IA no SOC

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Arquitetura de SOC Moderno e Agentic SOC | 5h |
| 2 | SIEM: Correlação e Detecção com ML | 5h |
| 3 | SOAR: Orquestração e Automação | 5h |
| 4 | Playbooks Automatizados com IA | 5h |
| 5 | Priorização de Alertas e Redução de Falsos Positivos | 5h |
| 6 | Métricas de SOC e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- MUNIZ, Joseph; MCINTYRE, Gary. **Security Operations Center**. Cisco Press, 2015.
- ROTHMAN, Mike; PESCATORE, John. **Security Operations Center Guidance**. SANS Institute, 2023.

**Complementar:**
- Google Cloud Blog. **The Dawn of Agentic AI in Security Operations**. 2025.
- IBM. **Agentic AI Enables an Autonomous SOC**. 2025.

---

### Módulo 5: Desenvolvimento de Agentes de IA para Cibersegurança

**Carga Horária:** 40 horas (12h teóricas + 28h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
Introdução a Agentes de IA: conceitos, arquiteturas e frameworks. LangChain, CrewAI e AutoGPT para segurança. Desenvolvimento de agentes autônomos para SOC. Agentes de triagem de alertas. Agentes de threat hunting. Agentes de resposta a incidentes. Agentes multi-modelo e orquestração. Integração de agentes com ferramentas de segurança (APIs, SIEM, SOAR). Segurança de agentes: controle de permissões, human-in-the-loop. Vibe Coding para desenvolvimento acelerado de agentes. Casos de uso: Dropzone AI, Google Gemini Security Agents, IBM ATOM.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Compreender arquiteturas de agentes de IA (ReAct, Plan-and-Execute)
2. Desenvolver agentes de segurança com LangChain e CrewAI
3. Criar agentes de triagem automática de alertas
4. Implementar agentes de threat hunting
5. Construir agentes de resposta a incidentes
6. Integrar agentes com ferramentas de SOC
7. Aplicar controles de segurança em agentes (permissões, auditoria)
8. Usar Vibe Coding para acelerar desenvolvimento

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Introdução a Agentes de IA: Conceitos e Arquiteturas | 5h |
| 2 | Frameworks: LangChain, LangGraph e CrewAI | 5h |
| 3 | Desenvolvimento de Agente de Triagem de Alertas | 5h |
| 4 | Agente de Threat Hunting Automatizado | 5h |
| 5 | Agente de Resposta a Incidentes | 5h |
| 6 | Integração com APIs e Ferramentas de Segurança | 5h |
| 7 | Segurança de Agentes: Permissões, Auditoria e Human-in-the-Loop | 5h |
| 8 | Projeto: Construindo um AI SOC Agent e CTF do Módulo | 5h |

#### Laboratórios Práticos

| Lab | Descrição | Ferramentas |
|-----|-----------|-------------|
| 5.1 | Setup de ambiente LangChain/CrewAI | Python, LangChain, Claude Code |
| 5.2 | Agente de análise de logs | LangChain, Elastic |
| 5.3 | Agente de triagem com VirusTotal | CrewAI, APIs |
| 5.4 | Agente de hunting MITRE ATT&CK | LangGraph, ATT&CK |
| 5.5 | Agente de resposta automatizada | SOAR APIs |
| 5.6 | Integração multi-ferramenta | APIs diversas |
| 5.7 | Implementação de guardrails em agentes | NeMo Guardrails |
| 5.8 | Projeto final: AI SOC Agent | Stack completa |

#### Bibliografia

**Básica:**
- LangChain. **LangChain Documentation**. 2025. https://python.langchain.com/
- CrewAI. **CrewAI Documentation**. 2025. https://docs.crewai.com/
- Google Cloud. **The Dawn of Agentic AI in Security Operations at RSAC 2025**. 2025.

**Complementar:**
- IBM. **Agentic AI Enables an Autonomous SOC**. 2025.
- Radiant Security. **AI Agents in the SOC: Transforming Cybersecurity Operations**. 2025.
- OWASP. **Top 10 for Agentic Applications**. 2026.

---

### Módulo 6: Threat Intelligence, Hunting e Resposta a Incidentes

**Carga Horária:** 30 horas (10h teóricas + 20h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Fundamentos de Cyber Threat Intelligence (CTI). MITRE ATT&CK e frameworks de CTI. Coleta automatizada de IOCs com ML e agentes. NLP para processamento de relatórios de ameaças. Threat hunting proativo com IA. Ciclo de resposta a incidentes (NIST SP 800-61). Detecção e triagem automatizada. Contenção e recuperação com agentes. Documentação automatizada com LLMs.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Aplicar o ciclo de inteligência em cibersegurança
2. Utilizar MITRE ATT&CK para hunting e detecção
3. Automatizar coleta e análise de IOCs com agentes
4. Desenvolver hunting queries baseadas em IA
5. Implementar resposta automatizada a incidentes
6. Documentar incidentes com assistência de LLMs

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Cyber Threat Intelligence e MITRE ATT&CK | 5h |
| 2 | Coleta e Análise de IOCs com IA | 5h |
| 3 | Threat Hunting Proativo com Agentes | 5h |
| 4 | Resposta a Incidentes: Detecção e Triagem | 5h |
| 5 | Contenção Automatizada e Playbooks | 5h |
| 6 | Documentação com LLMs e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- MITRE. **ATT&CK Framework Documentation**. 2024.
- NIST. **SP 800-61 Rev. 2: Computer Security Incident Handling Guide**. 2012.

**Complementar:**
- SANS. **Incident Handler's Handbook**. 2023.
- JOHANSEN, Gerard. **Digital Forensics and Incident Response**. 2nd ed. Packt, 2020.

---

## TRILHA 3: SEGURANÇA DE AMBIENTES DE IA (140h)

### Módulo 7: Segurança de LLMs e Modelos Generativos

**Carga Horária:** 40 horas (12h teóricas + 28h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
Arquitetura de Large Language Models. Superfície de ataque em sistemas de IA generativa. Prompt injection: direto e indireto. Jailbreaking de LLMs. Data poisoning e model poisoning. Extração de dados de treinamento. Model stealing e inversão de modelos. Segurança de APIs de LLM. Defesas e guardrails. Frameworks de segurança para LLMs. Ferramentas de red teaming para IA. **Segurança de ferramentas de Vibe Coding.**

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Identificar vulnerabilidades em sistemas de LLM
2. Conduzir testes de prompt injection
3. Implementar guardrails de segurança
4. Proteger APIs de modelos de IA
5. Detectar e prevenir data poisoning
6. Realizar red teaming em sistemas de IA
7. **Avaliar riscos de segurança em código gerado por IA**

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Arquitetura de LLMs e Superfície de Ataque | 5h |
| 2 | Prompt Injection: Técnicas e Defesas | 5h |
| 3 | Jailbreaking e Bypass de Guardrails | 5h |
| 4 | Data Poisoning e Model Poisoning | 5h |
| 5 | Extração de Dados e Model Stealing | 5h |
| 6 | Segurança de APIs de LLM e Vibe Coding | 5h |
| 7 | Implementação de Guardrails e Defesas | 5h |
| 8 | Red Teaming de IA e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- OWASP. **OWASP Top 10 for Large Language Model Applications 2025**. 2025.
- PEREZ, Fabio; RIBEIRO, Ian. **Ignore This Title and HackAPrompt**. 2023.

**Complementar:**
- Anthropic. **Claude's Character and Safety**. 2024.
- Google. **Secure AI Framework (SAIF)**. 2024.

---

### Módulo 8: OWASP Top 10 para IA/LLM

**Carga Horária:** 40 horas (12h teóricas + 28h práticas)

**Número de Aulas:** 8 aulas de 5 horas

#### Ementa
OWASP Top 10 para LLM Applications 2025: análise detalhada. LLM01: Prompt Injection. LLM02: Insecure Output Handling. LLM03: Training Data Poisoning. LLM04: Model Denial of Service. LLM05: Supply Chain Vulnerabilities. LLM06: Sensitive Information Disclosure. LLM07: Insecure Plugin Design. LLM08: Excessive Agency. LLM09: Overreliance. LLM10: Model Theft. **OWASP Top 10 for Agentic Applications. Segurança de agentes autônomos.**

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Identificar cada vulnerabilidade do OWASP Top 10 LLM
2. Explorar vulnerabilidades em ambiente controlado
3. Implementar mitigações para cada categoria
4. Conduzir assessments de segurança em aplicações de LLM
5. **Avaliar riscos de agentes autônomos de IA**
6. **Implementar controles de segurança para agentes**

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | OWASP Top 10 LLM: Visão Geral e LLM01-Prompt Injection | 5h |
| 2 | LLM02-Insecure Output e LLM03-Data Poisoning | 5h |
| 3 | LLM04-Model DoS e LLM05-Supply Chain | 5h |
| 4 | LLM06-Information Disclosure e LLM07-Insecure Plugin | 5h |
| 5 | LLM08-Excessive Agency e LLM09-Overreliance | 5h |
| 6 | LLM10-Model Theft e Mitigações Gerais | 5h |
| 7 | **OWASP Top 10 for Agentic Applications** | 5h |
| 8 | Assessment de Segurança e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- OWASP. **OWASP Top 10 for Large Language Model Applications v2.0**. 2025.
- OWASP. **OWASP Top 10 for Agentic Applications**. 2026.

**Complementar:**
- NIST. **AI Risk Management Framework (AI RMF 1.0)**. 2023.
- European Union. **EU AI Act**. 2024.

---

### Módulo 9: Governança e Ética em IA

**Carga Horária:** 30 horas (15h teóricas + 15h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Princípios de IA responsável e ética. Vieses em sistemas de IA: identificação e mitigação. Fairness, Accountability, Transparency (FAT). Explicabilidade e interpretabilidade de modelos (XAI). Governança corporativa de IA. Frameworks de governança: NIST AI RMF, ISO 42001. EU AI Act e regulamentações globais. **Governança de ferramentas de Vibe Coding e código gerado por IA.** Comitês de ética em IA. Auditoria de sistemas de IA.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Aplicar princípios de IA responsável em projetos
2. Identificar e mitigar vieses em modelos de ML
3. Implementar práticas de explicabilidade
4. Desenvolver políticas de governança de IA
5. **Estabelecer políticas para uso de Vibe Coding**
6. Garantir conformidade com regulamentações

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Ética em IA: Princípios e Dilemas | 5h |
| 2 | Vieses em IA: Identificação e Mitigação | 5h |
| 3 | Explicabilidade e Interpretabilidade (XAI) | 5h |
| 4 | Frameworks de Governança: NIST AI RMF, ISO 42001 | 5h |
| 5 | Regulamentações e Governança de Vibe Coding | 5h |
| 6 | Auditoria de IA e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- NIST. **AI Risk Management Framework (AI RMF 1.0)**. 2023.
- ISO/IEC 42001:2023 - Artificial Intelligence Management System

**Complementar:**
- European Union. **Artificial Intelligence Act**. 2024.
- JOBIN, Anna et al. **The Global Landscape of AI Ethics Guidelines**. Nature Machine Intelligence, 2019.

---

### Módulo 10: Proteção de Dados e Privacidade em IA

**Carga Horária:** 30 horas (12h teóricas + 18h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Privacidade em sistemas de ML. Ataques de privacidade: membership inference, model inversion. Differential Privacy: conceitos e implementação. Federated Learning: aprendizado descentralizado. Privacy-Preserving Machine Learning (PPML). LGPD aplicada a sistemas de IA. **Privacidade em ferramentas de Vibe Coding e dados enviados a LLMs.**

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Identificar riscos de privacidade em sistemas de ML
2. Implementar Differential Privacy
3. Projetar sistemas com Federated Learning
4. Garantir conformidade com LGPD em projetos de IA
5. **Avaliar riscos de privacidade em Vibe Coding**

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Privacidade em ML: Ameaças e Ataques | 5h |
| 2 | Differential Privacy: Teoria e Prática | 5h |
| 3 | Federated Learning | 5h |
| 4 | Privacy-Preserving ML | 5h |
| 5 | LGPD, Privacidade e Vibe Coding | 5h |
| 6 | Implementação de Privacidade e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- DWORK, Cynthia; ROTH, Aaron. **The Algorithmic Foundations of Differential Privacy**. NOW Publishers, 2014.
- Brasil. **Lei Geral de Proteção de Dados (Lei 13.709/2018)**. 2018.

**Complementar:**
- KAIROUZ, Peter et al. **Advances and Open Problems in Federated Learning**. 2021.

---

## TRILHA 4: LIDERANÇA E APLICAÇÃO (60h)

### Módulo 11: GRC para Ambientes de IA

**Carga Horária:** 30 horas (12h teóricas + 18h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Governança, Risco e Compliance em ambientes de IA. Risk assessment para projetos de IA e agentes autônomos. Controles de segurança específicos para IA. Compliance com frameworks regulatórios. Third-party risk management em IA. **Políticas de uso de IA generativa e Vibe Coding na organização.** Auditoria de sistemas de IA. Comunicação de riscos para stakeholders.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. Conduzir risk assessments para projetos de IA
2. Implementar controles de GRC específicos para IA
3. **Desenvolver políticas de uso de IA generativa e Vibe Coding**
4. Gerenciar riscos de terceiros em IA
5. Comunicar riscos de IA para executivos

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | GRC Tradicional vs GRC para IA | 5h |
| 2 | Risk Assessment para IA e Agentes | 5h |
| 3 | Controles de Segurança para IA | 5h |
| 4 | Third-Party Risk e Políticas de Vibe Coding | 5h |
| 5 | Métricas, Reporting e Comunicação de Riscos | 5h |
| 6 | Continuidade de Negócios e CTF do Módulo | 5h |

#### Bibliografia

**Básica:**
- NIST. **AI Risk Management Framework Playbook**. 2023.
- ISO 31000:2018 - Risk Management Guidelines

**Complementar:**
- ISACA. **Risk IT Framework**. 2nd ed. 2020.

---

### Módulo 12: Projeto Aplicado - CTF Final

**Carga Horária:** 30 horas (6h teóricas + 24h práticas)

**Número de Aulas:** 6 aulas de 5 horas

#### Ementa
Projeto integrador combinando todos os conhecimentos do MBA. **Desenvolvimento de agente de segurança completo usando Vibe Coding.** Capture The Flag (CTF) com cenários de IA e cibersegurança. Desafios de red team: ataque a sistemas de IA. Desafios de blue team: defesa com IA e agentes. Elaboração de relatório executivo. Apresentação de resultados.

#### Objetivos de Aprendizagem
Ao final do módulo, o aluno será capaz de:
1. **Desenvolver agente de segurança funcional**
2. Aplicar conhecimentos integrados em cenários realistas
3. Resolver desafios complexos de CTF
4. Trabalhar em equipe sob pressão
5. Elaborar relatórios executivos de segurança
6. Apresentar resultados para stakeholders

#### Conteúdo Programático

| Aula | Tema | CH |
|------|------|-----|
| 1 | Preparação: Revisão e Formação de Equipes | 5h |
| 2 | **Projeto: Desenvolvimento de AI Security Agent** | 5h |
| 3 | CTF Red Team: Atacando Sistemas de IA | 5h |
| 4 | CTF Blue Team: Defendendo com IA e Agentes | 5h |
| 5 | Elaboração de Relatório Executivo | 5h |
| 6 | Apresentação Final e Certificação | 5h |

#### Bibliografia

- Todos os materiais das disciplinas anteriores
- LangChain, CrewAI Documentation

---

## Resumo de Carga Horária

| Componente | Horas |
|------------|-------|
| Carga Horária Teórica | 141h (34%) |
| Carga Horária Prática | 279h (66%) |
| **Carga Horária Total** | **420h** |

---

## Mapa de Pré-requisitos

```
Módulo 1 ──┐
           ├──> Módulo 3 ──> Módulo 4 ──> Módulo 5 ──> Módulo 6
Módulo 2 ──┘                    │              │
                               │              │
           ┌───────────────────┘              │
           │                                  │
           ├──> Módulo 7 ──> Módulo 8 ────────┤
           │                                  │
           └──> Módulo 9 ──> Módulo 10        │
                    │                         │
                    └──> Módulo 11 ──> Módulo 12
```

---

## Diferenciais de Agentes e Vibe Coding

| Aspecto | Descrição |
|---------|-----------|
| **40% das grandes empresas** | Terão agentes de IA em SOCs até 2026 (Deloitte) |
| **Módulo dedicado** | 40h focadas em desenvolvimento de agentes |
| **Vibe Coding integrado** | Competência transversal em todos os módulos práticos |
| **Frameworks atuais** | LangChain, CrewAI, ferramentas 2025 |
| **Projeto final** | Construção de AI Security Agent funcional |

---

## Certificações Mapeadas

| Certificação | Módulos Relacionados |
|--------------|---------------------|
| CompTIA Security+ | Módulo 1 |
| CompTIA CySA+ | Módulos 3, 4, 5, 6 |
| CECyber CASP | Módulos 5, 7, 8, 12 |
| CISSP (parcial) | Módulos 1, 9, 11 |

---

*Documento parte integrante do PPC*

*Atualizado: Dezembro 2025*
