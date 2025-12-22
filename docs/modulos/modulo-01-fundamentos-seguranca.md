# Módulo 1: Fundamentos de Segurança da Informação

## Informações Gerais

| Item | Descrição |
|------|-----------|
| **Módulo** | 1 |
| **Trilha** | Fundamentos |
| **Disciplina** | Fundamentos de Segurança da Informação |
| **Carga Horária** | 40 horas |
| **Teoria/Prática** | 16h teóricas (40%) / 24h práticas (60%) |
| **Número de Aulas** | 8 aulas de 5 horas |
| **Pré-requisitos** | Nenhum |
| **Certificação Relacionada** | CompTIA Security+ (SY0-701) |

## Ementa

Princípios fundamentais de segurança da informação: confidencialidade, integridade e disponibilidade. Gestão de riscos em segurança da informação. Controles de segurança: preventivos, detectivos e corretivos. Arquitetura de redes seguras. Fundamentos de criptografia. Autenticação e controle de acesso. Segurança em sistemas operacionais. Frameworks de segurança: NIST CSF, ISO 27001/27002, CIS Controls. Ameaças e vulnerabilidades contemporâneas. Preparatório CompTIA Security+.

## Objetivos de Aprendizagem

Ao final deste módulo, o aluno será capaz de:

1. Aplicar os princípios de Confidencialidade, Integridade e Disponibilidade (CIA) em cenários corporativos reais
2. Conduzir análise de riscos básica utilizando metodologias reconhecidas
3. Selecionar e implementar controles de segurança apropriados para diferentes cenários
4. Projetar e avaliar arquiteturas de rede seguras
5. Aplicar técnicas criptográficas para proteção de dados
6. Implementar mecanismos de autenticação e controle de acesso
7. Configurar hardening em sistemas operacionais Windows e Linux
8. Mapear controles para frameworks de segurança (NIST CSF, ISO 27001)

## Competências Desenvolvidas

| Competência | Nível | Indicadores |
|-------------|-------|-------------|
| Análise de Riscos | Intermediário | Identifica ameaças, vulnerabilidades e calcula risco |
| Arquitetura de Segurança | Básico-Intermediário | Projeta redes seguras com segmentação adequada |
| Criptografia Aplicada | Básico | Seleciona algoritmos adequados para cada caso |
| Gestão de Identidades | Básico-Intermediário | Implementa autenticação multifator |
| Hardening de Sistemas | Intermediário | Configura sistemas seguros |

---

# PLANOS DE AULA DETALHADOS

---

## AULA 1: Princípios de Segurança - CIA, AAA e Defesa em Profundidade

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 1 de 8 |
| **Tema** | Princípios de Segurança: CIA, AAA, Defesa em Profundidade |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 1 |

### Objetivos da Aula

**Objetivo Geral:**
Compreender os princípios fundamentais que norteiam a segurança da informação e sua aplicação em ambientes corporativos.

**Objetivos Específicos:**
1. Definir e exemplificar os pilares CIA (Confidencialidade, Integridade, Disponibilidade)
2. Explicar os conceitos de Autenticação, Autorização e Auditoria (AAA)
3. Aplicar o princípio de defesa em profundidade em arquiteturas de segurança
4. Diferenciar controles preventivos, detectivos e corretivos
5. Identificar trade-offs entre segurança e usabilidade

### Descrição da Aula

Esta aula inaugural estabelece as bases conceituais da segurança da informação, apresentando os princípios que guiam todas as decisões de segurança em organizações. O aluno será introduzido à tríade CIA, entendendo como cada componente protege diferentes aspectos dos ativos de informação. A aula também aborda o modelo AAA e o conceito de defesa em profundidade, essenciais para a construção de arquiteturas de segurança robustas.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Abertura | Expositiva | Apresentação do módulo, objetivos e metodologia |
| 0:30-1:00 | Tríade CIA | Expositiva-dialogada | Confidencialidade, Integridade, Disponibilidade |
| 1:00-1:30 | Modelo AAA | Expositiva | Autenticação, Autorização, Accounting |
| 1:30-2:00 | Defesa em Profundidade | Expositiva-dialogada | Camadas de proteção e controles |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:15 | **Lab 1.1** | Prática | Análise de caso: violações de CIA |
| 3:15-4:15 | **Lab 1.2** | Prática | Mapeamento de controles por camada |
| 4:15-4:45 | Quiz | Avaliativa | Avaliação de conhecimentos |
| 4:45-5:00 | Encerramento | Discussão | Síntese e preview da próxima aula |

### Conteúdo Programático Detalhado

#### 1. Tríade CIA (30 min)

**Confidencialidade:**
- Definição: garantir que a informação seja acessível apenas a pessoas autorizadas
- Controles: criptografia, controle de acesso, classificação de dados
- Exemplos de violação: vazamento de dados, espionagem industrial
- Métricas: número de acessos não autorizados, dados expostos

**Integridade:**
- Definição: garantir exatidão e completude da informação
- Controles: hashing, assinaturas digitais, controle de versão
- Exemplos de violação: alteração de registros, man-in-the-middle
- Métricas: alterações não autorizadas detectadas

**Disponibilidade:**
- Definição: garantir acesso à informação quando necessário
- Controles: redundância, backup, DRP, alta disponibilidade
- Exemplos de violação: DDoS, ransomware, falhas de hardware
- Métricas: uptime, MTTR, MTBF

#### 2. Modelo AAA (30 min)

**Autenticação:**
- Fatores: algo que sabe, tem, é
- MFA: combinação de fatores
- Protocolos: RADIUS, TACACS+, LDAP, SAML, OAuth

**Autorização:**
- Modelos: MAC, DAC, RBAC, ABAC
- Princípio do menor privilégio
- Segregação de funções

**Accounting (Auditoria):**
- Logs e trilhas de auditoria
- Não-repúdio
- Requisitos de conformidade

#### 3. Defesa em Profundidade (30 min)

**Conceito:**
- Múltiplas camadas de proteção
- Falha de uma camada não compromete todo o sistema
- Analogia: castelo medieval

