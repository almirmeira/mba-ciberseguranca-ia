# Security Architecture - Fintech Digital Bank
## Documentação de Arquitetura de Segurança (Exemplo Baseado em Práticas de Mercado)

> **Nota**: Este documento é um exemplo educacional baseado em práticas públicas de fintechs brasileiras como Nubank. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## 1. Informações do Documento

| Campo | Valor |
|-------|-------|
| **Nome do Sistema/Projeto** | NeoBank Digital - Plataforma Core Banking |
| **Versão da Arquitetura** | 3.0 |
| **Arquiteto Responsável** | Security Architecture Team |
| **Data de Criação** | Dezembro 2025 |
| **Última Atualização** | Dezembro 2025 |
| **Classificação** | Confidencial |

---

## 2. Visão Geral da Arquitetura

### 2.1 Descrição do Sistema

A plataforma NeoBank Digital é um banco digital completo que atende mais de 50 milhões de clientes no Brasil. O sistema processa milhões de transações diárias incluindo PIX, cartões, empréstimos e investimentos. A arquitetura é baseada em microserviços, cloud-native, com forte integração de IA/ML para detecção de fraude e scoring de crédito.

**Características Principais:**
- Arquitetura de microserviços (>500 serviços)
- Multi-cloud (AWS primário, GCP secundário)
- Processamento em tempo real (latência <100ms)
- 99.99% uptime SLA
- Suporte a >120 milhões de usuários simultâneos

### 2.2 Diagrama de Contexto (Nível 0)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           AMBIENTE EXTERNO                                   │
│                                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │
│  │   Clientes   │  │   Parceiros  │  │   Open       │  │   Threat     │    │
│  │   Mobile/Web │  │   B2B/B2C    │  │   Finance    │  │   Actors     │    │
│  │   (50M+)     │  │   (APIs)     │  │   (BACEN)    │  │   (Ameaças)  │    │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘    │
│         │                 │                 │                 │             │
└─────────┼─────────────────┼─────────────────┼─────────────────┼─────────────┘
          │                 │                 │                 │
          ▼                 ▼                 ▼                 ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         EDGE SECURITY LAYER                                  │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  CloudFlare Enterprise + AWS Shield Advanced + WAF + Bot Management   │  │
│  │  • DDoS Protection (L3-L7)     • Rate Limiting (10K req/min/user)    │  │
│  │  • Bot Detection (ML-based)    • Geo-blocking (sanctioned countries) │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                              DMZ / INGRESS                                   │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │   API Gateway   │  │    Web App      │  │   Open Finance  │             │
│  │   (Kong/AWS)    │  │   Firewall      │  │   Gateway       │             │
│  │   • OAuth 2.0   │  │   • OWASP Top10 │  │   • mTLS        │             │
│  │   • JWT Valid.  │  │   • Custom Rules│  │   • Consent     │             │
│  │   • Rate Limit  │  │   • ML Anomaly  │  │   • BACEN Spec  │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                       APPLICATION LAYER (KUBERNETES)                         │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                    Service Mesh (Istio)                                │  │
│  │    • mTLS between all services    • Circuit breakers                  │  │
│  │    • Traffic policies             • Observability (traces)            │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │  Account    │ │  Payments   │ │   Cards     │ │   Loans     │           │
│  │  Service    │ │  Service    │ │   Service   │ │   Service   │           │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘           │
│                                                                              │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │   Auth      │ │   KYC/AML   │ │   Fraud     │ │  AI/ML      │           │
│  │  Service    │ │   Service   │ │  Detection  │ │  Platform   │           │
│  │  (Keycloak) │ │             │ │  (RT ML)    │ │  (Kubeflow) │           │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘           │
└─────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            DATA LAYER                                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │   PostgreSQL    │  │     Redis       │  │   Kafka         │             │
│  │   Cluster (RDS) │  │   Cluster       │  │   Cluster       │             │
│  │   • TDE (AES256)│  │   • Auth + TLS  │  │   • Encryption  │             │
│  │   • Audit Logs  │  │   • Persistence │  │   • ACLs        │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
│                                                                              │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │   S3 Encrypted  │  │   ML Model      │  │   Data Lake     │             │
│  │   (Documents)   │  │   Registry      │  │   (Databricks)  │             │
│  │   • SSE-KMS     │  │   • MLflow      │  │   • Delta Lake  │             │
│  │   • Versioning  │  │   • Signed      │  │   • Encryption  │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         MANAGEMENT LAYER                                     │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │  HashiCorp      │  │    SIEM         │  │   CI/CD         │             │
│  │  Vault          │  │  (Splunk)       │  │  (GitLab)       │             │
│  │  • HSM Backend  │  │  • UEBA         │  │  • SAST/DAST    │             │
│  │  • Dynamic Sec. │  │  • SOAR         │  │  • Container    │             │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Arquitetura de Rede

