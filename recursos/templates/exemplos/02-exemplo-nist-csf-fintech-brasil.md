# NIST CSF Profile - Fintech Brasileira
## Perfil de Segurança Cibernética (Exemplo Baseado em Práticas de Mercado)

> **Nota**: Este documento é um exemplo educacional baseado em práticas públicas de fintechs brasileiras e requisitos regulatórios do BACEN. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## 1. Informações da Organização

| Campo | Descrição |
|-------|-----------|
| **Nome da Organização** | NeoBank Brasil S.A. (Exemplo Fictício) |
| **Setor** | Serviços Financeiros - Fintech / Banco Digital |
| **Tamanho** | Grande (>5.000 funcionários, >50M clientes) |
| **Data de Criação do Perfil** | Janeiro 2025 |
| **Versão do CSF** | 2.0 |
| **Responsável** | CISO - Chief Information Security Officer |

---

## 2. Objetivo do Perfil

### 2.1 Tipo de Perfil
- [x] Perfil Atual (Current Profile) - Estado atual da postura de segurança
- [x] Perfil Alvo (Target Profile) - Estado desejado de segurança
- [ ] Perfil Comunitário - Baseado em setor específico

### 2.2 Propósito
```
[x] Avaliação inicial de maturidade
[x] Comunicação com stakeholders
[x] Planejamento de melhorias
[x] Conformidade regulatória (BACEN, LGPD, PCI-DSS)
[x] Gestão de riscos de terceiros
[ ] Outro: _______________
```

---

## 3. Contexto Organizacional

### 3.1 Ativos Críticos
| Categoria | Descrição | Prioridade |
|-----------|-----------|------------|
| Sistemas de Missão Crítica | Core Banking (processamento de transações), PIX, Cartões | Crítica |
| Dados Sensíveis | PII de 50M+ clientes, dados financeiros, KYC/AML | Crítica |
| Infraestrutura de IA/ML | Modelos de crédito, detecção de fraude, chatbots | Alta |
| Propriedade Intelectual | Algoritmos proprietários, código-fonte | Alta |

### 3.2 Requisitos Regulatórios
| Regulamentação | Aplicável | Requisitos Chave |
|----------------|-----------|------------------|
| **LGPD** | **Sim** | Consentimento, DPIA, direitos dos titulares, notificação de incidentes |
| **Resolução BACEN 4.893/2021** | **Sim** | Política de segurança cibernética, testes de intrusão, gestão de incidentes |
| **Resolução CMN 4.658/2018** | **Sim** | Contratação de nuvem, processamento de dados |
| **PCI-DSS v4.0** | **Sim** | Segurança de dados de cartão, criptografia, acesso |
| **ISO 27001** | **Sim** | SGSI certificado |
| **SOX** | Sim (IPO) | Controles financeiros |
| **Open Finance Brasil** | **Sim** | APIs seguras, consentimento, compartilhamento |

### 3.3 Tolerância a Riscos
| Categoria | Nível Aceitável | Justificativa |
|-----------|-----------------|---------------|
| Risco Operacional | **Baixo** | 99.99% uptime requerido |
| Risco de Reputação | **Muito Baixo** | Confiança é core do negócio |
| Risco Financeiro | Médio | Reservas de capital adequadas |
| Risco Regulatório | **Muito Baixo** | Licença bancária em jogo |

---

## 4. Avaliação por Função do CSF 2.0

### Escala de Maturidade (Tiers)
| Tier | Nome | Descrição |
|------|------|-----------|
| 1 | Parcial | Práticas ad-hoc, reativas |
| 2 | Informado | Práticas aprovadas, mas não consistentes |
| 3 | Repetível | Práticas formalizadas e consistentes |
| 4 | Adaptável | Práticas adaptativas, melhoria contínua |

---