**Camadas típicas:**
- Física: controle de acesso físico, CFTV
- Perímetro: firewalls, IDS/IPS, WAF
- Rede: segmentação, VLANs, NAC
- Host: antivírus, EDR, hardening
- Aplicação: secure coding, WAF, input validation
- Dados: criptografia, DLP, mascaramento

### Materiais e Recursos

**Materiais do Professor:**
- Slides da aula (PDF)
- Vídeo-aula gravada (1h)
- Casos de estudo preparados
- Gabarito das atividades

**Materiais do Aluno:**
- Apostila do módulo (cap. 1)
- Artigo: "CIA Triad in Modern Security" (IEEE)
- Planilha de mapeamento de controles

**Recursos Tecnológicos:**
- AVA Moodle
- Ferramenta de quiz (Kahoot/Socrative)
- Draw.io para diagramas

**Leitura Prévia Obrigatória:**
- CompTIA Security+ Study Guide, Cap. 1 (30 páginas)

**Leitura Complementar:**
- NIST SP 800-12: An Introduction to Information Security

### Atividades Práticas

#### Laboratório 1.1: Análise de Casos de Violação CIA (60 min)

**Objetivo:** Analisar incidentes reais e identificar qual pilar da CIA foi violado.

**Cenário:** O aluno recebe 5 casos de incidentes de segurança reais (anonimizados):
1. Vazamento de dados do Equifax (2017)
2. Ataque NotPetya (2017)
3. Ataque DDoS ao Dyn (2016)
4. SolarWinds supply chain (2020)
5. Ransomware Colonial Pipeline (2021)

**Tarefas:**
1. Para cada caso, identificar:
   - Qual(is) pilar(es) CIA foi violado
   - Vetor de ataque utilizado
   - Controles que poderiam ter prevenido
   - Impacto estimado

2. Preencher matriz de análise
3. Apresentar conclusões em fórum

**Entregável:** Relatório de análise (template fornecido)

**Critérios de Avaliação:**
- Identificação correta dos pilares: 40%
- Análise de controles: 30%
- Qualidade da argumentação: 30%

#### Laboratório 1.2: Mapeamento de Controles por Camada (60 min)

**Objetivo:** Projetar defesa em profundidade para um cenário corporativo.

**Cenário:** Empresa de e-commerce com:
- 500 funcionários
- Loja online com 10.000 transações/dia
- Dados de cartão de crédito
- Infraestrutura híbrida (on-premise + cloud)

**Tarefas:**
1. Desenhar arquitetura de rede segura (Draw.io)
2. Identificar controles para cada camada:
   - Física
   - Perímetro
   - Rede
   - Host
   - Aplicação
   - Dados
3. Justificar a escolha de cada controle
4. Identificar pontos únicos de falha

**Entregável:** Diagrama + documento de justificativa

### Abordagem Metodológica

**Metodologias Utilizadas:**
- **Aula expositiva dialogada:** Para conceitos fundamentais
- **Aprendizagem Baseada em Problemas (PBL):** Análise de casos reais
- **Sala de Aula Invertida:** Leitura prévia obrigatória
- **Gamificação:** Quiz interativo com ranking

**Estratégias de Engajamento:**
- Perguntas direcionadas durante exposição
- Discussão de casos da atualidade
- Conexão com experiências dos alunos

**Diferenciação:**
- Conteúdo extra para alunos avançados
- Monitoria para alunos com dificuldade
- Múltiplos formatos de conteúdo (vídeo, texto, áudio)

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Quiz | 30% | 10 questões objetivas, mínimo 70% |
| Lab 1.1 | 35% | Análise correta e justificada |
| Lab 1.2 | 25% | Arquitetura adequada e justificativas |
| Participação | 10% | Contribuições em fórum |

### Referências Bibliográficas

**Referências Básicas:**
1. STALLINGS, William; BROWN, Lawrie. **Segurança de Computadores: Princípios e Práticas**. 2ª ed. Rio de Janeiro: Elsevier, 2014. Cap. 1.
2. CompTIA. **CompTIA Security+ Study Guide (SY0-701)**. Indianapolis: Sybex, 2024. Cap. 1.
3. NIST. **SP 800-12 Rev. 1: An Introduction to Information Security**. 2017.

**Referências Complementares:**
1. HARRIS, Shon. **CISSP All-in-One Exam Guide**. 9th ed. New York: McGraw-Hill, 2024. Cap. 1-2.
2. ANDRESS, Jason. **The Basics of Information Security**. 2nd ed. Syngress, 2014.

**Artigos e Papers:**
1. Samonas, S.; Coss, D. "The CIA Strikes Back: Redefining Confidentiality, Integrity and Availability in Security". Journal of Information System Security, 2014.

---

## AULA 2: Gestão de Riscos e Frameworks (NIST, ISO 27001)

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 2 de 8 |
| **Tema** | Gestão de Riscos e Frameworks de Segurança |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 2 |

### Objetivos da Aula

**Objetivo Geral:**
Compreender os processos de gestão de riscos e principais frameworks de segurança da informação.

**Objetivos Específicos:**
1. Definir conceitos de ameaça, vulnerabilidade, risco e impacto
2. Aplicar metodologias de análise de risco (quantitativa e qualitativa)
3. Conhecer os principais frameworks: NIST CSF, ISO 27001, CIS Controls
4. Mapear controles entre diferentes frameworks
5. Calcular métricas de risco: SLE, ALE, ARO

### Descrição da Aula

Esta aula apresenta os fundamentos da gestão de riscos em segurança da informação, capacitando o aluno a identificar, analisar e tratar riscos. São apresentados os principais frameworks utilizados globalmente, com ênfase no NIST Cybersecurity Framework e ISO 27001, estabelecendo a base para decisões de segurança baseadas em risco.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão da aula anterior e dúvidas |
| 0:30-1:15 | Gestão de Riscos | Expositiva | Conceitos e metodologias |
| 1:15-2:00 | Frameworks | Expositiva-dialogada | NIST CSF, ISO 27001, CIS Controls |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:15 | **Lab 2.1** | Prática | Análise de risco quantitativa |
| 3:15-4:15 | **Lab 2.2** | Prática | Mapeamento de controles NIST CSF |
| 4:15-4:45 | Quiz | Avaliativa | Avaliação de conhecimentos |
| 4:45-5:00 | Encerramento | Discussão | Síntese e próximos passos |

