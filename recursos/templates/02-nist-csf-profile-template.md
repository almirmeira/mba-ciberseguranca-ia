# NIST Cybersecurity Framework Profile Template
## Perfil de Segurança Cibernética

---

## 1. Informações da Organização

| Campo | Descrição |
|-------|-----------|
| **Nome da Organização** | |
| **Setor** | |
| **Tamanho** | Pequena / Média / Grande |
| **Data de Criação do Perfil** | |
| **Versão do CSF** | 2.0 |
| **Responsável** | |

---

## 2. Objetivo do Perfil

### 2.1 Tipo de Perfil
- [ ] Perfil Atual (Current Profile) - Estado atual da postura de segurança
- [ ] Perfil Alvo (Target Profile) - Estado desejado de segurança
- [ ] Perfil Comunitário - Baseado em setor específico

### 2.2 Propósito
```
[ ] Avaliação inicial de maturidade
[ ] Comunicação com stakeholders
[ ] Planejamento de melhorias
[ ] Conformidade regulatória
[ ] Gestão de riscos de terceiros
[ ] Outro: _______________
```

---

## 3. Contexto Organizacional

### 3.1 Ativos Críticos
| Categoria | Descrição | Prioridade |
|-----------|-----------|------------|
| Sistemas de Missão Crítica | | |
| Dados Sensíveis | | |
| Infraestrutura de IA/ML | | |
| Propriedade Intelectual | | |

### 3.2 Requisitos Regulatórios
| Regulamentação | Aplicável | Requisitos Chave |
|----------------|-----------|------------------|
| LGPD | Sim / Não | |
| PCI-DSS | Sim / Não | |
| ISO 27001 | Sim / Não | |
| SOX | Sim / Não | |
| BACEN/CMN | Sim / Não | |
| AI Act (EU) | Sim / Não | |

### 3.3 Tolerância a Riscos
| Categoria | Nível Aceitável |
|-----------|-----------------|
| Risco Operacional | Baixo / Médio / Alto |
| Risco de Reputação | Baixo / Médio / Alto |
| Risco Financeiro | Baixo / Médio / Alto |
| Risco Regulatório | Baixo / Médio / Alto |

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
| **Contexto Organizacional** | Missão e objetivos de segurança definidos | GV.OC-01 | | | | |
| | Stakeholders identificados | GV.OC-02 | | | | |
| | Requisitos legais e regulatórios | GV.OC-03 | | | | |
| | Ativos críticos identificados | GV.OC-04 | | | | |
| | Objetivos de resiliência definidos | GV.OC-05 | | | | |
| **Estratégia de Gestão de Riscos** | Apetite de risco estabelecido | GV.RM-01 | | | | |
| | Estratégia de risco documentada | GV.RM-02 | | | | |
| | Riscos de supply chain considerados | GV.RM-03 | | | | |
| **Papéis e Responsabilidades** | Papéis de segurança definidos | GV.RR-01 | | | | |
| | Responsabilidades atribuídas | GV.RR-02 | | | | |
| | Recursos adequados alocados | GV.RR-03 | | | | |
| **Políticas** | Política de segurança estabelecida | GV.PO-01 | | | | |
| | Políticas comunicadas | GV.PO-02 | | | | |
| **Supervisão** | Resultados de segurança monitorados | GV.OV-01 | | | | |
| | Performance revisada periodicamente | GV.OV-02 | | | | |
| **Gestão de Riscos de Supply Chain** | Processos SCRM implementados | GV.SC-01 | | | | |
| | Fornecedores avaliados | GV.SC-02 | | | | |

---