### 4.1 GOVERN (GV) - Governar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Contexto Organizacional** | Missão e objetivos de segurança definidos | GV.OC-01 | 4 | 4 | 0 | - |
| | Stakeholders identificados | GV.OC-02 | 4 | 4 | 0 | - |
| | Requisitos legais e regulatórios mapeados | GV.OC-03 | 4 | 4 | 0 | - |
| | Ativos críticos identificados | GV.OC-04 | 4 | 4 | 0 | - |
| | Objetivos de resiliência definidos | GV.OC-05 | 3 | 4 | 1 | Média |
| **Estratégia de Gestão de Riscos** | Apetite de risco estabelecido | GV.RM-01 | 4 | 4 | 0 | - |
| | Estratégia de risco documentada | GV.RM-02 | 4 | 4 | 0 | - |
| | Riscos de supply chain considerados | GV.RM-03 | 3 | 4 | 1 | Alta |
| **Papéis e Responsabilidades** | Papéis de segurança definidos | GV.RR-01 | 4 | 4 | 0 | - |
| | Responsabilidades atribuídas | GV.RR-02 | 4 | 4 | 0 | - |
| | Recursos adequados alocados | GV.RR-03 | 4 | 4 | 0 | - |
| **Políticas** | Política de segurança estabelecida | GV.PO-01 | 4 | 4 | 0 | - |
| | Políticas comunicadas | GV.PO-02 | 4 | 4 | 0 | - |
| **Supervisão** | Resultados de segurança monitorados | GV.OV-01 | 4 | 4 | 0 | - |
| | Performance revisada periodicamente | GV.OV-02 | 4 | 4 | 0 | - |
| **Gestão de Riscos de Supply Chain** | Processos SCRM implementados | GV.SC-01 | 3 | 4 | 1 | Alta |
| | Fornecedores avaliados | GV.SC-02 | 3 | 4 | 1 | Alta |

**Média GOVERN: 3.7 → 4.0**

---

### 4.2 IDENTIFY (ID) - Identificar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Ativos** | Inventário de ativos físicos | ID.AM-01 | 4 | 4 | 0 | - |
| | Inventário de software | ID.AM-02 | 4 | 4 | 0 | - |
| | Mapeamento de fluxos de dados | ID.AM-03 | 4 | 4 | 0 | - |
| | Inventário de sistemas externos | ID.AM-04 | 3 | 4 | 1 | Alta |
| | Classificação de ativos por criticidade | ID.AM-05 | 4 | 4 | 0 | - |
| | **Inventário de modelos de IA/ML** | ID.AM-06* | 3 | 4 | 1 | **Alta** |
| **Avaliação de Riscos** | Vulnerabilidades identificadas | ID.RA-01 | 4 | 4 | 0 | - |
| | Threat intelligence utilizada | ID.RA-02 | 4 | 4 | 0 | - |
| | Ameaças identificadas | ID.RA-03 | 4 | 4 | 0 | - |
| | Impactos potenciais analisados | ID.RA-04 | 4 | 4 | 0 | - |
| | Riscos priorizados | ID.RA-05 | 4 | 4 | 0 | - |
| | **Riscos de IA/ML avaliados** | ID.RA-06* | 2 | 4 | 2 | **Crítica** |
| **Melhoria** | Lições aprendidas incorporadas | ID.IM-01 | 4 | 4 | 0 | - |
| | Melhorias implementadas | ID.IM-02 | 4 | 4 | 0 | - |

**Média IDENTIFY: 3.6 → 4.0**

---

### 4.3 PROTECT (PR) - Proteger

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Identidade e Acesso** | Identidades gerenciadas | PR.AA-01 | 4 | 4 | 0 | - |
| | Autenticação robusta (MFA) | PR.AA-02 | 4 | 4 | 0 | - |
| | Acesso baseado em função (RBAC) | PR.AA-03 | 4 | 4 | 0 | - |
| | Credenciais protegidas (Vault) | PR.AA-04 | 4 | 4 | 0 | - |
| | Acesso privilegiado gerenciado (PAM) | PR.AA-05 | 4 | 4 | 0 | - |
| **Conscientização e Treinamento** | Treinamento de segurança | PR.AT-01 | 4 | 4 | 0 | - |
| | Papéis privilegiados treinados | PR.AT-02 | 4 | 4 | 0 | - |
| | **Treinamento em segurança de IA** | PR.AT-03* | 2 | 4 | 2 | **Crítica** |
| **Segurança de Dados** | Dados em repouso protegidos (AES-256) | PR.DS-01 | 4 | 4 | 0 | - |
| | Dados em trânsito protegidos (TLS 1.3) | PR.DS-02 | 4 | 4 | 0 | - |
| | Ativos formalmente gerenciados | PR.DS-03 | 4 | 4 | 0 | - |
| | Backup adequado (3-2-1) | PR.DS-04 | 4 | 4 | 0 | - |
| | Integridade de dados verificada | PR.DS-05 | 4 | 4 | 0 | - |
| | **Dados de treinamento de IA protegidos** | PR.DS-06* | 3 | 4 | 1 | Alta |
| **Segurança de Plataforma** | Configurações de segurança (hardening) | PR.PS-01 | 4 | 4 | 0 | - |
| | Software atualizado | PR.PS-02 | 4 | 4 | 0 | - |
| | Hardware gerenciado | PR.PS-03 | 4 | 4 | 0 | - |
| | Logs ativados | PR.PS-04 | 4 | 4 | 0 | - |
| **Resiliência de Infraestrutura** | Redes protegidas (microsegmentação) | PR.IR-01 | 4 | 4 | 0 | - |
| | Ambientes seguros mantidos | PR.IR-02 | 4 | 4 | 0 | - |

