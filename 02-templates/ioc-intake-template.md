# IOC Intake — Template (Triagem e Validação de Indicadores)

Template para registrar, triar e validar IOCs (indicadores), garantindo qualidade, contexto e rastreabilidade antes de aplicar em bloqueios/detecções.

> Objetivo: reduzir falsos positivos, evitar bloqueios perigosos (ex.: CDNs) e manter ciclo de vida (expiração/revogação).

---

## 1) Identificação

- **ID do registro:** IOC-______
- **Data de recebimento:** ____/____/____
- **Recebido por:** ______________________________________
- **Fonte:** (interna/externa) _____________________________
- **TLP:** (Branco / Verde / Âmbar / Vermelho) _____________
- **Severidade:** Baixa / Média / Alta / Crítica
- **Confiança inicial:** Baixa / Média / Alta

**Relacionamento com:**
- **Campanha/Relatório:** _________________________________
- **PIR(s):** _____________________________________________
- **Incidente (se houver):** _______________________________

---

## 2) Detalhes do IOC

### 2.1 Tipo de IOC
- [ ] IP
- [ ] Domínio
- [ ] URL
- [ ] Hash (MD5/SHA1/SHA256)
- [ ] Email/Remetente
- [ ] User-Agent
- [ ] Certificado (fingerprint)
- [ ] Outros: ______________________

### 2.2 Valor do IOC
- **IOC:** ________________________________________________

### 2.3 Contexto mínimo (obrigatório)
- **O que este IOC representa?** (ex.: C2, phishing, payload, infraestrutura, sender)  
  ___________________________________________________________
- **Onde foi observado?** (ambiente interno/OSINT) ___________
- **Quando foi observado?** (data/hora) ______________________
- **Evidência/Referência:** (link, relatório, log sanitizado) ___

---

## 3) Validação e qualidade

### 3.1 Checagens de qualidade (marcar)
- [ ] Formato válido (IP/domínio/hash etc.)
- [ ] Não é item genérico (ex.: domínio amplo, CDN, provedor popular) sem contexto
- [ ] Possui contexto suficiente para uso
- [ ] Data/recência conhecida
- [ ] Fonte confiável (ou cruzada com outra fonte)

### 3.2 Enriquecimento (opcional)
- Reputação/observações adicionais: _________________________
- Infraestrutura relacionada: ______________________________
- Observações de histórico: ________________________________

---

## 4) Avaliação de risco de falso positivo

> Especialmente importante para IPs/domínios.

- **Risco de falso positivo:** Baixo / Médio / Alto
- **Motivo:** _____________________________________________

**Recomendação:**
- [ ] Bloquear (somente se FP baixo e impacto aceitável)
- [ ] Detectar (preferível quando FP médio)
- [ ] Monitorar (quando FP alto ou contexto fraco)
- [ ] Não utilizar (sem qualidade / inválido)

---

## 5) Ação recomendada e implementação

### 5.1 Ação definida
- **Ação:** Bloquear / Detectar / Monitorar / Não usar
- **Justificativa:** _______________________________________

### 5.2 Onde aplicar (marcar)
- [ ] E-mail (gateway / antiphishing)
- [ ] Proxy/DNS
- [ ] Firewall
- [ ] EDR
- [ ] SIEM
- [ ] WAF
- [ ] Outros: ______________________

### 5.3 Tickets e rastreabilidade
- Ticket/Change ID: _______________________________________
- Owner implementação: _____________________________________
- Data de implantação: ____/____/____

---

## 6) Ciclo de vida (expiração e manutenção)

- **Status do IOC:** Novo / Em triagem / Validado / Implantado / Monitorado / Expirado / Revogado
- **Data de expiração recomendada:** ____/____/____
- **Motivo da expiração:** (fim de campanha / FP / desatualizado) _________
- **Plano de revisão:** (ex.: semanal) _______________________

---

## 7) Evidência de resultado (feedback loop)

> Registrar se o IOC gerou detecções úteis ou falsos positivos.

- **Resultado observado:** Útil / Falso positivo / Inconclusivo
- **Detalhes:** ____________________________________________
- **Ajustes necessários:** __________________________________
- **Data do feedback:** ____/____/____
- **Quem forneceu feedback (SOC/IR/TI):** ___________________

---
