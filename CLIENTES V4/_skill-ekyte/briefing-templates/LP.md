# Template LP — Landing Page

Sigla: `LP` — task_type_id: `29727`. SLA: 7 dias.

Briefing pra produção de **landing page completa**. Mais profundo que CA (envolve copy + design + tráfego + estrutura de formulário).

---

## Composição do briefing final

```
[1] _header-universal.md   ← Drive, NotebookLM, Referência, KV
[2] _base-criativo.md      ← Direcionamento, Objetivo, Público, Faixa, Sexo, Ganchos
[3] LP.md (este)           ← Tipo de LP + Copy + Design + Estrutura + Tráfego
```

---

## Markdown específico de LP

```
7️⃣ TIPO DE LANDING PAGE

{{tipo_lp_marcado}}

8️⃣ COPYWRITING

Modelo de documento: {{link_doc_copy_OR_omit}}
Headline de referência: {{headline_OR_omit}}
Subheadline de referência: {{subheadline_OR_omit}}
Tom de voz: {{tom_de_voz}}
Análise de Performance: {{link_analise_OR_omit}}

9️⃣ DESIGN

KV: ver bloco header
Direcionamento visual: {{direcionamento_visual_OR_omit}}
Análise de Performance: {{link_analise_OR_omit}}

🔟 ESTRUTURA DA PÁGINA

{{estrutura_OR_perguntar_no_preview}}

1️⃣1️⃣ FORMULÁRIO

{{formulario_descricao_OR_omit}}

1️⃣2️⃣ TRÁFEGO

Landing Page existente (se reformulação): {{lp_atual_OR_omit}}
Direcionamento de tráfego: {{tagueamento_e_utm_OR_omit}}

1️⃣3️⃣ APROVAÇÃO

{{aprovacao_OR_padrao}}
```

---

## Perguntas ativas — específicas de LP

### 10. Tipo de Landing Page
> **10) Tipo de Landing Page** (escolhe um):
> 1) LP de Captação
> 2) LP de Obrigado
> 3) LP de Vendas
> 4) Carta de Vendas
> 5) LP Institucional
> 6) LP tipo catálogo
> 7) Outro: ___

### 11. Modelo de documento de copy (opcional)
> **11) Modelo de documento de copy** (opcional): Tem link de documento de copy compartilhado com o copywriter? (ex: Google Docs)

Se vazio, omitir.

### 12-14. Headline / Subheadline / Tom de voz
Mesmas perguntas do `CA.md` itens 12, 13, 14.

### 15. Direcionamento visual (opcional)
Mesma do `CA.md` item 19.

### 16. Estrutura da página
> **16) Estrutura da página:** Lista as seções desejadas em ordem (ex: Hero / Prova social / Mix de produtos / Formulário / Rodapé). Se quiser que a skill sugira com base no NotebookLM, diga "sugira".

Se "sugira": skill propõe 5-7 seções padrão pro tipo de LP escolhido + ajusta com sintese do NotebookLM. Fabio confirma.

### 17. Formulário
> **17) Formulário** (se aplicável): Tem qualificação progressiva? Quantas etapas? Campos obrigatórios? (resposta em texto livre)

Se a LP é de Obrigado/Institucional/Vendas e não tem formulário, omitir bloco inteiro.

### 18. LP atual (se reformulação)
> **18) LP atual** (se reformulação): Cole o link da LP que está sendo substituída. Se é LP nova do zero, diga "nova".

Se "nova", omitir linha.

### 19. Tagueamento e UTMs
> **19) Tagueamento e UTMs**: Comportamento de eventos (ex: "Disparar conversão só pra MQL", "GA4 + Meta Pixel padrão")

Se Fabio disser "padrão", usar texto genérico: `Implementar Meta Pixel + Google Tag Manager. Configurar evento de conversão conforme objetivo da campanha. UTMs obrigatórias em todas as origens de tráfego.`

### 20. Aprovação
> **20) Aprovação:** Aprovação interna (V4) e/ou cliente antes de publicar?

Default: `Aprovação interna obrigatória. Aprovação com cliente obrigatória antes da publicação.`

---

## Pré-preenchimento via NotebookLM (extras pra LP)

Além das 5 perguntas padrão do `_base-criativo.md`, a `/ekyte-briefing` pode adicionar:

6. Existe conteúdo institucional ou tom de comunicação documentado pra esse cliente? Cite. Se não, 'NAO ENCONTRADO'.
7. Quais elementos de prova social (parceiros, números, depoimentos) o cliente já comunica? Cite. Se não, 'NAO ENCONTRADO'.

(Limite de 5 ainda vale — priorizar essas se faltar info de avatar/oferta.)

---

## Conversão pra HTML

Padrão usual. Numerais 🔟 1️⃣1️⃣ 1️⃣2️⃣ 1️⃣3️⃣ são Unicode válidos e renderizam.