### Conteúdo Programático Detalhado

#### 1. Fundamentos de Gestão de Riscos (45 min)

**Conceitos Fundamentais:**
- **Ativo:** Recurso com valor para a organização
- **Ameaça:** Potencial causa de incidente indesejado
- **Vulnerabilidade:** Fraqueza que pode ser explorada
- **Risco:** Probabilidade × Impacto
- **Controle:** Medida que modifica o risco

**Análise Qualitativa:**
- Matriz de probabilidade × impacto
- Classificação: Alto, Médio, Baixo
- Vantagens: rápida, intuitiva
- Desvantagens: subjetiva

**Análise Quantitativa:**
- **SLE** (Single Loss Expectancy) = Valor do Ativo × Fator de Exposição
- **ARO** (Annual Rate of Occurrence) = Frequência anual
- **ALE** (Annual Loss Expectancy) = SLE × ARO
- **ROI de Segurança** = (ALE antes - ALE depois - Custo do controle) / Custo do controle

**Tratamento de Riscos:**
- Mitigar: implementar controles
- Aceitar: assumir o risco
- Transferir: seguros, terceirização
- Evitar: eliminar a atividade

#### 2. Frameworks de Segurança (45 min)

**NIST Cybersecurity Framework 2.0:**
- Govern (novo), Identify, Protect, Detect, Respond, Recover
- Tiers: Parcial, Informado, Repetível, Adaptativo
- Profiles: Current State, Target State

**ISO/IEC 27001:2022:**
- Sistema de Gestão de Segurança da Informação (SGSI)
- 93 controles em 4 temas
- Ciclo PDCA
- Certificação acreditada

**CIS Controls v8:**
- 18 controles prioritizados
- Implementation Groups (IG1, IG2, IG3)
- Mapeamento para outros frameworks

**Comparativo:**

| Aspecto | NIST CSF | ISO 27001 | CIS Controls |
|---------|----------|-----------|--------------|
| Tipo | Framework | Norma | Controles |
| Certificável | Não | Sim | Não |
| Complexidade | Média | Alta | Baixa-Média |
| Custo | Gratuito | Gratuito* | Gratuito |
| Foco | Gestão de risco | SGSI | Priorização |

### Materiais e Recursos

**Materiais do Professor:**
- Slides da aula (PDF)
- Planilha de cálculo de ALE
- Templates de frameworks

**Materiais do Aluno:**
- NIST CSF 2.0 (documento oficial)
- ISO 27001:2022 Annex A (resumo)
- CIS Controls v8 (documento)

**Leitura Prévia Obrigatória:**
- NIST Cybersecurity Framework 2.0 (Executive Summary)

### Atividades Práticas

#### Laboratório 2.1: Análise de Risco Quantitativa (60 min)

**Objetivo:** Calcular métricas de risco e ROI de controles de segurança.

**Cenário:**
Servidor de banco de dados com:
- Valor: R$ 500.000 (dados + sistema)
- Vulnerabilidade: SQL Injection
- Probabilidade de ataque: 2 vezes/ano
- Fator de exposição: 60%

**Tarefas:**
1. Calcular SLE, ARO e ALE
2. Avaliar controle (WAF): custo R$ 50.000/ano, reduz exposição para 10%
3. Calcular novo ALE e ROI
4. Recomendar decisão

**Entregável:** Planilha com cálculos e justificativa

#### Laboratório 2.2: Mapeamento NIST CSF (60 min)

**Objetivo:** Mapear a postura de segurança de uma organização usando NIST CSF.

**Cenário:** Avaliar hospital de médio porte

**Tarefas:**
1. Preencher Current Profile (estado atual)
2. Definir Target Profile (estado desejado)
3. Identificar gaps
4. Priorizar ações de remediação

**Entregável:** Assessment NIST CSF preenchido

### Abordagem Metodológica

- **Expositiva dialogada:** Conceitos de risco
- **Estudo de caso:** Análise de risco real
- **Hands-on:** Cálculos quantitativos
- **Gamificação:** Quiz competitivo

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Quiz | 30% | 10 questões sobre frameworks |
| Lab 2.1 | 35% | Cálculos corretos e decisão justificada |
| Lab 2.2 | 35% | Assessment completo e coerente |

### Referências Bibliográficas

**Referências Básicas:**
1. NIST. **Cybersecurity Framework 2.0**. 2024.
2. ISO/IEC 27001:2022 - Information Security Management Systems
3. CIS. **CIS Controls v8**. 2021.

**Referências Complementares:**
1. FREUND, Jack; JONES, Jack. **Measuring and Managing Information Risk: A FAIR Approach**. Butterworth-Heinemann, 2014.
2. NIST. **SP 800-30 Rev. 1: Guide for Conducting Risk Assessments**. 2012.

---

## AULA 3: Arquitetura de Redes Seguras

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 3 de 8 |
| **Tema** | Arquitetura de Redes Seguras |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 3 |

### Objetivos da Aula

**Objetivo Geral:**
Projetar e avaliar arquiteturas de rede seguras para ambientes corporativos.

**Objetivos Específicos:**
1. Aplicar princípios de segmentação de rede
2. Configurar firewalls e regras de filtragem
3. Implementar zonas de segurança (DMZ, intranet, extranet)
4. Entender tecnologias de segurança de perímetro
5. Aplicar conceitos de Zero Trust Architecture

### Descrição da Aula

