# Relatório de Arquitetura de Segurança
## NeoBank Digital - Plataforma Core Banking Cloud-Native

> **Classificação**: Confidencial
> **Data**: Janeiro 2025
> **Versão**: 1.0

---

# PARTE I: RESUMO EXECUTIVO

## Destinatários
- CEO, CFO, COO
- Conselho de Administração
- Comitê de Riscos
- Investidores

---

## 1. Visão Geral para Liderança

### 1.1 Contexto do Negócio

A arquitetura de segurança do NeoBank Digital foi projetada para proteger uma plataforma que atende **mais de 50 milhões de clientes** e processa **milhões de transações diárias**. Em um ambiente onde bancos digitais são alvos constantes de ataques cibernéticos, a segurança é fundamental para a continuidade do negócio e confiança dos clientes.

### 1.2 Por Que Esta Arquitetura é Importante

| Aspecto | Impacto no Negócio |
|---------|-------------------|
| **Proteção de Receita** | Evita perdas de R$ 2-5 bilhões/ano em fraudes |
| **Confiança do Cliente** | 50M+ clientes dependem da segurança dos dados |
| **Compliance Regulatório** | Atende BACEN, LGPD, PCI-DSS (evita multas de até R$ 50M) |
| **Vantagem Competitiva** | Segurança como diferencial vs. bancos tradicionais |
| **Continuidade Operacional** | 99.99% uptime = máximo R$ 52 min de indisponibilidade/ano |

---

## 2. Indicadores-Chave de Proteção

### 2.1 Dashboard Executivo de Segurança

```
╔═══════════════════════════════════════════════════════════════════╗
║                    PAINEL DE SEGURANÇA - NEOBANK                  ║
╠═══════════════════════════════════════════════════════════════════╣
║                                                                    ║
║   DISPONIBILIDADE        ATAQUES BLOQUEADOS      TEMPO DETECÇÃO   ║
║   ┌──────────────┐       ┌──────────────┐       ┌──────────────┐  ║
║   │    99.99%    │       │   +10M/dia   │       │   4 minutos  │  ║
║   │   ▲ 0.01%    │       │   ▲ 15%      │       │   ▼ 60%      │  ║
║   └──────────────┘       └──────────────┘       └──────────────┘  ║
║                                                                    ║
║   FRAUDES EVITADAS       COMPLIANCE SCORE       ROI SEGURANÇA     ║
║   ┌──────────────┐       ┌──────────────┐       ┌──────────────┐  ║
║   │  R$ 3.2B/ano │       │     97%      │       │    340%      │  ║
║   │   ▲ 25%      │       │   ▲ 5%       │       │   ▲ 45%      │  ║
║   └──────────────┘       └──────────────┘       └──────────────┘  ║
║                                                                    ║
╚═══════════════════════════════════════════════════════════════════╝
```

### 2.2 Métricas de Valor para o Negócio

| Métrica | Valor Atual | Benchmark Mercado | Status |
|---------|-------------|-------------------|--------|
| Taxa de Fraude | 0.02% | 0.10% | 🟢 Excelente |
| Custo por Transação Segura | R$ 0.003 | R$ 0.008 | 🟢 Eficiente |
| Tempo de Resposta a Incidentes | 2 horas | 8 horas | 🟢 Superior |
| Satisfação Cliente (Segurança) | 4.7/5.0 | 4.0/5.0 | 🟢 Acima |
| Multas Regulatórias | R$ 0 | - | 🟢 Conformidade |

---

## 3. Investimento e Retorno

### 3.1 Estrutura de Investimento em Segurança

