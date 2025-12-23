# Exemplos Práticos de Templates Preenchidos

Esta pasta contém exemplos práticos de cada template, baseados em **casos reais** de cibersegurança e melhores práticas do mercado.

## Objetivos Educacionais

Estes exemplos foram elaborados para:

1. **Demonstrar aplicação prática** dos templates em cenários reais
2. **Ilustrar lições aprendidas** de incidentes famosos
3. **Servir como referência** para projetos próprios
4. **Facilitar o aprendizado** através de casos concretos

---

## Índice de Exemplos

| # | Template | Caso Base | Descrição |
|---|----------|-----------|-----------|
| 01 | [Risk Assessment](01-exemplo-risk-assessment-equifax.md) | **Equifax 2017** | Avaliação de riscos demonstrando como CVE-2017-5638 poderia ter sido identificado |
| 02 | [NIST CSF Profile](02-exemplo-nist-csf-fintech-brasil.md) | **Fintech Brasileira** | Perfil de segurança baseado em práticas do Nubank e requisitos BACEN |
| 03 | [Security Architecture](03-exemplo-security-architecture-fintech.md) | **Arquitetura Cloud-Native** | Arquitetura de segurança completa para banco digital |
| 04 | [Incident Response](04-exemplo-incident-response-colonial-pipeline.md) | **Colonial Pipeline 2021** | Playbook detalhado do maior ataque de ransomware a infraestrutura crítica dos EUA |
| 05 | [LLM Security Checklist](05-exemplo-llm-security-checklist-samsung.md) | **Samsung/ChatGPT 2023** | Checklist demonstrando falhas que levaram ao vazamento de código fonte |
| 06 | [AI Governance Policy](06-exemplo-ai-governance-policy-techcorp.md) | **Melhores Práticas** | Política completa baseada em Microsoft RAI, NIST AI RMF e requisitos brasileiros |
| 07 | [CTF Writeup](07-exemplo-ctf-writeup-htb-usage.md) | **HackTheBox Usage** | Writeup educacional de SQL Injection + Privilege Escalation |

---

## Casos Reais Referenciados

### Equifax (2017)
- **O que aconteceu**: Vazamento de 147,9 milhões de registros
- **Causa**: CVE-2017-5638 (Apache Struts) não corrigido
- **Lição**: Importância crítica de patch management

### Colonial Pipeline (2021)
- **O que aconteceu**: Ransomware paralisou 45% do combustível da Costa Leste dos EUA
- **Causa**: Senha de VPN comprometida sem MFA
- **Lição**: MFA obrigatório para todos os acessos remotos

### Samsung/ChatGPT (2023)
- **O que aconteceu**: Código fonte e dados confidenciais vazados via ChatGPT
- **Causa**: Ausência de políticas e controles para uso de LLMs
- **Lição**: Governança de IA antes de liberar ferramentas

### HackTheBox Usage (2024)
- **Vulnerabilidades**: SQL Injection, Arbitrary File Upload, Wildcard Injection
- **Lição**: Importância de testes de segurança em aplicações web

---

## Como Usar Estes Exemplos

### Para Estudos
1. Leia o exemplo completo para entender o contexto
2. Compare com o template vazio correspondente
3. Identifique os pontos-chave de cada seção

### Para Projetos Reais
1. Use como ponto de partida, **não copie diretamente**
2. Adapte para o contexto específico da sua organização
3. Atualize dados, métricas e responsáveis
4. Revise com especialistas antes de oficializar

### Para Apresentações
1. Extraia diagramas e tabelas relevantes
2. Cite as fontes originais dos casos
3. Adapte o nível de detalhe para a audiência

---

## Fontes e Referências

### Incidentes
- [Wikipedia - Equifax Data Breach](https://en.wikipedia.org/wiki/2017_Equifax_data_breach)
- [CISA - Colonial Pipeline](https://www.cisa.gov/news-events/news/attack-colonial-pipeline-what-weve-learned-what-weve-done-over-past-two-years)
- [CyberNews - Samsung ChatGPT Leak](https://cybernews.com/security/chatgpt-samsung-leak-explained-lessons/)

### Frameworks
- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- [Microsoft Responsible AI](https://www.microsoft.com/en-us/ai/responsible-ai)

### Regulamentações
- [LGPD - Lei 13.709/2018](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/L13709.htm)
- [Resolução BACEN 4.893/2021](https://www.bcb.gov.br/)

---

## Avisos Importantes

> **Uso Educacional**: Estes exemplos são para fins educacionais. Dados sensíveis foram removidos ou substituídos por valores fictícios.

> **Não Copiar Diretamente**: Cada organização tem contexto único. Use como inspiração, não como solução pronta.

> **Manter Atualizado**: Frameworks e regulamentações evoluem. Verifique versões atuais antes de usar em produção.

---

*MBA Cibersegurança & Inteligência Artificial*