Esta aula aborda os fundamentos de arquitetura de redes seguras, desde a tradicional abordagem perimetral até os conceitos modernos de Zero Trust. O aluno aprenderá a projetar redes com segmentação adequada, configurar firewalls e implementar zonas de segurança.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão e dúvidas |
| 0:30-1:15 | Segmentação | Expositiva | VLANs, subnets, zonas |
| 1:15-2:00 | Zero Trust | Expositiva-dialogada | Princípios e implementação |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:30 | **Lab 3.1** | Prática | Configuração de firewall |
| 3:30-4:30 | **Lab 3.2** | Prática | Projeto de rede segura |
| 4:30-5:00 | Discussão | Colaborativa | Apresentação de projetos |

### Conteúdo Programático Detalhado

#### 1. Segmentação de Rede (45 min)

**Por que segmentar:**
- Limitação de lateral movement
- Contenção de incidentes
- Conformidade regulatória
- Proteção de dados sensíveis

**Tecnologias de Segmentação:**
- **VLANs:** Segmentação lógica Layer 2
- **Subnets:** Segmentação Layer 3
- **Micro-segmentação:** Software-defined (NSX, ACI)
- **Air gap:** Isolamento físico

**Zonas de Segurança:**
- **DMZ:** Serviços públicos
- **Intranet:** Recursos internos
- **Extranet:** Parceiros
- **Management Zone:** Administração
- **Data Zone:** Bancos de dados

#### 2. Dispositivos de Segurança (30 min)

**Firewall:**
- Stateless vs Stateful
- Next-Generation Firewall (NGFW)
- Regras: source, destination, port, action
- Application-aware filtering

**Outros dispositivos:**
- **IDS/IPS:** Detecção/Prevenção de intrusão
- **WAF:** Web Application Firewall
- **NAC:** Network Access Control
- **Proxy:** Forward e reverse

#### 3. Zero Trust Architecture (30 min)

**Princípios:**
- Never trust, always verify
- Assume breach
- Verify explicitly
- Least privilege access

**Componentes:**
- Identity-centric security
- Micro-segmentation
- Continuous verification
- Device trust

**NIST SP 800-207 Zero Trust Architecture**

### Atividades Práticas

#### Laboratório 3.1: Configuração de Firewall (75 min)

**Ambiente:** pfSense em VM

**Objetivo:** Configurar firewall com múltiplas zonas

**Tarefas:**
1. Criar interfaces: WAN, LAN, DMZ
2. Configurar regras de firewall:
   - Permitir HTTP/HTTPS da WAN para DMZ
   - Permitir SSH da LAN para DMZ
   - Bloquear DMZ para LAN
   - Permitir LAN para Internet
3. Configurar NAT
4. Testar conectividade
5. Analisar logs

**Entregável:** Screenshot das regras + relatório de testes

#### Laboratório 3.2: Projeto de Rede Segura (60 min)

**Cenário:** Empresa de fintech com 200 funcionários

**Requisitos:**
- Aplicação web para clientes
- Sistema interno ERP
- Banco de dados com dados financeiros
- VPN para trabalho remoto
- Compliance PCI-DSS

**Tarefas:**
1. Desenhar topologia de rede
2. Definir zonas de segurança
3. Especificar regras de firewall
4. Planejar segmentação interna
5. Incluir elementos de Zero Trust

**Entregável:** Diagrama + documento de especificação

### Abordagem Metodológica

- **Expositiva:** Conceitos de arquitetura
- **Demonstração:** Configuração de firewall
- **Hands-on:** Labs práticos
- **PBL:** Projeto de rede

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 3.1 | 40% | Configuração correta do firewall |
| Lab 3.2 | 50% | Projeto completo e adequado |
| Participação | 10% | Discussão e apresentação |

### Referências Bibliográficas

1. NIST. **SP 800-207: Zero Trust Architecture**. 2020.
2. NORTHCUTT, Stephen. **Network Perimeter Security**. New Riders, 2006.
3. CISCO. **SAFE Reference Architecture**. 2023.

---

## AULA 4: Fundamentos de Criptografia

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 4 de 8 |
| **Tema** | Fundamentos de Criptografia |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 4 |

### Objetivos da Aula

**Objetivo Geral:**
Compreender e aplicar técnicas criptográficas para proteção de dados em repouso e em trânsito.

**Objetivos Específicos:**
1. Diferenciar criptografia simétrica e assimétrica
2. Compreender funções hash e suas aplicações
3. Aplicar assinaturas digitais e certificados
4. Configurar TLS/SSL para comunicações seguras
5. Entender PKI (Public Key Infrastructure)

### Descrição da Aula

Esta aula apresenta os fundamentos da criptografia moderna, desde os algoritmos básicos até a infraestrutura de chaves públicas. O aluno aprenderá quando e como aplicar diferentes técnicas criptográficas para proteger dados em diversos cenários.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão e contextualização |
| 0:30-1:15 | Criptografia Simétrica/Assimétrica | Expositiva | AES, RSA, ECC |
| 1:15-2:00 | Hash e Assinaturas | Expositiva-dialogada | SHA, HMAC, certificados |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:30 | **Lab 4.1** | Prática | Operações criptográficas com OpenSSL |
| 3:30-4:30 | **Lab 4.2** | Prática | Configuração de TLS/certificados |
| 4:30-5:00 | Quiz | Avaliativa | Avaliação de conhecimentos |

### Conteúdo Programático Detalhado

#### 1. Criptografia Simétrica (25 min)

**Conceito:** Mesma chave para cifrar e decifrar

**Algoritmos:**
- **AES (Advanced Encryption Standard):** 128, 192, 256 bits - Padrão atual
- **3DES:** Legado, em desuso
- **ChaCha20:** Alternativa moderna ao AES

**Modos de operação:**
- ECB: Inseguro
- CBC: Comum, precisa de IV
- GCM: Autenticado, preferido
- CTR: Stream cipher mode

**Aplicações:** Criptografia de disco, VPNs, bases de dados

#### 2. Criptografia Assimétrica (25 min)

**Conceito:** Par de chaves (pública e privada)

**Algoritmos:**
- **RSA:** 2048-4096 bits, mais comum
- **ECC (Elliptic Curve):** Chaves menores, mesma segurança
- **DSA:** Apenas assinaturas

