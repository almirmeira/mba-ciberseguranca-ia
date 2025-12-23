# LLM Security Checklist
## Lista de Verificação de Segurança para Large Language Models

---

## Informações do Projeto

| Campo | Valor |
|-------|-------|
| **Nome do Projeto/Aplicação** | |
| **Modelo(s) Utilizado(s)** | |
| **Responsável pela Avaliação** | |
| **Data da Avaliação** | |
| **Versão do Checklist** | 1.0 |

---

## Referências

Este checklist é baseado em:
- OWASP Top 10 for LLM Applications 2025
- NIST AI Risk Management Framework
- MITRE ATLAS (Adversarial Threat Landscape for AI Systems)
- Anthropic Security Best Practices
- Google Secure AI Framework (SAIF)

---

## 1. Prompt Injection (LLM01)

### 1.1 Direct Prompt Injection
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 1.1.1 | Input sanitization implementado antes do prompt | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.1.2 | Delimitadores claros entre system prompt e user input | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.1.3 | Validação de formato/tipo de input | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.1.4 | Limite de caracteres no input do usuário | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.1.5 | Testes com payloads de prompt injection realizados | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.1.6 | Detecção de tentativas de jailbreak | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 1.2 Indirect Prompt Injection
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 1.2.1 | Dados externos são sanitizados antes de entrar no contexto | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.2.2 | URLs/sites acessados pelo modelo são validados | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.2.3 | Documentos importados são verificados | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.2.4 | Outputs de outros modelos são tratados como untrusted | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 1.2.5 | RAG sources são validadas e confiáveis | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### Mitigações Recomendadas
```
□ Implementar input validation layer
□ Usar técnicas de prompt hardening
□ Separar contexto privilegiado de user input
□ Implementar output filtering
□ Monitorar padrões de prompt injection
□ Considerar uso de guardrails (Guardrails AI, NeMo, etc.)
```

---

## 2. Sensitive Information Disclosure (LLM02)

### 2.1 Proteção de Dados no Training
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 2.1.1 | Dados de treinamento não contêm PII sem mascaramento | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.1.2 | Credenciais/secrets removidos dos dados de treino | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.1.3 | Differential privacy aplicada (se aplicável) | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.1.4 | Auditoria de dados de treinamento realizada | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 2.2 Proteção de Dados em Runtime
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 2.2.1 | Output filtering para PII/dados sensíveis | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.2.2 | System prompt não é revelado ao usuário | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.2.3 | Logs não armazenam dados sensíveis em claro | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.2.4 | Respostas não incluem informações de infraestrutura | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.2.5 | Rate limiting para prevenir extraction attacks | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.2.6 | Detecção de membership inference attacks | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 2.3 Conformidade LGPD/GDPR
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 2.3.1 | Base legal para processamento de dados pessoais | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.3.2 | Direito de acesso/retificação/exclusão atendido | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.3.3 | Política de retenção de dados definida | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 2.3.4 | DPIA (Data Protection Impact Assessment) realizado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 3. Supply Chain Vulnerabilities (LLM03)

### 3.1 Modelos e Componentes
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 3.1.1 | Modelos baixados de fontes confiáveis | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.1.2 | Integridade de modelos verificada (checksums) | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.1.3 | Modelos assinados digitalmente | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.1.4 | Inventário de modelos e versões mantido | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.1.5 | Licenças de modelos revisadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 3.2 Bibliotecas e Dependências
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 3.2.1 | Dependências escaneadas para vulnerabilidades | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.2.2 | Versões de bibliotecas pinadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.2.3 | SBOM (Software Bill of Materials) mantido | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.2.4 | Processo de atualização de dependências definido | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 3.3 Dados e Datasets
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 3.3.1 | Proveniência dos dados de treinamento conhecida | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.3.2 | Datasets verificados para data poisoning | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 3.3.3 | Fontes de dados RAG validadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 4. Data and Model Poisoning (LLM04)

### 4.1 Prevenção de Poisoning
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 4.1.1 | Dados de treinamento validados e limpos | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.1.2 | Outlier detection em dados de treino | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.1.3 | Acesso ao pipeline de treino controlado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.1.4 | Fine-tuning data validado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.1.5 | RLHF feedback source validado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 4.2 Detecção de Poisoning
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 4.2.1 | Baseline de comportamento do modelo estabelecido | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.2.2 | Monitoramento de drift implementado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.2.3 | Testes de regressão automatizados | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 4.2.4 | Validação contra ground truth periódica | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 5. Improper Output Handling (LLM05)

### 5.1 Validação de Output
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 5.1.1 | Outputs são tratados como untrusted | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.1.2 | Encoding apropriado antes de renderizar | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.1.3 | Outputs não são executados diretamente | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.1.4 | Sanitização de HTML/JavaScript | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.1.5 | SQL/Command injection prevention | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 5.2 Agentic Systems
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 5.2.1 | Ações do agente requerem confirmação humana | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.2.2 | Sandbox para execução de código gerado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.2.3 | Limites de ações por sessão | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.2.4 | Logging de todas as ações do agente | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 5.2.5 | Rollback capability para ações | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 6. Excessive Agency (LLM06)

### 6.1 Princípio do Menor Privilégio
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 6.1.1 | Modelo tem apenas permissões necessárias | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.1.2 | Plugins/ferramentas com escopo mínimo | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.1.3 | APIs acessíveis pelo modelo são limitadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.1.4 | Acesso a dados restrito ao necessário | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 6.2 Human-in-the-Loop
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 6.2.1 | Ações críticas requerem aprovação humana | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.2.2 | Transações financeiras com confirmação | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.2.3 | Modificações de dados com revisão | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 6.2.4 | Comunicações externas supervisionadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 7. System Prompt Leakage (LLM07)

