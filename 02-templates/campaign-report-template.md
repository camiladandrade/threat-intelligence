# Relatório de Campanha — Template (Threat Intelligence)

Template para relatório completo de campanha/ameaça, com foco em **contexto, evidência, impacto** e **ações recomendadas**.

> Uso típico: ransomware/campanha de phishing em massa, exploração de CVE, atividade persistente, ameaça relevante ao setor/stack.
> Público: Segurança/SOC/IR/TI e resumo executivo para liderança.

---

## 1) Identificação

- **Título:** _______________________________________________
- **Data:** ____/____/____
- **Autor(a):** ____________________________________________
- **TLP:** (Branco / Verde / Âmbar / Vermelho) _______________
- **Severidade:** Baixa / Média / Alta / Crítica
- **Confiança:** Baixa / Média / Alta
- **Janela analisada:** _____________________________________
- **Relacionamento com PIR(s):** (PIR-___, PIR-___) ___________

---

## 2) Resumo executivo (para liderança)

- **O que é:** ______________________________________________
- **Impacto potencial no negócio:** __________________________
- **Nível de exposição da organização:** _____________________
- **Ações prioritárias (Top 3):**
  1) ____________________________________
  2) ____________________________________
  3) ____________________________________

---

## 3) Contexto e panorama da campanha

### 3.1 Descrição da campanha
- O que caracteriza a campanha e qual o objetivo provável (ex.: extorsão, fraude, espionagem):  
  ___________________________________________________________

### 3.2 Alvos comuns (setores, regiões, perfis)
- ___________________________________________________________

### 3.3 Linha do tempo (se aplicável)
| Data/Período | Evento | Observação |
|---|---|---|
|  |  |  |

---

## 4) Vetores e TTPs (Táticas, Técnicas e Procedimentos)

### 4.1 Acesso inicial (Initial Access)
- Possíveis vetores:
  - [ ] Phishing
  - [ ] Exploração de vulnerabilidade
  - [ ] Credenciais roubadas
  - [ ] Terceiros/fornecedores
  - [ ] Outros: ______________________
- Detalhes: ________________________________________________

### 4.2 Execução, persistência e movimentação
> Liste apenas o que for relevante e com confiança adequada.

- **Execução:** _____________________________________________
- **Persistência:** _________________________________________
- **Escalada de privilégio:** _______________________________
- **Movimentação lateral:** _________________________________
- **Comando e controle (C2):** ______________________________
- **Exfiltração/impacto:** __________________________________

### 4.3 Mapeamento MITRE ATT&CK (opcional)
| Tática | Técnica | ID ATT&CK | Evidência/Notas |
|---|---|---|---|
|  |  |  |  |

---

## 5) Indicadores (IOCs) e artefatos

> Evite colocar lista completa em canal aberto. Prefira anexar em local controlado e referenciar aqui.

- **Status do pacote de IOCs:** Novo / Em triagem / Validado / Implantado / Monitorado / Expirado
- **Ação recomendada:** Bloquear / Detectar / Monitorar
- **Link controlado do pacote:** ____________________________

### 5.1 Resumo de IOCs (alto nível)
- Tipos: IP / Domínio / URL / Hash / Email / User-Agent / Outros
- Quantidade aproximada: ____
- Janela de validade/expiração: _____________________________

---

## 6) Exposição e impacto na organização

### 6.1 Exposição interna (o que sabemos)
- **Tecnologias/sistemas potencialmente afetados:** ___________
- **Superfície de ataque relevante:** _______________________
- **Sinais internos relacionados (se houver):** ______________

### 6.2 Impacto no negócio (mapa)
Marcar e detalhar:
- [ ] Interrupção operacional: _______________________________
- [ ] Financeiro: ___________________________________________
- [ ] Dados/PII (LGPD): ____________________________________
- [ ] Reputação: ____________________________________________
- [ ] Compliance/contratos: _________________________________

---

## 7) Recomendações (ações priorizadas)

### 7.1 Ações imediatas (0–7 dias)
1. ____________________________________ (Owner: ___ / Prazo: ___)
2. ____________________________________ (Owner: ___ / Prazo: ___)
3. ____________________________________ (Owner: ___ / Prazo: ___)

### 7.2 Ações de curto prazo (7–30 dias)
1. ____________________________________
2. ____________________________________

### 7.3 Ações estruturais (30–90 dias)
1. ____________________________________
2. ____________________________________

---

## 8) Detecção e resposta (orientação para SOC/IR)

### 8.1 Hipóteses de detecção (alto nível)
- Logs/fontes recomendadas: _________________________________
- Regras/casos de uso sugeridos: ____________________________
- Alertas para triagem: _____________________________________

### 8.2 Playbooks relacionados
- Link para playbook IR (se aplicável): _____________________
- Link para runbook técnico: ________________________________

---

## 9) Observações e limitações

- O que não foi possível confirmar: _________________________
- Lacunas de dados: _________________________________________
- Riscos de falso positivo: _________________________________

---

## 10) Fontes e referências

> 3–10 fontes, e indicar o nível de confiança quando necessário.

- ____________________________________
- ____________________________________
- ____________________________________

---

## 11) Apêndices (opcional)

- Lista detalhada de IOCs (link controlado)
- Prints/logs sanitizados
- Consultas/queries (sem dados sensíveis)
- Timeline detalhada

---
