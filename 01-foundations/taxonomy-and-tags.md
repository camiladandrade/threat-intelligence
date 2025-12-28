# Taxonomia e Tags — Threat Intelligence (Padronização)

Este documento define uma taxonomia simples para padronizar:
- classificação de informações (TLP)
- tipo de ameaça e severidade
- status e ciclo de vida de IOCs
- tags para organização e busca

> Objetivo: consistência entre entregas (briefs, relatórios, IOCs) e facilidade de operação (SOC/IR/TI/GRC).

---

## 1) TLP (Traffic Light Protocol)

Usar TLP para orientar **com quem** e **como** compartilhar informações.

- **TLP:BRANCO (WHITE)**  
  Pode ser compartilhado publicamente.  
  Ex.: recomendações genéricas, conteúdos públicos.

- **TLP:VERDE (GREEN)**  
  Compartilhamento com comunidade/grupos confiáveis, sem divulgação pública ampla.  
  Ex.: informação útil para times e parceiros próximos.

- **TLP:ÂMBAR (AMBER)**  
  Compartilhamento restrito a pessoas/áreas que “precisam saber”.  
  Ex.: detalhes operacionais e IOCs internos.

- **TLP:VERMELHO (RED)**  
  Compartilhamento extremamente restrito (pessoas específicas).  
  Ex.: informações sensíveis durante incidente ativo.

> Regra prática: se tiver dúvida, classificar como **TLP:ÂMBAR**.

---

## 2) Classificação do tipo de ameaça (categorias)

Use uma ou mais categorias:

- **Ransomware**
- **Phishing / BEC (fraude corporativa)**
- **Malware / InfoStealer**
- **Exploração de vulnerabilidades (CVE)**
- **Acesso inicial / credenciais**
- **Ataque a terceiros / cadeia de suprimentos**
- **DDoS / indisponibilidade**
- **Exfiltração / vazamento de dados**
- **Insider**
- **Cloud / IAM / abuso de OAuth**
- **Outros:** ______________________

---

## 3) Severidade (orientada a negócio)

A severidade deve refletir risco para o negócio (não só “barulho técnico”).

### 3.1 Níveis
- **Crítica:** impacto alto + probabilidade alta / campanha ativa / exploração confirmada em nossa stack
- **Alta:** impacto alto ou probabilidade alta; exige ação priorizada
- **Média:** relevante, mas sem urgência imediata; tratar em cadência
- **Baixa:** informativa; monitorar

### 3.2 Critérios (sugestão de decisão rápida)
Considere:
- campanha ativa no setor?
- exploração confirmada (in-the-wild)?
- nossa tecnologia/stack exposta?
- ativo/processo Tier-0/Tier-1 afetado?
- impacto LGPD/compliance possível?
- mitigação existe e é simples (patch/config)?

---

## 4) Nível de confiança (confiança analítica)

Indique confiança na conclusão:
- **Alta:** múltiplas fontes confiáveis / evidência forte / validação interna
- **Média:** evidência razoável, mas incompleta ou com suposições
- **Baixa:** informação preliminar / fonte única / sem validação

> Sempre explicar “por que” (1 linha) quando a confiança não for alta.

---

## 5) Status do IOC (ciclo de vida)

Padronize o estado de cada IOC (indicador):

- **Novo:** recebido e ainda não triado
- **Em triagem:** sendo validado (qualidade, contexto, falsos positivos)
- **Validado:** considerado relevante e pronto para uso (detecção/bloqueio)
- **Implantado:** aplicado em controles (SIEM, EDR, proxy, firewall, e-mail)
- **Monitorado:** em observação (alto risco de FP, uso seletivo)
- **Expirado:** não é mais relevante (janela de campanha encerrou)
- **Revogado:** inválido/incorreto (ou gerava FP crítico)

Campos recomendados para IOC:
- tipo (IP/domínio/hash/URL/email sender)
- data de coleta e expiração
- fonte
- confiança
- contexto (ameaça/campanha)
- ação recomendada (bloquear/detectar/monitorar)

---

## 6) Tipos de IOC (padronização)

- **IP**
- **Domínio**
- **URL**
- **Hash** (MD5/SHA1/SHA256)
- **Email/Remetente**
- **Arquivo/Nome**
- **User-Agent**
- **Certificado (fingerprint)** (quando aplicável)

> Boas práticas:
- evitar bloquear IPs/CDNs sem validação (alto risco de falso positivo)
- sempre que possível, preferir indicadores mais específicos (hash, path, assinatura)

---

## 7) Tags (padrão de rotulagem)

Use tags para busca e organização. Sugestão de grupos:

### 7.1 Tags por tema
- `ransomware`, `phishing`, `infostealer`, `cve`, `iam`, `cloud`, `supply-chain`, `data-exfil`

### 7.2 Tags por tecnologia/stack
- `windows`, `linux`, `m365`, `azure`, `aws`, `google-workspace`
- `vpn`, `rdp`, `citrix`, `okta`, `ad`, `entra-id`
- `nginx`, `apache`, `k8s`, `docker`

### 7.3 Tags por ação recomendada
- `patch-now`, `hardening`, `block`, `detect`, `monitor`, `user-awareness`

### 7.4 Tags por público
- `exec`, `ti`, `soc`, `ir`, `grc`, `privacy`

### 7.5 Tags por fase (exemplo)
- `planning`, `collection`, `analysis`, `dissemination`, `feedback`

---

## 8) Padrão de título para entregas (recomendado)

### 8.1 Threat Brief
`[TLP:ÂMBAR] [Severidade] Tema — Impacto principal (Data)`

Ex.:  
`[TLP:ÂMBAR] [Alta] Exploração de CVE em VPN — Risco de acesso inicial (2026-01-10)`

### 8.2 Resumo semanal
`[TLP:VERDE] Weekly TI Summary — Semana XX (AAAA-MM-DD)`

---

## 9) Conexão com os templates

- Threat Brief: `02-templates/threat-brief-template.md`
- Intake de IOC (template): `02-templates/ioc-intake-template.md` (quando criado)
- Fluxo IOC: `05-detection-and-response/ioc-handling-and-lifecycle.md` (quando criado)

---