### 3.1 Diagrama de Zonas de Segurança

```
┌────────────────────────────────────────────────────────────────────────────────┐
│                                  INTERNET                                       │
└────────────────────────────────────┬───────────────────────────────────────────┘
                                     │
                    ┌────────────────┴────────────────┐
                    │       EDGE SECURITY             │
                    │  CloudFlare + AWS Shield        │
                    │  • 100+ Tbps DDoS capacity     │
                    │  • <50ms latency global        │
                    │  • WAF: 10K+ rules             │
                    │  • Bot Score: ML-based         │
                    └────────────────┬────────────────┘
                                     │
┌────────────────────────────────────┴───────────────────────────────────────────┐
│ ZONA 1: DMZ (Demilitarized Zone)                              Trust: UNTRUSTED │
│ VPC: 10.0.0.0/16  │  Region: sa-east-1 (São Paulo)                             │
│ ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐              │
│ │   ALB/NLB        │  │   API Gateway    │  │   Bastion Host   │              │
│ │   (Public)       │  │   (Kong)         │  │   (Session Mgr)  │              │
│ │   • TLS 1.3 only │  │   • OAuth 2.0    │  │   • No SSH keys  │              │
│ │   • Cert pinning │  │   • Rate limiting│  │   • MFA required │              │
│ │   • Health checks│  │   • API versioning│ │   • Audit logged │              │
│ └──────────────────┘  └──────────────────┘  └──────────────────┘              │
│                                                                                 │
│ Security Groups: INGRESS 443 only, EGRESS to App Zone                          │
│ NACLs: Deny all except allowed ports, Deny sanctioned IPs                      │
└────────────────────────────────────┬───────────────────────────────────────────┘
                                     │ AWS PrivateLink / Transit Gateway
┌────────────────────────────────────┴───────────────────────────────────────────┐
│ ZONA 2: APPLICATION (Kubernetes EKS)                          Trust: INTERNAL  │
│ VPC: 10.1.0.0/16  │  Private Subnets Only                                      │
│ ┌────────────────────────────────────────────────────────────────────────────┐ │
│ │                         EKS CLUSTER (v1.29)                                 │ │
│ │  ┌──────────────────────────────────────────────────────────────────────┐  │ │
│ │  │                    ISTIO SERVICE MESH                                 │  │ │
│ │  │  • Automatic mTLS (STRICT mode)                                      │  │ │
│ │  │  • Authorization Policies (RBAC)                                     │  │ │
│ │  │  • Rate Limiting per service                                         │  │ │
│ │  │  • Request authentication (JWT)                                      │  │ │
│ │  └──────────────────────────────────────────────────────────────────────┘  │ │
│ │                                                                             │ │
│ │  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐ │ │
│ │  │ Namespace: │ │ Namespace: │ │ Namespace: │ │ Namespace: │ │Namespace:│ │ │
│ │  │ core-      │ │ payments   │ │ lending    │ │ ai-ml      │ │ security │ │ │
│ │  │ banking    │ │            │ │            │ │            │ │          │ │ │
│ │  │ ────────── │ │ ────────── │ │ ────────── │ │ ────────── │ │──────────│ │ │
│ │  │ account-svc│ │ pix-svc    │ │ credit-svc │ │ fraud-ml   │ │ auth-svc │ │ │
│ │  │ user-svc   │ │ card-svc   │ │ loan-svc   │ │ scoring-ml │ │ kyc-svc  │ │ │
│ │  │ notif-svc  │ │ transfer   │ │ collection │ │ chatbot    │ │ aml-svc  │ │ │
│ │  └────────────┘ └────────────┘ └────────────┘ └────────────┘ └──────────┘ │ │
│ │                                                                             │ │
│ │  Network Policies: Namespace isolation, explicit allow rules               │ │
│ │  Pod Security Standards: Restricted (no root, read-only fs)               │ │
│ │  Secrets: External Secrets Operator → HashiCorp Vault                     │ │
│ └─────────────────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────┬───────────────────────────────────────────┘
                                     │ VPC Peering / PrivateLink
┌────────────────────────────────────┴───────────────────────────────────────────┐
│ ZONA 3: DATA                                                  Trust: SENSITIVE │
│ VPC: 10.2.0.0/16  │  Isolated Subnets                                          │
│ ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐              │
│ │  Aurora          │  │   ElastiCache    │  │   MSK (Kafka)    │              │
│ │  PostgreSQL      │  │   (Redis)        │  │                  │              │
│ │                  │  │                  │  │   • Encryption   │              │
│ │  • Multi-AZ      │  │  • Cluster mode  │  │     in transit   │              │
│ │  • TDE enabled   │  │  • Auth tokens   │  │   • ACLs         │              │
│ │  • IAM auth      │  │  • TLS required  │  │   • 3x replicas  │              │
│ │  • Audit logs    │  │  • VPC only      │  │                  │              │
│ │  • 15min PITR    │  │                  │  │                  │              │
│ └──────────────────┘  └──────────────────┘  └──────────────────┘              │
│                                                                                 │
│ ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐              │
│ │   S3 Buckets     │  │   SageMaker      │  │   Databricks     │              │
│ │   (Encrypted)    │  │   (ML Training)  │  │   (Analytics)    │              │
│ │                  │  │                  │  │                  │              │
│ │  • SSE-KMS       │  │  • VPC-only      │  │  • Unity Catalog │              │
│ │  • Versioning    │  │  • No internet   │  │  • Column-level  │              │
│ │  • Object Lock   │  │  • Encrypted vol │  │    encryption    │              │
│ │  • Replication   │  │  • Role-based    │  │  • Audit logs    │              │
│ └──────────────────┘  └──────────────────┘  └──────────────────┘              │
│                                                                                 │
│ Access: App Zone only via PrivateLink, No internet access                       │
│ Encryption: All data encrypted with customer-managed KMS keys                   │
└────────────────────────────────────┬───────────────────────────────────────────┘
                                     │
┌────────────────────────────────────┴───────────────────────────────────────────┐
│ ZONA 4: MANAGEMENT                                           Trust: PRIVILEGED │
│ VPC: 10.3.0.0/16  │  Restricted Access                                         │
│ ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐              │
│ │  HashiCorp       │  │   Splunk         │  │   GitLab         │              │
│ │  Vault           │  │   Enterprise     │  │   (CI/CD)        │              │
│ │                  │  │                  │  │                  │              │
│ │  • HSM-backed    │  │  • 90-day retain │  │  • Private       │              │
│ │  • Auto-unseal   │  │  • 10TB/day      │  │    runners       │              │
│ │  • Namespaces    │  │  • ES|QL         │  │  • SAST/DAST     │              │
│ │  • Audit logs    │  │  • SOAR integ.   │  │  • Secrets scan  │              │
│ └──────────────────┘  └──────────────────┘  └──────────────────┘              │
│                                                                                 │
│ Access: Bastion only, MFA required, Just-in-Time access                         │
└────────────────────────────────────────────────────────────────────────────────┘
```

