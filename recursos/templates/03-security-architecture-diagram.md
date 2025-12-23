# Security Architecture Diagram Template
## Documentação de Arquitetura de Segurança

---

## 1. Informações do Documento

| Campo | Valor |
|-------|-------|
| **Nome do Sistema/Projeto** | |
| **Versão da Arquitetura** | |
| **Arquiteto Responsável** | |
| **Data de Criação** | |
| **Última Atualização** | |
| **Classificação** | Confidencial / Interno / Público |

---

## 2. Visão Geral da Arquitetura

### 2.1 Descrição do Sistema
```
[Descreva brevemente o propósito do sistema, seus principais usuários e funcionalidades]
```

### 2.2 Diagrama de Contexto (Nível 0)

```
┌─────────────────────────────────────────────────────────────────┐
│                        AMBIENTE EXTERNO                          │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐  │
│  │ Usuários │    │ Parceiros│    │   APIs   │    │ Atacantes│  │
│  │ Finais   │    │ B2B      │    │ Externas │    │ (Ameaças)│  │
│  └────┬─────┘    └────┬─────┘    └────┬─────┘    └────┬─────┘  │
│       │               │               │               │         │
└───────┼───────────────┼───────────────┼───────────────┼─────────┘
        │               │               │               │
        ▼               ▼               ▼               ▼
┌─────────────────────────────────────────────────────────────────┐
│                    PERÍMETRO DE SEGURANÇA                        │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │                      WAF / CDN / DDoS                      │  │
│  └───────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────┐  │
│  │                    Firewall Externo                        │  │
│  └───────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────────────────────────────────┐
│                         DMZ                                      │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │
│  │   API       │    │   Web       │    │   Reverse   │         │
│  │   Gateway   │    │   Servers   │    │   Proxy     │         │
│  └─────────────┘    └─────────────┘    └─────────────┘         │
└─────────────────────────────────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────────────────────────────────┐
│                    REDE INTERNA                                  │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │
│  │ Application │    │   Backend   │    │  Microser-  │         │
│  │  Servers    │    │   Services  │    │   vices     │         │
│  └─────────────┘    └─────────────┘    └─────────────┘         │
└─────────────────────────────────────────────────────────────────┘
        │
        ▼
┌─────────────────────────────────────────────────────────────────┐
│                    ZONA DE DADOS                                 │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │
│  │  Database   │    │   Data      │    │   ML/AI     │         │
│  │  Cluster    │    │   Lake      │    │   Models    │         │
│  └─────────────┘    └─────────────┘    └─────────────┘         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3. Arquitetura de Rede

### 3.1 Diagrama de Zonas de Segurança

```
┌────────────────────────────────────────────────────────────────────────────┐
│                                INTERNET                                     │
└────────────────────────────────────┬───────────────────────────────────────┘
                                     │
                    ┌────────────────┴────────────────┐
                    │         Edge Security           │
                    │  • CDN (CloudFlare/Akamai)     │
                    │  • DDoS Protection              │
                    │  • Bot Management               │
                    └────────────────┬────────────────┘
                                     │
┌────────────────────────────────────┴───────────────────────────────────────┐
│ ZONA 1: DMZ (Zona Desmilitarizada)                           Trust: LOW   │
│ ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│ │     WAF      │  │   Load       │  │   API        │  │   Bastion    │   │
│ │              │  │   Balancer   │  │   Gateway    │  │   Host       │   │
│ │ • OWASP Top10│  │ • SSL Term.  │  │ • Rate Limit │  │ • SSH Jump   │   │
│ │ • Rate Limit │  │ • Health Chk │  │ • Auth       │  │ • MFA        │   │
│ └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘   │
└────────────────────────────────────┬───────────────────────────────────────┘
                                     │ Firewall Interno
