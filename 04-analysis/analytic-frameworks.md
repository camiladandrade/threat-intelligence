# Frameworks de Análise — Como aplicar na prática (ATT&CK • Kill Chain • Diamond)

Este documento explica como usar frameworks de análise em Threat Intelligence (TI) para:
- estruturar raciocínio
- padronizar relatórios
- conectar TI com detecção e resposta a incidentes

> Objetivo: evitar análises “soltas” e melhorar consistência entre entregas (briefs, weekly, campanha).

---

## 1) Quando usar cada framework (guia rápido)

### MITRE ATT&CK
Use quando o foco for **comportamento do adversário** (TTPs) e conexão com:
- detecções (SIEM/EDR)
- gaps de controle
- priorização de hardening

**Melhor para:** transformar inteligência em casos de uso de detecção.

---

### Cyber Kill Chain
Use quando o objetivo for narrar e entender a **sequência do ataque**:
- do acesso inicial ao impacto
- com pontos de interrupção (controls)

**Melhor para:** briefings executivos e análises de incidente/campanha.

---

### Diamond Model
Use quando você precisa entender relações entre:
- **Adversário**
- **Infraestrutura**
- **Capacidade**
- **Vítima**

**Melhor para:** investigar campanha e mapear infraestrutura (C2), e relacionar clusters.

---

## 2) MITRE ATT&CK — aplicação prática

### 2.1 Como usar no dia a dia
1. Identificar **tática** (ex.: Initial Access, Execution, Credential Access)
2. Mapear **técnicas** prováveis/observadas
3. Verificar:
   - controles existentes (preventivos/detectivos)
   - evidências e logs necessários
   - lacunas (gaps) e ações

### 2.2 Modelo de tabela ATT&CK (para relatórios)
| Tática | Técnica | ID ATT&CK | Evidência/Observação | Detecção atual? | Gap | Ação recomendada |
|---|---|---|---|---|---|---|
| Initial Access |  |  |  | Sim/Não/Parcial |  |  |

### 2.3 Exemplo (alto nível, fictício)
| Tática | Técnica | ID | Observação | Detecção? | Gap | Ação |
|---|---|---|---|---|---|---|
| Initial Access | Phishing | T1566 | campanhas setoriais | Parcial | pouca visibilidade em e-mail | ajustar regras + awareness |
| Credential Access | Credential Dumping | T1003 | pós-compromisso | Sim | cobertura limitada | ampliar alertas em endpoints |

> Observação: em conteúdo público, manter exemplos **fictícios** e sem detalhes sensíveis.

---

## 3) Kill Chain — aplicação prática

### 3.1 Etapas (versão simplificada)
1. Reconhecimento
2. Weaponization (preparação)
3. Delivery (entrega)
4. Exploitation (exploração)
5. Installation (instalação)
6. Command & Control (C2)
7. Actions on Objectives (impacto/objetivo)

### 3.2 Como usar
- Identificar quais etapas estão presentes na campanha
- Mapear pontos de controle onde é possível interromper
- Gerar recomendações por etapa (prevenir/detectar/responder)

### 3.3 Modelo de tabela (para campanha)
| Etapa | O que ocorre | Sinais/Logs | Controles | Detecções | Ações recomendadas |
|---|---|---|---|---|---|
| Delivery |  |  |  |  |  |

---

## 4) Diamond Model — aplicação prática

### 4.1 Elementos principais
- **Adversário:** quem (grupo/cluster, quando possível)
- **Capacidade:** ferramentas, malware, TTPs
- **Infraestrutura:** domínios, IPs, servidores, serviços
- **Vítima:** setor, região, perfil, organização/ativos

### 4.2 Como usar
- Ajuda a identificar padrões: “mesma infraestrutura em múltiplas campanhas”
- Ajuda a correlacionar clusters quando atribuição é incerta
- Ajuda a definir o que monitorar (infraestrutura) e onde reforçar controles (vítima)

### 4.3 Modelo de registro (resumo)
- Adversário/Cluster: _______________________________
- Capacidade (TTPs/malware): ________________________
- Infraestrutura (tipos): ___________________________
- Vítimas/Alvos: ___________________________________
- Confiança: Baixa/Média/Alta
- Observações: ____________________________________

---

## 5) Como escolher um “formato padrão” para entregas

### 5.1 Para Threat Brief (executivo)
- Use **Kill Chain** para narrativa
- Inclua 3–5 técnicas ATT&CK apenas se ajudarem nas ações
- Foque em risco/impacto/decisão

### 5.2 Para Weekly Summary
- Use ATT&CK de forma leve (técnicas recorrentes)
- Use categorias simples (CVE, phishing, ransomware)
- Mantenha recomendação clara e curta

### 5.3 Para Relatório de Campanha
- Use **Diamond** para estrutura e contexto
- Use ATT&CK para mapear TTPs e ações/detecções
- Use Kill Chain para timeline e pontos de interrupção

---

## 6) Conectando análise com ações (o que “fecha a conta”)

Ao final de qualquer análise, responder:
- **O que mudou?**
- **Qual o risco para nós?**
- **Onde estamos expostos?**
- **O que fazer agora (0–7 dias)?**
- **O que melhorar (30–90 dias)?**
- **Como vamos medir se funcionou?**

---

## 7) Conexões com este repositório

- Relatório de Campanha: `02-templates/campaign-report-template.md`
- Threat Brief: `02-templates/threat-brief-template.md`
- PIRs: `01-foundations/requirements-and-priorities.md`
- Plano de Coleta: `03-collection-and-sources/collection-plan.md`

---
