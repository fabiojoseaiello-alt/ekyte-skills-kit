# Template CA — Criativo Ads

Sigla: `CA` — task_type_id padrão: `29740` (variante V4S: `37979`).

Briefing pra produção de **criativos de tráfego pago** (Meta, Google Display, etc). Foco em headline, copy, KV, formato.

---

## Composição do briefing final

```
[1] _header-universal.md   ← Drive, NotebookLM, Referência, KV (KV obrigatório se aplicável)
[2] _base-criativo.md      ← Direcionamento, Objetivo, Público, Faixa, Sexo, Ganchos
[3] CA.md (este)           ← Copywriting + Design (variante CA)
```

---

## Markdown específico de CA

```
7️⃣ COPYWRITING

Quantidade de peças: {{qtd_pecas}}
Tema central: {{tema_central}}
Headline de referência: {{headline_OR_omit}}
Subheadline de referência: {{subheadline_OR_omit}}
Tom de voz: {{tom_de_voz}}
Análise de Performance: {{link_analise_OR_omit}}

8️⃣ DESIGN

Formato dos criativos: {{formato_marcado}}
KV da campanha: ver bloco header
Direcionamento visual: {{direcionamento_visual_OR_omit}}
Análise de Performance: {{link_analise_OR_omit}}

9️⃣ TRÁFEGO

Plataforma de veiculação: {{plataforma}}
Landing Page de destino: {{lp_link_OR_omit}}
```

---

## Perguntas ativas — específicas de CA

Vêm depois das perguntas do `_base-criativo.md` (1 a 9). Continuação:

### 10. Quantidade de peças
> **10) Quantidade de peças:** Quantos criativos? (a `[NN]` do título já tem a info, mas confirma se distribui igual ou se vai variar)

Pré-preencher com NN do título.

### 11. Tema central
> **11) Tema central das copies:** Qual o ângulo principal? (1 frase)

### 12. Headline de referência
> **12) Headline de referência** (opcional): Tem uma frase-âncora que o copy deve seguir?

Se vazio, omitir.

### 13. Subheadline
> **13) Subheadline de referência** (opcional)

Se vazio, omitir.

### 14. Tom de voz
> **14) Tom de voz:** Direto / Formal / Provocativo / Educativo / Aspiracional / Outro?

Pré-preencher via NotebookLM (síntese geralmente captura tom de voz da marca).

### 15. Formato dos criativos
> **15) Formato dos criativos** (marca um ou mais):
> 1) Feed estático
> 2) Feed carrossel
> 3) Stories
> 4) Reels / Vídeo curto
> 5) Display
> 6) Outro: ___

### 16. Plataforma
> **16) Plataforma de veiculação** (marca um ou mais):
> 1) Meta (Facebook + Instagram)
> 2) Google (Display, Demand Gen)
> 3) TikTok Ads
> 4) LinkedIn Ads
> 5) Outro: ___

### 17. LP de destino (opcional)
> **17) LP de destino** (opcional): Tem link da página pra qual o tráfego vai? Cole aqui ou diga "ainda não tem".

Se "ainda não tem", colocar `<<sem LP definida — confirmar com gestor de tráfego antes de publicar>>` em destaque.

### 18. Link de análise de performance (opcional)
> **18) Análise de Performance** (opcional): Tem link da última análise do Cientista? (ex: doc/sheet com aprendizados de campanha anterior)

Se vazio, omitir.

### 19. Direcionamento visual (opcional)
> **19) Direcionamento visual** (opcional): Algo específico sobre estética? (ex: "fotos com pessoas reais", "evitar cores frias", "manter paleta da última black")

Se vazio, omitir.

---

## Conversão pra HTML

Mesmo padrão dos outros: `<div>` por linha, `<div><br></div>` em branco, `<a target="_blank">` em links, títulos em `<strong>` CAIXA ALTA.

Exemplo de seção 7️⃣ renderizada:

```html
<div><strong>7️⃣ COPYWRITING</strong></div>
<div><br></div>
<div>Quantidade de peças: 9</div>
<div>Tema central: Reativação de carrinho abandonado em ticket alto</div>
<div>Headline de referência: "Voltou a pensar nele? A gente também."</div>
<div>Tom de voz: Direto e empático</div>
```