```
INVESTIMENTO ANUAL EM SEGURANÇA: R$ 180 MILHÕES

┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Infraestrutura (35%)     ████████████████░░░░░  R$ 63M    │
│  Pessoal & SOC (30%)      ██████████████░░░░░░░  R$ 54M    │
│  Ferramentas/Licenças(20%)█████████░░░░░░░░░░░░  R$ 36M    │
│  Compliance & Auditoria(10%)████░░░░░░░░░░░░░░░  R$ 18M    │
│  Treinamento & Awareness(5%)██░░░░░░░░░░░░░░░░░  R$  9M    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 3.2 Análise de ROI

| Categoria | Perdas Evitadas (Anual) | Investimento | ROI |
|-----------|------------------------|--------------|-----|
| Prevenção de Fraudes | R$ 3.200.000.000 | R$ 80M | 4.000% |
| Evitar Multas BACEN/LGPD | R$ 50.000.000 | R$ 18M | 278% |
| Prevenção de Downtime | R$ 500.000.000 | R$ 45M | 1.111% |
| Proteção de Reputação | R$ 2.000.000.000* | R$ 37M | 5.405% |
| **TOTAL** | **R$ 5.750.000.000** | **R$ 180M** | **3.194%** |

*Valor estimado de perda de market share em caso de breach significativo

---

## 4. Principais Camadas de Proteção

### 4.1 Visão Simplificada da Arquitetura

```
┌─────────────────────────────────────────────────────────────────┐
│                        CLIENTES (50M+)                          │
│                    Mobile App / Web Browser                      │
└──────────────────────────────┬──────────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────────┐
│  CAMADA 1: ESCUDO EXTERNO                                       │
│  • Proteção contra DDoS (100+ Tbps de capacidade)               │
│  • Firewall de Aplicação Web (WAF) com IA                       │
│  • Detecção de Bots Maliciosos                                  │
│  🛡️ BLOQUEIA: +10 milhões de ataques/dia                        │
└──────────────────────────────┬──────────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────────┐
│  CAMADA 2: CONTROLE DE ACESSO                                   │
│  • Autenticação biométrica + PIN                                │
│  • Verificação de dispositivo                                   │
│  • Análise de risco em tempo real                               │
│  🔐 VALIDA: 120 milhões de autenticações/dia                    │
└──────────────────────────────┬──────────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────────┐
│  CAMADA 3: PROTEÇÃO DE APLICAÇÃO                                │
│  • 500+ microserviços isolados                                  │
│  • Comunicação criptografada entre serviços                     │
│  • Detecção de fraude com Machine Learning                      │
│  🔒 PROCESSA: Milhões de transações/dia com <100ms latência     │
└──────────────────────────────┬──────────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────────┐
│  CAMADA 4: PROTEÇÃO DE DADOS                                    │
│  • Criptografia de ponta (AES-256)                              │
│  • Dados de cartão tokenizados (PCI-DSS)                        │
│  • Backup criptografado com recuperação em 15 min               │
│  💾 PROTEGE: Petabytes de dados sensíveis                       │
└─────────────────────────────────────────────────────────────────┘
```

### 4.2 Proteções Específicas para IA/ML

| Modelo | Função | Proteção | Risco Mitigado |
|--------|--------|----------|----------------|
| Detecção de Fraude | Bloqueia transações suspeitas | Monitoramento de adversarial attacks | Fraude financeira |
| Scoring de Crédito | Avalia risco de empréstimo | Testes de fairness e bias | Discriminação e compliance |
| Chatbot com IA | Atendimento ao cliente | Guardrails e filtro de conteúdo | Vazamento de dados |

---

## 5. Postura de Compliance

### 5.1 Status Regulatório

| Regulamentação | Status | Última Auditoria | Próxima Revisão |
|----------------|--------|------------------|-----------------|
| BACEN 4.893/2021 | ✅ Conforme | Out 2024 | Abr 2025 |
| LGPD | ✅ Conforme | Nov 2024 | Mai 2025 |
| PCI-DSS v4.0 | ✅ Conforme | Set 2024 | Set 2025 |
| ISO 27001:2022 | ✅ Certificado | Dez 2024 | Dez 2025 |
| SOC 2 Type II | ✅ Certificado | Out 2024 | Out 2025 |

### 5.2 Open Finance (BACEN)

A arquitetura está preparada para Open Finance com:
- **mTLS obrigatório** para todas as APIs
- **Gestão de consentimento** conforme especificações BACEN
- **Certificados ICP-Brasil** para comunicação com PIX/SPI
- **Logs de auditoria** com retenção de 10 anos

---

## 6. Riscos Residuais e Próximos Passos

### 6.1 Riscos Identificados e Mitigações

| Risco | Probabilidade | Impacto | Mitigação | Responsável |
|-------|---------------|---------|-----------|-------------|
| Ataque avançado a modelos ML | Média | Alto | Adversarial testing em progresso | CISO |
| Insider threat (funcionário) | Baixa | Muito Alto | Zero Trust + UEBA | CTO/CISO |
| Vulnerabilidade em terceiros | Média | Alto | Security assessment contínuo | Compliance |
| Indisponibilidade multi-região | Muito Baixa | Crítico | DR em GCP secundário | CTO |

### 6.2 Roadmap de Segurança 2025

| Iniciativa | Objetivo | Investimento |
|------------|----------|--------------|
| LLM Security Framework | Proteger chatbots e GenAI | R$ 15M |
| Confidential Computing | Proteção de dados em uso | R$ 25M |
| Quantum-Safe Crypto | Preparação pós-quântica | R$ 10M |
| Red Team Contínuo | Testes avançados | R$ 8M |

---

## 7. Recomendações para o Board

### 7.1 Aprovações Necessárias

1. **Manter investimento de R$ 180M** em segurança para 2025
2. **Aprovar budget adicional de R$ 58M** para iniciativas de IA segura e criptografia pós-quântica
3. **Revisar política de risco** para incluir riscos de IA/ML
4. **Nomear responsável de IA no Comitê de Riscos**

### 7.2 Indicadores para Monitoramento pelo Board

- Taxa de fraude mensal (meta: <0.03%)
- Score de compliance trimestral (meta: >95%)
- Incidentes de segurança críticos (meta: 0)
- ROI de segurança anual (meta: >300%)

---

# PARTE II: RELATÓRIO TÉCNICO

## Destinatários
- CISO (Chief Information Security Officer)
- Security Architects
- Gerente de Segurança da Informação
- Time de SOC/IR
- DevSecOps Team

---

## 1. Análise Técnica da Arquitetura

### 1.1 Stack Tecnológico de Segurança

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         STACK DE SEGURANÇA COMPLETO                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  EDGE SECURITY                                                              │
│  ├── CloudFlare Enterprise (WAF + Bot Management + DDoS)                    │
│  ├── AWS Shield Advanced (L3/L4 DDoS)                                       │
│  └── Custom ML-based Bot Detection                                          │
│                                                                             │
│  API SECURITY                                                               │
│  ├── Kong Gateway (Rate Limiting, OAuth 2.0, JWT Validation)                │
│  ├── OPA - Open Policy Agent (ABAC/RBAC)                                    │
│  └── Custom Fraud Signal Injection                                          │
│                                                                             │
│  CONTAINER/KUBERNETES SECURITY                                              │
│  ├── Istio Service Mesh (mTLS STRICT mode, AuthorizationPolicy)             │
│  ├── Falco (Runtime Security)                                               │
│  ├── Trivy (Container Scanning)                                             │
│  ├── Kyverno (Policy Engine)                                                │
│  └── External Secrets Operator → HashiCorp Vault                            │
│                                                                             │
│  IDENTITY & ACCESS                                                          │
│  ├── Keycloak (Customer IAM - 50M+ users)                                   │
│  ├── Okta (Employee SSO/MFA)                                                │
│  ├── Teleport (Zero Trust Access)                                           │
│  └── AWS IAM + Service Control Policies                                     │
│                                                                             │
│  DATA SECURITY                                                              │
│  ├── AWS KMS (HSM-backed key management)                                    │
│  ├── HashiCorp Vault (Dynamic secrets, PKI)                                 │
│  ├── Amazon Macie (PII Detection/DLP)                                       │
│  └── Databricks Unity Catalog (Data Governance)                             │
│                                                                             │
│  MONITORING & RESPONSE                                                      │
│  ├── Splunk Enterprise (SIEM - 10TB/day)                                    │
│  ├── Splunk SOAR (150+ playbooks)                                           │
│  ├── CrowdStrike Falcon (EDR)                                               │
│  └── PagerDuty (Incident Management)                                        │
│                                                                             │
│  DEVSECOPS                                                                  │
│  ├── GitLab Ultimate (SAST, DAST, Dependency Scanning)                      │
│  ├── Snyk (SCA + Container Security)                                        │
│  ├── SonarQube (Code Quality + Security)                                    │
│  └── OWASP ZAP (Dynamic Testing)                                            │
│                                                                             │
│  ML SECURITY                                                                │
│  ├── MLflow (Model Registry + Signing)                                      │
│  ├── Evidently AI (Drift Detection)                                         │
│  ├── Fairlearn (Bias Detection)                                             │
│  └── Custom Guardrails (LLM Safety)                                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 1.2 Arquitetura de Zonas de Segurança

| Zona | CIDR | Trust Level | Componentes | Controles de Acesso |
|------|------|-------------|-------------|---------------------|
| DMZ | 10.0.0.0/16 | UNTRUSTED | ALB, API Gateway, Bastion | SG: 443 inbound only, NACL: deny sanctioned |
| Application | 10.1.0.0/16 | INTERNAL | EKS, Microservices | mTLS, Network Policies, Pod Security |
| Data | 10.2.0.0/16 | SENSITIVE | Aurora, Redis, Kafka, S3 | PrivateLink only, no internet |
| Management | 10.3.0.0/16 | PRIVILEGED | Vault, Splunk, GitLab | Bastion only, JIT access, MFA |

### 1.3 Fluxo de Tráfego Seguro

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                          FLUXO DE REQUISIÇÃO SEGURA                          │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  CLIENTE                                                                     │
│     │                                                                        │
│     │ 1. HTTPS/TLS 1.3 + Certificate Pinning                                │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ CLOUDFLARE EDGE                                                     │     │
│  │ • WAF Rules (OWASP + Custom)                                       │     │
│  │ • Bot Score < 30 → CAPTCHA                                          │     │
│  │ • Rate Limit: 10K req/min/IP                                        │     │
│  │ • Geo-blocking: Sanctioned countries                                │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│     │                                                                        │
│     │ 2. Proxied request (cleaned)                                          │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ AWS ALB (DMZ)                                                       │     │
│  │ • TLS Termination (TLS 1.3 only)                                   │     │
│  │ • X-Forwarded headers validation                                    │     │
│  │ • Health check routing                                              │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│     │                                                                        │
│     │ 3. Internal TLS                                                        │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ KONG API GATEWAY                                                    │     │
│  │ • JWT Validation (RS256, 15min TTL)                                │     │
│  │ • OAuth 2.0 Scope verification                                      │     │
│  │ • Rate Limiting per user: 1000 req/min                             │     │
│  │ • Request size limit: 10MB                                          │     │
│  │ • Fraud signal injection (device_id, ip_risk, user_risk)           │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│     │                                                                        │
│     │ 4. gRPC-TLS (mTLS via Istio)                                          │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ OPA (Open Policy Agent)                                             │     │
│  │ • ABAC policy evaluation                                            │     │
│  │ • Resource ownership check (user.id == resource.owner_id)           │     │
│  │ • Transaction limit enforcement                                      │     │
│  │ • Time-based controls (night transfers require step-up)             │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│     │                                                                        │
│     │ 5. Authorized request                                                  │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ MICROSERVICE (Kubernetes)                                           │     │
│  │ • Network Policy: namespace isolation                               │     │
│  │ • Pod Security Standard: restricted                                 │     │
│  │ • Secrets from External Secrets Operator                            │     │
│  │ • ReadOnlyRootFilesystem: true                                      │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│     │                                                                        │
│     │ 6. IAM Auth + TLS                                                      │
│     ▼                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐     │
│  │ DATABASE (Aurora PostgreSQL)                                        │     │
│  │ • TDE (AES-256)                                                     │     │
│  │ • Column-level encryption (PII)                                     │     │
│  │ • Audit logging enabled                                             │     │
│  │ • IAM authentication (no passwords)                                 │     │
│  └────────────────────────────────────────────────────────────────────┘     │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Controles de Segurança Detalhados

### 2.1 Segurança de Perímetro

#### 2.1.1 WAF Configuration

```yaml
# CloudFlare WAF Rules (Exemplo)
waf_rules:
  owasp_core_ruleset: enabled
  paranoia_level: 2

  custom_rules:
    - name: "Block SQL Injection"
      expression: |
        (http.request.uri.path contains "UNION" and
         http.request.uri.path contains "SELECT") or
        (http.request.body contains "' OR 1=1" or
         http.request.body contains "'; DROP TABLE")
      action: block

    - name: "Rate Limit API"
      expression: |
        http.request.uri.path matches "^/api/.*"
      rate_limit:
        requests_per_minute: 10000
        key: ip.src
      action: challenge

    - name: "Block Sanctioned Countries"
      expression: |
        ip.geoip.country in {"KP" "IR" "CU" "SY" "RU"}
      action: block
