# Template CRM — Configuração / Acompanhamento de CRM

Sigla: `CRM` (12 variantes — desambiguação obrigatória), `ACRM`, `ATM`, `CB`. Aplicável também a outros tipos relacionados a infra de relacionamento.

Briefing pra **implementação, configuração ou acompanhamento de CRM, automação de e-mail, ferramentas de relacionamento**. Tom narrativo + checklist (referência: briefing Chatwoot/Cliente Gama que foi modelo).

Usa **só** `_header-universal.md` (sem KV) + este. Adiciona **3 campos obrigatórios extras** específicos de CRM.

---

## Composição do briefing final

```
[1] _header-universal.md       ← Drive, NotebookLM, Referência (KV omitido)
[1.5] CRM-extra-header.md      ← Planilha Backup, Ferramenta, Acesso (inline neste arquivo)
[2] CRM.md (este)              ← Briefing narrativo + checklist
```

---

## Bloco extra CRM (header complementar)

Vem **logo após** o header universal. Sempre presente em briefings CRM.

```
🔧 INFRA DA OPERAÇÃO CRM

Planilha de Backup: {{backup_link_OR_pendente}}
Ferramenta: {{ferramenta_nome}}
Acesso da Ferramenta: {{acesso_link_OR_credencial}}
```

### Como preencher

- **Planilha de Backup:** lookup em `clientes/_skill-ekyte/backups-crm.md`. Se cliente vazio, perguntar e oferecer salvar via `/ekyte-briefing-refresh`.
- **Ferramenta:** input do Fabio ("CRM no Chatwoot", "automação no RD") OU pergunta no preview.
- **Acesso da Ferramenta:** link de painel/login OU credencial mascarada (ex: "credencial no 1Password — vault Cliente Gama"). Pergunta no preview.

---

## Markdown específico de CRM

Estrutura narrativa estilo Chatwoot. Não numerada por número — numerada por seção semântica.

```
🎯 OBJETIVO

{{objetivo_narrativo}}

🏢 CONTEXTO E REGRAS DE NEGÓCIO

{{contexto_e_regras_narrativo}}

📦 ENTREGÁVEIS ESPERADOS (CHECKLIST)

{{checklist_entregaveis}}

⏱️ PRAZOS E DEPENDÊNCIAS

Prioridade: {{prioridade}}
Prazo desejado de entrega: {{prazo}}
Dependências (acessos, decisões, integrações): {{dependencias_OR_omit}}

👥 STAKEHOLDERS

Decisor cliente: {{decisor_cliente}}
Operação no cliente: {{operacao_cliente_OR_omit}}
Decisor V4: {{decisor_v4_OR_padrao}}

📊 SUCESSO — COMO MEDIR

{{metricas_de_sucesso}}

⚠️ RISCOS E ATENÇÕES

{{riscos_OR_omit}}
```

---

## Perguntas ativas — CRM

### Bloco extra CRM (sempre antes das demais)

> **A) Ferramenta:** Qual CRM/automação? (ex: Chatwoot, RD Station, HubSpot, Pipedrive, Mautic)

> **B) Acesso da ferramenta:** Como o executor acessa? (link do painel + credencial em vault, ou link Lastpass/1Password)

> **C) Planilha de Backup:** Tem planilha mestre que registra o que foi feito? Cole o link. Se não tem, criar uma e me avisar.

### Briefing narrativo

> **1) Objetivo (narrativo, 2-4 frases):** O que essa task precisa entregar e qual é o impacto esperado? (Ex: "Subir Chatwoot pra centralizar atendimento de novos leads, com SLA configurado pra elevar conversão de 15% pra 27%")

> **2) Contexto e regras de negócio:** Conta o que torna essa task específica. Restrições, regras estranhas, decisões já tomadas. (Pode ser longo — 1-2 parágrafos.) Pré-preenchimento via NotebookLM ajuda muito aqui.

