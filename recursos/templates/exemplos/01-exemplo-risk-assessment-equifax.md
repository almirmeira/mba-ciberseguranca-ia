# Risk Assessment - Caso Equifax 2017
## Avaliação de Riscos de Segurança Cibernética (Exemplo Baseado em Caso Real)

> **Nota**: Este documento é um exemplo educacional baseado em informações públicas sobre o vazamento de dados da Equifax em 2017. Foi elaborado para fins de aprendizado no contexto do MBA em Cibersegurança & IA.

---

## 1. Informações do Projeto

| Campo | Descrição |
|-------|-----------|
| **Nome do Projeto/Sistema** | Portal de Disputas Online - Equifax |
| **Responsável pela Avaliação** | Equipe de Segurança da Informação |
| **Data da Avaliação** | Março 2017 (Avaliação Hipotética Pré-Incidente) |
| **Versão do Documento** | 1.0 |
| **Próxima Revisão** | Setembro 2017 |

---

## 2. Escopo da Avaliação

### 2.1 Sistemas/Ativos em Escopo
| ID | Nome do Ativo | Tipo | Criticidade | Proprietário |
|----|---------------|------|-------------|--------------|
| A001 | Portal de Disputas Online | Aplicação Web | **Alta** | TI Corporativa |
| A002 | Apache Struts Framework | Componente de Software | **Alta** | Desenvolvimento |
| A003 | Banco de Dados de Consumidores | Dados | **Crítica** | Data Management |
| A004 | Servidores de Aplicação | Infraestrutura | Alta | Operações |
| A005 | Rede Interna Corporativa | Infraestrutura | Alta | Network Ops |
| A006 | Credenciais de Banco de Dados | Dados | **Crítica** | DBA Team |
| A007 | Certificados SSL/TLS | Infraestrutura | Alta | Security Ops |

### 2.2 Sistemas Fora do Escopo
- Sistemas de RH internos
- Aplicações de parceiros B2B (avaliação separada)

---

## 3. Metodologia de Avaliação

### 3.1 Framework Utilizado
- [x] NIST RMF
- [x] ISO 27005
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
| 5 - Crítico | > $500M | Parada total > 1 semana | Cobertura internacional | Class action, multas severas |
| 4 - Alto | $100M - 500M | Parada parcial 1-7 dias | Cobertura nacional negativa | Multas significativas |
| 3 - Médio | $10M - 100M | Degradação significativa | Cobertura regional negativa | Notificação a reguladores |
| 2 - Baixo | $1M - 10M | Degradação menor | Reclamações de clientes | Observações de auditoria |
| 1 - Mínimo | < $1M | Impacto negligenciável | Nenhum | Nenhum |

---

## 4. Identificação de Ameaças

### 4.1 Catálogo de Ameaças Identificadas
| ID | Categoria | Ameaça | Agente de Ameaça | Motivação |
|----|-----------|--------|------------------|-----------|
| T001 | Externa | Exploração de Vulnerabilidade Web (RCE) | APT / Estado-Nação | Espionagem, Roubo de Dados |
| T002 | Externa | SQL Injection | Criminosos Cibernéticos | Financeira |
| T003 | Externa | Exfiltração de Dados em Massa | APT | Roubo de Identidade |
| T004 | Interna | Falha em Aplicar Patches | Negligência | N/A |
| T005 | Externa | Movimentação Lateral | Atacantes Sofisticados | Acesso a mais dados |
| T006 | Interna | Credenciais em Texto Plano | Má Configuração | N/A |
| T007 | Externa | Persistência em Rede | APT | Acesso prolongado |
| T008 | Interna | Certificados Expirados | Negligência Operacional | N/A |

---

## 5. Identificação de Vulnerabilidades

