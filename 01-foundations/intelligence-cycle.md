# Ciclo de Inteligência — Threat Intelligence (Fundamentos)

Este documento define o **Ciclo de Inteligência** aplicado a Threat Intelligence (TI) em contexto corporativo, conectando **necessidades do negócio**, coleta, análise e entrega acionável para Segurança/TI/Liderança.

> Objetivo: transformar “informação” em **inteligência acionável** (decisões, prioridades e controles).

---

## 1) O que é Threat Intelligence (TI)

Threat Intelligence é o processo de coletar, analisar e disseminar informações sobre ameaças para:
- reduzir risco
- antecipar movimentos de atacantes
- priorizar ações (patching, detecções, hardening)
- apoiar resposta a incidentes e decisões executivas

**Inteligência boa** é:
- relevante (responde a uma necessidade)
- contextualizada (impacto e exposição)
- acionável (gera uma ação clara)
- confiável (fontes e confiança explícitas)

---

## 2) Etapas do Ciclo de Inteligência

### 2.1 Planejamento e Direcionamento
Definir **o que precisamos saber** e **por quê**.
- Requisitos de inteligência (PIRs)
- prioridades por risco e contexto do negócio
- escopo, cadência e stakeholders
- critérios de qualidade (o que é “bom o suficiente”)

**Saídas típicas:**
- lista de PIRs (prioridades)
- plano de coleta
- formato de entrega (brief executivo, resumo semanal, alerta)

---

### 2.2 Coleta
Coletar dados relevantes para responder os PIRs:
- fontes internas (IR, SOC, SIEM, VM, tickets, logs, EDR)
- fontes externas (OSINT, advisories, reports, feeds)

**Boas práticas:**
- coletar com foco (evitar “volume por volume”)
- registrar fonte e data
- manter rastreabilidade (o que veio de onde)

**Saídas típicas:**
- dados brutos (indicadores, relatórios, alertas)
- sinalizações iniciais para triagem

---

### 2.3 Processamento (Preparação)
Organizar e preparar dados para análise:
- normalização (formatos)
- deduplicação (remover repetidos)
- enriquecimento (contexto: reputação, histórico, geolocalização — quando aplicável)
- classificação (TLP, tags, categorias)

**Saídas típicas:**
- dataset “limpo” (pronto para análise)
- lista de itens priorizados para investigação

---

### 2.4 Análise e Produção
Transformar dados em inteligência:
- responder PIRs com evidências e nível de confiança
- identificar padrões (técnicas, vetores, alvos)
- avaliar impacto e exposição da organização
- recomendar ações

Frameworks comuns:
- MITRE ATT&CK (técnicas e táticas)
- Cyber Kill Chain
- Diamond Model

**Saídas típicas:**
- threat brief (executivo)
- resumo semanal
- relatório de campanha
- recomendações para detecção e hardening

---

### 2.5 Disseminação (Entrega)
Entregar o produto para o público certo, no formato certo:
- **Executivo:** risco, impacto, decisões, prioridades
- **SOC/IR:** detecções, triagem, IOCs (com contexto)
- **TI/Infra/Produto:** hardening, patching, mudanças

**Boas práticas:**
- objetivo e ação no topo
- linguagem adequada ao público
- rastreabilidade (o que suportou a conclusão)
- nível de urgência explícito

**Saídas típicas:**
- briefings e alertas
- tickets de ação (patch, regras, bloqueios)
- documentação para auditoria (evidências)

---

### 2.6 Feedback e Melhoria Contínua
Coletar retorno:
- o produto ajudou a tomar decisão?
- foi acionável?
- quais sinais foram úteis (ou ruído)?
- quais PIRs mudaram?

O feedback vira:
- ajuste de PIRs
- ajuste de fontes e coleta
- melhoria do formato e cadência

**Saídas típicas:**
- métricas de TI (uso, eficácia)
- backlog de melhorias
- refinamento de prioridades

---

## 3) Papéis (visão simples)

- **Liderança/Negócio:** define prioridades e tolerância a risco
- **TI/Infra/SRE:** implementa mudanças, patches e hardening
- **SOC/IR:** consome TI para detecção e resposta; devolve feedback
- **Threat Intel:** coordena ciclo, produz entregas e integra áreas
- **GRC:** conecta TI a risco, auditoria e evidências

---

## 4) Produtos de TI (exemplos)

- **Threat Brief (executivo)**
- **Resumo semanal**
- **Alerta de ameaça emergente**
- **Relatório de campanha**
- **Pacote de IOCs com contexto**
- **Recomendações de detecção (casos de uso)**
- **Recomendações de hardening e patching**

---

## 5) Critérios de qualidade (check rápido)

Uma entrega de TI deve responder “sim” a:
- [ ] atende um PIR ou necessidade real?
- [ ] tem contexto (quem/como/por quê)?
- [ ] tem ação recomendada clara?
- [ ] deixa explícita a confiança e limitações?
- [ ] tem público e cadência adequados?

---

## 6) Conexão com este repositório

- PIRs e prioridades: `01-foundations/requirements-and-priorities.md`
- Templates de entrega: `02-templates/`
- Plano de coleta e validação: `03-collection-and-sources/`
- Frameworks de análise: `04-analysis/`
- Integração com detecção e IR: `05-detection-and-response/`

---
