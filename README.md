# Threat Intelligence (TI) — Playbook & Templates

Repositório com **frameworks, templates e fluxos** de Threat Intelligence (TI) voltados para **ambiente corporativo**, conectando **contexto de negócio, detecção e resposta a incidentes**.

> Objetivo: demonstrar uma abordagem prática e estruturada de TI — do ciclo de inteligência até a entrega de briefings e o uso operacional de IOCs.

---

## 🎯 O que você encontra aqui

- Fundamentos do **Ciclo de Inteligência**
- Definição de **Requisitos de Inteligência (PIRs)** e prioridades
- Templates para:
  - **Threat Brief executivo** (1 página)
  - **Resumo semanal de TI**
  - **Relatório de campanha**
  - **Intake/triagem de IOCs**
- Plano de coleta e validação de fontes
- Frameworks de análise (ATT&CK, Diamond, Kill Chain) e boas práticas
- Fluxo TI → Detecções → Feedback de IR/SOC
- Estudos de caso fictícios (quando aplicável)

---

## 🗂️ Estrutura do repositório (mapa)

- **`01-foundations/`**  
  Fundamentos, ciclo de inteligência, PIRs e taxonomia.

- **`02-templates/`**  
  Templates prontos (executivo e operacional).

- **`03-collection-and-sources/`**  
  Plano de coleta, fontes e triagem/validação.

- **`04-analysis/`**  
  Frameworks e guidelines (inclusive cuidado com atribuição).

- **`05-detection-and-response/`**  
  Ciclo de vida de IOC, integração com detecções e feedback loop com IR/SOC.

- **`06-case-studies/`**  
  Estudos fictícios (sem dados sensíveis), com estrutura para futuros exemplos.

---

## ✅ Como usar (fluxo recomendado)

1) **Fundação**
- `01-foundations/intelligence-cycle.md`
- `01-foundations/requirements-and-priorities.md`
- `01-foundations/taxonomy-and-tags.md`

2) **Entrega rápida (para liderança)**
- `02-templates/threat-brief-template.md`
- `02-templates/weekly-ti-summary-template.md`

3) **Operacional (para SOC/IR)**
- `02-templates/ioc-intake-template.md`
- `05-detection-and-response/ioc-handling-and-lifecycle.md`
- `05-detection-and-response/ti-to-detections-workflow.md`
- `05-detection-and-response/feedback-loop.md`

4) **Análise aprofundada**
- `02-templates/campaign-report-template.md`
- `04-analysis/analytic-frameworks.md`
- `04-analysis/attribution-guidelines.md`

---

## 🔒 Boas práticas (e limites)

- Não incluir credenciais, dados de produção, PII ou detalhes sensíveis.
- IOCs e exemplos devem ser **fictícios/sanitizados** quando necessário.
- Atribuição é tratada com cautela: priorizar **confiança e evidência**.

---

## 👩‍💻 Autora

**Camila Andrade**  
Líder em Segurança da Informação | GRC • Gestão de Vulnerabilidades • IR • Threat Intelligence  
🔗 [LinkedIn](https://www.linkedin.com/in/camiladandrade/) | 🌐 [Site Pessoal](https://camiladandrade.com/)