```

#### 2.1.2 DDoS Mitigation

| Layer | Protection | Capacity | Response Time |
|-------|-----------|----------|---------------|
| L3/L4 | AWS Shield Advanced | 100+ Tbps | <1 second |
| L7 | CloudFlare + WAF | 10M+ req/sec | <10ms |
| Application | Kong Rate Limiting | Customizable | Real-time |

### 2.2 Segurança de Identidade

#### 2.2.1 Fluxo de Autenticação de Clientes

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    AUTENTICAÇÃO MULTI-FATOR (CLIENTES)                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  FATOR 1: BIOMETRIA (Device-bound)                                     │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • Face ID / Touch ID (iOS)                                       │   │
│  │ • Fingerprint / Face (Android)                                   │   │
│  │ • Keys stored in Secure Enclave / TEE                           │   │
│  │ • WebAuthn/FIDO2 compliant                                       │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  FATOR 2: PIN (Knowledge)                                              │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • 6 dígitos numéricos                                            │   │
│  │ • Encrypted with device key                                      │   │
│  │ • 5 tentativas → bloqueio temporário                            │   │
│  │ • 10 tentativas → bloqueio permanente                           │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  FATOR 3: CONTEXTO (Risk-based - Opcional)                            │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • Device fingerprinting                                          │   │
│  │ • Geolocalização                                                 │   │
│  │ • Behavioral biometrics (typing pattern)                        │   │
│  │ • Network reputation                                             │   │
│  │ • ML Risk Score → Step-up auth se score > threshold             │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  STEP-UP AUTH (Transações Sensíveis)                                   │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ Triggers:                                                        │   │
│  │ • PIX > R$ 5.000                                                 │   │
│  │ • Transferência para novo destinatário                          │   │
│  │ • Alteração de dados cadastrais                                  │   │
│  │ • Primeiro acesso em novo dispositivo                           │   │
│  │                                                                  │   │
│  │ Verificação adicional:                                           │   │
│  │ • SMS OTP (6 dígitos, 5 min TTL)                                │   │
│  │ • Re-autenticação biométrica                                     │   │
│  │ • Confirmação por email                                          │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

#### 2.2.2 Configuração de Tokens JWT

```json
{
  "access_token": {
    "algorithm": "RS256",
    "ttl": "15 minutes",
    "claims": {
      "sub": "user_uuid",
      "aud": "neobank-api",
      "iss": "keycloak.neobank.internal",
      "scope": ["account:read", "transfer:write", "pix:write"],
      "device_id": "device_fingerprint_hash",
      "risk_level": "low|medium|high"
    }
  },
  "refresh_token": {
    "ttl": "7 days",
    "rotation": "on_use",
    "absolute_ttl": "30 days",
    "revocation": "immediate_on_logout"
  }
}
```

### 2.3 Segurança de Dados

#### 2.3.1 Estratégia de Criptografia

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     HIERARQUIA DE CHAVES (KMS)                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│                    ┌────────────────────────┐                          │
│                    │    AWS Root Key        │                          │
│                    │    (HSM-backed)        │                          │
│                    │    Managed by AWS      │                          │
│                    └───────────┬────────────┘                          │
│                                │                                        │
│            ┌───────────────────┼───────────────────┐                   │
│            │                   │                   │                    │
│            ▼                   ▼                   ▼                    │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐          │
│  │ Customer Master │ │  Database       │ │  Secrets        │          │
│  │ Key (CMK)       │ │  Master Key     │ │  Master Key     │          │
│  │ -annual rotate  │ │  -monthly rotate│ │  -daily rotate  │          │
│  └────────┬────────┘ └────────┬────────┘ └────────┬────────┘          │
│           │                   │                   │                    │
│           ▼                   ▼                   ▼                    │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐          │
│  │ Data Encryption │ │ Column/Field    │ │ Dynamic Secrets │          │
│  │ Keys (DEK)      │ │ Encryption Keys │ │ (Vault)         │          │
│  │ -per object     │ │ -per table/col  │ │ -per request    │          │
│  └─────────────────┘ └─────────────────┘ └─────────────────┘          │
│                                                                         │
│  Envelope Encryption: DEK encrypted with CMK, CMK encrypted with Root  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

#### 2.3.2 Mapeamento de Dados Sensíveis

| Dado | Classificação | Storage | Encryption | Masking | Retention |
|------|---------------|---------|------------|---------|-----------|
| CPF | Restrito | Aurora | Column-level AES-256 | XXX.XXX.XXX-XX | 10 anos |
| Número do Cartão | PCI | Tokenization Vault | HSM-backed | **** **** **** 1234 | PCI rules |
| CVV | PCI | Não armazenado | N/A | N/A | Não retido |
| Senha/PIN | Restrito | Aurora | bcrypt + pepper | Nunca exibido | Até alteração |
| Saldo | Confidencial | Aurora | TDE | Valor real | 10 anos |
| Biometria | Restrito | Device-only | Secure Enclave | N/A | Device-bound |
| Logs de Acesso | Interno | Splunk | TLS + S3 SSE | IP parcial | 90 dias hot, 7 anos cold |

### 2.4 Segurança de Kubernetes/Containers

#### 2.4.1 Pod Security Standards

```yaml
# Pod Security Policy (Restricted)
apiVersion: policy/v1
kind: PodSecurityPolicy
metadata:
  name: restricted