### 5.1 Vulnerabilidades Técnicas
| ID | Descrição | Ativos Afetados | CVE | CVSS |
|----|-----------|-----------------|-----|------|
| V001 | **Apache Struts RCE - Jakarta Multipart Parser** | A002, A001 | **CVE-2017-5638** | **10.0 (Crítico)** |
| V002 | Falta de segmentação de rede adequada | A004, A005 | N/A | N/A |
| V003 | Credenciais de BD em texto plano | A003, A006 | N/A | N/A |
| V004 | Ausência de MFA em contas privilegiadas | A003, A004 | N/A | N/A |
| V005 | Certificados SSL expirados (9 meses) | A007 | N/A | N/A |
| V006 | Detecção de intrusão ineficaz | A005 | N/A | N/A |
| V007 | Credenciais padrão (admin/admin) | A003 | N/A | N/A |

### 5.2 Vulnerabilidades Organizacionais
| ID | Descrição | Área Afetada | Controles Existentes |
|----|-----------|--------------|---------------------|
| V101 | Processo de patching ineficiente | TI/Operações | Política existe mas não é seguida |
| V102 | Falta de inventário atualizado de ativos | Governança | Parcial |
| V103 | Ausência de monitoramento de certificados | Security Ops | Nenhum |
| V104 | Comunicação falha entre equipes de segurança | Organização | Ad-hoc |

---

## 6. Análise de Riscos

### 6.1 Matriz de Riscos (Avaliação Pré-Incidente)

| ID Risco | Ameaça | Vulnerabilidade | Ativo | Prob. | Impacto | Risco Inerente | Controles Existentes | Risco Residual |
|----------|--------|-----------------|-------|-------|---------|----------------|---------------------|----------------|
| **R001** | T001 | V001 (CVE-2017-5638) | A001, A002 | **5** | **5** | **25 (Crítico)** | Nenhum (patch não aplicado) | **25 (Crítico)** |
| **R002** | T003 | V002 | A003 | 4 | 5 | **20 (Crítico)** | Firewall básico | **18 (Crítico)** |
| **R003** | T005 | V003 | A006 | 4 | 5 | **20 (Crítico)** | Nenhum | **20 (Crítico)** |
| R004 | T004 | V101 | A002 | 5 | 4 | **20 (Crítico)** | Política (não seguida) | **18 (Alto)** |
| R005 | T006 | V006, V005 | A005 | 4 | 4 | **16 (Alto)** | Certificado expirado | **16 (Alto)** |
| R006 | T007 | V004 | A003, A004 | 3 | 5 | **15 (Alto)** | Senha básica | **14 (Alto)** |
| R007 | T002 | V007 | A003 | 3 | 5 | **15 (Alto)** | Credenciais padrão | **15 (Alto)** |

### 6.2 Mapa de Calor de Riscos

```
Impacto
    5 │  R004  R001   R001  R001  ████
      │        R002   R002  R002  R003
    4 │        R005   R005  ████  ████
      │               R005
    3 │              ████   ████  ████
      │
    2 │
      │
    1 │
      └──────────────────────────────────
        1      2      3      4      5
                  Probabilidade

    ████ = Risco Crítico (Ação Imediata)
```

### 6.3 Análise do Risco Principal (R001)

