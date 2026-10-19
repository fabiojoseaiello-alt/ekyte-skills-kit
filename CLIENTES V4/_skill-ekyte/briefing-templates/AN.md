# Template AN — Análise de Dados / Projeção

Sigla: `AN` — task_type_id: `37680`.

Briefing pra **análises de dados, projeções, compilados de performance**. Não é criativo. Usa **só** `_header-universal.md` (sem KV) + este.

---

## Composição do briefing final

```
[1] _header-universal.md   ← Drive, NotebookLM, Referência (KV omitido)
[2] AN.md (este)           ← Briefing analítico
```

---

## Markdown específico de AN

```
1️⃣ OBJETIVO DA ANÁLISE

{{objetivo_analise}}

2️⃣ PERGUNTA(S)-CHAVE

{{perguntas_chave}}

3️⃣ ESCOPO

Período analisado: {{periodo}}
Fontes de dados: {{fontes}}
Filtros / segmentos: {{filtros_OR_omit}}

4️⃣ MÉTRICAS

{{metricas_marcadas}}

5️⃣ FORMATO DA ENTREGA

{{formato_entrega_marcado}}

6️⃣ AUDIÊNCIA

Quem vai consumir: {{audiencia}}
Nível técnico esperado: {{nivel_tecnico}}

7️⃣ CONTEXTO E HIPÓTESES

Contexto de negócio: {{contexto_negocio}}
Hipóteses iniciais: {{hipoteses_OR_omit}}
Resultados esperados: {{resultado_esperado_OR_omit}}

8️⃣ DEPENDÊNCIAS E RESTRIÇÕES

Acessos necessários: {{acessos_OR_omit}}
Restrições / dados sensíveis: {{restricoes_OR_omit}}

9️⃣ PRÓXIMOS PASSOS APÓS A ANÁLISE

{{proximos_passos_OR_omit}}
```

---

## Perguntas ativas — AN

### 1. Objetivo da análise
> **1) Objetivo da análise:** O que essa análise precisa responder/provar? (1-2 frases)

### 2. Perguntas-chave
> **2) Perguntas-chave** (até 3): Liste as perguntas específicas que a análise deve responder

### 3. Escopo - Período
> **3) Período analisado:** Datas de corte (ex: "Q1/2026", "últimos 90 dias", "01/01-31/03/26")

### 4. Escopo - Fontes
> **4) Fontes de dados** (marca uma ou mais):
> 1) Meta Ads
> 2) Google Ads
> 3) GA4 / Analytics
> 4) CRM (Kommo, Chatwoot, etc)
> 5) Planilha interna
> 6) BigQuery / Data warehouse
> 7) Outro: ___

### 5. Filtros (opcional)
> **5) Filtros / segmentos** (opcional): Recorte específico (ex: "só campanhas de prospect", "apenas leads MQL", "público mobile")

### 6. Métricas
> **6) Métricas principais** (marca uma ou mais):
> 1) CAC / CPL
> 2) ROAS / ROI
> 3) Conversão (CR%)
> 4) Funil completo (impressão → lead → venda)
> 5) Frequência / alcance
> 6) Tempo até conversão
> 7) Outro: ___

### 7. Formato da entrega
> **7) Formato da entrega**:
> 1) Documento Google Docs (texto + insights)
> 2) Planilha Google Sheets (tabular)
> 3) Slide / apresentação
> 4) Dashboard (Looker / Data Studio)
> 5) Comentário direto no ekyte / chat
> 6) Outro: ___

### 8. Audiência
> **8) Quem vai consumir** + **nível técnico**:
> Audiência (ex: cliente C-level, gestor de tráfego, time interno) — Nível técnico (executivo / operacional / técnico)

### 9. Contexto de negócio
> **9) Contexto de negócio:** Por que essa análise é necessária agora? Algum gatilho específico (queda de performance, planejamento, dúvida do cliente)?

### 10. Hipóteses iniciais (opcional)
> **10) Hipóteses iniciais** (opcional): Tem suposições do que a análise vai mostrar?

### 11. Resultado esperado (opcional)
> **11) Resultado esperado** (opcional): Que decisão/ação deve sair dessa análise?

### 12. Acessos necessários (opcional)
> **12) Acessos necessários** (opcional): Tem credencial / dashboard / painel que precisa ser fornecido?

### 13. Restrições (opcional)
> **13) Restrições** (opcional): Dados sensíveis? Anonimização? Só compartilhar internamente?

### 14. Próximos passos (opcional)
> **14) Próximos passos** (opcional): O que acontece depois da análise?

---

## Pré-preenchimento via NotebookLM

1. Existe análise anterior similar no histórico do cliente? Cite. Se não, 'NAO ENCONTRADO'.
2. Quais KPIs principais o cliente acompanha? Cite. Se não, 'NAO ENCONTRADO'.
3. Há histórico de hipóteses de negócio documentadas? Cite. Se não, 'NAO ENCONTRADO'.
4. Qual o stakeholder consumidor das análises desse cliente? Cite. Se não, 'NAO ENCONTRADO'.
5. Existem benchmarks ou metas documentados? Cite. Se não, 'NAO ENCONTRADO'.

---

## Conversão pra HTML

Padrão.
