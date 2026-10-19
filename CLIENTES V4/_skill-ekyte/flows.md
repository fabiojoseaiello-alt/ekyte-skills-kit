# Cache ekyte — Fluxos por tipo de tarefa

Gerado 2026-06-02 via `/ekyte-refresh` → `get_task_type_flow` (MCP oficial). Workflow base **Padrão Colli&Co (Oficial)** (3535).

**O que é:** as fases REAIS (effort/duration > 0) de cada tipo, em ordem, com `phaseId`. Usado pela `/ekyte-task` pra mostrar o fluxo e resolver `nome da fase → phaseId` ao trocar responsável de etapa.

**phaseId é global** (compartilhado entre tipos: `1`=Briefing, `5`=Copywriter, `6`=Designer…). Executor default não fica aqui (varia por workspace) — a skill lê o real via `get_detailed_task` em runtime.

Refresh: `/ekyte-refresh`.

---

## Fluxo Prisma — workflow [PROJETO PRISMA] V4 Colli&Co (22012)

⚠️ **O workflow inteiro foi RECRIADO em 2026-07-13 09:21** (mesmo dia, horas antes do lote de 10 tasks do /ekyte-task). Tudo abaixo desta linha é a leitura live pós-reconstrução (via `get_task_type_flow`, confirmado em `get_detailed_task` de tasks reais criadas). A versão anterior (2026-06-26) ficou desatualizada — os `active` flags mudaram bastante entre as duas versões. **Sempre re-checar `get_task_type_flow` em runtime antes de montar `flow` de create_task** — não confiar cegamente neste cache se fizer tempo desde 2026-07-13.

**allocationType=10** (Agile). Executores default por fase variam por tipo (Fabio `a2f17bce-eed7-4ea6-beda-9efd449010ec`, Vinícius Colli `9a2b34d0-013b-49c5-bcff-c05f287bf296`, André Emanuel `aadf78c4-e642-450b-9ba1-fde2a0cab489` nas fases de Design).

### M-CRM — [00][M-CRM] Projeto Prisma | Manutencao CRM (81153) · 11 fases ativas (live 2026-07-13)

Backlog `#82168`(Fabio,seq1) → Analise Cientista `#82171`(Fabio,seq4) → Execucao Tecnica `#82180`(Fabio,seq7) → Revisao IA/QA `#82179`(Fabio,seq8) → (opcional) Refacao Interna `#82182`(Vinícius,seq11) → (opcional) Ajuste Cliente `#82175`(Vinícius,seq12) → Configuracao `#82176`(Vinícius,seq13) → Go Live/Publicacao `#82174`(Vinícius,seq14) → Desenvolvimento de Relatorio `#82184`(Vinícius,seq16) → Monitoramento `#82172`(Fabio,seq17) → Reuniao `#82185`(Vinícius,seq18)

Inativas: Briefing+Copy `#82169` · Coleta de Evidencias `#82170` · Planejamento `#82183` · Em producao-Design `#82181` · Aprovacao Cientista `#82178` · Aprovacao Cliente `#82177`

Usado em 2026-07-13 para: Cliente Mu (Validar API, Subir arquivos IA — entrada em Execução Técnica), Cliente Lambda (Ajustar automação), Cliente Zeta (Ajustar automação).

### PRI-A — [00][PRI-A] Projeto Prisma | Analise e Direcionamento (81136) · 8 fases ativas (live 2026-07-13)

Backlog `#82168`(Fabio,seq1) → Coleta de Evidencias `#82170`(Fabio,seq3) → Analise Cientista `#82171`(Fabio,seq4) → Planejamento `#82183`(Fabio,seq5) → Revisao IA/QA `#82179`(Fabio,seq8) → Desenvolvimento de Relatorio `#82184`(Vinícius,seq15) → Monitoramento `#82172`(Fabio,seq16) → Reuniao `#82185`(Vinícius,seq16)

Inativas: Briefing+Copy `#82169` · Em producao-Design `#82181` · Execucao Tecnica `#82180` · Aprovacao Cientista `#82178` · Aprovacao Cliente `#82177` · (opcional) Refacao Interna `#82182` · (opcional) Ajuste Cliente `#82175` · Configuracao `#82176` · Go Live/Publicacao `#82174`

Usado em 2026-07-13 para: Cliente Teta (Revisão BI — entrada em Análise Cientista), Cliente Lambda (Estudo palavras-chave — entrada em Backlog).