### 3.2 Matriz de Comunicação entre Zonas

| Origem | Destino | Porta/Protocolo | Direção | Propósito | Controle |
|--------|---------|-----------------|---------|-----------|----------|
| Internet | DMZ (ALB) | 443/HTTPS | Inbound | Tráfego de clientes | WAF + CloudFlare |
| DMZ | Application | 8443/gRPC-TLS | Inbound | API calls | mTLS (Istio) |
| Application | Data | 5432/TLS | Inbound | Database | IAM Auth + TLS |
| Application | Data | 6379/TLS | Inbound | Cache | Token Auth + TLS |
| Application | Data | 9092/TLS | Inbound | Events | SASL + TLS |
| Management | All | 22/SSH | Outbound | Admin (via Bastion) | Session Manager + MFA |
| All | Management | 514/TLS | Outbound | Logs | Fluentd + TLS |
| Application | External (PIX) | 443/mTLS | Outbound | BACEN SPI | Certificado ICP-Brasil |

---

## 4. Arquitetura de Identidade e Acesso

### 4.1 Diagrama de Autenticação e Autorização

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                          IDENTITY ARCHITECTURE                                   │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────┐                                                            │
│  │   Mobile App    │                                                            │
│  │   (Cliente)     │                                                            │
│  └────────┬────────┘                                                            │
│           │ 1. Biometria + PIN                                                  │
│           ▼                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                    KEYCLOAK (Identity Provider)                          │    │
│  │  ┌───────────────────────────────────────────────────────────────────┐  │    │
│  │  │ AUTENTICAÇÃO                                                       │  │    │
│  │  │ • Biometria (Device-bound keys)                                   │  │    │
│  │  │ • PIN (6 dígitos, encrypted)                                      │  │    │
│  │  │ • SMS OTP (fallback)                                              │  │    │
│  │  │ • Device fingerprinting                                           │  │    │
│  │  │ • Risk-based authentication (ML)                                  │  │    │
│  │  │ • Step-up auth para transações sensíveis                          │  │    │
│  │  └───────────────────────────────────────────────────────────────────┘  │    │
│  │  ┌───────────────────────────────────────────────────────────────────┐  │    │
│  │  │ TOKENS                                                             │  │    │
│  │  │ • Access Token (JWT, 15min TTL)                                   │  │    │
│  │  │ • Refresh Token (7 days, rotated)                                 │  │    │
│  │  │ • ID Token (user claims)                                          │  │    │
│  │  │ • Scope-based permissions                                         │  │    │
│  │  └───────────────────────────────────────────────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│           │ 2. JWT Token                                                        │
│           ▼                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                        API GATEWAY (Kong)                                │    │
│  │  • JWT validation          • Rate limiting per user/scope              │    │
│  │  • Scope verification      • Request logging                           │    │
│  │  • IP reputation check     • Fraud signals injection                   │    │
│  └────────────────────────────────────────────────────────────────────────┘    │
│           │ 3. Validated Request + User Context                                 │
│           ▼                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                    AUTHORIZATION (OPA - Open Policy Agent)               │    │
│  │  ┌───────────────────────────────────────────────────────────────────┐  │    │
│  │  │ POLÍTICAS                                                          │  │    │
│  │  │ • ABAC (Attribute-Based Access Control)                           │  │    │
│  │  │ • Resource ownership verification                                 │  │    │
│  │  │ • Transaction limits enforcement                                  │  │    │
│  │  │ • Geographic restrictions                                         │  │    │
│  │  │ • Time-based access controls                                      │  │    │
│  │  └───────────────────────────────────────────────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│           │ 4. Authorized                                                        │
│           ▼                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         MICROSERVICES                                    │    │
│  │                                                                          │    │
│  │  mTLS (Istio) │ Service Accounts (K8s) │ Least Privilege                │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│                        INTERNAL USERS (Employees)                                │
│                                                                                  │
│  ┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐   │
│  │  Okta (SSO)     │ ──────▶ │  MFA (FIDO2)    │ ──────▶ │  JIT Access     │   │
│  │  • SAML 2.0     │         │  • YubiKey      │         │  • Teleport     │   │
│  │  • SCIM         │         │  • Biometric    │         │  • Time-limited │   │
│  └─────────────────┘         └─────────────────┘         └─────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Matriz de Papéis e Permissões (Clientes)

