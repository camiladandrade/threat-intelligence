# Diretrizes de Atribuição — Threat Intelligence (Cautela e Confiança)

Este documento define como tratar **atribuição** (quem está por trás de uma atividade/campanha) de forma responsável, evitando conclusões precipitadas e mantendo consistência analítica.

> Objetivo: reduzir riscos reputacionais e técnicos por atribuição incorreta (“nomear grupo errado”), priorizando o que realmente importa: **TTPs, impacto e ações**.

---

## 1) Princípio central

Atribuição raramente é “certeza absoluta”.  
Em ambiente corporativo, geralmente importa mais:
- **o que a ameaça faz** (TTPs)
- **como entra** (vetores)
- **o que afeta** (ativos e impactos)
- **como mitigar/detectar**

> Use atribuição como contexto, não como “título principal” da entrega (salvo quando houver evidência forte).

---

## 2) Tipos de atribuição (o que você está afirmando)

### 2.1 Atribuição de campanha (cluster)
“Esses eventos parecem fazer parte da mesma campanha por similaridade de TTPs/infra.”

✅ Mais segura e comum.

### 2.2 Atribuição a grupo (nome conhecido)
“Isso se parece com o grupo X.”

⚠️ Arriscada; nomes variam entre fontes e podem confundir.

### 2.3 Atribuição geopolítica/Estado-nação
“Isso é Estado-nação Y.”

❗ Alto risco; exige evidência muito forte e normalmente não é necessário para decisões corporativas.

---

## 3) Níveis de confiança (modelo simples)

- **Alta:** múltiplas evidências fortes e consistentes; consenso entre fontes confiáveis; validação interna quando possível.
- **Média:** evidência razoável, mas com lacunas; alguns elementos podem ser imitáveis.
- **Baixa:** similaridade superficial; dependência de fonte única; alto risco de “false flag”.

> Sempre explicitar o nível de confiança e o porquê quando mencionar atribuição.

---

## 4) Evidências que ajudam (e as que não ajudam)

### 4.1 Evidências mais fortes (melhor sinal)
- infraestrutura correlacionada consistentemente ao longo do tempo (com boa metodologia)
- TTPs específicos e raros combinados (padrões difíceis de “copiar por acaso”)
- evidência técnica detalhada (artefatos, cadeia de execução) com metodologia transparente
- correlação com múltiplas fontes independentes

### 4.2 Evidências fracas (alto risco)
- nomes de grupo citados sem metodologia
- um único IOC isolado (IP/domínio) como “prova”
- similaridade genérica (ex.: “usa phishing”, “usa PowerShell”)
- afirmações de rede social sem validação

---

## 5) Regras práticas (para uso corporativo)

1. **Se não for necessário para ação, não faça atribuição.**
2. Prefira termos como:
   - “campanha”, “cluster”, “atividade”, “ameaça”
3. Se mencionar grupo:
   - use “**associado**”, “**possivelmente ligado**”, “**similar a**”
   - inclua confiança e fontes
4. Nunca baseie atribuição em:
   - um único indicador
   - uma única fonte não-verificada
5. Evite atribuição geopolítica em relatórios públicos/demonstrativos.

---

## 6) Padronização de linguagem (frases prontas)

### 6.1 Para confiança baixa
- “Há indícios limitados sugerindo…”
- “Algumas características são consistentes com…”
- “Atribuição não confirmada; foco nas TTPs e mitigação.”

### 6.2 Para confiança média
- “A atividade é compatível com…”
- “Múltiplos elementos apontam para…”
- “Ainda há lacunas; recomendamos tratar como… (TTPs/impacto).”

### 6.3 Para confiança alta
- “Evidências consistentes e múltiplas fontes indicam…”
- “A atividade está fortemente associada a…”
- “Atribuição feita com confiança alta devido a… (1–2 razões).”

---

## 7) Nomes de grupos (evitar confusão)

Problema: o mesmo grupo pode ter nomes diferentes entre fornecedores/pesquisadores.

Boas práticas:
- se usar nome, cite como “apelido” e mantenha consistência dentro do documento
- quando possível, referenciar como “cluster” interno (ex.: CL-2026-01)
- focar em TTPs e infraestrutura, não em “marca do grupo”

---

## 8) Quando a atribuição é útil (casos em que vale)

- para orientar comunicação com liderança quando houver risco reputacional setorial
- para antecipar TTPs prováveis (quando o perfil do adversário é consistente)
- para contexto em campanhas longas (cluster) e melhoria de detecção

Mesmo nesses casos, a ação recomendada deve ficar independente do nome do grupo.

---

## 9) Checklist de atribuição (antes de publicar)

- [ ] Isso é necessário para decisões/ações?
- [ ] Tenho evidência suficiente (não só “parece”)?
- [ ] Tenho mais de uma fonte confiável?
- [ ] Declarei nível de confiança e limitações?
- [ ] Usei linguagem cuidadosa (sem afirmações absolutas)?
- [ ] O relatório continua útil mesmo sem atribuição?

---

## 10) Conexões com este repositório

- Taxonomia e confiança: `01-foundations/taxonomy-and-tags.md`
- Relatório de Campanha: `02-templates/campaign-report-template.md`
- Frameworks de análise: `04-analysis/analytic-frameworks.md`

---