**Aplicações:**
- Troca de chaves
- Assinaturas digitais
- Certificados

**Trade-offs:** Mais seguro, porém mais lento que simétrico

#### 3. Hash e Integridade (20 min)

**Funções Hash:**
- **MD5:** Quebrado, não usar
- **SHA-1:** Deprecado
- **SHA-256/SHA-3:** Recomendados
- Propriedades: determinístico, one-way, collision resistant

**Aplicações:**
- Verificação de integridade
- Armazenamento de senhas (com salt)
- Blockchain

**HMAC:** Hash com chave para autenticação de mensagens

#### 4. PKI e Certificados (20 min)

**Componentes PKI:**
- CA (Certificate Authority)
- RA (Registration Authority)
- Repositório de certificados
- CRL/OCSP

**Certificado X.509:**
- Subject, Issuer, Validity
- Public Key
- Extensions (SAN, EKU)
- Signature

**Cadeia de confiança:** Root CA → Intermediate CA → End Entity

### Atividades Práticas

#### Laboratório 4.1: Operações Criptográficas com OpenSSL (75 min)

**Ambiente:** Linux com OpenSSL

**Tarefas:**

1. **Criptografia Simétrica:**
```bash
# Gerar chave aleatória
openssl rand -hex 32 > key.txt

# Cifrar arquivo com AES-256-GCM
openssl enc -aes-256-gcm -in plaintext.txt -out encrypted.bin -K $(cat key.txt) -iv $(openssl rand -hex 12)

# Decifrar
openssl enc -d -aes-256-gcm -in encrypted.bin -out decrypted.txt -K $(cat key.txt) -iv [IV usado]
```

2. **Criptografia Assimétrica:**
```bash
# Gerar par de chaves RSA
openssl genrsa -out private.pem 2048
openssl rsa -in private.pem -pubout -out public.pem

# Cifrar com chave pública
openssl rsautl -encrypt -pubin -inkey public.pem -in plaintext.txt -out encrypted.bin

# Decifrar com chave privada
openssl rsautl -decrypt -inkey private.pem -in encrypted.bin -out decrypted.txt
```

3. **Hashing:**
```bash
# Gerar hash SHA-256
openssl dgst -sha256 file.txt

# Verificar integridade
openssl dgst -sha256 -verify public.pem -signature sig.bin file.txt
```

4. **Assinatura Digital:**
```bash
# Assinar arquivo
openssl dgst -sha256 -sign private.pem -out sig.bin file.txt

# Verificar assinatura
openssl dgst -sha256 -verify public.pem -signature sig.bin file.txt
```

**Entregável:** Relatório com comandos executados e outputs

#### Laboratório 4.2: Configuração de TLS (60 min)

**Objetivo:** Configurar servidor web com HTTPS

**Ambiente:** Nginx em VM

**Tarefas:**
1. Gerar CSR (Certificate Signing Request)
2. Criar certificado auto-assinado (para lab)
3. Configurar Nginx com TLS 1.3
4. Testar com `openssl s_client`
5. Analisar com SSL Labs (se possível) ou `testssl.sh`

**Configuração exemplo:**
```nginx
server {
    listen 443 ssl http2;
    ssl_certificate /etc/nginx/ssl/cert.pem;
    ssl_certificate_key /etc/nginx/ssl/key.pem;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;
    ssl_prefer_server_ciphers on;
}
```

**Entregável:** Configuração + relatório de testes

### Abordagem Metodológica

- **Expositiva:** Conceitos criptográficos
- **Demonstração:** Comandos OpenSSL
- **Hands-on:** Labs práticos
- **Análise:** Configurações seguras vs inseguras

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Quiz | 25% | Conceitos de criptografia |
| Lab 4.1 | 40% | Execução correta das operações |
| Lab 4.2 | 35% | Configuração TLS funcional e segura |

### Referências Bibliográficas

1. FERGUSON, Niels; SCHNEIER, Bruce. **Practical Cryptography**. Wiley, 2003.
2. STALLINGS, William. **Cryptography and Network Security**. 8th ed. Pearson, 2023.
3. NIST. **SP 800-175B: Guideline for Using Cryptographic Standards**. 2020.

---

## AULA 5: Autenticação, Autorização e IAM

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 5 de 8 |
| **Tema** | Autenticação, Autorização e Identity Access Management |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 5 |

### Objetivos da Aula

**Objetivo Geral:**
Implementar sistemas de autenticação e autorização seguros em ambientes corporativos.

**Objetivos Específicos:**
1. Implementar autenticação multifator (MFA)
2. Configurar sistemas de Single Sign-On (SSO)
3. Aplicar modelos de controle de acesso (RBAC, ABAC)
4. Entender protocolos de autenticação (OAuth 2.0, SAML, OIDC)
5. Gerenciar identidades em ambientes híbridos

### Descrição da Aula

Esta aula aborda os mecanismos de gestão de identidades e acessos, essenciais para a segurança de qualquer organização. O aluno aprenderá a implementar autenticação forte, configurar SSO e aplicar modelos de autorização adequados.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão da aula anterior |
| 0:30-1:15 | Autenticação | Expositiva | MFA, protocolos, biometria |
| 1:15-2:00 | Autorização e IAM | Expositiva-dialogada | RBAC, ABAC, PAM |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:30 | **Lab 5.1** | Prática | Configuração de MFA |
| 3:30-4:30 | **Lab 5.2** | Prática | Implementação de RBAC |
| 4:30-5:00 | Discussão | Colaborativa | Casos de uso e desafios |

### Conteúdo Programático Detalhado

#### 1. Autenticação (45 min)

**Fatores de Autenticação:**
- **Algo que você sabe:** Senha, PIN
- **Algo que você tem:** Token, smartphone, smart card
- **Algo que você é:** Biometria (fingerprint, face, iris)

**Autenticação Multifator (MFA):**
- Combinação de 2+ fatores
- TOTP (Time-based One-Time Password)
- FIDO2/WebAuthn
- Push notifications
- SMS (não recomendado)

