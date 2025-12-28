# Fontes e Ferramentas — Threat Intelligence (Guia)

Este documento organiza **fontes e ferramentas** usadas em Threat Intelligence (TI), com foco em:
- consistência de coleta
- qualidade e rastreabilidade
- uso seguro (TLP, dados sensíveis, LGPD)
- alinhamento com os PIRs

> Objetivo: reduzir “coleta aleatória” e padronizar o que é confiável e útil.

---

## 1) Princípios (regras do jogo)

- Priorizar fontes que entreguem **contexto e evidências**, não só IOCs soltos.
- Sempre registrar **fonte**, **data**, **TLP** e **confiança**.
- Evitar dependência de “uma única fonte”.
- Separar claramente:
  - **fontes internas** (mais relevantes para exposição real)
  - **fontes externas** (panorama e sinais do mercado)
- Seguir políticas internas de segurança e privacidade (LGPD e confidencialidade).

---

## 2) Fontes internas (mais valiosas)

> Fontes internas mostram exposição real e reduzem “TI de notícia”.

### 2.1 SOC / SIEM
- alertas relevantes e tendências (top regras, top entidades)
- correlações e padrões (ex.: picos de falhas de login)
- queries e dashboards (sem dados sensíveis em entregas públicas)

**Uso típico:** hipóteses de detecção, validação de campanha, priorização.

---

### 2.2 EDR/XDR
- detecções e telemetria de endpoint
- evidências (processos, conexões, hashes)
- timelines de atividade

**Uso típico:** validação de IOC, enriquecimento e resposta.

---

### 2.3 Incidentes (IR) e pós-incidente (PIR)
- causa raiz, vetor inicial, falhas de controle
- TTPs observadas e lições aprendidas
- recomendações de melhoria

**Uso típico:** refinar PIRs e gerar ações estruturais.

---

### 2.4 Gestão de Vulnerabilidades (VM)
- CVEs relevantes e exposição (stack afetada)
- SLA/aging e backlog por criticidade
- vulnerabilidades exploradas ativamente (quando mapeadas)

**Uso típico:** patching orientado a risco e briefings de CVEs.

---

### 2.5 IAM / Identidade / Acessos
- tentativas anômalas de login
- padrões de abuso (MFA, tokens, OAuth)
- acessos privilegiados e revisões

**Uso típico:** TI aplicada a “acesso inicial” e prevenção de comprometimento.

---

### 2.6 Infra / Cloud / Rede
- mudanças e incidentes de disponibilidade
- logs relevantes (WAF, DNS, proxy, firewall)
- exposição pública (serviços, endpoints)

**Uso típico:** hardening, segmentação e mitigação.

---

## 3) Fontes externas (panorama e sinais)

> Categorizar ajuda a evitar “colecionar link”.

### 3.1 Comunicados oficiais (vendors, CERTs, advisories)
- alertas de CVEs, patches e mitigação
- notas de incidentes e recomendações

**Uso típico:** priorização de patch, mudanças de configuração, briefings executivos.

---

### 3.2 Relatórios de pesquisa (setor e campanhas)
- relatórios técnicos com TTPs, vetores e recomendações
- análises por setor, região e tecnologias

**Uso típico:** planejamento, tendência e construção de casos de uso.

---

### 3.3 OSINT técnico (repositórios e publicações técnicas)
- análises de malware, PoCs, técnicas de exploração
- discussões técnicas e indicadores (com validação)

**Uso típico:** enriquecer entendimento e orientar detecções.

---

### 3.4 Feeds de indicadores (IOC feeds)
- indicadores em volume (com variabilidade de qualidade)
- exigem triagem rigorosa

**Uso típico:** monitoramento e detecção (raramente “bloqueio direto”).

---

### 3.5 Comunidades e grupos (quando aplicável)
- grupos de confiança (com TLP e regras claras)
- troca de sinais com peers do setor

**Uso típico:** “early warning” e contexto adicional.

---

## 4) Ferramentas (categorias)

> Não precisa listar marcas específicas; o que importa é o “tipo de ferramenta”.

### 4.1 Coleta e agregação
- leitores RSS / agregadores
- automações (coleta periódica por tema/PIR)
- normalização de formatos (CSV/JSON)

### 4.2 Enriquecimento e reputação
- enriquecimento de domínio/IP/hash
- correlacionadores e graph de relacionamento (quando aplicável)

### 4.3 Gestão de IOCs e integração
- repositório central de IOCs (com status e expiração)
- integração com SIEM/EDR/proxy/DNS/firewall
- versionamento e auditoria (quem mudou o quê)

### 4.4 Análise
- mapeamento MITRE ATT&CK
- timelines e correlação de eventos
- análise de malware (ambiente isolado, quando aplicável)

### 4.5 Entrega e comunicação
- templates e relatórios (brief, weekly summary)
- wiki/portal interno
- trilhas de auditoria (evidências)

---

## 5) Segurança e compliance no uso de fontes

- Respeitar TLP e contratos/licenças de uso.
- Não inserir dados sensíveis em ferramentas externas sem autorização.
- Sanitizar evidências (PII, credenciais, detalhes internos).
- Se a fonte exigir restrição, sinalizar isso nas entregas.

---

## 6) Registro mínimo por item coletado (padrão)

Para qualquer item que vire análise ou ação, registrar:
- PIR relacionado
- fonte (nome + tipo) e data
- TLP
- confiança (baixa/média/alta)
- resumo do “por que importa”
- ação recomendada (se houver)
- link para ticket/evidência (quando operacionalizado)

---

## 7) Conexões com o repositório

- Plano de Coleta: `03-collection-and-sources/collection-plan.md`
- Validação e Triagem: `03-collection-and-sources/validation-and-triage.md`
- PIRs: `01-foundations/requirements-and-priorities.md`
- Templates: `02-templates/`

---
