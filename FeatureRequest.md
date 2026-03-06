# ✨ Feature Request: Sugestões de Produtos Baseadas em IA (Recomendação)

## Tipo

**Enhancement** | Prioridade: 🟡 Média | Categoria: **IA & UX**

## Descrição da Funcionalidade

Implementação de uma seção de "Produtos Recomendados para Você" na página de detalhes do produto. A funcionalidade deve utilizar um modelo de recomendação simples (filtragem colaborativa ou baseada em conteúdo) para exibir itens que outros usuários também compraram ou que possuem categorias similares.

## Justificativa (Valor de Negócio)

* **Aumento de Ticket Médio:** Estimular o *cross-selling* (venda cruzada).
* **Melhoria na Retenção:** Mantém o usuário navegando por mais tempo na loja.
* **Personalização:** Oferece uma experiência de compra mais moderna e menos estática.

## Descrição da Solução Proposta

1. **Backend:** Criar um novo endpoint `GET /api/v1/recommendations/{product_id}` que retorna os 4 produtos mais similares.
2. **AI Engine:** Integrar um script Python que analisa a correlação de categorias e tags entre produtos.
3. **Frontend:** Adicionar um componente de *Carousel* abaixo da descrição do produto principal.

## Critérios de Aceitação

* [ ] O componente deve carregar de forma assíncrona para não atrasar o LCP (Largest Contentful Paint).
* [ ] Caso a API de recomendações falhe, o componente deve ficar oculto (Graceful Degradation).
* [ ] As recomendações devem ser atualizadas em tempo real conforme o estoque muda.
* [ ] Layout responsivo testado em telas mobile e desktop.

## Impacto na Arquitetura

* **Nova Tabela:** `product_correlations` no PostgreSQL para busca rápida.
* **Novo Job:** Tarefa agendada (Cron) para re-calcular as similaridades uma vez por dia.

