# Cache ekyte — IDs e mapeamentos

Cache lazy: começa com os tipos de tarefa pré-populados; workspaces e projetos são seus e entram na primeira execução. Forçar refresh total: `/ekyte-refresh`.

Última atualização total: (preencher na primeira execução)

---

## Defaults globais

- **Fluxo obrigatorio para novas tasks (desde 2026-06-09):** Projeto Prisma. Nao criar novas tasks pelo fluxo legado/padrao anterior.
- **Responsável (sempre):** `<seu-email>@v4company.com`
- **Período ativo:** (trimestre vigente, ex.: Q4/2026)
- **Padrão de título:** `[NN][SIGLA][IA] Cliente | Demanda específica`
- **Padrão de título WEB:** `[NN][WEB][IA] Cliente | Demanda específica`
- **Tag IA:** vai no título como `[IA]` (MCP não expõe tag nativa)

---

## Workspaces (fixos — pré-carregados)

Os clientes que você atende. Qualquer pedido fora dessa lista → IA recusa e pede confirmação explícita antes de tocar. Preencha com `list_short_workspaces` do MCP Ekyte ou peça "entrou cliente novo" na `/ekyte-refresh`.

| Cliente (alias) | workspace_id | Nome no ekyte |
|---|---|---|
| (seu cliente) | `<id>` | `<nome no Ekyte>` |

---

## Projetos (trimestre vigente — descobertos via /ekyte-task ou /ekyte-refresh)

| Workspace | project_id | Nome no ekyte |
|---|---|---|

---

## Tipos de tarefa — Projeto Prisma (workflow_id 22012)

Novo fluxo obrigatório desde 2026-06-09. Todas as tasks novas usam esses tipos.

| Sigla | task_type_id | Nome completo | Fluxo resumido |
|---|---|---|---|
| PRI-A | `81136` | Projeto Prisma \| Análise e Direcionamento | Backlog → Coleta Evidências → Análise Cientista → Planejamento → Revisão IA/QA → Monitoramento |
| **DP** | `81142` | **Projeto Prisma \| Design Performance** | Backlog → Briefing+Copy → Em produção-Design → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| PCP | `81138` | Projeto Prisma \| Publicação de Campanha | Backlog → Briefing+Copy → Revisão IA/QA → Configuração → Go Live → Monitoramento |
| MAN | `81139` | Projeto Prisma \| Manutenção Técnica | Backlog → Análise Cientista → Execução Técnica → Revisão IA/QA → Monitoramento |
| IMP | `81140` | Projeto Prisma \| Implementação Técnica | Backlog → Planejamento → Execução Técnica → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| ATD | `81141` | Projeto Prisma \| Atendimento ao Cliente | Backlog → Análise Cientista → Monitoramento |
| LP | `81149` | Projeto Prisma \| Landing Page | Backlog → Briefing+Copy → Em produção-Design → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| CA | `81150` | Projeto Prisma \| Criativos Ads | Backlog → Briefing+Copy → Em produção-Design → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| RV | `81151` | Projeto Prisma \| Roteiro de Vídeo | Backlog → Briefing+Copy → Em produção-Design → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| BN | `81152` | Projeto Prisma \| Banners | Backlog → Briefing+Copy → Em produção-Design → Revisão IA/QA → Aprovação Cientista → Aprovação Cliente → Go Live → Monitoramento |
| M-CRM | `81153` | Projeto Prisma \| Manutenção CRM | Backlog → Análise Cientista → Execução Técnica → Revisão IA/QA → Monitoramento |
| M-CAMP | `81154` | Projeto Prisma \| Manutenção Campanhas | Backlog → Análise Cientista → Execução Técnica → Revisão IA/QA → Monitoramento |
| RI | `81145` | Projeto Prisma \| Reunião Interna | Backlog → Reunião → Desenvolvimento Relatório |
| RE | `81146` | Projeto Prisma \| Reunião Externa | Backlog → Reunião → Desenvolvimento Relatório |

