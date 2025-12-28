# Fluxo TI → Detecções — Do insight à operação (com feedback)

Este documento descreve como transformar Threat Intelligence (TI) em **detecções acionáveis** (SIEM/EDR/XDR/WAF/Email/DNS) e como manter um **feedback loop** com SOC/IR para melhorar qualidade e reduzir falsos positivos.

> Objetivo: garantir que TI gere impacto prático (detectar mais cedo, responder melhor, reduzir risco).

---

## 1) Visão geral do fluxo

1. **Entrada (TI):** sinal/relatório/IOC/TTP ligado a PIR
2. **Triagem:** relevância + confiança + exposição interna
3. **Produção:** hipótese de detecção + recomendação (o que procurar)
4. **Implementação:** regra/caso de uso + tuning
5. **Validação:** teste em amostras e verificação de ruído
6. **Operação:** monitoramento em produção
7. **Feedback:** utilidade e ajustes (encerrar/ajustar/expandir)

---

## 2) Entradas típicas (o que inicia o processo)

- CVE explorada ativamente e aplicável à nossa stack
- TTPs recorrentes observadas no setor
- Indicadores (IOCs) com contexto suficiente
- Mudança de comportamento de ameaças (ex.: novo vetor de acesso inicial)
- Insights pós-incidente (PIR / lições aprendidas)

---

## 3) Triagem (decisão rápida)

### 3.1 Checklist de triagem
- [ ] Está ligado a um PIR/risco relevante?
- [ ] Afeta nossa stack/ativos críticos?
- [ ] Confiança é suficiente? (baixa/média/alta)
- [ ] Há hipótese clara do que detectar?
- [ ] O custo de ruído é aceitável?

**Saída da triagem:**
- **Criar/ajustar detecção** (prioridade P1/P2/P3)
- **Monitorar** (sem detecção agora)
- **Descartar** (ruído)

---

## 4) Hipóteses de detecção (como TI traduz para SOC)

TI deve propor **hipóteses testáveis**, não só “um IOC”.

### 4.1 Modelo de hipótese
- **Hipótese:** “Se X ocorrer, pode indicar Y.”
- **O que procurar:** eventos/artefatos/telemetria
- **Onde procurar:** fonte de log/controle (SIEM/EDR/WAF/DNS)
- **Janela de tempo:** minutos/horas/dias
- **Critério de alerta:** combinação e limiar
- **Risco de falso positivo:** baixo/médio/alto
- **Ação de resposta:** triagem/runbook

### 4.2 Exemplos (genéricos)
- “Múltiplas falhas de login + sucesso posterior em conta privilegiada”
- “Execução de binário incomum + conexão externa para domínio recém-criado”
- “Download de payload por script + persistência criada”

> Em conteúdo público, mantenha exemplos **abstratos** e sem detalhes sensíveis.

---

## 5) Artefatos gerados (o que TI entrega para implementação)

Para cada detecção/caso de uso, TI deve entregar:
- **título do caso de uso**
- **descrição e motivação**
- **mapeamento ATT&CK** (quando aplicável)
- **fontes de log necessárias**
- **pseudológica da regra** (alto nível)
- **limitações conhecidas**
- **recomendação de severidade**
- **ações de triagem/resposta**
- **critério de sucesso** (como medir utilidade)

---

## 6) Implementação (onde colocar e como)

### 6.1 Onde implementar (exemplos)
- **SIEM:** correlação multi-fonte e contexto
- **EDR/XDR:** comportamento de endpoint
- **WAF:** padrões de exploração web
- **DNS/Proxy:** domínios suspeitos, categorias
- **Email Security:** remetente, URLs, padrões de phishing
- **Cloud logs:** IAM, tokens, APIs

### 6.2 Versionamento e rastreabilidade
Registrar:
- ID do caso de uso (ex.: DET-001)
- PIR relacionado
- ticket/change ID
- owner (SOC/Engenharia/SecOps)
- data de implantação
- revisões e tuning

---

## 7) Tuning e redução de falsos positivos

### 7.1 Estratégias comuns
- segmentar por ambiente (prod vs dev)
- adicionar contexto (ex.: “somente contas privilegiadas”)
- combinar sinais (em vez de evento único)
- ajustar limiares e janelas
- criar listas de allow/deny controladas

### 7.2 Regras de ouro
- comece com **detecção** antes de **bloqueio** quando FP for risco
- documente exceções (quem, por que, por quanto tempo)
- mantenha evidência do tuning (para auditoria e melhoria)

---

## 8) Validação (antes e depois de produção)

### 8.1 Testes recomendados
- testar em logs históricos (se possível)
- teste controlado (ambiente isolado)
- simulação/tabletop (quando aplicável)

### 8.2 Critérios de sucesso
- taxa de falsos positivos aceitável
- detecção com contexto suficiente para triagem
- tempo de resposta reduzido (quando aplicável)

---

## 9) Feedback loop (SOC/IR → TI)

### 9.1 O que o SOC/IR deve devolver
- utilidade: baixa/média/alta
- FP: motivo e padrão (o que gerou ruído)
- gaps: logs faltando, cobertura limitada
- sugestões: contexto extra e melhorias

### 9.2 Cadência recomendada
- revisão rápida semanal (15–30 min) TI + SOC
- revisão mensal (mais profunda) com backlog de melhorias

---

## 10) Tabela de controle (modelo)

| ID | Caso de uso | PIR | Fonte(s) | Severidade | Status | FP (baixo/médio/alto) | Owner | Última revisão | Observações |
|---|---|---|---|---|---|---|---|---|---|
| DET-001 |  |  |  |  | Em teste / Em produção / Desativado |  |  |  |  |

---

## 11) Conexões com o repositório

- PIRs: `01-foundations/requirements-and-priorities.md`
- Validação e triagem: `03-collection-and-sources/validation-and-triage.md`
- IOC Intake: `02-templates/ioc-intake-template.md`
- Frameworks ATT&CK: `04-analysis/analytic-frameworks.md`

---