### DP — [00][DP] Projeto Prisma | Design Performance (81142) · 10 fases ativas (live 2026-07-13)

Backlog `#82168`(Fabio,seq1) → Briefing+Copy `#82169`(Fabio,seq2) → Em producao-Design `#82181`(**André Emanuel**,seq6) → Revisao IA/QA `#82179`(André,seq8) → Aprovacao Cientista `#82178`(Fabio,seq9) → Aprovacao Cliente `#82177`(André,seq10) → (opcional) Refacao Interna `#82182`(André,seq11) → (opcional) Ajuste Cliente `#82175`(André,seq12) → Go Live/Publicacao `#82174`(Fabio,seq14) → Monitoramento `#82172`(Fabio,seq16)

Inativas: Coleta de Evidencias `#82170` · Analise Cientista `#82171` · Planejamento `#82183` · Execucao Tecnica `#82180` · Configuracao `#82176` · Desenvolvimento de Relatorio `#82184` · Reuniao `#82185`

Usado em 2026-07-13 para: Cliente Mu (Criativos vídeo B2B), Cliente Lambda (Ads Aniversário) — ambas entrando direto em Em Produção-Design com André.

### PCP — [00][PCP] Projeto Prisma | Publicacao de Campanha (81138) · 6 fases ativas (live 2026-07-13)

Backlog `#82168`(Fabio,seq1) → Briefing+Copy `#82169`(Fabio,seq2) → Revisao IA/QA `#82179`(Fabio,seq8) → Configuracao `#82176`(Fabio,seq13) → Go Live/Publicacao `#82174`(Fabio,seq14) → Monitoramento `#82172`(Fabio,seq16)

Inativas: Coleta de Evidencias `#82170` · Analise Cientista `#82171` · Planejamento `#82183` · Em producao-Design `#82181` · Execucao Tecnica `#82180` · Aprovacao Cientista `#82178` · Aprovacao Cliente `#82177` · (opcional) Refacao Interna `#82182` · (opcional) Ajuste Cliente `#82175` · Desenvolvimento de Relatorio `#82184` · Reuniao `#82185`

Usado em 2026-07-13 para: Cliente Nu (Campanha forms nativo Noivas + Debutantes — entrada em Configuração).

---

## Fluxo por tipo (fases reais, em ordem)

### AC — [AC]  V4 Colli&Co | Ajustes Criativo Ads/Copywriting (38179) · 13 fases · SLA 6d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### ACRM — [ACRM] V4 Colli&Co | Acompanhamento de CRM (34436) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Integração CRM / Trackeamento `#3452` → Publicação/Configuração `#14` → Monitoramento `#16`

### AN — [AN] V4 Colli&Co | Análise de dados / Projeção (37680) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### AP — [AP] V4 Colli&Co | Aprovação, alteração e publicação ªQ (37681) · 20 fases · SLA 26d
Briefing `#1` → Análise `#2` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Produção (Cliente) `#890` → Designer `#6` → Alterações Design `#3693` → VideoMaker `#1585` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Desdobramento `#476` → Revisão (Head) `#109` → Publicação/Configuração `#14` → Monitoramento `#16`

### ATM — [ATM] V4 Colli&Co | Automação de e-mail marketing (34438) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Gestor de tráfego `#12707` → Monitoramento `#16`

### ATWPP — [ATWPP] V4 Colli&Co | Atendimento/comunicação whatsapp (32813) · 2 fases · SLA 0d
Briefing `#1` → Designer `#6`

### AUX — [AUX] V4 Colli&Co | Análise UX (37921) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### AV — [AV] V4 Colli&Co | Confecção do Avatar para Whats App (40142) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### CA — [CA]  V4 Colli&Co | Criativo Ads (29740) · 16 fases · SLA 11d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Acompanhamento de aprovação da Copy `#8137` → Designer `#6` → Alterações Design `#3693` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### CB — [CB] V4 Colli&Co |Configuração do Copybase (33949) · 4 fases · SLA 2d
Briefing `#1` → Copywriter `#5` → Aprovação do Cliente `#534` → Configuração `#1129`

### CD — [CD] V4 Colli&Co | Solicitação de Cardápio (37683) · 20 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Produção (Cliente) `#890` → Designer `#6` → Alterações Design `#3693` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Acompanhamento de aprovação (Design) `#8139` → Desdobramento `#476` → Revisão (Head) `#109` → Publicação/Configuração `#14` → Divulgação `#15` → Monitoramento `#16`