spec:
  privileged: false
  allowPrivilegeEscalation: false
  requiredDropCapabilities:
    - ALL
  volumes:
    - 'configMap'
    - 'emptyDir'
    - 'projected'
    - 'secret'
    - 'downwardAPI'
    - 'persistentVolumeClaim'
  hostNetwork: false
  hostIPC: false
  hostPID: false
  runAsUser:
    rule: 'MustRunAsNonRoot'
  seLinux:
    rule: 'RunAsAny'
  fsGroup:
    rule: 'RunAsAny'
  readOnlyRootFilesystem: true
```

#### 2.4.2 Network Policies

```yaml
# Isolamento de Namespace
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-all
  namespace: payments
spec:
  podSelector: {}
  policyTypes:
    - Ingress
    - Egress
---
# Allow específico
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-pix-service
  namespace: payments
spec:
  podSelector:
    matchLabels:
      app: pix-service
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: security
        - podSelector:
            matchLabels:
              app: api-gateway
      ports:
        - protocol: TCP
          port: 8080
  egress:
    - to:
        - namespaceSelector:
            matchLabels:
              name: data
      ports:
        - protocol: TCP
          port: 5432
```

---

## 3. Arquitetura de Segurança para IA/ML

### 3.1 Pipeline MLSecOps

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      PIPELINE ML SEGURO (MLSECOPS)                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  DATA PREPARATION                                                       │
│  ────────────────                                                       │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ 1. Data Extraction (Aurora → Databricks)                        │   │
│  │    • Query via IAM auth (no credentials in code)                │   │
│  │    • Encrypted connection (TLS)                                  │   │
│  │                                                                  │   │
│  │ 2. PII Detection (Amazon Macie)                                 │   │
│  │    • Automated scanning of training datasets                    │   │
│  │    • Alert on unmasked CPF, card numbers, etc.                  │   │
│  │                                                                  │   │
│  │ 3. Data Anonymization (Databricks)                              │   │
│  │    • K-anonymity for demographic data                           │   │
│  │    • Differential privacy for aggregations                      │   │
│  │                                                                  │   │
│  │ 4. Bias Check (Fairlearn)                                       │   │
│  │    • Demographic parity                                          │   │
│  │    • Equalized odds                                              │   │
│  │    • Block training if bias > threshold                         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                               │                                        │
│                               ▼                                        │
│  MODEL TRAINING                                                        │
│  ──────────────                                                        │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ SageMaker (VPC-only, no internet)                               │   │
│  │ • Training instance: ml.p4d.24xlarge (isolated VPC)             │   │
│  │ • Model artifacts: encrypted S3 bucket                          │   │
│  │ • Training logs: CloudWatch (encrypted)                         │   │
│  │ • No public endpoints                                            │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                               │                                        │
│                               ▼                                        │
│  MODEL VALIDATION                                                      │
│  ────────────────                                                      │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ Security & Quality Gates                                        │   │
│  │ • Performance metrics (accuracy > 95%)                          │   │
│  │ • Fairness metrics (demographic parity > 0.90)                  │   │
│  │ • Adversarial robustness (ART library)                          │   │
│  │ • Model explainability (SHAP values)                            │   │
│  │ • Security scan (dependency check)                              │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                               │                                        │
│                               ▼                                        │
│  MODEL REGISTRY                                                        │
│  ──────────────                                                        │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ MLflow Model Registry                                           │   │
│  │ • Version control (git-like)                                    │   │
│  │ • Model signing (SHA256 + RSA signature)                        │   │
│  │ • Immutable artifacts                                           │   │
│  │ • Approval workflow (Data Science → Security → Production)      │   │
│  │ • Model card (documentation, limitations, intended use)         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                               │                                        │
│                               ▼                                        │
│  DEPLOYMENT                                                            │
│  ──────────                                                            │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ EKS + Istio (Production)                                        │   │
│  │ • Canary deployment (5% → 25% → 100%)                           │   │
│  │ • Auto-rollback on error rate > 1%                              │   │
│  │ • Input validation (schema enforcement)                         │   │
│  │ • Output filtering (PII detection)                              │   │
│  │ • Rate limiting (per user/IP)                                   │   │
│  │ • Audit logging (all predictions)                               │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                               │                                        │
│                               ▼                                        │
│  MONITORING                                                            │
│  ──────────                                                            │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ Continuous Monitoring                                           │   │
│  │ • Model drift detection (Evidently AI)                          │   │
│  │ • Fairness monitoring (weekly reports)                          │   │
│  │ • Adversarial attack detection                                  │   │
│  │ • Performance degradation alerts                                │   │
│  │ • Automatic retraining triggers                                 │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3.2 Controles de Segurança para LLMs

| Controle | Implementação | Risco Mitigado |
|----------|---------------|----------------|
| Input Sanitization | Regex + ML classifier para prompt injection | Jailbreak, prompt injection |
| Output Filtering | PII detector + content safety classifier | Data leakage, harmful content |
| Rate Limiting | 100 req/min/user, 1000 req/min/IP | Resource exhaustion, DoS |
| Context Isolation | Separate sessions, no persistent memory | Context leakage |
| Guardrails | Refusal patterns, topic restrictions | Off-topic abuse |
| Audit Logging | All prompts/responses logged (redacted PII) | Forensics, compliance |

### 3.3 Modelo de Detecção de Fraude - Controles Específicos

```yaml
# Fraud Detection Model Security Config
model:
  name: fraud-detect
  version: 3.2.1

