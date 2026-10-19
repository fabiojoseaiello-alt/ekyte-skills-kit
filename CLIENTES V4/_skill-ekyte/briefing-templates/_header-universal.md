# Header Universal — Bloco fixo de todo briefing

Este bloco vai no **topo** de **todo** briefing montado pela `/ekyte-briefing`, independente da sigla. Vem logo após o título do briefing (`BRIEFING — <CLIENTE> — <TIPO>`) e antes do conteúdo específico do template da sigla.

---

## Markdown do bloco (template a preencher)

```
🔗 ATIVOS DA CAMPANHA

Drive do Cliente: {{drive_link}}
NotebookLM: {{notebook_link}}
Referência: {{referencia_link_OR_omit}}
KV da campanha: {{kv_link_OR_omit_se_nao_aplicavel}}
```

---

## Regras de preenchimento

### `{{drive_link}}` — sempre obrigatório

Lookup em `clientes/_skill-ekyte/drives.md`. 
- Se cliente está mapeado: injeta direto.
- Se cliente não tem (`_sem Drive ainda_`): perguntar no preview e oferecer `/ekyte-briefing-refresh` pra persistir.

### `{{notebook_link}}` — sempre obrigatório

Ler `clientes/<cliente>/CLAUDE.md`, achar bloco `## NotebookLM`, extrair URL/ID. Mostrar como link clicável (ex: `https://notebooklm.google.com/notebook/<id>`).
- Se cliente não tem NotebookLM cadastrado: avisar que `/cs-notebooklm-consulta-cliente` não vai rodar e seguir sem síntese (briefing fica mais raso).

### `{{referencia_link_OR_omit}}` — opcional

Vem do input do Fabio ("usa essa ref: <link>") OU pergunta ativa no preview. **Se não houver, omitir a linha inteira.** Não escrever "Referência: nenhuma" — fica feio.

### `{{kv_link_OR_omit_se_nao_aplicavel}}` — opcional, **só pra siglas criativas**

Aplicável **só** para: CA, LP, RV, KV, MT, EV, DC, DLP, DE, AC, OCA, SM, EM, PAPP, PI, PMS, PPSH, PSMS, PWPP. Para outras siglas (PC, AN, CRM, RI, REL, OVERVIEW, etc), **omitir a linha inteira**.

Vem do input ("usa esse KV: <link>") OU pergunta ativa. Se não houver e a sigla é criativa, perguntar; se Fabio disser "sem KV específico", omitir.

---

## Conversão pra HTML (Quill/Ekyte)

Cada linha vira `<div>...</div>`. Linha vazia entre blocos vira `<div><br></div>`. Links viram `<a href="..." target="_blank">URL</a>`. Título da seção em CAIXA ALTA + emoji 🔗 (UI do Ekyte não usa `<h>`, hierarquia é convenção visual).

Exemplo final renderizado:

```html
<div><strong>🔗 ATIVOS DA CAMPANHA</strong></div>
<div><br></div>
<div>Drive do Cliente: <a href="https://drive.google.com/..." target="_blank">https://drive.google.com/...</a></div>
<div>NotebookLM: <a href="https://notebooklm.google.com/..." target="_blank">https://notebooklm.google.com/...</a></div>
<div>KV da campanha: <a href="https://..." target="_blank">https://...</a></div>
<div><br></div>
```

(Linha de "Referência" omitida porque vazia. Linha de KV presente porque sigla é criativa.)
