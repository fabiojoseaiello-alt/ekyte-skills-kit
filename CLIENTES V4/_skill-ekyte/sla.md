# SLA por tipo de tarefa

A MCP do ekyte **não expõe** o campo "dias para concluir" (a coluna existe na UI web mas o n8n não retorna). Esta tabela é manual, calibrada com input do Fabio. Vai crescendo conforme novos tipos aparecem.

**Default genérico** (quando o tipo não está nessa tabela): IA pergunta o prazo no preview, ou usa **3 dias úteis** se o usuário disser "padrão".

---

## Tabela SLA (em dias corridos a partir de hoje)

| Sigla | Tipo | SLA |
|---|---|---|
| CA | Criativo Ads — estático e variação simples | **5 dias** |
| CA-VÍDEO | Criativo Ads — vídeo, incluindo vídeo com IA | **7 dias** |
| LP | Landing Page | **7 dias** |
| RV | Roteiro de vídeo | **7 dias** |
| GP | Solicitação ao GP | **1 dia** |
| PC | Publicação de campanhas | **mesmo dia** (D+0) |
| WEB | Personalizada / demanda Web | **a definir caso a caso (sempre perguntar)** |

---

## Como aplicar

Ao criar uma task:

1. Identificar a sigla pelo input do usuário ou pela escolha de tipo no preview.
2. Consultar a tabela acima.
3. Se houver SLA: `current_due_date_create_task` = hoje + SLA.
4. Se NÃO houver SLA: perguntar prazo no preview ou usar default genérico (3 dias úteis) se o usuário pedir "padrão".
5. Se o usuário disser "urgente" ou der prazo explícito, sobrescrever a tabela.

## Como atualizar

Quando o Fabio fornecer SLA de um tipo novo, adicionar à tabela acima e marcar a data da atualização no rodapé.

---

**Última atualização:** 2026-04-28 (sabatina inicial)