| Perfil | Visualizar Saldo | Transferir | PIX | Empréstimo | Investir | Limite |
|--------|-----------------|------------|-----|------------|----------|--------|
| Básico | ✅ | ✅ até R$1K | ✅ até R$1K | ❌ | ❌ | R$1.000/dia |
| Standard | ✅ | ✅ até R$10K | ✅ até R$10K | ✅ | ✅ | R$10.000/dia |
| Premium | ✅ | ✅ até R$100K | ✅ até R$100K | ✅ | ✅ | R$100.000/dia |
| Corporate | ✅ | ✅ customizado | ✅ customizado | ✅ | ✅ | Customizado |

### 4.3 Matriz de Papéis (Funcionários)

| Papel | Production Read | Production Write | Data Access | Secrets | Admin |
|-------|----------------|------------------|-------------|---------|-------|
| Developer | ✅ (logs only) | ❌ | ❌ | Dev only | ❌ |
| SRE | ✅ | ✅ (limited) | ❌ | Prod (JIT) | ❌ |
| DBA | ❌ | ❌ | ✅ (masked) | Prod (JIT) | ❌ |
| Security | ✅ | ❌ | ✅ (audit) | ✅ | ❌ |
| Admin | ✅ | ✅ | ✅ | ✅ | ✅ |