### 4.2 IDENTIFY (ID) - Identificar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Ativos** | Inventário de ativos físicos | ID.AM-01 | | | | |
| | Inventário de software | ID.AM-02 | | | | |
| | Mapeamento de fluxos de dados | ID.AM-03 | | | | |
| | Inventário de sistemas externos | ID.AM-04 | | | | |
| | Classificação de ativos por criticidade | ID.AM-05 | | | | |
| | **Inventário de modelos de IA/ML** | ID.AM-06* | | | | |
| **Avaliação de Riscos** | Vulnerabilidades identificadas | ID.RA-01 | | | | |
| | Threat intelligence utilizada | ID.RA-02 | | | | |
| | Ameaças identificadas | ID.RA-03 | | | | |
| | Impactos potenciais analisados | ID.RA-04 | | | | |
| | Riscos priorizados | ID.RA-05 | | | | |
| | **Riscos de IA/ML avaliados** | ID.RA-06* | | | | |
| **Melhoria** | Lições aprendidas incorporadas | ID.IM-01 | | | | |
| | Melhorias implementadas | ID.IM-02 | | | | |

---

### 4.3 PROTECT (PR) - Proteger

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Identidade e Acesso** | Identidades gerenciadas | PR.AA-01 | | | | |
| | Autenticação robusta | PR.AA-02 | | | | |
| | Acesso baseado em função | PR.AA-03 | | | | |
| | Credenciais protegidas | PR.AA-04 | | | | |
| | Acesso privilegiado gerenciado | PR.AA-05 | | | | |
| **Conscientização e Treinamento** | Treinamento de segurança | PR.AT-01 | | | | |
| | Papéis privilegiados treinados | PR.AT-02 | | | | |
| | **Treinamento em segurança de IA** | PR.AT-03* | | | | |
| **Segurança de Dados** | Dados em repouso protegidos | PR.DS-01 | | | | |
| | Dados em trânsito protegidos | PR.DS-02 | | | | |
| | Ativos formalmente gerenciados | PR.DS-03 | | | | |
| | Backup adequado | PR.DS-04 | | | | |
| | Integridade de dados verificada | PR.DS-05 | | | | |
| | **Dados de treinamento de IA protegidos** | PR.DS-06* | | | | |
| **Segurança de Plataforma** | Configurações de segurança | PR.PS-01 | | | | |
| | Software atualizado | PR.PS-02 | | | | |
| | Hardware gerenciado | PR.PS-03 | | | | |
| | Logs ativados | PR.PS-04 | | | | |
| | Mídias removíveis gerenciadas | PR.PS-05 | | | | |
| **Resiliência de Infraestrutura** | Redes protegidas | PR.IR-01 | | | | |
| | Ambientes seguros mantidos | PR.IR-02 | | | | |

---

### 4.4 DETECT (DE) - Detectar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Monitoramento Contínuo** | Redes monitoradas | DE.CM-01 | | | | |
| | Ambiente físico monitorado | DE.CM-02 | | | | |
| | Atividade de usuários monitorada | DE.CM-03 | | | | |
| | Código malicioso detectado | DE.CM-04 | | | | |
| | Acessos não autorizados detectados | DE.CM-05 | | | | |
| | Dispositivos externos monitorados | DE.CM-06 | | | | |
| | **Modelos de IA monitorados (drift, adversarial)** | DE.CM-07* | | | | |
| **Análise de Eventos Adversos** | Anomalias detectadas | DE.AE-01 | | | | |
| | Eventos correlacionados | DE.AE-02 | | | | |
| | Alertas gerados | DE.AE-03 | | | | |
| | Impacto estimado | DE.AE-04 | | | | |

---

### 4.5 RESPOND (RS) - Responder

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Gestão de Incidentes** | Plano de resposta executado | RS.MA-01 | | | | |
| | Incidentes categorizados | RS.MA-02 | | | | |
| | Incidentes priorizados | RS.MA-03 | | | | |
| | Incidentes escalados | RS.MA-04 | | | | |
| **Análise de Incidentes** | Incidentes investigados | RS.AN-01 | | | | |
| | Causa raiz determinada | RS.AN-02 | | | | |
| | Forense realizada | RS.AN-03 | | | | |
| **Comunicação e Relatórios** | Stakeholders notificados | RS.CO-01 | | | | |
| | Relatórios de incidentes | RS.CO-02 | | | | |
| | Informações compartilhadas | RS.CO-03 | | | | |
| **Mitigação** | Incidentes contidos | RS.MI-01 | | | | |
| | Incidentes erradicados | RS.MI-02 | | | | |