### CJ — [CJ]  V4 Colli&Co | Copy Jornada (29732) · 13 fases · SLA 3d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### CP — [CP]  V4 Colli&Co | Solicitação ao Copy (38177) · 13 fases · SLA 3d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### CRM — [CRM] V4 Colli&Co | Configuração de CRM (34435) · 14 fases · SLA 1d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Integração CRM / Trackeamento `#3452` → Publicação/Configuração `#14` → Monitoramento `#16`

### DC — [DC]  V4 Colli&Co | Desdobramento de Criativo Ads (38176) · 13 fases · SLA 6d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### DE — [DE] V4 Colli&Co | Desdobramento de E-mail Marketing (38181) · 13 fases · SLA 5d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### DLP — [DLP] V4 Colli&Co | Desdobramento de Landing Page (38178) · 13 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### EA — [EA] V4 Colli&Co | Entrega avulsa (34454) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### EB — [EB]  V4 Colli&Co | E-book (29733) · 13 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### EG — [EG] V4 Colli&Co | Solicitação de Embalagens (37685) · 22 fases · SLA 22d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Alterações Design `#3693` → VideoMaker `#1585` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Acompanhamento de aprovação (Design) `#8139` → Desdobramento `#476` → Revisão (Head) `#109` → Integração CRM / Trackeamento `#3452` → Configuração `#1129` → Publicação/Configuração `#14` → Divulgação `#15` → Monitoramento `#16`

### EKT — [EKT] V4 Colli&Co | Organização/Acompanhamento Ekyte (34483) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### EM — [EM]  V4 Colli&Co | E-mail Marketing (29734) · 13 fases · SLA 5d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### ENG — [01][ENG] Solicitação Eng. Dados (43411) · 3 fases · SLA 10d
Análise `#2` → Aprovação interna `#1834` → Configuração `#1129`

### EV — [EV] V4 Colli&Co | Edição de Vídeo (29730) · 14 fases · SLA 3d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → VideoMaker `#1585` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### GP — [GP] V4 Colli&Co | Solicitação ao GP (30064) · 13 fases · SLA 1d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### IE — [IE] Tribo de M&P | Iniciativa estratégica (59457) · 3 fases · SLA 4d
Briefing `#1` → Gestor de tráfego `#12707` → Monitoramento `#16`

### KV — [KV] V4 Colli&Co | Key Visual (29748) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### LP — [LP] V4 Colli&Co | Landing Page (29727) · 13 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### MT — [MT] V4 Colli&Co | Motion (29728) · 13 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### OCA — [OCA]  V4 Colli&Co | Otimização Criativo Ads (61585) · 13 fases · SLA 6d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### OFF — [OFF] V4 Colli&Co | Materiais offline (30082) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### OTM — [OTM] V4 Colli&Co | Otimização de campanhas (34442) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### OV — [OV] V4 Colli&Co | Nome do Overdelivery (30083) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### OVERVIEW — [OVERVIEW] Overview Diário das Contas (70418) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PA — [PA]  V4 Colli&Co | Pauta xªQ (32247) · 7 fases · SLA 3d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Configuração `#1129`

### PAPP — [PAPP] V4 Colli&Co | Produção InApp (37916) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PC — [PC] V4 Colli&Co| Publicação de campanhas (34482) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Gestor de tráfego `#12707` → Monitoramento `#16`

### PI — [PI] V4 Colli&Co | Produção IS (37914) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PMS — [PMS] V4 Colli&Co | Produção Marketing Screen (37999) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PP — [PP]  V4 Colli&Co | Pré-pauta xªQ (32246) · 7 fases · SLA 2d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Configuração `#1129`

### PPSH — [PPSH] V4 Colli&Co | Produção Push (37917) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PPT — [PPT] V4 Colli&Co| PPT (30063) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### PSMS — [PSMS] V4 Colli&Co | Produção SMS (37919) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### PWPP — [PWPP] V4 Colli&Co | Produção WhatsApp (37918) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### RE — [RE] V4 Colli&Co | Reuniões externas (34441) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16` → Reunião `#50436`

### REL — [REL]  V4 Colli&Co | Preenchimento de relatórios (34439) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Configuração `#1129` → Publicação/Configuração `#14` → Monitoramento `#16`

