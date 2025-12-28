# Plano de Coleta — Threat Intelligence (Collection Plan)

Este documento define como a área de TI (Threat Intelligence) realiza **coleta focada**, conectada aos **PIRs** (Requisitos Prioritários de Inteligência), para evitar excesso de ruído e maximizar entregas acionáveis.

> Objetivo: garantir que a coleta responda perguntas prioritárias e alimente decisões (patching, detecção, hardening, governança).

---

## 1) Escopo e premissas

- **Escopo do programa de TI:** (unidade/ambiente) ______________________
- **Públicos atendidos:** Liderança / GRC / TI / SOC / IR
- **Cadência padrão:** semanal (resumo) + sob demanda (alertas)
- **Restrições:** sem dados sensíveis; seguir TLP e políticas internas.

---

## 2) Entradas do plano (de onde vem a prioridade)

A coleta deve partir de:
- PIRs e prioridades (`01-foundations/requirements-and-priorities.md`)
- top riscos do Risk Register (GRC)
- histórico de incidentes (IR)
- exposição/vulnerabilidades relevantes (VM)
- mudanças relevantes (cloud, fornecedores, novos sistemas)

---

## 3) Mapa PIR → Coleta (tabela principal)

> Mantenha essa tabela viva. Ela é o “coração” do plano.

| PIR | Pergunta (resumo) | O que coletar | Fontes internas | Fontes externas | Cadência | Owner | Saída esperada |
|---|---|---|---|---|---|---|---|
| PIR-001 |  |  |  |  |  |  |  |
| PIR-002 |  |  |  |  |  |  |  |

---

## 4) Fontes internas (exemplos)

> Ajuste conforme sua realidade. O foco aqui é mostrar o raciocínio.

- **SOC/SIEM:** alertas, correlação, tendências, top regras acionadas
- **EDR/XDR:** detecções, artefatos, comportamentos e IOCs internos
- **IR:** incidentes, PIRs, lições aprendidas e lacunas
- **VM:** CVEs relevantes, exposição, SLA, backlog por criticidade
- **IAM/Logs:** padrões anômalos (login, MFA, tokens), acessos privilegiados
- **TI/Infra:** mudanças recentes, falhas recorrentes, disponibilidade

**Boas práticas:**
- ter canal/rotina de ingestão (semanal) com SOC/IR/VM
- padronizar “intake” (quando vira alerta vs quando vira análise)

---

## 5) Fontes externas (exemplos)

> Evite “lista infinita”. Priorize fontes com consistência e reputação.

- **Advisories e comunicados oficiais** (vendors, CERTs)
- **Relatórios de pesquisa** (ameaças por setor/stack)
- **Feeds de indicadores** (quando aplicável e com validação)
- **OSINT** (repositórios públicos, posts técnicos, etc.)

**Boas práticas:**
- registrar fonte, data e TLP
- validar antes de operacionalizar IOCs
- preferir contexto e TTPs a IOCs “soltos”

---

## 6) Triagem (o que entra vs o que vira ruído)

### 6.1 Critérios de triagem (filtros)
Um item deve virar trabalho de TI se:
- está ligado a um PIR ou risco relevante
- tem relação com nossa stack/tecnologias
- indica exploração ativa ou tendência crescente
- traz recomendação acionável (patch/hardening/detecção)

### 6.2 Classificação rápida (resultado)
- **Alerta imediato:** ação urgente (0–7 dias)
- **Análise:** requer correlação e contexto (7–30 dias)
- **Monitoramento:** acompanhar evolução
- **Descartado:** ruído / baixa relevância

---

## 7) Operacionalização (como a coleta vira ação)

### 7.1 Ações típicas geradas
- ticket de patch/mitigação (VM/TI)
- ajuste de configuração (hardening)
- criação/ajuste de regra de detecção (SOC/SIEM/EDR)
- atualização de playbooks (IR)
- briefing executivo (liderança)

### 7.2 Padrão de rastreabilidade
Para cada item operacionalizado, registrar:
- PIR relacionado
- fonte(s) e confiança
- ação recomendada
- ticket/change ID
- owner e prazo
- evidência/resultado (feedback loop)

---

## 8) Qualidade e métricas do plano de coleta

Sugestões de indicadores:
- % de entregas no prazo por PIR
- nº de ações geradas por semana/mês (tickets)
- tempo médio de “sinal → ação” (lead time)
- taxa de falsos positivos (IOCs/regras)
- utilidade percebida (feedback SOC/TI: baixa/média/alta)

---

## 9) Cadência de revisão do plano

- Revisão rápida: semanal (o que entrou, o que virou ação)
- Revisão formal: mensal (prioridades/PIRs e eficácia)
- Revisão profunda: trimestral (alinhamento com riscos e roadmap)

Gatilhos para revisão imediata:
- incidente relevante
- CVE crítica na stack
- mudança grande (cloud/fornecedor)
- aumento de ruído ou falsos positivos

---

## 10) Conexões com este repositório

- PIRs: `01-foundations/requirements-and-priorities.md`
- Taxonomia e tags: `01-foundations/taxonomy-and-tags.md`
- Weekly Summary: `02-templates/weekly-ti-summary-template.md`
- Threat Brief: `02-templates/threat-brief-template.md`
- IOC Intake: `02-templates/ioc-intake-template.md`

---
