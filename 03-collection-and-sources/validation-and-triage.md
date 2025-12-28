# Validação e Triagem — Threat Intelligence (Qualidade e Operação)

Este documento define como realizar **triagem e validação** de informações/indicadores antes de:
- publicar entregas (briefs e relatórios)
- criar tickets de ação (patch/hardening)
- aplicar IOCs em bloqueios e detecções

> Objetivo: reduzir ruído e falsos positivos, garantindo que TI gere ações seguras e eficazes.

---

## 1) Princípios

- **Foco em valor:** tudo deve responder um PIR, risco relevante ou necessidade real.
- **Contexto acima de volume:** IOC sem contexto é “dado”, não inteligência.
- **Rastreabilidade:** sempre registrar fonte, data e por que foi considerado relevante.
- **Segurança operacional:** evitar ações que gerem indisponibilidade por bloqueios incorretos.
- **Confiança explícita:** dizer claramente o que é confirmado vs hipótese.

---

## 2) Triagem (decisão rápida)

### 2.1 Perguntas rápidas (gate)
Antes de virar trabalho:
1. Isso se conecta a um **PIR** ou risco relevante?
2. Afeta nossa **stack/tecnologias** ou ativos críticos?
3. Há **exploração ativa** ou sinais de campanha em andamento?
4. Existe **ação recomendada** clara (patch/detect/hardening)?

Se “não” para a maioria → **monitorar** ou **descartar**.

### 2.2 Classificação do item (resultado)
- **Alerta imediato (P1):** ação em 0–7 dias (alto impacto/urgência)
- **Análise (P2):** exige correlação e validação (7–30 dias)
- **Monitoramento (P3):** acompanhar evolução sem ação agora
- **Descartado:** ruído, baixa relevância ou baixa qualidade

---

## 3) Validação de fontes (confiabilidade)

### 3.1 Critérios para avaliar uma fonte
- reputação e histórico de acerto
- transparência sobre metodologia e evidência
- atualização e recência
- possibilidade de corroborar com outras fontes
- nível de detalhe (TTPs/contexto vs afirmações vagas)

### 3.2 Confiança (padrão)
- **Alta:** múltiplas fontes confiáveis + validação interna quando possível
- **Média:** boa evidência, mas incompleta ou sem validação interna
- **Baixa:** fonte única, conteúdo superficial ou não verificável

> Boas práticas: registrar “por que” a confiança é média/baixa.

---

## 4) Validação de indicadores (IOCs) — qualidade antes de operar

### 4.1 Checklist mínimo (obrigatório)
- [ ] formato válido (IP/domínio/hash/URL)
- [ ] data de observação conhecida (recência)
- [ ] contexto (representa o quê? C2/phishing/payload?)
- [ ] fonte registrada (link/relatório)
- [ ] risco de falso positivo avaliado

### 4.2 Regras de ouro (para evitar desastre)
- **Não bloquear** IP/domínio sem contexto (muito risco de falso positivo)
- Evitar bloqueio de:
  - CDNs, provedores grandes e serviços compartilhados (sem validação forte)
  - domínios genéricos / encurtadores (sem política específica)
- Preferir ações:
  - **Detectar** e correlacionar antes de bloquear, quando houver risco
  - **Monitorar** quando o contexto for limitado
- Sempre definir:
  - **prazo de expiração**
  - **status** (novo/validado/implantado/expirado/revogado)

### 4.3 Quando bloquear (critérios)
Bloqueio é recomendado quando:
- confiança alta
- impacto do falso positivo é aceitável
- há evidência clara de malícia
- existe plano de rollback (se der problema)

---

## 5) Normalização e enriquecimento (quando vale a pena)

> Só enriquecer quando isso melhora decisão.

Exemplos de enriquecimento útil:
- relacionar IOC com campanha/ameaça
- mapear TTPs (ATT&CK)
- identificar tecnologia afetada (stack)
- identificar janela de validade (ativa vs antiga)

---

## 6) Como transformar em ação (operacionalização)

### 6.1 Tipos de saída (o que gerar)
- **Ticket de patch/mitigação** (VM/TI)
- **Ajuste de detecção** (SIEM/EDR)
- **Hardening/configuração** (IAM, e-mail, rede)
- **Threat Brief** (quando impacta liderança)
- **Atualização de playbook** (IR)

### 6.2 Rastreabilidade mínima (para auditoria e lições)
Para qualquer ação:
- PIR relacionado
- fonte(s) + confiança
- decisão (bloquear/detectar/monitorar/patch)
- ticket/change ID
- owner e prazo
- evidência/resultado (feedback loop)

---

## 7) Tratamento de falsos positivos

### 7.1 Sinais de falso positivo
- picos de bloqueio em serviços legítimos
- impacto em produtividade/sistemas
- IOC “amplo” (shared hosting, CDN, IP rotativo)
- ausência de contexto/campanha

### 7.2 Ações recomendadas
- rebaixar de **bloquear** para **detectar/monitorar**
- ajustar escopo (ex.: aplicar só em segmento/ambiente)
- adicionar exceções controladas (com prazo)
- registrar lição aprendida para melhorar intake/validação

---

## 8) Ciclo de vida (expiração e manutenção)

Regras sugeridas:
- todo IOC deve ter **data de expiração**
- revisar IOCs implantados em cadência (semanal/mensal)
- expirar ou revogar IOCs antigos para reduzir ruído
- registrar “por que” expirou/revogou

---

## 9) Modelos rápidos (para uso no dia a dia)

### 9.1 Mini-template de triagem (1 minuto)
- Item: ______________________
- PIR relacionado: ____________
- Relevância p/ nossa stack: baixa/média/alta
- Exploração ativa: sim/não/indefinido
- Ação: alerta/análise/monitorar/descartar
- Confiança: baixa/média/alta
- Próximo passo: ______________________

### 9.2 Mini-template de validação de IOC
- IOC: ________________________
- Tipo: _______________________
- Contexto: ____________________
- Fonte/data: _________________
- FP risk: baixo/médio/alto
- Ação: bloquear/detectar/monitorar
- Expiração: ____/____/____

---

## 10) Conexões com o repositório

- Plano de Coleta: `03-collection-and-sources/collection-plan.md`
- Taxonomia e Tags: `01-foundations/taxonomy-and-tags.md`
- IOC Intake: `02-templates/ioc-intake-template.md`
- Fluxo IOC (futuro): `05-detection-and-response/ioc-handling-and-lifecycle.md`

---