┌────────────────────────────────────┴───────────────────────────────────────┐
│ ZONA 2: Aplicação                                           Trust: MEDIUM │
│ ┌──────────────────────────────────────────────────────────────────────┐  │
│ │                        Kubernetes Cluster                             │  │
│ │  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐     │  │
│ │  │ Frontend   │  │ Backend    │  │ Auth       │  │ AI/ML      │     │  │
│ │  │ Services   │  │ APIs       │  │ Service    │  │ Inference  │     │  │
│ │  └────────────┘  └────────────┘  └────────────┘  └────────────┘     │  │
│ │                                                                       │  │
│ │  Network Policies │ Service Mesh (Istio/Linkerd) │ mTLS              │  │
│ └──────────────────────────────────────────────────────────────────────┘  │
└────────────────────────────────────┬───────────────────────────────────────┘
                                     │ Segmentação
┌────────────────────────────────────┴───────────────────────────────────────┐
│ ZONA 3: Dados                                                Trust: HIGH  │
│ ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│ │  PostgreSQL  │  │   Redis      │  │   S3/Blob    │  │   ML Model   │   │
│ │  Cluster     │  │   Cluster    │  │   Storage    │  │   Registry   │   │
│ │              │  │              │  │              │  │              │   │
│ │ • Encryption │  │ • Auth       │  │ • Encryption │  │ • Signed     │   │
│ │ • Audit Logs │  │ • TLS        │  │ • Versioning │  │ • Versioned  │   │
│ └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘   │
└────────────────────────────────────┬───────────────────────────────────────┘
                                     │