---

## 5. Arquitetura de Dados e Criptografia

### 5.1 Diagrama de Proteção de Dados

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                       DATA PROTECTION ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  DADOS EM TRÂNSITO                                                               │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                                                                            │  │
│  │  Client ─────TLS 1.3────▶ ALB ─────mTLS────▶ Service ─────TLS────▶ DB    │  │
│  │         (certificate      (Istio)                          (IAM Auth)     │  │
│  │          pinning)                                                          │  │
│  │                                                                            │  │
│  │  Configuração TLS:                                                         │  │
│  │  • Cipher Suites: TLS_AES_256_GCM_SHA384, TLS_CHACHA20_POLY1305_SHA256   │  │
│  │  • Certificate: DigiCert EV + Let's Encrypt (backup)                      │  │
│  │  • HSTS: max-age=31536000; includeSubDomains; preload                    │  │
│  │  • Certificate Transparency: Required                                     │  │
│  │                                                                            │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  DADOS EM REPOUSO                                                                │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                                                                            │  │
│  │  ┌────────────────────┐    ┌────────────────────┐    ┌─────────────────┐ │  │
│  │  │   Aurora PostgreSQL │    │   S3 Buckets       │    │   EBS Volumes   │ │  │
│  │  │                     │    │                     │    │                 │ │  │
│  │  │ • TDE (AES-256)     │    │ • SSE-KMS          │    │ • Encrypted     │ │  │
│  │  │ • Column-level      │    │ • Bucket policies  │    │ • Auto-rotate   │ │  │
│  │  │   encryption (PII)  │    │ • Object Lock      │    │ • Snapshots     │ │  │
│  │  │ • Field-level       │    │ • Versioning       │    │   encrypted     │ │  │
│  │  │   (card numbers)    │    │ • Replication      │    │                 │ │  │
│  │  └────────────────────┘    └────────────────────┘    └─────────────────┘ │  │
│  │                                     │                                      │  │
│  │                                     ▼                                      │  │
│  │                    ┌───────────────────────────────┐                       │  │
│  │                    │    AWS KMS (HSM-backed)       │                       │  │
│  │                    │                               │                       │  │
│  │                    │ • Customer Managed Keys (CMK) │                       │  │
│  │                    │ • Annual rotation             │                       │  │
│  │                    │ • Cross-region replication    │                       │  │
│  │                    │ • Key policies (IAM)          │                       │  │
│  │                    │ • CloudTrail logging          │                       │  │
│  │                    └───────────────────────────────┘                       │  │
│  │                                                                            │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  DADOS EM USO                                                                    │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                                                                            │  │
│  │  • Application-level encryption for sensitive fields                      │  │
│  │  • Tokenization for card numbers (PCI-DSS)                                │  │
│  │  • Data masking in non-production environments                            │  │
│  │  • AWS Nitro Enclaves for ML inference on sensitive data (planned)        │  │
│  │                                                                            │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 5.2 Classificação de Dados

