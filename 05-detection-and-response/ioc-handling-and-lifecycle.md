# Ciclo de Vida de IOCs — Do intake à expiração (IOC Handling)

Este documento padroniza o **ciclo de vida de IOCs (Indicadores de Comprometimento)** para uso seguro e eficaz em detecção/bloqueio/monitoramento.

> Objetivo: evitar IOCs “eternos”, reduzir falsos positivos e manter rastreabilidade (quem aplicou, onde, quando e por quê).

---

## 1) Princípios

- IOC sem contexto é **dado**, não inteligência.
- Sempre avaliar risco de **falso positivo** antes de bloquear.
- Todo IOC deve ter:
  - **status**
  - **confiança**
  - **data de expiração**
  - **ação recomendada** (bloquear/detectar/monitorar)
- Prefira “**detectar**” antes de “**bloquear**” quando FP for risco.
- Manter trilha de auditoria: fonte, decisões e tickets.

---

## 2) Estados (status) do IOC

Status padrão (use estes nomes para consistência):
1. **Novo** — recebido, ainda não triado
2. **Em triagem** — validação e enriquecimento em andamento
3. **Validado** — contexto suficiente + decisão de uso definida
4. **Implantado** — aplicado em controles (SIEM/EDR/DNS etc.)
5. **Monitorado** — ativo, mas com cautela/escopo limitado (FP médio/alto)
6. **Expirado** — não é mais relevante (fim de campanha / recência vencida)
7. **Revogado** — inválido/incorreto (ou causou FP crítico)

---

## 3) Campos obrigatórios (mínimo para qualquer IOC)

- **ID do IOC:** IOC-_____
- **Tipo:** IP / Domínio / URL / Hash / Email / UA / Outros
- **Valor:** ____________________________
- **Fonte + data de coleta:** ____________________________
- **Contexto:** C2 / phishing / payload / infraestrutura / outro
- **TLP:** Branco / Verde / Âmbar / Vermelho
- **Confiança:** baixa/média/alta
- **Risco de FP:** baixo/médio/alto
- **Ação recomendada:** bloquear/detectar/monitorar/não usar
- **Data de expiração:** ____/____/____
- **Owner:** ____________________________
- **Tickets/Changes:** ____________________________
- **Onde implantado:** SIEM/EDR/DNS/Proxy/Firewall/Email/WAF/Cloud

> Sugestão: padronizar isso em planilha/DB interna; aqui no repo, manter o template e exemplo fictício.

---

## 4) Fluxo operacional (passo a passo)

### 4.1 Intake (entrada)
Entrada pode vir de:
- relatório/campanha
- IR/SOC (observado internamente)
- feeds/OSINT (com triagem)
- advisories e fornecedores

**Ação:** registrar usando `02-templates/ioc-intake-template.md`

---

### 4.2 Triagem e validação
Aplicar:
- `03-collection-and-sources/validation-and-triage.md`
- enriquecimento mínimo (quando útil)
- avaliação de falso positivo

**Saída:** decisão de uso e status “Validado”.

---

### 4.3 Decisão de uso (bloquear vs detectar vs monitorar)

**Bloquear** quando:
- confiança alta
- FP baixo
- impacto do bloqueio é aceitável
- existe plano de rollback

**Detectar** quando:
- confiança média/alta
- FP médio
- precisa de contexto adicional (correlação)

**Monitorar** quando:
- contexto parcial
- FP alto
- objetivo é observar tendência antes de agir

**Não usar** quando:
- qualidade ruim, obsoleto, sem contexto

---

### 4.4 Implantação (aplicar em controles)
Registrar:
- onde foi aplicado (SIEM/EDR/DNS/Proxy etc.)
- ticket/change ID
- data e owner
- versão/observações

> Recomendação: aplicar com escopo controlado quando houver risco (ex.: somente ambiente ou segmento).

---

### 4.5 Operação e monitoramento
Durante a operação, registrar:
- alertas gerados
- utilidade (deteções válidas)
- falsos positivos (e causa)
- necessidade de tuning

---

### 4.6 Expiração e “higiene” de IOCs
Todos os IOCs devem expirar para evitar ruído.

**Regras sugeridas de expiração (ajuste conforme contexto):**
- **Hash de malware:** 90–180 dias (ou enquanto campanha ativa)
- **Domínio/URL de phishing:** 14–30 dias
- **IPs (infra compartilhada):** 7–30 dias (alto risco de mudança)
- **Email sender:** 30–90 dias (com validação)

> Importante: se IOC expira, ele deve ser removido/ajustado nas integrações.

---

### 4.7 Revogação (quando dá errado)
Revogar quando:
- IOC é inválido ou foi “recycled”
- causou FP crítico / indisponibilidade
- evidência mostrou uso legítimo

**Ação:** registrar motivo e remover/rollback nos controles.

---

## 5) Boas práticas por tipo de IOC

### 5.1 IP
- Alto risco de FP (IPs mudam e podem ser reutilizados)
- Preferir detecção/correlação antes de bloqueio
- Documentar escopo e tempo de validade curto

### 5.2 Domínio/URL
- Validar se é domínio “amplo” ou infra compartilhada
- Preferir bloquear **URLs específicas** quando possível
- Expiração geralmente curta (phishing muda rápido)

### 5.3 Hash
- Mais específico e bom para EDR
- Cuidado com variantes (hash muda)
- Complementar com comportamento/TTP

---

## 6) Métricas recomendadas (para melhorar qualidade)

- % de IOCs validados vs recebidos
- tempo médio de validação (intake → validado)
- taxa de falsos positivos por tipo
- % de IOCs expirados no prazo
- nº de detecções úteis geradas por pacote de IOCs

---

## 7) Checklist rápido (antes de aplicar)

- [ ] contexto suficiente?
- [ ] confiança e FP avaliados?
- [ ] ação definida (bloquear/detectar/monitorar)?
- [ ] expiração definida?
- [ ] rollback possível?
- [ ] ticket e owner registrados?

---

## 8) Conexões com o repositório

- IOC Intake: `02-templates/ioc-intake-template.md`
- Validação e triagem: `03-collection-and-sources/validation-and-triage.md`
- TI → Detecções: `05-detection-and-response/ti-to-detections-workflow.md`
- Taxonomia e tags: `01-foundations/taxonomy-and-tags.md`

---