**Protocolos:**
- **SAML 2.0:** Enterprise SSO, XML-based
- **OAuth 2.0:** Authorization framework
- **OpenID Connect (OIDC):** Identity layer on OAuth 2.0
- **RADIUS/TACACS+:** Network authentication

#### 2. Autorização (30 min)

**Modelos de Controle de Acesso:**

**DAC (Discretionary Access Control):**
- Proprietário define permissões
- Exemplo: permissões de arquivos Unix/Windows

**MAC (Mandatory Access Control):**
- Sistema define permissões baseado em labels
- Exemplo: SELinux, classificação militar

**RBAC (Role-Based Access Control):**
- Permissões atribuídas a roles
- Usuários atribuídos a roles
- Mais comum em enterprises

**ABAC (Attribute-Based Access Control):**
- Decisões baseadas em atributos
- Contexto: usuário, recurso, ambiente, ação
- Mais flexível, mais complexo

#### 3. Identity Access Management (15 min)

**Componentes IAM:**
- Directory Services (AD, LDAP)
- Identity Provider (IdP)
- Access Management
- Identity Governance

**Privileged Access Management (PAM):**
- Vault de credenciais privilegiadas
- Just-in-time access
- Session recording
- Least privilege

### Atividades Práticas

#### Laboratório 5.1: Configuração de MFA (75 min)

**Ambiente:** Servidor Linux com Apache/Nginx + Google Authenticator

**Tarefas:**
1. Instalar e configurar libpam-google-authenticator
2. Configurar SSH com MFA
3. Testar autenticação com app TOTP
4. Configurar backup codes
5. Documentar processo

**Entregável:** Relatório de configuração com evidências

#### Laboratório 5.2: Implementação de RBAC (60 min)

**Cenário:** Sistema de gestão hospitalar

**Roles definidos:**
- Médico: acesso a prontuários de seus pacientes
- Enfermeiro: acesso limitado a prontuários
- Recepcionista: agendamento, dados cadastrais
- Admin: gestão de usuários
- Auditor: logs de acesso (somente leitura)

**Tarefas:**
1. Modelar roles e permissões
2. Implementar em banco de dados (SQL)
3. Criar consultas de verificação de acesso
4. Testar cenários de acesso
5. Documentar modelo

**Entregável:** Modelo de dados + scripts SQL + documentação

### Abordagem Metodológica

- **Expositiva dialogada:** Conceitos de IAM
- **Demonstração:** Fluxos de autenticação
- **Hands-on:** Configuração de MFA e RBAC
- **Estudo de caso:** Problemas de IAM em empresas

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 5.1 | 40% | MFA funcionando corretamente |
| Lab 5.2 | 45% | Modelo RBAC completo e funcional |
| Participação | 15% | Discussão de casos |

### Referências Bibliográficas

1. BENANTAR, Messaoud. **Access Control Systems: Security, Identity Management and Trust Models**. Springer, 2006.
2. NIST. **SP 800-63B: Digital Identity Guidelines**. 2020.
3. FIDO Alliance. **FIDO2 Specifications**. 2024.

---

## AULA 6: Segurança de Sistemas Operacionais

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 6 de 8 |
| **Tema** | Segurança de Sistemas Operacionais |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h teoria / 3.5h prática |
| **Data Sugerida** | Semana 6 |

### Objetivos da Aula

**Objetivo Geral:**
Implementar hardening em sistemas operacionais Windows e Linux.

**Objetivos Específicos:**
1. Aplicar técnicas de hardening em Windows Server
2. Aplicar técnicas de hardening em Linux
3. Configurar políticas de segurança (GPO, SELinux)
4. Implementar logging e auditoria
5. Utilizar benchmarks de segurança (CIS)

### Descrição da Aula

Esta aula foca na segurança de sistemas operacionais, capacitando o aluno a configurar servidores de forma segura seguindo melhores práticas e benchmarks reconhecidos como CIS.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão e contextualização |
| 0:30-1:15 | Windows Hardening | Expositiva | GPO, Windows Security |
| 1:15-1:45 | Linux Hardening | Expositiva | SELinux, AppArmor |
| 1:45-2:00 | **Intervalo** | - | - |
| 2:00-3:15 | **Lab 6.1** | Prática | Hardening Windows |
| 3:15-4:30 | **Lab 6.2** | Prática | Hardening Linux |
| 4:30-5:00 | Quiz | Avaliativa | Avaliação de conhecimentos |

### Conteúdo Programático Detalhado

#### 1. Hardening Windows (45 min)

**Group Policy Objects (GPO):**
- Políticas de senha
- Bloqueio de conta
- Auditoria de eventos
- Restrições de software

**Windows Security Features:**
- Windows Defender
- Credential Guard
- Device Guard
- BitLocker

**CIS Benchmark Windows Server:**
- Account Policies
- Local Policies
- Event Log Settings
- System Services

#### 2. Hardening Linux (30 min)

**Segurança Básica:**
- Gerenciamento de usuários
- Permissões de arquivos
- sudo e limitações
- Serviços desnecessários

**Mandatory Access Control:**
- **SELinux:** Enforcing, Permissive, Disabled
- **AppArmor:** Profiles e enforcement

**Auditoria:**
- auditd
- rsyslog
- journald

**CIS Benchmark Linux:**
- Filesystem Configuration
- Software Updates
- Secure Boot Settings
- Network Configuration

### Atividades Práticas

#### Laboratório 6.1: Hardening Windows Server (75 min)

**Ambiente:** Windows Server 2022 em VM

**Tarefas baseadas no CIS Benchmark:**

1. **Políticas de Conta:**
   - Password minimum length: 14
   - Password complexity: Enabled
   - Account lockout threshold: 5 attempts
   - Account lockout duration: 30 minutes

2. **Políticas Locais:**
   - Rename Administrator account
   - Disable Guest account
   - Audit logon events: Success, Failure

3. **Serviços:**
   - Desabilitar serviços desnecessários
   - Configurar Windows Firewall

4. **Windows Defender:**
   - Configurar proteções
   - Atualizar definições