**Média PROTECT: 3.8 → 4.0**

---

### 4.4 DETECT (DE) - Detectar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Monitoramento Contínuo** | Redes monitoradas (NDR) | DE.CM-01 | 4 | 4 | 0 | - |
| | Ambiente físico monitorado | DE.CM-02 | 4 | 4 | 0 | - |
| | Atividade de usuários monitorada (UEBA) | DE.CM-03 | 4 | 4 | 0 | - |
| | Código malicioso detectado (EDR) | DE.CM-04 | 4 | 4 | 0 | - |
| | Acessos não autorizados detectados | DE.CM-05 | 4 | 4 | 0 | - |
| | Dispositivos externos monitorados | DE.CM-06 | 4 | 4 | 0 | - |
| | **Modelos de IA monitorados (drift, adversarial)** | DE.CM-07* | 2 | 4 | 2 | **Crítica** |
| **Análise de Eventos Adversos** | Anomalias detectadas (ML-based) | DE.AE-01 | 4 | 4 | 0 | - |
| | Eventos correlacionados (SIEM) | DE.AE-02 | 4 | 4 | 0 | - |
| | Alertas gerados | DE.AE-03 | 4 | 4 | 0 | - |
| | Impacto estimado | DE.AE-04 | 4 | 4 | 0 | - |

**Média DETECT: 3.6 → 4.0**

---

### 4.5 RESPOND (RS) - Responder

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Incidentes** | Plano de resposta executado | RS.MA-01 | 4 | 4 | 0 | - |
| | Incidentes categorizados | RS.MA-02 | 4 | 4 | 0 | - |
| | Incidentes priorizados | RS.MA-03 | 4 | 4 | 0 | - |
| | Incidentes escalados | RS.MA-04 | 4 | 4 | 0 | - |
| **Análise de Incidentes** | Incidentes investigados | RS.AN-01 | 4 | 4 | 0 | - |
| | Causa raiz determinada | RS.AN-02 | 4 | 4 | 0 | - |
| | Forense realizada | RS.AN-03 | 4 | 4 | 0 | - |
| **Comunicação e Relatórios** | Stakeholders notificados | RS.CO-01 | 4 | 4 | 0 | - |
| | Relatórios de incidentes (BACEN) | RS.CO-02 | 4 | 4 | 0 | - |
| | Informações compartilhadas (ISACs) | RS.CO-03 | 3 | 4 | 1 | Média |
| **Mitigação** | Incidentes contidos | RS.MI-01 | 4 | 4 | 0 | - |
| | Incidentes erradicados | RS.MI-02 | 4 | 4 | 0 | - |

**Média RESPOND: 3.9 → 4.0**

---

### 4.6 RECOVER (RC) - Recuperar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Planejamento de Recuperação** | Plano de recuperação executado | RC.RP-01 | 4 | 4 | 0 | - |
| | Pontos de recuperação selecionados | RC.RP-02 | 4 | 4 | 0 | - |
| | Integridade de backups verificada | RC.RP-03 | 4 | 4 | 0 | - |
| | Funções críticas restauradas (<4h RTO) | RC.RP-04 | 4 | 4 | 0 | - |
| | Integridade de ativos verificada | RC.RP-05 | 4 | 4 | 0 | - |
| | **Modelos de IA restaurados/retreinados** | RC.RP-06* | 2 | 4 | 2 | **Crítica** |
| **Comunicação de Recuperação** | Atividades de recuperação comunicadas | RC.CO-01 | 4 | 4 | 0 | - |
| | Reputação gerenciada | RC.CO-02 | 4 | 4 | 0 | - |

**Média RECOVER: 3.5 → 4.0**

---

## 5. Análise de Gaps

### 5.1 Resumo por Função
| Função | Maturidade Atual (Média) | Maturidade Alvo | Gap |
|--------|-------------------------|-----------------|-----|
| GOVERN | 3.7 | 4.0 | 0.3 |
| IDENTIFY | 3.6 | 4.0 | 0.4 |
| PROTECT | 3.8 | 4.0 | 0.2 |
| DETECT | 3.6 | 4.0 | 0.4 |
| RESPOND | 3.9 | 4.0 | 0.1 |
| RECOVER | 3.5 | 4.0 | 0.5 |
| **GERAL** | **3.7** | **4.0** | **0.3** |