### RI — [RI] V4 Colli&Co | Reuniões internas (34440) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16` → Reunião `#50436`

### RV — [RV] V4 Colli&Co| Roteiro de vídeo (37666) · 7 fases · SLA 7d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Produção (Cliente) `#890` → Monitoramento `#16`

### SE — [SE] V4 Colli&Co | Sales enablement (34437) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Configuração `#1129` → Publicação/Configuração `#14` → Monitoramento `#16`

### SL — [SL] V4 Colli&Co | Social Listening (37688) · sem fases de esforço
Tipo de rotina/sem fluxo de produção. Ler em runtime via `get_detailed_task`.

### SM — [SM] V4 Colli&Co | dia/mês | Nome do post | formato (32249) · 8 fases · SLA 1d
Briefing `#1` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Configuração `#1129`

### SV — [SV]  V4 Colli&Co | Script de Vendas (29745) · 13 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Publicação/Configuração `#14` → Monitoramento `#16`

### TRK — [TRK] V4 Colli&Co | Traqueamento Integração (34484) · 14 fases · SLA 0d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Designer `#6` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Integração CRM / Trackeamento `#3452` → Publicação/Configuração `#14` → Monitoramento `#16`

### WPP — [WPP] V4 Colli&Co| Régua WPP (38781) · 17 fases · SLA 1d
Briefing `#1` → Copywriter `#5` → Revisão da copy `#992` → Ajustes Copy `#1835` → Aprovação Refação da Copy `#10666` → Aprovação do Cliente `#534` → Acompanhamento de aprovação da Copy `#8137` → Designer `#6` → Alterações Design `#3693` → Aprovação interna `#1834` → Aprovação Refação do Design `#10668` → Aprovação do cliente (Design) `#535` → Fazer alterações solicitadas pelo Cliente (Design) `#1409` → Aprovação Refação do Design (Cliente) `#10669` → Acompanhamento de aprovação (Design) `#8139` → Publicação/Configuração `#14` → Monitoramento `#16`

---

## Dicionário mestre de fases (phaseId → nome) — 27 fases distintas

Lookup `nome da fase → phaseId` (case-insensitive, match parcial).

| phaseId | Fase |
|---|---|
| 1 | Briefing |
| 2 | Análise |
| 5 | Copywriter |
| 6 | Designer |
| 14 | Publicação/Configuração |
| 15 | Divulgação |
| 16 | Monitoramento |
| 109 | Revisão (Head) |
| 476 | Desdobramento |
| 534 | Aprovação do Cliente |
| 535 | Aprovação do cliente (Design) |
| 890 | Produção (Cliente) |
| 992 | Revisão da copy |
| 1129 | Configuração |
| 1409 | Fazer alterações solicitadas pelo Cliente (Design) |
| 1585 | VideoMaker |
| 1834 | Aprovação interna |
| 1835 | Ajustes Copy |
| 3452 | Integração CRM / Trackeamento |
| 3693 | Alterações Design |
| 8137 | Acompanhamento de aprovação da Copy |
| 8139 | Acompanhamento de aprovação (Design) |
| 10666 | Aprovação Refação da Copy |
| 10668 | Aprovação Refação do Design |
| 10669 | Aprovação Refação do Design (Cliente) |
| 12707 | Gestor de tráfego |
| 50436 | Reunião |
| 82168 | Backlog (Prisma) |
| 82169 | Briefing + Copy (Prisma) |
| 82170 | Coleta de Evidencias (Prisma) |
| 82171 | Analise Cientista (Prisma) |
| 82172 | Monitoramento (Prisma) |
| 82174 | Go Live / Publicacao (Prisma) |
| 82175 | (opcional) Ajuste Cliente (Prisma) |
| 82176 | Configuracao (Prisma) |
| 82177 | Aprovacao Cliente (Prisma) |
| 82178 | Aprovacao Cientista (Prisma) |
| 82179 | Revisao IA / QA (Prisma) |
| 82180 | Execucao Tecnica (Prisma) |
| 82181 | Em producao - Design (Prisma) |
| 82182 | (opcional) Refacao Interna (Prisma) |
| 82183 | Planejamento (Prisma) |
| 82184 | Desenvolvimento de Relatorio (Prisma) |
| 82185 | Reuniao (Prisma) |
