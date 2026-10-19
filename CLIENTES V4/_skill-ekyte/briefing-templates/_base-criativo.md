# Base Criativo — Compartilhado por CA, LP, RV (e outros criativos)

Bloco-base com perguntas estruturais comuns aos briefings de produção criativa. **Importado** pelos templates `CA.md`, `LP.md`, `RV.md`. Não usar isolado.

Vem **depois** do `_header-universal.md` e **antes** das seções específicas da sigla.

---

## Markdown do bloco

```
1️⃣ DIRECIONAMENTO DA CAMPANHA

Tema/Produto: {{tema_produto}}
Motivação: {{motivacao}}
Condição/Oferta: {{condicao_OR_omit}}
Observações Relevantes: {{observacoes_OR_omit}}

2️⃣ OBJETIVO

{{objetivo_marcado}}

3️⃣ PÚBLICO — NÍVEL DE CONSCIÊNCIA

{{nivel_consciencia_marcado}}

4️⃣ FAIXA ETÁRIA

{{faixa_etaria_marcada}}

5️⃣ SEXO

{{sexo_marcado}}

6️⃣ GANCHOS

{{ganchos_marcados}}
```

---

## Perguntas ativas — em lote, antes do preview

A `/ekyte-briefing` faz **uma rodada única** ao Fabio com todas estas perguntas. Resposta esperada: linha curta por pergunta, em texto livre ou números separados por vírgula.

### 1. Tema/Produto
> **1) Tema/Produto:** Qual é a temática ou o produto da campanha?

Aceita texto livre. Se Fabio já mencionou no input ("foco em remarketing produto X"), **pré-preencher** e perguntar só "está certo? quer adicionar algo?".

### 2. Motivação
> **2) Motivação:** Qual é a finalidade da campanha?

Aceita texto livre. Pode vir do input.

### 3. Condição/Oferta
> **3) Condição/Oferta** (opcional): Tem oferta? Desconto, brinde, frete grátis, condição especial?

Se resposta vazia/"não", omitir linha no briefing final.

### 4. Observações relevantes
> **4) Observações relevantes** (opcional): Algo crítico que precisa ser respeitado? (ex: restrição visual, deadline interno, aprovação de stakeholder)

Se vazia, omitir.

### 5. Objetivo
> **5) Objetivo da campanha:**
> 1) Alcance
> 2) Contato no WhatsApp
> 3) Geração de cadastro
> 4) Visualização de vídeo
> 5) Remarketing
> 6) Compra
>
> Pode marcar mais de um (ex: 1,5,6).

Renderizar como lista de itens marcados:
```
• Remarketing
• Compra
```

### 6. Público — Nível de Consciência
> **6) Público — Nível de Consciência:**
> 1) Inconsciente
> 2) Consciente do problema
> 3) Consciente da solução
> 4) Consciente do produto
> 5) Totalmente Consciente
>
> Marca um ou mais.

### 7. Faixa Etária
> **7) Faixa Etária:**
> 1) 18-24
> 2) 25-34
> 3) 35-44
> 4) 45-54
> 5) 55-64
> 6) 65+
>
> Marca um ou mais.

### 8. Sexo
> **8) Sexo:**
> 1) Masculino
> 2) Feminino
> 3) Ambos

### 9. Ganchos
> **9) Ganchos** (escolha 1-3):
> 1) Dor x Prazer
> 2) Especificidade
> 3) Curiosidade
> 4) Escassez
> 5) Medo da Perda
> 6) Autoridade
> 7) Novidade
> 8) Oportunidade

---

## Pré-preenchimento via NotebookLM

Antes de fazer as perguntas, a `/ekyte-briefing` chama `/cs-notebooklm-consulta-cliente` com perguntas dirigidas pelo tipo de criativo:

1. Quais ofertas o cliente já realizou em campanhas anteriores? Cite trecho e fonte. Se não houver, 'NAO ENCONTRADO'.
2. Qual é o ICP/avatar principal documentado? Faixa etária, sexo, nível de consciência? Cite. Se não houver, 'NAO ENCONTRADO'.
3. Quais ganchos / dores principais aparecem nos materiais do cliente? Cite trechos. Se não houver, 'NAO ENCONTRADO'.
4. Existe restrição documentada de imagem/copy/oferta para esse cliente? Cite. Se não houver, 'NAO ENCONTRADO'.
5. Qual o tom de voz da marca segundo os materiais? Cite. Se não houver, 'NAO ENCONTRADO'.

A síntese volta e a skill **pré-preenche** o que conseguir antes de mostrar as perguntas. Quando pré-preencher, marcar visualmente: `[sugerido pelo NotebookLM, confirma?]`.

---

## Conversão pra HTML

Cada linha vira `<div>`. Cada item de lista marcada vira `<div>• item</div>`. Títulos de seção em CAIXA ALTA + emoji numérico, envolvidos em `<strong>`. Sem `<ul>`/`<li>`/`<h>`.

Exemplo de renderização:

```html
<div><strong>1️⃣ DIRECIONAMENTO DA CAMPANHA</strong></div>
<div><br></div>
<div>Tema/Produto: Remarketing produto X</div>
<div>Motivação: Reativar carrinho abandonado de tickets &gt; R$ 500</div>
<div><br></div>
<div><strong>2️⃣ OBJETIVO</strong></div>
<div><br></div>
<div>• Remarketing</div>
<div>• Compra</div>
```
