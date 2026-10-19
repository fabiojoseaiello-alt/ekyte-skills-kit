# Template RV — Roteiro de Vídeo

Sigla: `RV` — task_type_id: `37666`. SLA: 7 dias.

Briefing pra produção de **roteiro de vídeo** (peça-base que vira motion/edição depois). Importa estrutura de roteiro: gancho, desenvolvimento, CTA.

---

## Composição do briefing final

```
[1] _header-universal.md   ← Drive, NotebookLM, Referência, KV
[2] _base-criativo.md      ← Direcionamento, Objetivo, Público, Faixa, Sexo, Ganchos
[3] RV.md (este)           ← Estrutura de roteiro + Formato + Duração
```

---

## Markdown específico de RV

```
7️⃣ FORMATO E DURAÇÃO

Formato: {{formato_marcado}}
Duração alvo: {{duracao}}
Plataforma: {{plataforma}}

8️⃣ ESTRUTURA DO ROTEIRO

🎬 Gancho (3-5s iniciais): {{gancho}}
🎯 Desenvolvimento: {{desenvolvimento}}
📣 CTA final: {{cta_final}}

9️⃣ TOM E REFERÊNCIAS

Tom de voz: {{tom_de_voz}}
Referências de vídeos similares: {{referencias_OR_omit}}
Análise de Performance: {{link_analise_OR_omit}}

🔟 PRODUÇÃO

Quem grava: {{quem_grava}}
Locução off / on / dublado: {{tipo_locucao}}
Trilha sonora: {{trilha_OR_padrao}}
Legendas obrigatórias: {{legendas_sim_nao}}
```

---

## Perguntas ativas — específicas de RV

### 10. Formato
> **10) Formato do vídeo** (marca um ou mais):
> 1) Reels / Stories vertical (9:16)
> 2) Feed quadrado (1:1)
> 3) YouTube horizontal (16:9)
> 4) TikTok (9:16)
> 5) Outro: ___

### 11. Duração
> **11) Duração alvo:** Em segundos. (ex: "15s", "30s", "60s", "até 90s")

### 12. Plataforma
> **12) Plataforma de veiculação** (mesma pergunta do CA item 16)

### 13. Gancho
> **13) Gancho dos primeiros 3-5s:** O que prende a atenção logo no início? (1 frase ou descrição visual)

Pré-preenchimento via NotebookLM se há ganchos documentados; senão, perguntar.

### 14. Desenvolvimento
> **14) Desenvolvimento:** Mensagem central do vídeo, em 2-4 linhas. O que o roteiro precisa comunicar?

### 15. CTA final
> **15) CTA final:** Chamada pra ação no fechamento. (ex: "Acesse o link na bio", "Cadastre-se no formulário", "Compre agora")

### 16. Tom de voz
Mesma do `CA.md`.

### 17. Referências (opcional)
> **17) Referências de vídeos similares** (opcional): Tem link de vídeos que servem de referência?

### 18. Análise de Performance (opcional)
Mesma do `CA.md`.

### 19. Quem grava
> **19) Quem grava:** Cliente / V4 produz / Banco de imagens / Animação / Misto

### 20. Tipo de locução
> **20) Locução** (escolhe um):
> 1) Off (narração sobre imagem)
> 2) On (pessoa aparece falando)
> 3) Dublado / sintético (IA)
> 4) Sem locução (texto + música)

### 21. Trilha sonora
> **21) Trilha sonora:** Algo específico ou "padrão" (banco V4)?

Default: `Trilha do banco V4 que case com tom da marca.`

### 22. Legendas
> **22) Legendas obrigatórias:** Sim/não. (Default: sim — Meta exige pra autoplay sem som.)

Default: sim.

---

## Conversão pra HTML

Padrão. Emojis 🎬 🎯 📣 dentro do `<div>` da estrutura — preservam Unicode.
