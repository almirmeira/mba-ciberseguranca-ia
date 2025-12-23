# Risk Assessment Template
## Avaliação de Riscos de Segurança Cibernética

---

## 1. Informações do Projeto

| Campo | Descrição |
|-------|-----------|
| **Nome do Projeto/Sistema** | |
| **Responsável pela Avaliação** | |
| **Data da Avaliação** | |
| **Versão do Documento** | |
| **Próxima Revisão** | |

---

## 2. Escopo da Avaliação

### 2.1 Sistemas/Ativos em Escopo
| ID | Nome do Ativo | Tipo | Criticidade | Proprietário |
|----|---------------|------|-------------|--------------|
| A001 | | Aplicação / Infraestrutura / Dados | Alta / Média / Baixa | |
| A002 | | | | |
| A003 | | | | |

### 2.2 Sistemas Fora do Escopo
-
-

---

## 3. Metodologia de Avaliação

### 3.1 Framework Utilizado
- [ ] NIST RMF
- [ ] ISO 27005
- [ ] FAIR
- [ ] OCTAVE
- [ ] Outro: ____________

### 3.2 Critérios de Classificação

#### Probabilidade de Ocorrência
| Nível | Descrição | Frequência |
|-------|-----------|------------|
| 5 - Muito Alta | Quase certo | Múltiplas vezes por ano |
| 4 - Alta | Provável | Uma vez por ano |
| 3 - Média | Possível | Uma vez a cada 2-3 anos |
| 2 - Baixa | Improvável | Uma vez a cada 5-10 anos |
| 1 - Muito Baixa | Rara | Menos de uma vez em 10 anos |

#### Impacto
| Nível | Financeiro | Operacional | Reputacional | Regulatório |
|-------|------------|-------------|--------------|-------------|
| 5 - Crítico | > R$ 10M | Parada total > 1 semana | Cobertura nacional negativa | Multas severas/perda de licença |
| 4 - Alto | R$ 1M - 10M | Parada parcial 1-7 dias | Cobertura regional negativa | Multas significativas |
| 3 - Médio | R$ 100K - 1M | Degradação significativa | Reclamações de clientes | Notificação a reguladores |
| 2 - Baixo | R$ 10K - 100K | Degradação menor | Impacto interno apenas | Observações de auditoria |
| 1 - Mínimo | < R$ 10K | Impacto negligenciável | Nenhum | Nenhum |

---

## 4. Identificação de Ameaças

### 4.1 Catálogo de Ameaças
| ID | Categoria | Ameaça | Agente de Ameaça | Motivação |
|----|-----------|--------|------------------|-----------|
| T001 | Externa | Ransomware | Criminosos Cibernéticos | Financeira |
| T002 | Externa | Phishing/Engenharia Social | Atacantes Oportunistas | Financeira |
| T003 | Externa | APT (Advanced Persistent Threat) | Estado-Nação | Espionagem |
| T004 | Interna | Vazamento de Dados | Insider Malicioso/Negligente | Financeira/Vingança |
| T005 | Externa | Ataques DDoS | Hacktivistas | Ideológica |
| T006 | IA/ML | Adversarial Attacks | Atacantes Sofisticados | Subversão de Sistemas |
| T007 | IA/ML | Data Poisoning | Competidores/Atacantes | Comprometer Modelos |
| T008 | IA/ML | Model Extraction | Competidores | Roubo de PI |
| T009 | | | | |

---

## 5. Identificação de Vulnerabilidades

### 5.1 Vulnerabilidades Técnicas
| ID | Descrição | Ativos Afetados | CVE (se aplicável) | CVSS |
|----|-----------|-----------------|-------------------|------|
| V001 | | | | |
| V002 | | | | |

### 5.2 Vulnerabilidades Organizacionais
| ID | Descrição | Área Afetada | Controles Existentes |
|----|-----------|--------------|---------------------|
| V101 | Falta de treinamento em segurança | RH/Todos | |
| V102 | Políticas desatualizadas | Governança | |
| V103 | | | |

### 5.3 Vulnerabilidades Específicas de IA/ML
| ID | Descrição | Modelo/Sistema Afetado | Tipo |
|----|-----------|------------------------|------|
| V201 | Dados de treinamento não validados | | Data Quality |
| V202 | Falta de monitoramento de drift | | Model Monitoring |
| V203 | Ausência de explicabilidade | | Transparency |
| V204 | | | |

---

## 6. Análise de Riscos

### 6.1 Matriz de Riscos

| ID Risco | Ameaça | Vulnerabilidade | Ativo | Probabilidade | Impacto | Risco Inerente | Controles | Risco Residual |
|----------|--------|-----------------|-------|---------------|---------|----------------|-----------|----------------|
| R001 | T001 | V001 | A001 | 4 | 5 | 20 (Crítico) | | |
| R002 | T006 | V201 | A002 | 3 | 4 | 12 (Alto) | | |
| R003 | | | | | | | | |

### 6.2 Mapa de Calor de Riscos

```
Impacto
    5 │  M   A   C   C   C
    4 │  B   M   A   C   C
    3 │  B   M   M   A   A
    2 │  B   B   M   M   A
    1 │  B   B   B   M   M
      └──────────────────────
        1   2   3   4   5
            Probabilidade

Legenda: B=Baixo, M=Médio, A=Alto, C=Crítico
```

---

## 7. Plano de Tratamento de Riscos

### 7.1 Estratégias de Tratamento
| ID Risco | Estratégia | Descrição do Tratamento | Responsável | Prazo | Status |
|----------|------------|-------------------------|-------------|-------|--------|
| R001 | Mitigar | Implementar backup imutável + EDR | | | |
| R002 | Mitigar | Implementar validação de inputs adversariais | | | |
| R003 | Aceitar | Risco dentro do apetite | | N/A | |
| R004 | Transferir | Contratar seguro cyber | | | |
| R005 | Evitar | Descontinuar sistema legado | | | |

### 7.2 Controles Recomendados
| Controle | Tipo | Riscos Mitigados | Custo Estimado | Eficácia |
|----------|------|------------------|----------------|----------|
| MFA em todos os sistemas | Preventivo | R001, R002 | | Alta |
| SIEM/SOC 24x7 | Detectivo | R001, R003, R004 | | Alta |
| Treinamento de Segurança | Preventivo | R002 | | Média |
| Red Team IA | Detectivo | R006, R007, R008 | | Alta |
| | | | | |

---

## 8. Métricas e KPIs

### 8.1 Indicadores de Risco
| Métrica | Valor Atual | Meta | Tendência |
|---------|-------------|------|-----------|
| Número de riscos críticos | | < 2 | |
| % de riscos com tratamento definido | | 100% | |
| Tempo médio de remediação | | < 30 dias | |
| % de controles implementados | | > 90% | |

---

## 9. Anexos

### 9.1 Glossário
- **Risco Inerente**: Risco antes da aplicação de controles
- **Risco Residual**: Risco após a aplicação de controles
- **Apetite de Risco**: Nível de risco que a organização está disposta a aceitar

### 9.2 Referências
- NIST SP 800-30: Guide for Conducting Risk Assessments
- ISO/IEC 27005: Information Security Risk Management
- NIST AI RMF: AI Risk Management Framework

---

## 10. Aprovações

| Papel | Nome | Assinatura | Data |
|-------|------|------------|------|
| Avaliador | | | |
| Revisor Técnico | | | |
| CISO | | | |
| Proprietário do Risco | | | |

---

*Template versão 1.0 - MBA Cibersegurança & IA*
