# Template PC — Publicação de Campanha

Sigla: `PC` — task_type_id: `34482`. SLA: mesmo dia.

Briefing pra **publicação/subida de campanha** no gerenciador (Meta Ads, Google Ads, etc). Operacional. **Não usa** `_base-criativo.md` (não é briefing criativo). Usa **só** `_header-universal.md` + este.

---

## Composição do briefing final

```
[1] _header-universal.md   ← Drive, NotebookLM, Referência, KV (KV omitido — PC não é criativo)
[2] PC.md (este)           ← Briefing completo de publicação
```

Nota: como PC não é sigla criativa, **omitir a linha de KV** no `_header-universal.md`. Drive, NotebookLM e Referência continuam.

---

## Markdown específico de PC

```
1️⃣ BRIEFING GERAL

Objetivo da Campanha: {{objetivo}}
Plataformas de Publicação: {{plataformas_marcadas}}

2️⃣ SEGMENTAÇÃO DE PÚBLICO

Dados Demográficos:
• Idade: {{idade}}
• Sexo: {{sexo}}
• Localização: {{localizacao}}
• Renda: {{renda_OR_omit}}
• Ocupação: {{ocupacao_OR_omit}}

Dados Psicográficos:
• Interesses: {{interesses_OR_omit}}
• Comportamento de compra: {{comportamento_OR_omit}}
• Hobbies: {{hobbies_OR_omit}}
• Valores: {{valores_OR_omit}}

Custom Audiences:
• Públicos personalizados: {{custom_audiences_OR_omit}}
• Públicos semelhantes (lookalike): {{lookalikes_OR_omit}}

3️⃣ ORÇAMENTO

Total da campanha: {{orcamento_total}}
Distribuição: {{distribuicao}}

4️⃣ CRIATIVOS

Link dos criativos: {{link_criativos}}
Formatos de Anúncio: {{formatos_marcados}}

5️⃣ COPYS E HEADLINES

Mensagem principal: {{mensagem_principal}}
CTA: {{cta}}

6️⃣ KV (KEY VISUAL)

{{kv_link_OR_via_drive}}

7️⃣ CONFIGURAÇÕES DA CAMPANHA

Estratégia de lances: {{estrategia_lances}}
Objetivo da Campanha (gerenciador):
{{objetivo_gerenciador_marcado}}
Links e UTMs: {{links_utms}}
Landing Page de destino: {{lp_destino}}

8️⃣ CALENDÁRIO E PRAZOS

Data de Início: {{data_inicio}}
Data de Término: {{data_termino_OR_indefinido}}
Prazos Intermediários: {{prazos_intermediarios_OR_omit}}

9️⃣ MÉTRICAS E KPIs

{{kpis_marcados}}

🔟 TESTES A/B

{{testes_ab_OR_sem_teste}}

1️⃣1️⃣ RELATÓRIOS E ANÁLISES

{{frequencia_relatorios}}

1️⃣2️⃣ OBSERVAÇÕES E REFERÊNCIAS

Observações Relevantes: {{observacoes_OR_omit}}
Referências: {{referencias_OR_omit}}
```

---

## Perguntas ativas — PC

### 1. Objetivo
> **1) Objetivo da Campanha:** O que essa campanha precisa entregar? (ex: "aumentar visibilidade", "gerar leads B2B", "vender produto X em Black Friday")

### 2. Plataformas
> **2) Plataformas de Publicação** (marca uma ou mais):
> 1) Meta Ads (Facebook + Instagram)
> 2) Google Ads (Search/Display/Demand Gen)
> 3) LinkedIn Ads
> 4) TikTok Ads
> 5) YouTube Ads
> 6) Outro: ___

### 3. Demográficos
> **3) Demográficos:** Responda em uma linha cada — Idade / Sexo / Localização / Renda (opc) / Ocupação (opc)

### 4. Psicográficos (opcional)
> **4) Psicográficos** (opcional): Interesses / Comportamento / Hobbies / Valores. Se não tem, "skip".

### 5. Custom Audiences (opcional)
> **5) Custom Audiences** (opcional): Públicos personalizados (listas, retargeting) e lookalikes. Se não, "skip".

### 6. Orçamento
> **6) Orçamento:** Total e distribuição (ex: "R$ 15.000 — R$ 500/dia por 30 dias")

### 7. Link dos criativos
> **7) Link dos criativos:** Drive ou Frame.io com as peças aprovadas

Se vazio, marcar `<<criativos pendentes — não publicar antes de receber link>>` em destaque.

### 8. Formatos
> **8) Formatos de Anúncio** (marca um ou mais):
> 1) Imagens estáticas
> 2) Vídeo
> 3) Carrossel
> 4) Texto-only

### 9. Mensagem principal e CTA
> **9) Mensagem principal e CTA:** Frase central da copy + chamada pra ação

### 10. Estratégia de lances
> **10) Estratégia de lances** (escolhe um):
> 1) CPC (Custo por Clique)
> 2) CPM (Custo por Mil Impressões)
> 3) CPA (Custo por Aquisição)
> 4) ROAS-target
> 5) Lance mais baixo (default Meta)
> 6) Outro: ___

### 11. Objetivo do gerenciador
> **11) Objetivo da Campanha no gerenciador**:
> 1) Conscientização (Awareness/Reach)
> 2) Consideração (Tráfego, Engajamento, Vídeo)
> 3) Conversão (Vendas, Leads, App)

### 12. UTMs e LP
> **12) Links de destino + UTMs:** Cole o link da LP e a estrutura de UTM (ex: `utm_source=meta&utm_medium=paid&utm_campaign=lp-b2b-maio`)

### 13. Calendário
> **13) Datas:** Início / Término (ou "indefinido"). Tem marcos intermediários?

### 14. KPIs
> **14) KPIs principais** (marca um ou mais):
> 1) CTR
> 2) CPC
> 3) CPA / CPL
> 4) ROAS
> 5) Frequência
> 6) CPM
> 7) Outro: ___

### 15. Testes A/B (opcional)
> **15) Testes A/B** (opcional): Vai testar criativo, copy, público? Se não, "sem teste".

### 16. Frequência de relatórios
> **16) Frequência de relatórios:** Daily / Semanal / Quinzenal / Mensal / Sob demanda

### 17. Observações e referências (opcional)
> **17) Observações** (opcional) **e Referências** (opcional)

Vazias → omitir.

---

## Pré-preenchimento via NotebookLM

Perguntas dirigidas pra PC:

1. Quais segmentos de público o cliente já validou em campanhas anteriores? Cite. Se não, 'NAO ENCONTRADO'.
2. Qual histórico de orçamento médio mensal de tráfego pago? Cite. Se não, 'NAO ENCONTRADO'.
3. Existe diretriz documentada de plataformas preferenciais ou vetadas? Cite. Se não, 'NAO ENCONTRADO'.
4. Qual estrutura de UTM padrão é usada? Cite. Se não, 'NAO ENCONTRADO'.
5. Que KPIs já são acompanhados nos relatórios? Cite. Se não, 'NAO ENCONTRADO'.

---

## Conversão pra HTML

Padrão. Bullets `•` viram parte do `<div>` (sem `<ul>`).