---

### 4.6 RECOVER (RC) - Recuperar

| Categoria | Subcategoria | ID | Atual | Alvo | Gap | Prioridade |
|-----------|--------------|-----|-------|------|-----|------------|
| **Planejamento de Recuperação** | Plano de recuperação executado | RC.RP-01 | | | | |
| | Pontos de recuperação selecionados | RC.RP-02 | | | | |
| | Integridade de backups verificada | RC.RP-03 | | | | |
| | Funções críticas restauradas | RC.RP-04 | | | | |
| | Integridade de ativos verificada | RC.RP-05 | | | | |
| | **Modelos de IA restaurados/retreinados** | RC.RP-06* | | | | |
| **Comunicação de Recuperação** | Atividades de recuperação comunicadas | RC.CO-01 | | | | |
| | Reputação gerenciada | RC.CO-02 | | | | |

---

## 5. Análise de Gaps

### 5.1 Resumo por Função
| Função | Maturidade Atual (Média) | Maturidade Alvo | Gap |
|--------|-------------------------|-----------------|-----|
| GOVERN | | | |
| IDENTIFY | | | |
| PROTECT | | | |
| DETECT | | | |
| RESPOND | | | |
| RECOVER | | | |
| **GERAL** | | | |

### 5.2 Gaps Críticos Identificados
| # | Subcategoria | Gap | Risco Associado | Ação Recomendada |
|---|--------------|-----|-----------------|------------------|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

---

## 6. Roadmap de Implementação

### 6.1 Iniciativas Prioritárias
| Fase | Iniciativa | Subcategorias | Recursos | Dependências |
|------|------------|---------------|----------|--------------|
| 1 - Quick Wins | | | | |
| 2 - Fundamentos | | | | |
| 3 - Avançado | | | | |
| 4 - Otimização | | | | |

### 6.2 Métricas de Sucesso
| Métrica | Baseline | Meta | Método de Medição |
|---------|----------|------|-------------------|
| Maturidade Geral | | | |
| % de Controles Implementados | | | |
| Tempo de Detecção (MTTD) | | | |
| Tempo de Resposta (MTTR) | | | |

---

## 7. Controles Específicos para IA/ML

### 7.1 Mapeamento Adicional para Sistemas de IA
| Categoria NIST AI RMF | CSF 2.0 Relacionado | Controle Específico | Status |
|-----------------------|---------------------|---------------------|--------|
| MAP (Mapear) | ID.AM, ID.RA | Inventário de modelos, uso pretendido | |
| MEASURE (Medir) | DE.CM, DE.AE | Métricas de performance, fairness, robustez | |
| MANAGE (Gerenciar) | RS.MA, RC.RP | Planos de resposta para falhas de IA | |
| GOVERN (Governar) | GV.* | Políticas de IA responsável | |

*Nota: Subcategorias marcadas com asterisco (*) são extensões sugeridas para ambientes com IA/ML*

---

## 8. Aprovações

| Papel | Nome | Data | Assinatura |
|-------|------|------|------------|
| CISO | | | |
| CIO | | | |
| Gestor de Riscos | | | |
| Sponsor Executivo | | | |

---

## 9. Histórico de Revisões

| Versão | Data | Autor | Descrição |
|--------|------|-------|-----------|
| 1.0 | | | Criação inicial |
| | | | |

---

## 10. Referências

- NIST Cybersecurity Framework 2.0 (2024)
- NIST AI Risk Management Framework (AI RMF)
- NIST SP 800-53 Rev. 5
- ISO/IEC 27001:2022

---

*Template versão 1.0 - MBA Cibersegurança & IA*