```
╔══════════════════════════════════════════════════════════════════════╗
║                    RISCO CRÍTICO: CVE-2017-5638                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  VULNERABILIDADE: Apache Struts Jakarta Multipart Parser RCE         ║
║  CVSS Score: 10.0 (CRÍTICO)                                          ║
║  Data do Patch Disponível: 7 de Março de 2017                        ║
║  Status do Patch: NÃO APLICADO                                       ║
║                                                                       ║
║  CENÁRIO DE ATAQUE:                                                  ║
║  1. Atacante envia HTTP request com Content-Type malicioso           ║
║  2. Parser Jakarta falha na validação                                ║
║  3. Execução remota de código no servidor                            ║
║  4. Comprometimento total do sistema                                 ║
║                                                                       ║
║  IMPACTO POTENCIAL:                                                  ║
║  • Acesso não autorizado a 147+ milhões de registros                 ║
║  • PII: SSN, DOB, endereços, números de carteira de motorista        ║
║  • Multas regulatórias estimadas: $500M+                             ║
║  • Danos à reputação: Incalculáveis                                  ║
║                                                                       ║
║  RECOMENDAÇÃO: PATCH IMEDIATO (SLA: 24 HORAS)                        ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 7. O Que Realmente Aconteceu (Análise Pós-Incidente)

### 7.1 Timeline do Incidente Real

| Data | Evento |
|------|--------|
| 7 Mar 2017 | Apache lança patch para CVE-2017-5638 |
| 8 Mar 2017 | US-CERT emite alerta público |
| 9 Mar 2017 | Equifax recebe instrução interna para aplicar patch |
| **9 Mar 2017** | **Patch NÃO é aplicado no Portal de Disputas** |
| **10 Mar 2017** | **Atacantes ganham acesso inicial** |
| Mai-Jul 2017 | Atacantes exfiltram dados por 76 dias |
| 29 Jul 2017 | Equifax descobre a violação (certificado SSL renovado) |
| 7 Set 2017 | Divulgação pública |

### 7.2 Impacto Real

| Categoria | Impacto |
|-----------|---------|
| **Registros Afetados** | 147,9 milhões (EUA) + 15,2 milhões (UK) + 19.000 (Canadá) |
| **Dados Expostos** | SSN, DOB, endereços, números de carteira de motorista, cartões de crédito |
| **Queda das Ações** | 30% (imediato) |
| **Custo Total** | $1,38 bilhão |
| **Acordo FTC** | $700 milhões (2019) |
| **Atribuição** | Exército de Libertação Popular da China (indiciamento 2020) |

---

## 8. Plano de Tratamento de Riscos (Recomendações)

### 8.1 Estratégias de Tratamento

| ID Risco | Estratégia | Descrição do Tratamento | Responsável | Prazo | Custo Est. |
|----------|------------|-------------------------|-------------|-------|------------|
| R001 | **Mitigar** | Aplicar patch CVE-2017-5638 IMEDIATAMENTE | Security Ops | **24h** | $10K |
| R002 | Mitigar | Implementar segmentação de rede (microsegmentação) | Network Team | 90 dias | $500K |
| R003 | Mitigar | Implementar vault para credenciais (HashiCorp Vault) | DevOps | 60 dias | $200K |
| R004 | Mitigar | Automatizar patch management | IT Ops | 30 dias | $150K |
| R005 | Mitigar | Implementar monitoramento de certificados + auto-renovação | Security Ops | 15 dias | $50K |
| R006 | Mitigar | Implementar MFA obrigatório | IAM Team | 30 dias | $100K |
| R007 | Mitigar | Eliminar credenciais padrão, implementar política de senhas | DBA Team | 7 dias | $20K |

### 8.2 Controles Recomendados (Baseado em Lições Aprendidas)

| Controle | Tipo | Riscos Mitigados | Prioridade |
|----------|------|------------------|------------|
| **Patch Management Automatizado** | Preventivo | R001, R004 | **Crítica** |
| **Segmentação de Rede Zero Trust** | Preventivo | R002, R003, R005 | Crítica |
| **MFA Universal** | Preventivo | R006, R007 | Alta |
| **Gestão de Secrets (Vault)** | Preventivo | R003, R007 | Alta |
| **SIEM com Detecção de Exfiltração** | Detectivo | R002, R003 | Alta |
| **Monitoramento de Certificados** | Detectivo | R005 | Média |
| **Vulnerability Scanning Contínuo** | Detectivo | R001, R004 | Alta |
| **Penetration Testing Trimestral** | Detectivo | Todos | Alta |

---

## 9. Métricas e KPIs (Recomendados Pós-Incidente)

### 9.1 Indicadores de Risco

| Métrica | Estado Pré-Incidente | Meta Pós-Incidente | Atual |
|---------|---------------------|-------------------|-------|
| Tempo médio para aplicar patches críticos | >30 dias | **<48 horas** | |
| % de sistemas com vulnerabilidades críticas | Desconhecido | **<1%** | |
| % de contas privilegiadas com MFA | 0% | **100%** | |
| Tempo de detecção de intrusão (MTTD) | 76 dias | **<24 horas** | |
| Cobertura de segmentação de rede | Mínima | **>90%** | |
| Credenciais em texto plano | Presentes | **Zero** | |

---

## 10. Lições Aprendidas (Análise Crítica)

### 10.1 Falhas de Governança Identificadas

1. **Falha no Processo de Patching**: O patch estava disponível 2 dias antes do ataque, mas nunca foi aplicado ao sistema vulnerável.

2. **Falta de Visibilidade de Ativos**: A equipe de segurança não tinha inventário completo de onde Apache Struts era utilizado.

3. **Monitoramento Ineficaz**: Certificado SSL expirado por 9 meses impediu detecção de tráfego malicioso.

4. **Credenciais Inseguras**: Uso de "admin/admin" e credenciais em texto plano facilitou movimentação lateral.

5. **Comunicação Falha**: A instrução para aplicar o patch não chegou à pessoa responsável.

### 10.2 Recomendações de Melhoria

```
┌─────────────────────────────────────────────────────────────────────┐
│              FRAMEWORK DE MELHORIA PÓS-EQUIFAX                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. PROCESSOS                                                        │
│     □ Implementar SLA rígido para patches críticos (24-48h)         │
│     □ Automatizar deployment de patches com rollback                 │
│     □ Criar processo de verificação de patch application            │
│                                                                      │
│  2. TECNOLOGIA                                                       │
│     □ Implementar segmentação Zero Trust                            │
│     □ Deploy de SIEM com análise comportamental                     │
│     □ Vault para gestão de secrets                                  │
│     □ Monitoramento contínuo de certificados                        │
│                                                                      │
│  3. PESSOAS                                                          │
│     □ Treinamento obrigatório em segurança                          │
│     □ Responsabilidades claramente definidas                        │
│     □ Cultura de segurança top-down                                 │
│                                                                      │
│  4. GOVERNANÇA                                                       │
│     □ Inventário de ativos atualizado em tempo real                 │
│     □ Métricas de segurança reportadas ao Board                     │
│     □ Auditorias de segurança independentes                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 11. Referências

