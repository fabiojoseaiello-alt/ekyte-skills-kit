# Template — `publicos-cache.md` por cliente

Este é o **layout-padrão** do arquivo `clientes/<cliente>/publicos-cache.md`. Cada cliente que já teve público consultado no NotebookLM tem o seu, com 1 bloco por linha/categoria de produto.

**Granularidade:** linha/categoria (não SKU). Ex: "Colchões adultos", não "Linha Premium".

**TTL:** 90 dias a contar da `ult_consulta`. Cache fica válido até `ult_consulta + 90d`.

**Aviso preventivo:** quando idade do cache ≥ 75 dias (83% do TTL), a `/ekyte-briefing` mostra no preview: `⚠️ cache de público com 78d — quer atualizar antes de seguir?`. Fabio responde sim/não. Sem resposta = segue com o cache atual.

**Invalidação manual:** apagar o bloco da linha alvo OU rodar `/ekyte-publico-refresh <cliente> <linha>` (a ser implementado depois — por enquanto, apagar o bloco força MISS na próxima consulta).

---

## Formato do arquivo

```markdown
# Cache de Públicos — <Cliente>

Indexado por linha/categoria de produto. Popula automaticamente pela `/ekyte-briefing` quando a primeira task de uma linha consulta o NotebookLM. Reusado por todas as tasks subsequentes da mesma linha até o TTL (90d) expirar.

Última escrita: 2026-05-14

---

## <Nome da linha — ex: Colchões adultos>

- **ult_consulta:** 2026-05-14
- **expira:** 2026-08-12
- **fonte:** NotebookLM <id-do-notebook>

**Avatar:**
30-55 anos, classe B/C, mora em apartamento ou casa própria. Trabalha em escritório, tem dor de coluna recorrente. Decisão de compra dividida com cônjuge, ciclo longo (pesquisa 30-60 dias antes de comprar). Valoriza durabilidade, certificações (INMETRO, ABNT) e atestados médicos.

**Faixa etária dominante:** 35-44, 45-54 (secundário: 25-34)

**Sexo:** Ambos (leve viés feminino na decisão final)

**Nível de consciência:** 2 (consciente do problema — dor de coluna), 3 (consciente da solução — colchão de qualidade), 4 (consciente do produto — pesquisando marca)

**Ganchos com tração documentada:**
- Dor x Prazer (dor de coluna → noite restauradora)
- Autoridade (certificações, fisioterapeutas recomendam)
- Especificidade (mola ensacada, densidade, anos de garantia)

**Ofertas que já rodaram:**
- Frete grátis Brasil todo (sempre)
- 10x sem juros (sempre)
- Brinde travesseiro NASA em campanhas sazonais

**Restrições documentadas:**
- Nunca usar "barato" — posicionamento é qualidade
- Não comparar com concorrente nomeado
- Imagens precisam mostrar pessoa real dormindo (não 3D)

**Tom de voz:**
Acolhedor, técnico quando necessário, evita gírias. Trata cliente por "você" mas com respeito (não "tu" / "cara").

---

## <Próxima linha — ex: Alfa Baby>

- **ult_consulta:** 2026-04-22
- **expira:** 2026-07-21
- **fonte:** NotebookLM <id-do-notebook>

**Avatar:**
[...]

[etc]
```

---

## Como a `/ekyte-briefing` consome

Passo entre 3 (cache de sessão NotebookLM) e 4 (invocar /cs-notebooklm):

1. **Identificar a linha** a partir do input/título da task. Heurística:
   - Tem produto explícito no título? (`Linha Premium`, `Alfa Baby`) → mapear pra linha (Alfa Baby = linha "Alfa Baby"; Linha Premium = linha "Colchões adultos")
   - Sem produto explícito mas sinal contextual (`remarketing produto X`)? → perguntar ao Fabio qual linha
   - Sem sinal nenhum? → linha "Geral" (cliente sem segmentação por linha — ex: Cliente Gama, Cliente Delta)

2. **Abrir** `clientes/<cliente>/publicos-cache.md`. Se não existe, MISS automático.

3. **Buscar bloco** com header `## <Nome da linha>`. Match case-insensitive, ignorando acentos.

4. **Decidir hit/miss/stale:**
   - **HIT** (idade < 75d): usa direto. Pré-preenche campos 3-9 do `_base-criativo.md` com os valores do cache. Marca no preview: `[do cache: <linha> · 12d]`.
   - **STALE** (75d ≤ idade < 90d): usa o cache **mas** mostra aviso no preview: `⚠️ cache de <linha> com 78d, expira em 12d — quer atualizar antes de seguir?`. Sim = força MISS path. Não/sem resposta = HIT silencioso.
   - **MISS** (idade ≥ 90d OU bloco inexistente OU arquivo inexistente): segue fluxo normal — invoca `/cs-notebooklm-consulta-cliente`, monta briefing, e **após sucesso** escreve o bloco no `publicos-cache.md` do cliente (cria arquivo se preciso).

5. **No modo Inline Rápido da `/ekyte-task` (lote 3-5):**
   - HIT → usa cache, **não consulta NotebookLM** (era o ganho original do modo inline). Briefing inline fica completo sem custo extra.
   - MISS/STALE-com-update → invoca `/cs-notebooklm-consulta-cliente` **só com a pergunta de público** (avatar/faixa/sexo/consciência/ganchos), não as 5 padrão. ~1 min em vez de ~5. Após resposta, popula cache.

---

## Como escrever no cache (após consulta NotebookLM bem-sucedida)

A `/ekyte-briefing` chama uma função `popular_cache_publico(cliente, linha, sintese)`:

1. Abre/cria `clientes/<cliente>/publicos-cache.md`.
2. Se já existe bloco com `## <linha>`: substitui inteiro.
3. Se não existe: adiciona ao final.
4. Sempre atualiza o header "Última escrita: YYYY-MM-DD".
5. Sintese mínima esperada (se NotebookLM disse 'NAO ENCONTRADO' em algum campo, **não fabricar** — escreve `_não documentado_` no campo e deixa pra pergunta ativa):

```
Avatar: <texto narrativo curto, 2-4 linhas>
Faixa etária dominante: <lista de bins>
Sexo: <Masculino|Feminino|Ambos>
Nível de consciência: <lista de níveis 1-5 com label>
Ganchos com tração documentada: <lista de ganchos>
Ofertas que já rodaram: <lista> OU _não documentado_
Restrições documentadas: <lista> OU _não documentado_
Tom de voz: <texto curto> OU _não documentado_
```

---

## Clientes que já têm cache (manter atualizado por convenção)

Quando criar cache pra um cliente novo, adicionar nesta lista (e em `MEMORY.md` se for marco):

- _nenhum cliente populado ainda — primeiro uso da feature_

---

## Guardrails

1. **Nunca fabricar.** Se síntese do NotebookLM silenciou um campo, gravar `_não documentado_`. Não preencher por inferência.
2. **Linha "Geral" é fallback, não default.** Se o cliente realmente tem segmentação (Alfa, Cliente Beta, Cliente Kappa), forçar a identificação da linha antes de cair em "Geral".
3. **Não compartilhar cache entre clientes**, mesmo quando NotebookLM é compartilhado (Alfa+Beta). Cada cliente tem seu arquivo — público é por marca, não por notebook.
4. **Não cachear público se MISS de NotebookLM** (cliente sem notebook cadastrado): nesse caso o briefing vai pra pergunta ativa pura, sem cache.