**Entregável:** Relatório de configurações aplicadas + evidências

#### Laboratório 6.2: Hardening Linux (75 min)

**Ambiente:** Ubuntu Server 22.04 ou Rocky Linux 9

**Tarefas baseadas no CIS Benchmark:**

1. **Filesystem:**
```bash
# Verificar partições
df -h
# Configurar opções de montagem
# /tmp com noexec, nosuid, nodev
```

2. **Usuários e Grupos:**
```bash
# Configurar política de senhas
/etc/login.defs
# Configurar PAM
/etc/pam.d/common-password
```

3. **Serviços:**
```bash
# Listar serviços
systemctl list-units --type=service
# Desabilitar desnecessários
systemctl disable <service>
```

4. **Firewall:**
```bash
# Configurar UFW ou firewalld
ufw default deny incoming
ufw allow ssh
ufw enable
```

5. **Auditoria:**
```bash
# Instalar auditd
apt install auditd
# Configurar regras
/etc/audit/rules.d/
```

**Entregável:** Script de hardening + relatório

### Abordagem Metodológica

- **Expositiva:** Conceitos de hardening
- **Demonstração:** Configurações de segurança
- **Hands-on:** Labs práticos
- **Checklist:** Seguir benchmarks CIS

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Quiz | 20% | Conceitos de hardening |
| Lab 6.1 | 40% | Hardening Windows completo |
| Lab 6.2 | 40% | Hardening Linux completo |

### Referências Bibliográficas

1. CIS. **CIS Benchmark for Windows Server 2022**. 2024.
2. CIS. **CIS Benchmark for Ubuntu Linux 22.04 LTS**. 2024.
3. NSA. **Hardening Guide for Windows 10/11**. 2023.
4. Red Hat. **Security Hardening Guide**. 2024.

---

## AULA 7: Ameaças, Vulnerabilidades e Ataques

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 7 de 8 |
| **Tema** | Ameaças, Vulnerabilidades e Ataques Contemporâneos |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |
| **Data Sugerida** | Semana 7 |

### Objetivos da Aula

**Objetivo Geral:**
Compreender o cenário atual de ameaças e técnicas de ataque utilizadas por adversários.

**Objetivos Específicos:**
1. Classificar tipos de malware e suas características
2. Entender técnicas de engenharia social
3. Conhecer o MITRE ATT&CK Framework
4. Analisar ataques comuns (ransomware, phishing, supply chain)
5. Identificar indicadores de comprometimento (IOCs)

### Descrição da Aula

Esta aula apresenta o cenário contemporâneo de ameaças cibernéticas, desde malware tradicional até ataques sofisticados de APTs. O aluno aprenderá a identificar técnicas de ataque utilizando o framework MITRE ATT&CK e analisar indicadores de comprometimento.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Revisão e contextualização |
| 0:30-1:15 | Malware e Ameaças | Expositiva | Tipos, características, evolução |
| 1:15-2:00 | MITRE ATT&CK | Expositiva-dialogada | Framework, técnicas, mitigações |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:30 | **Lab 7.1** | Prática | Análise de malware (estático) |
| 3:30-4:30 | **Lab 7.2** | Prática | Mapeamento MITRE ATT&CK |
| 4:30-5:00 | Discussão | Colaborativa | Casos recentes |

### Conteúdo Programático Detalhado

#### 1. Taxonomia de Malware (45 min)

**Tipos de Malware:**
- **Vírus:** Replicação via arquivos host
- **Worm:** Auto-propagação pela rede
- **Trojan:** Disfarçado de software legítimo
- **Ransomware:** Criptografa dados, exige resgate
- **Spyware:** Coleta informações
- **Rootkit:** Esconde presença no sistema
- **RAT:** Remote Access Trojan
- **Botnet:** Rede de máquinas comprometidas

**Ameaças Contemporâneas:**
- Ransomware-as-a-Service (RaaS)
- Supply chain attacks
- Living off the land (LOLBins)
- Fileless malware
- AI-powered attacks

**Engenharia Social:**
- Phishing (email, spear, whaling)
- Vishing (voice)
- Smishing (SMS)
- Pretexting
- Baiting

#### 2. MITRE ATT&CK Framework (45 min)

**Estrutura:**
- Táticas: O que o adversário quer
- Técnicas: Como o adversário faz
- Procedimentos: Implementação específica

**Táticas (14):**
1. Reconnaissance
2. Resource Development
3. Initial Access
4. Execution
5. Persistence
6. Privilege Escalation
7. Defense Evasion
8. Credential Access
9. Discovery
10. Lateral Movement
11. Collection
12. Command and Control
13. Exfiltration
14. Impact

**Uso do ATT&CK:**
- Threat intelligence
- Detection engineering
- Red team operations
- Security assessment

### Atividades Práticas

#### Laboratório 7.1: Análise Estática de Malware (75 min)

**Ambiente:** REMnux ou Flare VM (sandbox)

**Amostra:** Malware educacional (safe sample)

**Tarefas:**
1. **Coleta de informações básicas:**
```bash
file sample.exe
strings sample.exe | head -50
```

2. **Hashes:**
```bash
md5sum sample.exe
sha256sum sample.exe
```

3. **Consulta em bases de threat intel:**
   - VirusTotal
   - MalwareBazaar
   - Hybrid Analysis

4. **Análise de imports/exports:**
```bash
pe-tree sample.exe
# ou objdump -p sample.exe
```

5. **Identificação de IOCs:**
   - URLs
   - IPs
   - Registry keys
   - File paths

**Entregável:** Relatório de análise com IOCs identificados

#### Laboratório 7.2: Mapeamento MITRE ATT&CK (60 min)

**Cenário:** Analisar relatório de incidente de ransomware

**Tarefas:**
1. Ler relatório de incidente fornecido
2. Identificar táticas e técnicas utilizadas
3. Mapear no ATT&CK Navigator
4. Identificar gaps de detecção
5. Propor mitigações

**Entregável:** Matriz ATT&CK preenchida + recomendações

### Abordagem Metodológica