### Fontes Utilizadas

- [Wikipedia - 2017 Equifax Data Breach](https://en.wikipedia.org/wiki/2017_Equifax_data_breach)
- [U.S. Senate Report - How Equifax Neglected Cybersecurity](https://www.hsgac.senate.gov/subcommittees/investigations/library/files/majority-and-minority-staff-report_-how-equifax-neglected-cybersecurity-and-suffered-a-devestating-data-breach/)
- [NIST National Vulnerability Database - CVE-2017-5638](https://nvd.nist.gov/vuln/detail/CVE-2017-5638)
- [CSO Online - Equifax Data Breach FAQ](https://www.csoonline.com/article/567833/equifax-data-breach-faq-what-happened-who-was-affected-what-was-the-impact.html)
- [Framework Security - The Equifax Hack](https://frameworksecurity.com/post/the-equifax-hack-a-cybersecurity-catastrophe)

### Frameworks de Referência
- NIST SP 800-30: Guide for Conducting Risk Assessments
- NIST Cybersecurity Framework 2.0
- ISO/IEC 27005: Information Security Risk Management

---

## 12. Aprovações (Documento Exemplo)

| Papel | Nome | Assinatura | Data |
|-------|------|------------|------|
| Avaliador | Security Analyst | [Exemplo] | Mar 2017 |
| Revisor Técnico | Tech Lead | [Exemplo] | Mar 2017 |
| CISO | Chief Information Security Officer | [Exemplo] | Mar 2017 |
| Proprietário do Risco | CIO | [Exemplo] | Mar 2017 |

---

*Exemplo educacional baseado no caso Equifax 2017 - MBA Cibersegurança & IA*
*Este documento demonstra como uma avaliação de riscos poderia ter identificado e prevenido o incidente.*