> ⚠️ **O "Fluxo resumido" desta tabela é incompleto** (verificado 2026-08-12 via `get_detailed_task_type`). Ele omite as fases opcionais que vêm **ativas** por default. Exemplo real do CA `81150`: as fases ativas são 10, não 8 — inclui `(opcional) Refação Interna 82182` e `(opcional) Ajuste Cliente 82175`. Não montar o `flow` do `create_task` a partir deste resumo; sempre puxar `get_detailed_task_type` e filtrar `active=1`.
>
> **Verificados em 2026-08-12** (fases ativas + executor default + effort):
> - **CA `81150`** — effort 360, daysToStart 3. Ativas: Backlog `82168` Fabio · Briefing+Copy `82169` Fabio · Em produção-Design `82181` **André** · Revisão IA/QA `82179` **André** · Aprovação Cientista `82178` Fabio · Aprovação Cliente `82177` **André** · Refação Interna `82182` **André** · Ajuste Cliente `82175` **André** · Go Live `82174` Fabio · Monitoramento `82172` Fabio
> - **PRI-A `81136`** — effort 240, daysToStart 3. Ativas (todas Fabio): Backlog `82168` · Coleta de Evidências `82170` · Análise Cientista `82171` · Planejamento `82183` · Revisão IA/QA `82179` · Monitoramento `82172`
> - **M-CAMP `81154`** — effort 120, daysToStart 2. Ativas (todas Fabio): Backlog `82168` · Análise Cientista `82171` · Execução Técnica `82180` · Revisão IA/QA `82179` · Monitoramento `82172`
>
> Pendentes de verificação: LP `81149`, DP `81142`, RV `81151`, IMP `81140`, MAN `81139`, BN `81152`, M-CRM `81153`.

**Fases Prisma (phaseId global):**
Backlog `82168` → Coleta Evidências `82170` → Briefing+Copy `82169` → Análise Cientista `82171` → Em produção-Design `82181` → Execução Técnica `82180` → Revisão IA/QA `82179` → Aprovação Cientista `82178` → Aprovação Cliente `82177` → (opcional) Refação Interna `82182` → (opcional) Ajuste Cliente `82175` → Configuração `82176` → Go Live/Publicação `82174` → Divulgação `82175` → Monitoramento `82172` → Planejamento `82183` → Desenvolvimento Relatório `82184` → Reunião `82185`

---

## Tipos de tarefa (Padrão Colli&Co Oficial)

89 tipos com sigla limpa `[NN][SIGLA]`. Workflow base: **Padrão Colli&Co (Oficial)** (workflow_id 3535). **Legado — usar Prisma para tasks novas.**

> **Fluxo (fases) de cada tipo:** ver `flows.md` (gerado 2026-06-02 — fases reais por tipo + dicionário `nome da fase → phaseId`). Usado pela `/ekyte-task` pra trocar responsável de etapa.

Quando uma sigla aparece em mais de um tipo (ex: `CA` em 2, `CRM` em 12), IA **deve** desambiguar antes de criar.

### Mais usados (ordem alfabética por sigla)