### 5.2 Gaps Críticos Identificados (Segurança de IA/ML)

| # | Subcategoria | Gap | Risco Associado | Ação Recomendada |
|---|--------------|-----|-----------------|------------------|
| 1 | ID.RA-06* (Riscos de IA/ML) | 2 | Modelos de crédito/fraude podem ser manipulados | Implementar AI Risk Assessment Framework |
| 2 | DE.CM-07* (Monitoramento de IA) | 2 | Drift e ataques adversariais não detectados | Deploy de MLOps Security Monitoring |
| 3 | PR.AT-03* (Treinamento IA) | 2 | Equipe não preparada para ameaças a IA | Programa de capacitação em AI Security |
| 4 | RC.RP-06* (Recuperação de IA) | 2 | Sem plano de recuperação para modelos comprometidos | Playbook de IR para sistemas de IA |
| 5 | GV.SC-01/02 (Supply Chain) | 1 | Fornecedores de IA/Cloud não totalmente avaliados | Aprimorar due diligence de fornecedores |

### 5.3 Visualização de Maturidade

```
                    RADAR DE MATURIDADE CSF 2.0

                         GOVERN (3.7)
                              │
                         4.0  │
                              │
                       3.0 ───┼─── 4.0
                              │
              RECOVER    ─────┼─────    IDENTIFY
               (3.5)          │           (3.6)
                              │
                       3.0    │    3.0
                              │
                              │
               RESPOND   ─────┼─────    PROTECT
                (3.9)         │          (3.8)
                              │
                         3.0  │
                              │
                        DETECT (3.6)

    ─── Atual     ─── Alvo (4.0)
```

---

## 6. Roadmap de Implementação

### 6.1 Iniciativas Prioritárias

| Fase | Iniciativa | Subcategorias | Investimento | Responsável |
|------|------------|---------------|--------------|-------------|
| **Q1 2025** | Framework de Riscos de IA/ML | ID.RA-06, GV.RM-03 | R$ 500K | CISO + Head of AI |
| **Q1 2025** | MLOps Security Monitoring | DE.CM-07, PR.DS-06 | R$ 800K | Security Ops + ML Team |
| **Q2 2025** | Programa de Treinamento AI Security | PR.AT-03 | R$ 200K | CISO + RH |
| **Q2 2025** | Playbook de IR para IA | RC.RP-06 | R$ 150K | CSIRT |
| **Q3 2025** | Supply Chain Security Enhancement | GV.SC-01, GV.SC-02 | R$ 400K | Procurement + Security |
| **Q3 2025** | Threat Intel Sharing (FS-ISAC) | RS.CO-03 | R$ 100K | Threat Intel Team |

### 6.2 Métricas de Sucesso
| Métrica | Baseline (Jan 2025) | Meta (Dez 2025) | Método de Medição |
|---------|---------------------|-----------------|-------------------|
| Maturidade Geral CSF | 3.7 | 4.0 | Assessment anual |
| Cobertura de Monitoramento de IA | 40% | 100% | Inventário de modelos |
| Tempo de Detecção de Drift | N/A | <24h | Alertas MLOps |
| Funcionários treinados em AI Security | 5% | 80% | LMS |
| Fornecedores de IA com due diligence | 60% | 100% | Registro de fornecedores |

---

## 7. Controles Específicos para IA/ML

### 7.1 Mapeamento NIST AI RMF ↔ CSF 2.0

| Categoria NIST AI RMF | CSF 2.0 Relacionado | Controle Implementado | Status |
|-----------------------|---------------------|----------------------|--------|
| **MAP (Mapear)** | ID.AM-06, ID.RA-06 | Inventário de 47 modelos em produção | ✅ Parcial |
| | | Risk assessment de modelos de crédito | ⚠️ Em progresso |
| **MEASURE (Medir)** | DE.CM-07, DE.AE-01 | Monitoramento de performance (acurácia, latência) | ✅ |
| | | Métricas de fairness (demographic parity) | ⚠️ Em progresso |
| | | Detecção de adversarial inputs | ❌ Não implementado |
| **MANAGE (Gerenciar)** | RS.MA, RC.RP-06 | Playbook de resposta para falhas de IA | ⚠️ Em desenvolvimento |
| | | Rollback automatizado de modelos | ✅ |
| **GOVERN (Governar)** | GV.* | Comitê de Ética em IA | ✅ |
| | | Política de IA Responsável | ✅ |