input_validation:
  schema:
    transaction_amount:
      type: float
      min: 0.01
      max: 1000000
    merchant_category:
      type: string
      allowed_values: [list of valid MCCs]
    device_fingerprint:
      type: string
      format: sha256

  rate_limits:
    per_user: 100/minute
    per_device: 50/minute
    burst: 20/second

adversarial_detection:
  enabled: true
  sensitivity: medium
  actions:
    - log
    - alert
    - block_if_confidence_high

output_controls:
  format: json
  fields:
    - fraud_score (0-1)
    - decision (approve/review/deny)
    - explanation_codes
  redact:
    - model_internals
    - feature_weights

monitoring:
  drift_detection:
    algorithm: kolmogorov_smirnov
    threshold: 0.05
    alert_channel: pagerduty
  performance:
    accuracy_threshold: 0.95
    latency_p99_threshold_ms: 100
```

---

## 4. Arquitetura SOC/SIEM

### 4.1 Fluxo de Dados de Segurança

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ARQUITETURA SOC - FLUXO DE DADOS                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  DATA SOURCES                          COLLECTION & PROCESSING          │
│  ────────────                          ──────────────────────           │
│                                                                         │
│  ┌───────────────┐                                                      │
│  │ CLOUD (AWS)   │                                                      │
│  │ • CloudTrail  │─────┐                                               │
│  │ • GuardDuty   │     │                                               │
│  │ • VPC Flow    │     │         ┌─────────────────────────────┐      │
│  │ • WAF Logs    │     │         │                             │      │
│  │ • Config      │     ├────────▶│     KINESIS FIREHOSE       │      │
│  └───────────────┘     │         │     + Lambda Transform      │      │
│                        │         │                             │      │
│  ┌───────────────┐     │         │  • JSON normalization       │      │
│  │ KUBERNETES    │     │         │  • Field extraction         │      │
│  │ • Audit logs  │─────┤         │  • Enrichment (GeoIP)       │      │
│  │ • Istio access│     │         │  • PII redaction            │      │
│  │ • Falco alerts│     │         │                             │      │
│  └───────────────┘     │         └──────────────┬──────────────┘      │
│                        │                        │                      │
│  ┌───────────────┐     │                        │                      │
│  │ APPLICATIONS  │     │                        │                      │
│  │ • App logs    │─────┤                        ▼                      │
│  │ • API logs    │     │         ┌─────────────────────────────┐      │
│  │ • Auth logs   │     │         │                             │      │
│  │ • DB audit    │     │         │     SPLUNK ENTERPRISE       │      │
│  └───────────────┘     │         │     (10 TB/day)             │      │
│                        │         │                             │      │
│  ┌───────────────┐     │         │  DETECTION ENGINE:          │      │
│  │ ENDPOINTS     │     │         │  • 500+ correlation rules   │      │
│  │ • CrowdStrike │─────┘         │  • ML anomaly detection     │      │
│  │ • Osquery     │               │  • MITRE ATT&CK mapping     │      │
│  └───────────────┘               │  • Threat intel correlation │      │
│                                  │                             │      │
│  ┌───────────────┐               │  DASHBOARDS:                │      │
│  │ THREAT INTEL  │               │  • Executive summary        │      │
│  │ • FS-ISAC     │──────────────▶│  • SOC operations           │      │
│  │ • MISP        │               │  • Compliance               │      │
│  │ • AlienVault  │               │  • ML model security        │      │
│  └───────────────┘               │                             │      │
│                                  └──────────────┬──────────────┘      │
│                                                 │                      │
│                                                 ▼                      │
│  RESPONSE                                                              │
│  ────────                        ┌─────────────────────────────┐      │
│                                  │                             │      │
│                                  │     SPLUNK SOAR             │      │
│  ┌───────────────┐               │     (Automation)            │      │
│  │ SOC TEAM      │               │                             │      │
│  │               │◀──────────────│  PLAYBOOKS (150+):          │      │
│  │ L1: 8 analysts│               │  • Phishing response        │      │
│  │ L2: 4 analysts│               │  • Malware containment      │      │
│  │ L3: 2 hunters │               │  • Account compromise       │      │
│  │ IR: 2 resp.   │               │  • Data exfiltration        │      │
│  │               │               │  • Insider threat           │      │
│  └───────────────┘               │  • ML model attack          │      │
│                                  │                             │      │
│                                  │  INTEGRATIONS:              │      │
│                                  │  • PagerDuty (alerting)     │      │
│                                  │  • Jira (ticketing)         │      │
│                                  │  • Slack (notifications)    │      │
│                                  │  • Teleport (access)        │      │
│                                  │                             │      │
│                                  └─────────────────────────────┘      │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Regras de Detecção Críticas

| ID | Nome | MITRE ATT&CK | Severidade | Resposta Automática |
|----|------|--------------|------------|---------------------|
| DET-001 | Brute Force Login | T1110 | Alta | Block IP após 10 falhas |
| DET-002 | Credential Stuffing | T1110.004 | Alta | CAPTCHA + rate limit |
| DET-003 | Privilege Escalation | T1078.003 | Crítica | Revoke session + alert |
| DET-004 | Data Exfiltration | T1048 | Crítica | Block + forensics |
| DET-005 | Lateral Movement | T1021 | Alta | Isolate + investigate |
| DET-006 | Anomalous API Usage | T1106 | Média | Enhanced logging |
| DET-007 | ML Model Tampering | N/A | Crítica | Rollback + alert |
| DET-008 | Adversarial Input | N/A | Alta | Block + analyze |

### 4.3 Métricas de SOC

| Métrica | Target | Atual | Status |
|---------|--------|-------|--------|
| MTTD (Mean Time to Detect) | <5 min | 4 min | 🟢 |
| MTTR (Mean Time to Respond) | <4 hours | 2 hours | 🟢 |
| False Positive Rate | <5% | 3% | 🟢 |
| Automation Rate | >75% | 78% | 🟢 |
| Alert-to-Incident Ratio | <100:1 | 55:1 | 🟢 |
| SOC Analyst Utilization | 70-80% | 75% | 🟢 |

---

## 5. Compliance e Auditoria

### 5.1 Mapeamento de Controles

| Requisito | Framework | Controle Implementado | Evidência |
|-----------|-----------|----------------------|-----------|
| Criptografia de dados | PCI-DSS 3.4 | AES-256 + Tokenization | Scan report, KMS logs |
| Controle de acesso | BACEN 4.893 | RBAC + MFA + JIT | IAM policies, audit logs |
| Logs de auditoria | LGPD Art. 37 | Splunk 90d + S3 7y | Retention config, samples |
| Gestão de vulnerabilidades | ISO 27001 A.12.6 | Qualys + Snyk | Scan reports, SLAs |
| Resposta a incidentes | NIST CSF RS | SOAR + Playbooks | IR reports, metrics |

### 5.2 Cronograma de Auditorias

| Auditoria | Frequência | Última | Próxima | Responsável |
|-----------|------------|--------|---------|-------------|
| PCI-DSS QSA | Anual | Set 2024 | Set 2025 | Deloitte |
| SOC 2 Type II | Anual | Out 2024 | Out 2025 | EY |
| ISO 27001 Surveillance | Anual | Dez 2024 | Dez 2025 | BSI |
| Pentest Externo | Semestral | Nov 2024 | Mai 2025 | Coalfire |
| Red Team | Anual | Ago 2024 | Ago 2025 | CrowdStrike |
| BACEN Inspection | Sob demanda | Jun 2024 | - | BACEN |

---

## 6. Gaps Identificados e Remediações

### 6.1 Análise de Gaps

| Gap | Risco | Prioridade | Remediação | Prazo |
|-----|-------|------------|------------|-------|
| Adversarial testing incompleto para ML | Ataques a modelos não detectados | Alta | Implementar ART library, red team ML | Q2 2025 |
| Guardrails LLM em progresso | Prompt injection, data leakage | Alta | Deploy NeMo Guardrails | Q1 2025 |
| Falta de Confidential Computing | Dados expostos em memória | Média | AWS Nitro Enclaves | Q3 2025 |
| Criptografia não quantum-safe | Vulnerável a computação quântica | Baixa | Migração para PQC | 2026 |

### 6.2 Plano de Remediação Detalhado

#### Gap 1: Adversarial Testing para ML

```
OBJETIVO: Implementar testes adversariais automatizados no pipeline ML