| Sigla | task_type_id | Nome | Notas |
|---|---|---|---|
| AC | `38179` | Ajustes Criativo Ads/Copywriting | |
| ACRM | `34436` | Acompanhamento de CRM | |
| AN | `37680` | Análise de dados / Projeção | |
| AP | `37681` | Aprovação, alteração e publicação ªQ | |
| ATM | `34438` | Automação de e-mail marketing | |
| ATWPP | `32813` | Atendimento/comunicação WhatsApp | |
| AUX | `37921` | Análise UX | (também 74563 = Diagnóstico CRO/SEO) |
| AV | `40142` | Confecção de Avatar WhatsApp | |
| **CA** | `29740` | **Criativo Ads** | (variante V4S: `37979`) — **SLA 11 dias** |
| CB | `33949` | Configuração do Copybase | |
| CD | `37683` | Solicitação de Cardápio | |
| CJ | `29732` | Copy Jornada | (variante franchising: `68564`) |
| **CP** | `38177` | **Solicitação ao Copy** | |
| CRM | `34435` | Configuração de CRM | (várias variantes numeradas, ver desambiguação) |
| DC | `38176` | Desdobramento de Criativo Ads | |
| DE | `38181` | Desdobramento de E-mail Marketing | |
| DLP | `38178` | Desdobramento de Landing Page | |
| EA | `34454` | Entrega avulsa | |
| EB | `29733` | E-book | |
| EG | `37685` | Solicitação de Embalagens | |
| EKT | `34483` | Organização/Acompanhamento Ekyte | |
| EM | `29734` | E-mail Marketing | |
| ENG | `43411` | Solicitação Eng. Dados | |
| EV | `29730` | Edição de Vídeo | |
| **GP** | `30064` | **Solicitação ao GP** | (variantes: `69969` Preenchimento Growth Pack, `61553` Implementação Growthpack) — **SLA 1 dia** |
| IE | `59457` | Iniciativa estratégica | |
| KV | `29748` | Key Visual | |
| **LP** | `29727` | **Landing Page** | **SLA 7 dias** |
| MT | `29728` | Motion | (variante XP/Trader: `44689`) |
| OCA | `61585` | Otimização Criativo Ads | |
| OFF | `30082` | Materiais offline | |
| OTM | `34442` | Otimização de campanhas | |
| OV | `30083` | Overdelivery | |
| OVERVIEW | `70418` | Overview Diário das Contas | |
| PA | `32247` | Pauta xªQ | |
| PAPP | `37916` | Produção InApp | |
| **PC** | `34482` | **Publicação de campanhas** | **SLA mesmo dia** |
| PI | `37914` | Produção IS | |
| PMS | `37999` | Produção Marketing Screen | |
| PP | `32246` | Pré-pauta xªQ | |
| PPSH | `37917` | Produção Push | |
| PPT | `30063` | PPT | |
| PSMS | `37919` | Produção SMS | |
| PWPP | `37918` | Produção WhatsApp | |
| RE | `34441` | Reuniões externas | |
| REL | `34439` | Preenchimento de relatórios | |
| RI | `34440` | Reuniões internas | (variantes: `55561` DCC, `55562` Atualização UCM/DCC) |
| **RV** | `37666` | **Roteiro de vídeo** | **SLA 7 dias** |
| SE | `34437` | Sales enablement | |
| SL | `37688` | Social Listening | |
| SM | `32249` | Social Media post | (variante Apsen: `38067`) |
| SV | `29745` | Script de Vendas | |
| TRK | `34484` | Traqueamento Integração | |
| WPP | `38781` | Régua WPP | |

### Siglas com múltiplos tipos (desambiguação obrigatória)

- **CA**: `29740` (V4 Colli&Co padrão) | `37979` (V4S)
- **CJ**: `29732` (V4 Colli&Co) | `68564` (franchising)
- **GP**: `30064` (Solicitação ao GP) | `69969` (Preenchimento Growth Pack) | `61553` (Implementação Growthpack)
- **MT**: `29728` (V4 Colli&Co) | `44689` (XP/Trader)
- **AUX**: `37921` (Análise UX) | `74563` (Diagnóstico CRO/SEO)
- **CRM**: `34435`, `48142`, `46788`, `44815`, `44818`, `44820`, `44821`, `46791`, `44822`, `44823`, `44827`, `45001` (12 variantes — sempre perguntar qual)
- **PMM**: `40771`, `40772`, `40774`, `40775`, `40776`, `40777`, `40821`, `40822`, `40823`, `40824`, `40825`, `40826`, `40827`, `40828` (14 variantes)
- **RI**: `34440`, `55561`, `55562`
- **SM**: `32249`, `38067`

### Demandas WEB (tipo "Personalizada")

Quando o pedido é **demanda Web**, **não** existe tipo padrão "WEB" no catálogo. Usar tipo **Personalizada** + prefixar `[WEB]` no título.

Atualmente não temos `task_type_id` confirmado pra tipo "Personalizada". **Primeira demanda WEB** → IA deve perguntar pelo task_type_id e salvar aqui.

| Tipo | task_type_id | Nota |
|---|---|---|
| Personalizada (WEB) | `1` | Tipo "Personalizada" oficial do Ekyte. Sempre prefixar `[WEB]` no título. Confirmado pelo Fabio 2026-05-04. |

