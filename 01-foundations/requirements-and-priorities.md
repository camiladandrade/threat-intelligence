# Requisitos e Prioridades de Inteligência — PIRs (Template + Guia)

Este documento define como criar e manter **PIRs (Priority Intelligence Requirements)** — Requisitos Prioritários de Inteligência — para garantir que Threat Intelligence entregue **valor para o negócio** e gere ações (patching, detecções, hardening e decisões).

> Objetivo: evitar TI “solta”, baseada só em notícias, e focar no que reduz risco de verdade.

---

## 1) O que são PIRs (e por que importam)

**PIRs** são perguntas prioritárias que a organização precisa responder sobre ameaças para:
- proteger ativos e processos críticos
- orientar coleta e análise
- direcionar detecções e controles
- suportar decisões de liderança

Um PIR bem escrito é:
- específico (não genérico)
- mensurável/observável (o que prova a resposta?)
- ligado a um ativo/processo crítico
- com owner e cadência de revisão

---

## 2) Como criar PIRs (passo a passo)

### Passo 1 — Entender o contexto do negócio
- quais são os processos/serviços Tier-0/Tier-1 (do BIA)
- quais são os dados críticos (PII, IP, financeiro, credenciais)
- quais fornecedores e integrações são essenciais
- quais mudanças relevantes ocorrerão (migração cloud, novos sistemas)

### Passo 2 — Mapear riscos e ameaças prováveis
- top riscos do Risk Register
- histórico de incidentes (IR)
- vulnerabilidades recorrentes (VM)
- exposição pública (serviços/tecnologias)

### Passo 3 — Priorizar por impacto e urgência
- impacto potencial (financeiro, operação, compliance, reputação)
- probabilidade (setor alvo, tecnologia exposta, histórico)
- “janela de risco” (campanhas ativas, CVEs recentes)

### Passo 4 — Definir entregas e consumidores
- quem precisa da resposta (exec, TI, SOC/IR, GRC)
- que tipo de produto (brief, alerta, caso de uso de detecção)
- qual cadência (semanal, mensal, sob demanda)

---

## 3) Template de PIR (modelo para copiar)

> Dica: mantenha PIRs em tabela para facilitar revisão e priorização.

| ID | PIR (pergunta) | Por que importa (impacto) | Escopo (ativos/processos) | Consumidor | Produto (formato) | Cadência | Fontes principais | Critério de sucesso | Status |
|---|---|---|---|---|---|---|---|---|---|
| PIR-001 |  |  |  |  |  |  |  |  |  |

---

## 4) Exemplos de PIRs (corporativo)

### PIR-001 — Ransomware (impacto operacional)
**Pergunta (PIR):**  
Quais grupos/campanhas de ransomware estão ativos no nosso setor e quais vetores iniciais estão sendo mais utilizados?

- **Por que importa:** indisponibilidade de operações, impacto financeiro e reputacional
- **Escopo:** ativos críticos, acessos remotos, backups/DR
- **Consumidor:** Liderança + TI + IR
- **Produto:** Threat Brief executivo + recomendações técnicas
- **Cadência:** quinzenal/mensal (e alertas quando necessário)
- **Critério de sucesso:** ações de hardening/backup priorizadas + detecções ajustadas

---

### PIR-002 — Vulnerabilidades exploradas (patching orientado a risco)
**Pergunta (PIR):**  
Quais CVEs relevantes para nossa tecnologia/stack estão sendo exploradas ativamente e qual a prioridade de correção?

- **Consumidor:** VM + TI + GRC
- **Produto:** alerta técnico + ticket de correção priorizado
- **Cadência:** semanal e sob demanda
- **Critério de sucesso:** redução de exposição e correções dentro do SLA

---

### PIR-003 — Credenciais e acesso inicial
**Pergunta (PIR):**  
Quais tendências de acesso inicial (phishing, infostealers, MFA fatigue, abuso de OAuth) aumentam risco para nossa organização?

- **Consumidor:** SOC/IR + IAM + liderança
- **Produto:** resumo + recomendações (MFA, políticas, detecções)
- **Cadência:** mensal
- **Critério de sucesso:** melhorias em controles e queda de eventos correlatos

---

### PIR-004 — Terceiros e cadeia de suprimentos
**Pergunta (PIR):**  
Quais fornecedores/terceiros críticos (ou classes de fornecedores) estão sob risco elevado e quais sinais devemos monitorar?

- **Consumidor:** GRC + Compras + TI + liderança
- **Produto:** briefing + plano de monitoramento + requisitos contratuais (quando aplicável)
- **Cadência:** mensal/trimestral
- **Critério de sucesso:** mitigação preventiva e melhoria de governança de terceiros

---

### PIR-005 — Dados sensíveis e LGPD
**Pergunta (PIR):**  
Quais ameaças e técnicas recentes aumentam risco de vazamento de dados pessoais e quais controles priorizar?

- **Consumidor:** GRC/Privacidade + TI + Segurança
- **Produto:** threat brief + recomendações de controle (DLP, classificação, access reviews)
- **Cadência:** mensal
- **Critério de sucesso:** melhoria de controles e evidências para auditoria

---

## 5) Priorização (modelo simples)

> Use uma pontuação para priorizar sem debate infinito.

**Pontuação sugerida (1–5):**
- Impacto no negócio
- Probabilidade/atividade no setor
- Exposição interna (o quanto “temos isso”)
- Urgência (janela de risco)

**Prioridade final:** soma (máx. 20) ou categorias:
- 16–20: Prioridade 1 (crítico)
- 11–15: Prioridade 2 (alto)
- 6–10: Prioridade 3 (médio)
- 0–5: Prioridade 4 (baixo)

---

## 6) Cadência de revisão dos PIRs

Recomendação:
- Revisão mensal (rápida) — ajustar prioridades e status
- Revisão trimestral (profunda) — alinhar com roadmap e riscos

Gatilhos para revisão imediata:
- incidente relevante
- mudança grande (cloud, fornecedor, produto)
- nova campanha/CVE crítica para stack
- auditoria/compliance exigindo foco

---

## 7) Métricas de eficácia (TI)

Sugestões:
- % de PIRs com entregas no prazo
- nº de ações geradas (tickets) por PIR
- tempo para transformar alerta em ação (lead time)
- feedback de SOC/TI (utilidade: baixa/média/alta)
- redução de exposição (ex.: CVEs exploradas corrigidas no SLA)

---

## 8) Conexões com este repositório

- Ciclo de inteligência: `01-foundations/intelligence-cycle.md`
- Templates de entrega: `02-templates/`
- Coleta e fontes: `03-collection-and-sources/`
- Integração com detecção: `05-detection-and-response/`

---