┌────────────────────────────────────┴───────────────────────────────────────┐
│ ZONA 4: Gerenciamento                                   Trust: RESTRICTED │
│ ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│ │    SIEM      │  │    Vault     │  │   CI/CD      │  │   Backup     │   │
│ │  (Splunk/ELK)│  │  (Secrets)   │  │   Pipeline   │  │   Systems    │   │
│ └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘   │
└────────────────────────────────────────────────────────────────────────────┘
```

### 3.2 Matriz de Comunicação entre Zonas

| Origem | Destino | Porta/Protocolo | Direção | Propósito | Controle |
|--------|---------|-----------------|---------|-----------|----------|
| Internet | DMZ | 443/HTTPS | Inbound | Tráfego Web | WAF |
| DMZ | Aplicação | 8080/HTTPS | Inbound | API Calls | mTLS |
| Aplicação | Dados | 5432/TCP | Inbound | Database | Network Policy |
| Aplicação | Dados | 6379/TCP | Inbound | Cache | Auth + TLS |
| Gerenciamento | Todas | 22/SSH | Outbound | Administração | Bastion + MFA |
| Todas | Gerenciamento | 514/Syslog | Outbound | Logs | TLS |

---

## 4. Arquitetura de Identidade e Acesso

### 4.1 Diagrama de Autenticação e Autorização

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        IDENTITY ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────┐         ┌─────────────────────────────────────────┐   │
│  │   Usuário   │────────▶│            Identity Provider            │   │
│  │             │         │  ┌─────────────────────────────────────┐│   │
│  └─────────────┘         │  │ • Azure AD / Okta / Keycloak       ││   │
│        │                 │  │ • MFA (TOTP/WebAuthn/Push)         ││   │
│        │ SSO Token       │  │ • Conditional Access               ││   │
│        │                 │  │ • Risk-Based Authentication        ││   │
│        ▼                 │  └─────────────────────────────────────┘│   │
│  ┌─────────────┐         └─────────────────────────────────────────┘   │
│  │ Application │                          │                            │
│  │             │                          │ OIDC/SAML                  │
│  └─────────────┘                          ▼                            │
│        │                 ┌─────────────────────────────────────────┐   │
│        │                 │            Authorization                 │   │
│        │ API Request     │  ┌─────────────────────────────────────┐│   │
│        │ + JWT           │  │ • RBAC (Role-Based Access Control) ││   │
│        ▼                 │  │ • ABAC (Attribute-Based)           ││   │
│  ┌─────────────┐         │  │ • Policy Engine (OPA/Cedar)        ││   │
│  │ API Gateway │────────▶│  │ • Just-In-Time Access              ││   │
│  │             │         │  └─────────────────────────────────────┘│   │
│  └─────────────┘         └─────────────────────────────────────────┘   │
│        │                                                                │
│        │ Authorized                                                     │
│        ▼                                                                │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                    Backend Services                              │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐              │   │
│  │  │ Service A   │  │ Service B   │  │ ML Service  │              │   │
│  │  │             │  │             │  │             │              │   │
│  │  │ mTLS + SPIFFE │ Service Account│ API Keys     │              │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘              │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Matriz de Papéis e Permissões

| Papel | Aplicação | Dados | Infraestrutura | ML/AI | Secrets |
|-------|-----------|-------|----------------|-------|---------|
| Admin | Full | Full | Full | Full | Full |
| Developer | Read/Write | Read | Read | Read/Write | Read (Dev) |
| Data Scientist | Read | Read/Write | None | Full | Read (ML) |
| Operator | Read | Read | Read/Write | Read | Read (Ops) |
| Auditor | Read | Read | Read | Read | None |
| Service Account | Scoped | Scoped | None | Scoped | Scoped |

---

## 5. Arquitetura de Dados e Criptografia

### 5.1 Diagrama de Proteção de Dados

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     DATA PROTECTION ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DADOS EM TRÂNSITO                                                       │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  Client ──TLS 1.3──▶ LB ──mTLS──▶ Service ──TLS──▶ Database   │    │
│  │                                                                  │    │
│  │  • Certificate Management (Let's Encrypt / ACM)                 │    │
│  │  • Certificate Pinning (Mobile)                                 │    │
│  │  • Perfect Forward Secrecy                                      │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  DADOS EM REPOUSO                                                        │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                                                                  │    │
│  │  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐      │    │
│  │  │   Database   │    │   Storage    │    │   Backups    │      │    │
│  │  │              │    │              │    │              │      │    │
│  │  │ • TDE        │    │ • AES-256    │    │ • Encrypted  │      │    │
│  │  │ • Column-lvl │    │ • CMK/BYOK   │    │ • Immutable  │      │    │
│  │  │ • Field-lvl  │    │ • Versioning │    │ • Air-gapped │      │    │
│  │  └──────────────┘    └──────────────┘    └──────────────┘      │    │
│  │                              │                                   │    │
│  │                              ▼                                   │    │
│  │                    ┌──────────────────┐                         │    │
│  │                    │   Key Management │                         │    │
│  │                    │   (HSM / Vault)  │                         │    │
│  │                    │                  │                         │    │
│  │                    │ • Key Rotation   │                         │    │
│  │                    │ • Access Audit   │                         │    │
│  │                    │ • Separation     │                         │    │
│  │                    └──────────────────┘                         │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  DADOS EM USO (Confidential Computing - Opcional)                       │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  • Intel SGX / AMD SEV / AWS Nitro Enclaves                     │    │
│  │  • Homomorphic Encryption (para ML específico)                  │    │
│  │  • Secure Multiparty Computation                                │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5.2 Classificação de Dados

| Classificação | Exemplos | Criptografia | Acesso | Retenção |
|---------------|----------|--------------|--------|----------|
| Público | Marketing | Opcional | Todos | Indefinido |
| Interno | Processos | TLS | Funcionários | 5 anos |
| Confidencial | Contratos | TLS + AES-256 | Need-to-know | 7 anos |
| Restrito | PII, Financeiro | Field-level + HSM | Aprovação | 10 anos |
| Secreto | Chaves, Credenciais | HSM | MFA + Aprovação | Rotação |

---

## 6. Arquitetura de Segurança para IA/ML

### 6.1 Diagrama de Pipeline ML Seguro

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SECURE ML PIPELINE ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DATA INGESTION                 TRAINING                 DEPLOYMENT      │
│  ┌──────────────┐              ┌──────────────┐        ┌──────────────┐ │
│  │   Data       │              │   Training   │        │   Model      │ │
│  │   Sources    │              │   Environment│        │   Serving    │ │
│  │              │              │              │        │              │ │
│  │ • Validation │─────────────▶│ • Isolated   │───────▶│ • Sandboxed  │ │
│  │ • Sanitize   │              │ • Versioned  │        │ • Monitored  │ │
│  │ • Audit Trail│              │ • Reproducible│       │ • Rate-limit │ │
│  └──────────────┘              └──────────────┘        └──────────────┘ │
│         │                             │                       │          │
│         ▼                             ▼                       ▼          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    SECURITY CONTROLS                             │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │                                                                  │    │
│  │  DATA SECURITY          MODEL SECURITY         INFERENCE SEC.   │    │
│  │  ┌────────────┐         ┌────────────┐        ┌────────────┐   │    │
│  │  │• Poisoning │         │• Extraction│        │• Adversarial│   │    │
│  │  │  Detection │         │  Prevention│        │  Detection  │   │    │
│  │  │• Privacy   │         │• Watermark │        │• Input Valid│   │    │
│  │  │  (DP, Fed) │         │• Signing   │        │• Output San.│   │    │
│  │  │• PII Mask  │         │• Encryption│        │• Rate Limit │   │    │
│  │  └────────────┘         └────────────┘        └────────────┘   │    │
│  │                                                                  │    │
│  │  MONITORING & OBSERVABILITY                                      │    │
│  │  ┌──────────────────────────────────────────────────────────┐   │    │
│  │  │ • Model Drift Detection    • Fairness Metrics            │   │    │
│  │  │ • Performance Degradation  • Explainability Logs         │   │    │
│  │  │ • Anomaly Detection        • Audit Trail                 │   │    │
│  │  │ • Adversarial Input Logs   • Compliance Reports          │   │    │
│  │  └──────────────────────────────────────────────────────────┘   │    │
│  │                                                                  │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    MODEL REGISTRY & GOVERNANCE                   │    │
│  │  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐│    │
│  │  │ Model      │  │ Version    │  │ Approval   │  │ Rollback   ││    │
│  │  │ Inventory  │  │ Control    │  │ Workflow   │  │ Capability ││    │
│  │  └────────────┘  └────────────┘  └────────────┘  └────────────┘│    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6.2 Controles de Segurança ML

| Fase | Ameaça | Controle | Implementação |
|------|--------|----------|---------------|
| Dados | Data Poisoning | Validação de integridade | Hash, proveniência |
| Dados | Privacy Leakage | Differential Privacy | DP-SGD, Federated Learning |
| Treino | Model Theft | Ambiente isolado | Air-gapped, TEE |
| Modelo | Extraction Attack | Rate limiting, watermarking | API controls |
| Inferência | Adversarial Input | Input validation | Adversarial training |
| Inferência | Prompt Injection | Input sanitization | Guardrails, filters |

---

## 7. Arquitetura de Monitoramento e Resposta

### 7.1 Diagrama SOC/SIEM

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SECURITY OPERATIONS CENTER                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DATA SOURCES                    COLLECTION              ANALYSIS        │
│  ┌────────────┐                 ┌──────────┐          ┌──────────────┐  │
│  │ Firewalls  │────────────────▶│          │          │              │  │
│  │ WAF        │                 │          │          │     SIEM     │  │
│  │ IDS/IPS    │                 │   Log    │─────────▶│   (Splunk/   │  │
│  └────────────┘                 │ Collector│          │    Elastic)  │  │
│  ┌────────────┐                 │          │          │              │  │
│  │ Servers    │────────────────▶│ (Fluentd/│          │ • Correlation│  │
│  │ Containers │                 │  Logstash│          │ • Rules      │  │
│  │ Cloud      │                 │  Vector) │          │ • ML Anomaly │  │
│  └────────────┘                 │          │          │ • Dashboards │  │
│  ┌────────────┐                 │          │          └──────────────┘  │
│  │ Apps       │────────────────▶│          │                 │          │
│  │ APIs       │                 │          │                 │          │
│  │ ML Models  │                 └──────────┘                 │          │
│  └────────────┘                                              │          │
│  ┌────────────┐                                              ▼          │
│  │ EDR        │                                      ┌──────────────┐   │
│  │ NDR        │─────────────────────────────────────▶│    SOAR      │   │
│  │ Cloud Sec  │                                      │ (Automation) │   │
│  └────────────┘                                      │              │   │
│                                                      │ • Playbooks  │   │
│  THREAT INTEL                                        │ • Enrichment │   │
│  ┌────────────┐                                      │ • Response   │   │
│  │ MISP       │─────────────────────────────────────▶│ • Ticketing  │   │
│  │ STIX/TAXII │                                      └──────────────┘   │
│  │ Feeds      │                                             │           │
│  └────────────┘                                             ▼           │
│                                                      ┌──────────────┐   │
│                                                      │   Incident   │   │
│                                                      │   Response   │   │
│                                                      │    Team      │   │
│                                                      └──────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Checklist de Revisão de Arquitetura

### 8.1 Perímetro e Rede
- [ ] WAF configurado com regras OWASP
- [ ] DDoS protection ativo
- [ ] Segmentação de rede implementada
- [ ] Firewalls com regras least-privilege
- [ ] VPN/Zero Trust para acesso remoto

### 8.2 Identidade e Acesso
- [ ] SSO implementado
- [ ] MFA obrigatório
- [ ] RBAC/ABAC configurado
- [ ] Secrets em vault seguro
- [ ] Service accounts com escopo mínimo

### 8.3 Dados
- [ ] Criptografia em trânsito (TLS 1.3)
- [ ] Criptografia em repouso
- [ ] Key management com HSM
- [ ] Backup criptografado e testado
- [ ] DLP implementado

### 8.4 Aplicação
- [ ] SAST/DAST no pipeline
- [ ] Dependency scanning
- [ ] Container security
- [ ] API security (rate limiting, auth)
- [ ] Input validation

### 8.5 IA/ML Específico
- [ ] Validação de dados de treinamento
- [ ] Model signing e versionamento
- [ ] Adversarial testing realizado
- [ ] Monitoramento de drift
- [ ] Guardrails para LLMs

### 8.6 Monitoramento
- [ ] Logs centralizados
- [ ] SIEM operacional
- [ ] Alertas configurados
- [ ] Incident response plan testado
- [ ] Métricas de segurança definidas

---

## 9. Diagramas Adicionais (Placeholder)

### 9.1 Diagrama de Fluxo de Dados (DFD)
```
[Inserir DFD específico do sistema]
```

### 9.2 Diagrama de Deployment
```
[Inserir diagrama de deployment - K8s, Cloud, etc.]
```

### 9.3 Diagrama de DR/BC
```
[Inserir diagrama de Disaster Recovery]
```

---

## 10. Ferramentas para Criação de Diagramas

| Ferramenta | Tipo | Uso Recomendado |
|------------|------|-----------------|
| Draw.io / Diagrams.net | Gratuito | Diagramas gerais |
| Lucidchart | Comercial | Colaboração |
| PlantUML | Código | Diagramas as Code |
| Mermaid | Código | Integração Markdown |
| Threat Dragon | Gratuito | Threat Modeling |
| Microsoft Visio | Comercial | Documentação formal |

---

## 11. Aprovações

| Papel | Nome | Data |
|-------|------|------|
| Arquiteto de Segurança | | |
| CISO | | |
| Arquiteto de Soluções | | |

---

*Template versão 1.0 - MBA Cibersegurança & IA*