| Classificação | Exemplos | Criptografia | Acesso | Retenção | Masking |
|---------------|----------|--------------|--------|----------|---------|
| **Público** | Taxa de juros, tarifas | TLS | Todos | Indefinido | Não |
| **Interno** | Processos, manuais | TLS + S3 SSE | Funcionários | 5 anos | Não |
| **Confidencial** | Dados de clientes (nome, email) | TLS + AES-256 + Column | Need-to-know | 10 anos | Sim (dev/test) |
| **Restrito** | CPF, dados financeiros, biometria | TLS + Field-level + HSM | Aprovação + MFA | 10 anos | Sim (obrigatório) |
| **PCI** | Números de cartão | Tokenization + HSM | PCI Zone only | Per PCI-DSS | Tokenizado |

---

## 6. Arquitetura de Segurança para IA/ML

### 6.1 Diagrama de Pipeline ML Seguro

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                      SECURE ML PIPELINE (MLSecOps)                               │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   DATA INGESTION              TRAINING                    DEPLOYMENT             │
│   ──────────────              ────────                    ──────────             │
│                                                                                  │
│  ┌─────────────────┐        ┌─────────────────┐        ┌─────────────────┐      │
│  │  Data Sources   │        │   SageMaker     │        │   EKS + Istio   │      │
│  │                 │        │   (VPC Only)    │        │   (Production)  │      │
│  │ • Aurora (prod) │───────▶│                 │───────▶│                 │      │
│  │ • S3 (features) │        │ • No internet   │        │ • A/B testing   │      │
│  │ • Kafka (events)│        │ • IAM roles     │        │ • Canary deploy │      │
│  │                 │        │ • Encrypted EBS │        │ • Auto-rollback │      │
│  └─────────────────┘        └─────────────────┘        └─────────────────┘      │
│          │                          │                          │                 │
│          ▼                          ▼                          ▼                 │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                        SECURITY CONTROLS                                   │  │
│  ├───────────────────────────────────────────────────────────────────────────┤  │
│  │                                                                            │  │
│  │  DATA SECURITY              MODEL SECURITY           INFERENCE SECURITY    │  │
│  │  ┌───────────────┐          ┌───────────────┐        ┌───────────────┐    │  │
│  │  │ • Data lineage │          │ • Model signing│        │ • Input valid. │    │  │
│  │  │   (Databricks) │          │   (MLflow)     │        │ • Rate limiting│    │  │
│  │  │ • PII detection│          │ • Version ctrl │        │ • Output filter│    │  │
│  │  │   (Macie)      │          │ • Access logs  │        │ • Guardrails   │    │  │
│  │  │ • Bias check   │          │ • Encrypted    │        │ • Adversarial  │    │  │
│  │  │   (Fairlearn)  │          │   artifacts    │        │   detection    │    │  │
│  │  │ • Drift detect │          │ • Watermarking │        │ • Audit logs   │    │  │
│  │  └───────────────┘          └───────────────┘        └───────────────┘    │  │
│  │                                                                            │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                      MONITORING & OBSERVABILITY                            │  │
│  │                                                                            │  │
│  │  ┌─────────────────────────────────────────────────────────────────────┐  │  │
│  │  │ Model Performance          Fairness Metrics         Security Events │  │  │
│  │  │ ─────────────────          ───────────────          ─────────────── │  │  │
│  │  │ • Accuracy: 97.2%          • Demographic: 0.95      • Anomalies: 12 │  │  │
│  │  │ • Latency: 45ms p99        • Equalized: 0.92        • Drift: None   │  │  │
│  │  │ • Throughput: 10K/s        • Individual: 0.89       • Attacks: 0    │  │  │
│  │  └─────────────────────────────────────────────────────────────────────┘  │  │
│  │                                                                            │  │
│  │  Alerting: PagerDuty │ Dashboards: Grafana │ Logs: Splunk                 │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                      MODEL REGISTRY (MLflow)                               │  │
│  │                                                                            │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │  │
│  │  │ fraud-detect │  │ credit-score │  │ churn-pred   │  │ chatbot-llm  │  │  │
│  │  │ v3.2.1       │  │ v2.8.0       │  │ v1.5.3       │  │ v1.0.0       │  │  │
│  │  │ ✅ Approved  │  │ ✅ Approved  │  │ ⚠️ Staging   │  │ ⚠️ Review    │  │  │
│  │  │ SHA256: a1b2 │  │ SHA256: c3d4 │  │ SHA256: e5f6 │  │ SHA256: g7h8 │  │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘  │  │
│  │                                                                            │  │
│  │  Governance: Model Card │ Approval: Security + Ethics │ Audit: Immutable  │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 6.2 Controles de Segurança para Modelos em Produção