### 7.2 Modelos de IA em Produção

| ID | Modelo | Tipo | Criticidade | Dados Utilizados | Monitoramento |
|----|--------|------|-------------|------------------|---------------|
| ML-001 | Credit Scoring v3.2 | XGBoost | Crítica | PII, Financeiro | Performance ✅, Fairness ⚠️ |
| ML-002 | Fraud Detection RT | Neural Network | Crítica | Transacional | Performance ✅, Adversarial ❌ |
| ML-003 | Chatbot Atendimento | LLM (GPT-4) | Alta | Conversacional | Usage ✅, Prompt Injection ⚠️ |
| ML-004 | Document OCR | CNN | Média | Documentos | Performance ✅ |
| ML-005 | Churn Prediction | Random Forest | Média | Comportamental | Performance ✅ |

---

## 8. Conformidade Regulatória

### 8.1 Mapeamento CSF → BACEN

| Resolução BACEN | Requisito | CSF 2.0 | Status |
|-----------------|-----------|---------|--------|
| 4.893/2021 Art. 3º | Política de segurança cibernética | GV.PO-01, GV.PO-02 | ✅ Conforme |
| 4.893/2021 Art. 5º | Procedimentos de prevenção e resposta | RS.MA, RS.MI | ✅ Conforme |
| 4.893/2021 Art. 6º | Testes de continuidade de negócios | RC.RP-01, RC.RP-04 | ✅ Conforme |
| 4.893/2021 Art. 7º | Testes de intrusão anuais | ID.RA-01, PR.PS | ✅ Conforme |
| 4.893/2021 Art. 18º | Comunicação de incidentes relevantes | RS.CO-02 | ✅ Conforme |

### 8.2 Mapeamento CSF → LGPD

| Artigo LGPD | Requisito | CSF 2.0 | Status |
|-------------|-----------|---------|--------|
| Art. 46 | Medidas de segurança | PR.DS, PR.AA | ✅ Conforme |
| Art. 48 | Notificação de incidentes | RS.CO-01, RS.CO-02 | ✅ Conforme |
| Art. 38 | DPIA/RIPD | ID.RA-04, GV.RM | ✅ Conforme |
| Art. 50 | Boas práticas e governança | GV.PO, GV.OV | ✅ Conforme |

---

## 9. Próximos Passos

### 9.1 Ações Imediatas (30 dias)

- [ ] Aprovar orçamento para iniciativas de AI Security
- [ ] Contratar especialista em MLSecOps
- [ ] Iniciar PoC de monitoramento de adversarial attacks
- [ ] Agendar workshops de AI Security para equipes de ML

### 9.2 Ações de Médio Prazo (90 dias)

- [ ] Completar risk assessment de todos os modelos críticos
- [ ] Implementar pipeline de monitoramento de drift
- [ ] Desenvolver playbook de IR para IA
- [ ] Treinar 50% da equipe de tecnologia em AI Security

### 9.3 Ações de Longo Prazo (12 meses)

- [ ] Atingir maturidade 4.0 em todas as funções
- [ ] Certificação ISO 42001 (AI Management System)
- [ ] Implementar red team de IA trimestral
- [ ] Integrar AI security no ciclo de desenvolvimento (AI-DevSecOps)

---

## 10. Aprovações

| Papel | Nome | Data | Assinatura |
|-------|------|------|------------|
| CISO | [Nome] | Jan 2025 | [Exemplo] |
| CTO | [Nome] | Jan 2025 | [Exemplo] |
| Head of AI | [Nome] | Jan 2025 | [Exemplo] |
| DPO | [Nome] | Jan 2025 | [Exemplo] |

---

## 11. Referências

### Fontes Utilizadas

- [Nubank - Cybersecurity Policy](https://nubank.com.br/en/contract/cybersecurity-policy/)
- [Nubank - Building Blog - Reinventing Cyber Risk](https://building.nubank.com/reinventing-it-and-cyber-risk-in-the-financial-market/)
- [BACEN - Resolução 4.893/2021](https://www.bcb.gov.br/estabilidadefinanceira/exibenormativo?tipo=Resolu%C3%A7%C3%A3o%20CMN&numero=4893)
- [ICLG - Fintech Laws Brazil 2024-2025](https://iclg.com/practice-areas/fintech-laws-and-regulations/brazil)
- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

---

*Exemplo educacional baseado em práticas de fintechs brasileiras - MBA Cibersegurança & IA*