- **Expositiva:** Taxonomia de malware
- **Estudo de caso:** Ataques recentes
- **Hands-on:** Análise de malware
- **Colaborativa:** Mapeamento ATT&CK

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 7.1 | 45% | Análise completa e IOCs corretos |
| Lab 7.2 | 45% | Mapeamento correto e mitigações adequadas |
| Participação | 10% | Discussão de casos |

### Referências Bibliográficas

1. MITRE. **ATT&CK Framework**. 2024. https://attack.mitre.org/
2. SIKORSKI, Michael; HONIG, Andrew. **Practical Malware Analysis**. No Starch Press, 2012.
3. HADNAGY, Christopher. **Social Engineering: The Science of Human Hacking**. 2nd ed. Wiley, 2018.

---

## AULA 8: Revisão Security+ e CTF do Módulo

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 8 de 8 |
| **Tema** | Revisão CompTIA Security+ e CTF Avaliativo |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h teoria / 4h prática |
| **Data Sugerida** | Semana 8 |

### Objetivos da Aula

**Objetivo Geral:**
Consolidar os conhecimentos do módulo e avaliar competências através de CTF.

**Objetivos Específicos:**
1. Revisar conteúdos alinhados ao Security+
2. Resolver desafios práticos de CTF
3. Aplicar conhecimentos integrados
4. Preparar-se para a certificação Security+

### Descrição da Aula

Esta aula final do módulo é dividida em revisão dos conceitos alinhados à certificação CompTIA Security+ e um CTF avaliativo que testa as competências desenvolvidas ao longo do módulo.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:15 | Abertura | Orientação | Instruções do CTF |
| 0:15-1:00 | Revisão Security+ | Expositiva | Principais domínios |
| 1:00-1:15 | **Intervalo** | - | - |
| 1:15-4:15 | **CTF do Módulo** | Prática/Avaliativa | Capture The Flag |
| 4:15-4:45 | Debriefing | Discussão | Resolução dos desafios |
| 4:45-5:00 | Encerramento | Feedback | Avaliação do módulo |

### Conteúdo Programático

#### Revisão Security+ (45 min)

**Domínios do Exame SY0-701:**

1. **General Security Concepts (12%)**
   - CIA, AAA, Zero Trust
   - Controles de segurança
   - Change management

2. **Threats, Vulnerabilities, and Mitigations (22%)**
   - Tipos de ataques
   - Malware
   - Mitigações

3. **Security Architecture (18%)**
   - Arquitetura segura
   - Virtualização
   - Cloud security

4. **Security Operations (28%)**
   - Monitoramento
   - Resposta a incidentes
   - Automação

5. **Security Program Management and Oversight (20%)**
   - Governança
   - Compliance
   - Gestão de riscos

### CTF do Módulo

**Formato:** Jeopardy-style CTF

**Categorias de Desafios:**

1. **Criptografia (4 desafios)**
   - Decodificar mensagem cifrada
   - Identificar algoritmo vulnerável
   - Quebrar hash fraco
   - Analisar certificado

2. **Redes (4 desafios)**
   - Analisar captura de tráfego
   - Identificar ataque em PCAP
   - Configurar firewall corretamente
   - Identificar segmentação inadequada

3. **Sistemas (4 desafios)**
   - Identificar configuração insegura
   - Hardening challenge
   - Privilege escalation
   - Log analysis

4. **Análise de Riscos (3 desafios)**
   - Calcular ALE
   - Mapear controles para framework
   - Priorizar vulnerabilidades

5. **Misc (5 desafios)**
   - Phishing analysis
   - OSINT challenge
   - Password cracking
   - Steganography
   - Trivia Security+

**Pontuação:**
- Fácil: 100 pontos
- Médio: 200 pontos
- Difícil: 300 pontos
- Total possível: ~3000 pontos

**Plataforma:** CTFd

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| CTF | 100% | Pontuação obtida (mínimo 40% para aprovação) |

**Conversão de Pontuação:**
- 90-100%: A (9-10)
- 80-89%: B (8-8.9)
- 70-79%: C (7-7.9)
- 60-69%: D (6-6.9)
- <60%: Recuperação necessária

### Referências Bibliográficas

1. CompTIA. **CompTIA Security+ Study Guide (SY0-701)**. Sybex, 2024.
2. CompTIA. **Security+ Practice Tests**. 2024.
3. Gibson, Darril. **CompTIA Security+ Get Certified Get Ahead**. 2024.

---

## Bibliografia Completa do Módulo

### Referências Básicas

1. STALLINGS, William; BROWN, Lawrie. **Segurança de Computadores: Princípios e Práticas**. 2ª ed. Rio de Janeiro: Elsevier, 2014.

2. CompTIA. **CompTIA Security+ Study Guide (SY0-701)**. Indianapolis: Sybex, 2024.

3. NIST. **Cybersecurity Framework 2.0**. Gaithersburg: NIST, 2024.

4. HARRIS, Shon. **CISSP All-in-One Exam Guide**. 9th ed. New York: McGraw-Hill, 2024.

### Referências Complementares

5. ISO/IEC 27001:2022 - Information Security Management Systems

6. NIST. **SP 800-53 Rev. 5: Security and Privacy Controls**. 2020.

7. CIS. **CIS Controls v8**. 2021.

8. MITRE. **ATT&CK Framework**. 2024.

9. SIKORSKI, Michael; HONIG, Andrew. **Practical Malware Analysis**. San Francisco: No Starch Press, 2012.

10. FERGUSON, Niels; SCHNEIER, Bruce. **Practical Cryptography**. Indianapolis: Wiley, 2003.

### Recursos Online

- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
- MITRE ATT&CK: https://attack.mitre.org/
- CIS Benchmarks: https://www.cisecurity.org/cis-benchmarks/
- OWASP: https://owasp.org/
- CompTIA Security+: https://www.comptia.org/certifications/security

---

*Documento parte integrante do PPC do MBA em Cibersegurança e Inteligência Artificial*

*CECyber - Academia de Cibersegurança*