| Modelo | Tipo | Controles Implementados | Monitoramento |
|--------|------|------------------------|---------------|
| fraud-detect | Neural Network | Input validation, rate limiting, adversarial detection | Drift, latency, accuracy |
| credit-score | XGBoost | Fairness constraints, SHAP explanations, audit logs | Bias metrics, performance |
| churn-pred | Random Forest | Feature validation, output filtering | Accuracy, drift |
| chatbot-llm | GPT-4 (Azure) | Guardrails, content filtering, prompt injection detection | Usage, safety scores |

---

## 7. Arquitetura de Monitoramento e Resposta

### 7.1 Diagrama SOC/SIEM

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    SECURITY OPERATIONS CENTER (SOC)                              │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  DATA SOURCES                    COLLECTION             ANALYSIS                │
│  ────────────                    ──────────             ────────                │
│                                                                                  │
│  ┌─────────────┐               ┌──────────────┐       ┌──────────────────────┐ │
│  │ CloudTrail  │──────────────▶│              │       │                      │ │
│  │ VPC Flow    │               │   Kinesis    │       │   SPLUNK ENTERPRISE  │ │
│  │ WAF Logs    │               │   Firehose   │──────▶│                      │ │
│  │ ALB Logs    │               │              │       │ • 10TB/day ingestion │ │
│  └─────────────┘               │   + Lambda   │       │ • 90-day hot storage │ │
│                                │   Transform  │       │ • 7-year cold (S3)   │ │
│  ┌─────────────┐               │              │       │                      │ │
│  │ K8s Audit   │──────────────▶│              │       │ Detection Rules:     │ │
│  │ Istio Logs  │               └──────────────┘       │ • 500+ correlation   │ │
│  │ App Logs    │                                      │ • ML anomaly detect  │ │
│  │ DB Audit    │                                      │ • MITRE ATT&CK map   │ │
│  └─────────────┘                                      │                      │ │
│                                                       │ Dashboards:          │ │
│  ┌─────────────┐                                      │ • Executive summary  │ │
│  │ CrowdStrike │─────────────────────────────────────▶│ • Threat hunting     │ │
│  │ (EDR)       │                                      │ • Compliance         │ │
│  │             │                                      │ • ML model security  │ │
│  └─────────────┘                                      └──────────────────────┘ │
│                                                                  │              │
│  ┌─────────────┐                                                │              │
│  │ Threat Intel│                                                ▼              │
│  │ • FS-ISAC   │───────────────────────────────▶ ┌──────────────────────────┐ │
│  │ • MISP      │                                 │    SPLUNK SOAR           │ │
│  │ • AlienVault│                                 │    (Automation)          │ │
│  └─────────────┘                                 │                          │ │
│                                                  │ • 150+ playbooks         │ │
│  ┌─────────────┐                                 │ • Auto-enrichment        │ │
│  │ Vuln Scans  │                                 │ • Auto-containment       │ │
│  │ • Qualys    │─────────────────────────────────│ • Case management        │ │
│  │ • Snyk      │                                 │ • Metrics & KPIs         │ │
│  └─────────────┘                                 └──────────────────────────┘ │
│                                                                  │              │
│                                                                  ▼              │
│                                                  ┌──────────────────────────┐ │
│                                                  │      SOC TEAM (24/7)     │ │
│                                                  │                          │ │
│                                                  │ L1: Alert Triage (8)    │ │
│                                                  │ L2: Investigation (4)   │ │
│                                                  │ L3: Threat Hunt (2)     │ │
│                                                  │ IR: Incident Resp (2)   │ │
│                                                  └──────────────────────────┘ │
│                                                                                  │
│  KEY METRICS                                                                     │
│  ───────────                                                                     │
│  • MTTD: 4 minutes       • MTTR: 2 hours        • False Positive Rate: 3%      │
│  • Alerts/day: 2,500     • Incidents/month: 45  • Automation Rate: 78%         │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Checklist de Revisão de Arquitetura