### 7.1 Proteção do System Prompt
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 7.1.1 | System prompt não contém secrets | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 7.1.2 | Instruções para não revelar system prompt | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 7.1.3 | Detecção de tentativas de extração | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 7.1.4 | Testes de extração realizados | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 7.1.5 | Output filtering para conteúdo do system prompt | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 8. Vector and Embedding Weaknesses (LLM08)

### 8.1 Segurança de RAG/Embeddings
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 8.1.1 | Vector database com controle de acesso | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 8.1.2 | Embeddings criptografados em repouso | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 8.1.3 | Fontes de dados para embedding validadas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 8.1.4 | Acesso a documentos baseado em permissões | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 8.1.5 | Prevenção de embedding injection | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 9. Misinformation (LLM09)

### 9.1 Prevenção de Alucinações
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 9.1.1 | RAG para grounding de respostas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.1.2 | Confidence scores disponíveis | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.1.3 | Citações/fontes incluídas nas respostas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.1.4 | Validação de fatos automatizada | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.1.5 | Avisos sobre limitações do modelo | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 9.2 Monitoramento de Qualidade
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 9.2.1 | Feedback loop para correções | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.2.2 | Métricas de qualidade definidas | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 9.2.3 | Revisão humana de outputs críticos | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 10. Unbounded Consumption (LLM10)

### 10.1 Rate Limiting e Quotas
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 10.1.1 | Rate limiting por usuário/API key | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.1.2 | Limite de tokens por request | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.1.3 | Limite de requests por período | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.1.4 | Quotas de custo por usuário/projeto | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.1.5 | Alertas de uso anômalo | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 10.2 Prevenção de DoS
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 10.2.1 | Proteção contra prompt loops | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.2.2 | Timeout para requests | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.2.3 | Queuing para alta demanda | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 10.2.4 | Scaling automático configurado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 11. Infraestrutura e Acesso

### 11.1 Autenticação e Autorização
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 11.1.1 | API keys rotacionadas regularmente | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.1.2 | OAuth/OIDC para autenticação | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.1.3 | RBAC implementado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.1.4 | MFA para acesso administrativo | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.1.5 | Secrets em vault seguro | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 11.2 Segurança de Rede
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 11.2.1 | TLS 1.3 para comunicação | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.2.2 | VPC/rede privada para modelo | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.2.3 | WAF configurado | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 11.2.4 | IP allowlisting (se aplicável) | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 12. Monitoramento e Logging

### 12.1 Observabilidade
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 12.1.1 | Logs de todas as interações | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.1.2 | Métricas de performance | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.1.3 | Alertas de anomalias | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.1.4 | Dashboard de monitoramento | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.1.5 | Retenção de logs adequada | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 12.2 Detecção de Ameaças
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 12.2.1 | Detecção de prompt injection | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.2.2 | Detecção de jailbreak attempts | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.2.3 | Detecção de data exfiltration | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 12.2.4 | Detecção de abuso | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

---

## 13. Testes de Segurança

### 13.1 Red Team / Adversarial Testing
| # | Verificação | Status | Observações |
|---|-------------|--------|-------------|
| 13.1.1 | Testes de prompt injection | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 13.1.2 | Testes de jailbreak | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 13.1.3 | Testes de data extraction | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 13.1.4 | Testes de adversarial inputs | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 13.1.5 | Testes de model extraction | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |
| 13.1.6 | Frequência de testes definida | ☐ N/A ☐ Sim ☐ Não ☐ Parcial | |

### 13.2 Ferramentas de Teste
| Ferramenta | Propósito | Utilizada |
|------------|-----------|-----------|
| Garak | Red teaming automatizado | ☐ |
| Promptfoo | Testing de prompts | ☐ |
| Microsoft PyRIT | Red teaming | ☐ |
| Rebuff | Detecção de injection | ☐ |
| LLM Guard | Proteção de I/O | ☐ |

---

## 14. Resumo e Scoring

### 14.1 Resumo por Categoria

| Categoria | Total Items | Sim | Não | Parcial | N/A | Score |
|-----------|-------------|-----|-----|---------|-----|-------|
| 1. Prompt Injection | | | | | | /100 |
| 2. Sensitive Info Disclosure | | | | | | /100 |
| 3. Supply Chain | | | | | | /100 |
| 4. Data/Model Poisoning | | | | | | /100 |
| 5. Output Handling | | | | | | /100 |
| 6. Excessive Agency | | | | | | /100 |
| 7. System Prompt Leakage | | | | | | /100 |
| 8. Vector/Embedding | | | | | | /100 |
| 9. Misinformation | | | | | | /100 |
| 10. Unbounded Consumption | | | | | | /100 |
| 11. Infraestrutura | | | | | | /100 |
| 12. Monitoramento | | | | | | /100 |
| 13. Testes | | | | | | /100 |
| **TOTAL** | | | | | | **/100** |

### 14.2 Risk Rating

```
Score 90-100: Baixo Risco - Controles robustos implementados
Score 70-89:  Risco Médio - Melhorias necessárias
Score 50-69:  Risco Alto - Ação corretiva urgente
Score <50:    Risco Crítico - Produção não recomendada
```

### 14.3 Itens Críticos Pendentes

| # | Item | Severidade | Responsável | Prazo |
|---|------|------------|-------------|-------|
| 1 | | Alta/Média/Baixa | | |
| 2 | | | | |
| 3 | | | | |

---

## 15. Aprovações

| Papel | Nome | Data | Assinatura |
|-------|------|------|------------|
| Security Engineer | | | |
| ML Engineer | | | |
| Security Manager | | | |
| Product Owner | | | |

---

*Template versão 1.0 - MBA Cibersegurança & IA*
*Baseado em OWASP Top 10 for LLM Applications 2025*