AÇÕES:
1. Integrar IBM Adversarial Robustness Toolbox (ART)
   - Ataques: FGSM, PGD, C&W
   - Métricas: Robustness accuracy, perturbation distance

2. Red Team específico para ML
   - Evasion attacks (fraudadores)
   - Model extraction attempts
   - Data poisoning simulation

3. Monitoramento contínuo
   - Detecção de inputs adversariais em produção
   - Alertas para padrões suspeitos

TIMELINE: Q2 2025
BUDGET: R$ 2M
OWNER: ML Security Lead
```

#### Gap 2: Guardrails para LLMs

```
OBJETIVO: Implementar controles de segurança para chatbot com IA generativa

AÇÕES:
1. Deploy NVIDIA NeMo Guardrails
   - Input rails: prompt injection detection
   - Output rails: PII filtering, topic restriction

2. Content Safety API
   - Integração com Azure Content Safety
   - Classificação de conteúdo (hate, violence, self-harm)

3. Prompt Engineering Guidelines
   - System prompt hardening
   - Jailbreak-resistant prompts

4. Monitoring & Logging
   - All conversations logged (redacted)
   - Anomaly detection on usage patterns

TIMELINE: Q1 2025
BUDGET: R$ 1.5M
OWNER: AI Platform Lead
```

---

## 7. Recomendações Técnicas

### 7.1 Curto Prazo (0-6 meses)

1. **Completar implementação de Guardrails para LLM** - Risco alto de prompt injection no chatbot
2. **Expandir adversarial testing** - Incluir todos os modelos em produção
3. **Implementar SBOM** (Software Bill of Materials) - Compliance e supply chain security
4. **Upgrade para EKS 1.30** - Security fixes e features

### 7.2 Médio Prazo (6-12 meses)

1. **Confidential Computing** - AWS Nitro Enclaves para processamento de dados sensíveis
2. **Zero Trust Network Access** - Expandir Teleport para todos os sistemas
3. **AI Red Team** - Equipe dedicada a testar modelos de ML
4. **Chaos Engineering** - Testes de resiliência de segurança

### 7.3 Longo Prazo (12-24 meses)

1. **Criptografia pós-quântica** - Migração gradual para algoritmos quantum-safe
2. **Homomorphic Encryption** - Computação sobre dados criptografados
3. **Federated Learning** - Treinamento descentralizado para privacidade
4. **Security Mesh Architecture** - Próxima geração de arquitetura de segurança

---

## 8. Conclusão

A arquitetura de segurança do NeoBank Digital representa uma implementação madura e abrangente de controles de segurança para um banco digital cloud-native. Com mais de 500 microserviços, 50 milhões de clientes e milhões de transações diárias, a arquitetura demonstra:

**Pontos Fortes:**
- Defense-in-depth com múltiplas camadas de proteção
- Zero Trust implementado para acessos internos
- SOC 24/7 com alta taxa de automação (78%)
- Pipeline DevSecOps maduro
- Compliance com principais frameworks (PCI-DSS, ISO 27001, LGPD, BACEN)

**Áreas de Melhoria:**
- Segurança de IA/ML precisa de amadurecimento (adversarial testing, guardrails)
- Preparação para ameaças quânticas
- Confidential computing para dados em uso

**Métricas de Sucesso:**
- Taxa de fraude 5x menor que mercado
- MTTD de 4 minutos
- Zero multas regulatórias
- ROI de segurança >3000%

A manutenção desta postura de segurança requer investimento contínuo, atualização constante das defesas e adaptação às novas ameaças, especialmente no domínio de IA/ML.

---

*Relatório elaborado para fins educacionais - MBA Cibersegurança & IA*