### 8.1 Perímetro e Rede
- [x] WAF configurado com regras OWASP + custom
- [x] DDoS protection ativo (CloudFlare + Shield)
- [x] Segmentação de rede implementada (4 zonas)
- [x] Firewalls com regras least-privilege
- [x] Zero Trust para acesso remoto (Teleport)

### 8.2 Identidade e Acesso
- [x] SSO implementado (Okta + Keycloak)
- [x] MFA obrigatório (FIDO2)
- [x] RBAC/ABAC configurado (OPA)
- [x] Secrets em vault seguro (HashiCorp)
- [x] Service accounts com escopo mínimo

### 8.3 Dados
- [x] Criptografia em trânsito (TLS 1.3)
- [x] Criptografia em repouso (AES-256)
- [x] Key management com HSM (KMS)
- [x] Backup criptografado e testado
- [x] DLP implementado (Macie)

### 8.4 Aplicação
- [x] SAST/DAST no pipeline (Snyk, OWASP ZAP)
- [x] Dependency scanning (Snyk)
- [x] Container security (Trivy, Falco)
- [x] API security (rate limiting, auth)
- [x] Input validation

### 8.5 IA/ML Específico
- [x] Validação de dados de treinamento
- [x] Model signing e versionamento (MLflow)
- [ ] Adversarial testing realizado (em progresso)
- [x] Monitoramento de drift (Evidently)
- [ ] Guardrails para LLMs (em progresso)

### 8.6 Monitoramento
- [x] Logs centralizados (Splunk)
- [x] SIEM operacional 24/7
- [x] Alertas configurados
- [x] Incident response plan testado
- [x] Métricas de segurança definidas

---

## 9. Referências

### Fontes Utilizadas

- [Nubank - Cybersecurity Policy](https://nubank.com.br/en/contract/cybersecurity-policy/)
- [Nubank - Building Blog](https://building.nubank.com/reinventing-it-and-cyber-risk-in-the-financial-market/)
- [Miracuves - How Nubank Works](https://miracuves.com/blog/what-is-nubank-and-how-does-it-work/)
- [AWS Well-Architected Framework - Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/)
- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)

### Ferramentas de Diagramação
- Mermaid (diagramas as code)
- ASCII Art (documentação inline)
- Lucidchart (diagramas formais)

---

## 10. Aprovações

| Papel | Nome | Data |
|-------|------|------|
| Security Architect | [Exemplo] | Dez 2025 |
| CISO | [Exemplo] | Dez 2025 |
| CTO | [Exemplo] | Dez 2025 |

---

*Exemplo educacional baseado em práticas de fintechs brasileiras - MBA Cibersegurança & IA*
