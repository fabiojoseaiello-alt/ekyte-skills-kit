# Fluxos verificados — Projeto Prisma (workflow 22012)

Extraído via `get_detailed_task_type` em **2026-08-12**. Use este arquivo para montar o array `flow` do `create_task`, não o "Fluxo resumido" do `cache.md` — aquele omite as fases opcionais que vêm **ativas** por default.

## Executores

| Pessoa | userId (GUID) |
|---|---|
| Fabio José Aiello Junior | `a2f17bce-eed7-4ea6-beda-9efd449010ec` |
| André Emanuel | `aadf78c4-e642-450b-9ba1-fde2a0cab489` |

Todos os tipos usam `allocationType: 10` (Agile → exige `phaseDueDate`).

---

## Família "produção" — CA, LP (verificados idênticos)

10 fases ativas. É a única família com André como executor default.

| seq | phaseId | Fase | Executor |
|---:|---:|---|---|
| 1 | `82168` | Backlog | Fabio |
| 2 | `82169` | Briefing + Copy | Fabio |
| 6 | `82181` | Em produção - Design | **André** |
| 8 | `82179` | Revisão IA / QA | **André** |
| 9 | `82178` | Aprovação Cientista | Fabio |
| 10 | `82177` | Aprovação Cliente | **André** |
| 11 | `82182` | (opcional) Refação Interna | **André** |
| 12 | `82175` | (opcional) Ajuste Cliente | **André** |
| 14 | `82174` | Go Live / Publicação | Fabio |
| 17 | `82172` | Monitoramento | Fabio |

Inativas (`active=0`): `82170`, `82171`, `82183`, `82180`, `82176`, `82184`, `82185`.

| Tipo | ID | effort | daysToStart |
|---|---|---:|---:|
| CA — Criativos Ads | `81150` | 360 (6h) | 3 |
| LP — Landing Page | `81149` | 360 (6h) | 3 |
| RV — Roteiro de Vídeo | `81151` | 360 (6h) | 3 |
| DP — Design Performance | `81142` | 360 (6h) | 3 |
| BN — Banners | `81152` | _a verificar_ | _a verificar_ |

Os quatro verificados (CA, LP, RV, DP) são **byte-idênticos** no conjunto de fases ativas e nos executores. Só o `description` (template de briefing) difere entre eles.

---

## Família "manutenção" — M-CAMP, MAN (verificados idênticos)

5 fases ativas, todas Fabio.

| seq | phaseId | Fase | Executor |
|---:|---:|---|---|
| 1 | `82168` | Backlog | Fabio |
| 4 | `82171` | Análise Cientista | Fabio |
| 7 | `82180` | Execução Técnica | Fabio |
| 8 | `82179` | Revisão IA / QA | Fabio |
| 17 | `82172` | Monitoramento | Fabio |

| Tipo | ID | effort | daysToStart |
|---|---|---:|---:|
| M-CAMP — Manutenção Campanhas | `81154` | 120 (2h) | 2 |
| MAN — Manutenção Técnica | `81139` | 120 (2h) | 2 |
| M-CRM — Manutenção CRM | `81153` | _a verificar_ | _a verificar_ |

---

## PRI-A — Análise e Direcionamento `81136`

effort 240 (4h), daysToStart 3. 6 fases ativas, todas Fabio.

| seq | phaseId | Fase | Executor |
|---:|---:|---|---|
| 1 | `82168` | Backlog | Fabio |
| 3 | `82170` | Coleta de Evidências | Fabio |
| 4 | `82171` | Análise Cientista | Fabio |
| 5 | `82183` | Planejamento | Fabio |
| 8 | `82179` | Revisão IA / QA | Fabio |
| 16 | `82172` | Monitoramento | Fabio |

---

## IMP — Implementação Técnica `81140`

effort 480 (8h), daysToStart 7. 8 fases ativas, todas Fabio.

| seq | phaseId | Fase | Executor |
|---:|---:|---|---|
| 1 | `82168` | Backlog | Fabio |
| 5 | `82183` | Planejamento | Fabio |
| 7 | `82180` | Execução Técnica | Fabio |
| 8 | `82179` | Revisão IA / QA | Fabio |
| 9 | `82178` | Aprovação Cientista | Fabio |
| 10 | `82177` | Aprovação Cliente | Fabio |
| 14 | `82174` | Go Live / Publicação | Fabio |
| 16 | `82172` | Monitoramento | Fabio |

---

## Pendentes de verificação

`BN 81152`, `M-CRM 81153`, `PCP 81138`, `ATD 81141`, e os tipos de reunião `RI 81145` / `RE 81146`.

---

## Família "produção" — nomes de tipo (para o preview)

| ID | Nome completo no Ekyte |
|---|---|
| `81150` | `[00][CA] Projeto Prisma \| Criativos Ads` |
| `81149` | `[00][LP] Projeto Prisma \| Landing Page` |
| `81151` | `[00][RV] Projeto Prisma \| Roteiro de Video` |
| `81142` | `[00][DP] Projeto Prisma \| Design Performance` |
| `81136` | `[00][PRI-A] Projeto Prisma \| Analise e Direcionamento` |
| `81154` | `[00][M-CAMP] Projeto Prisma \| Manutencao Campanhas` |
| `81139` | `[00][MAN] Projeto Prisma \| Manutencao Tecnica` |
| `81140` | `[00][IMP] Projeto Prisma \| Implementacao Tecnica` |

**Observação:** `IMP 81140`, `MAN 81139` e `DP 81142` têm `description` genérica ("Tipo do Projeto Prisma criado para o piloto Cientista + Designer. Fluxo enxuto: X") — não trazem template de briefing. Os outros cinco trazem template completo, que deve ser a base do `description` da task.