> **3) Entregáveis esperados (checklist):** Lista os entregáveis concretos. (ex: "Subir instância", "Conectar API oficial", "Configurar tags", "Criar usuários", "Treinamento equipe"). Default mínimo se Fabio quiser: skill propõe 4-6 itens baseados no objetivo.

> **4) Prioridade:** Baixa / Média / Alta / Altíssima

> **5) Prazo desejado:** Data específica ou janela (ex: "antes de 01/05", "fim de Q2/2026")

> **6) Dependências** (opcional): Algo que precisa estar pronto antes? (ex: "API liberada pelo cliente", "credencial Meta Business", "decisão sobre número único")

> **7) Decisor cliente:** Quem aprova do lado do cliente? (nome + cargo se relevante)

> **8) Operação cliente** (opcional): Quem opera no dia-a-dia? (ex: time comercial, vendedora X)

> **9) Decisor V4** (opcional): Quem aprova internamente? (default: Fabio)

> **10) Sucesso — métricas:** Como saber que funcionou? (ex: "tempo de primeira resposta < 10 min", "100% dos leads taggeados", "30% conversão no funil novo")

> **11) Riscos e atenções** (opcional): O que pode dar errado? Coisas pra ficar de olho.

---

## Pré-preenchimento via NotebookLM (CRÍTICO em CRM)

CRM exige briefing narrativo rico. NotebookLM é especialmente útil aqui pra trazer contexto que evita briefing genérico.

Perguntas dirigidas:

1. Existe histórico de implementação ou troca de CRM nesse cliente? Cite. Se não, 'NAO ENCONTRADO'.
2. Quais ferramentas de relacionamento já estão em uso no cliente? Cite. Se não, 'NAO ENCONTRADO'.
3. Há decisões documentadas sobre roteamento de leads, SLA de atendimento, ou regras de tags? Cite. Se não, 'NAO ENCONTRADO'.
4. Quem são os stakeholders documentados (decisores, operação)? Cite. Se não, 'NAO ENCONTRADO'.
5. Existem KPIs de atendimento/conversão acompanhados pelo cliente? Cite. Se não, 'NAO ENCONTRADO'.

A síntese do NotebookLM **deve** alimentar diretamente as seções 🏢 CONTEXTO e 👥 STAKEHOLDERS antes de mostrar perguntas.

---

## Exemplo de referência (tom esperado)

O briefing Chatwoot/Cliente Gama é a régua de profundidade:

```
🎯 Objetivo
Realizar a instalação, hospedagem e configuração completa da plataforma Chatwoot 
nos servidores da V4 para o cliente Cliente Gama. A ferramenta atuará como o hub 
centralizador do WhatsApp para todos os novos leads, permitindo supervisão de 
qualidade, gestão de SLA e garantia de follow-up, com a meta de elevar a taxa 
de conversão para 27%-30%.

🏢 Contexto e Regras de Negócio
Infraestrutura: O sistema será fornecido sem custo de software para a Fiber One 
e hospedado nos servidores da própria V4.
Estratégia de Roteamento: A partir de 1º de maio, o Chatwoot receberá apenas 
novos leads, concentrados em um único número de telefone principal.
Base Antiga: Clientes antigos e negociações em andamento antes de maio 
continuarão nos números individuais dos vendedores. Não migrar essa base.

📦 Entregáveis Esperados (Checklist V4)
• Infraestrutura e Hospedagem
• Conexão da API Oficial
• Setup de Tags e Tabulação
• Configuração de SLA
• Criação de Usuários e Permissões
• Treinamento Expresso
```

**Tom: gerencial, claro, com decisões e restrições explícitas.** Não é checklist seco — é briefing executivo.

---

## Conversão pra HTML

Padrão. Emojis 🎯 🏢 📦 ⏱️ 👥 📊 ⚠️ 🔧 sobrevivem. Bullets `•` viram parte do `<div>`.
