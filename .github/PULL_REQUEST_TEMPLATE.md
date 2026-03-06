# 🚀 Pull Request: [Título da Feature ou Fix]

## 📝 Resumo da Alteração
Ex: "Integração do módulo de checkout: Adição de persistência no Postgres e feedback visual de sucesso no Front-end."

## 🛠️ Mudanças por Camada

### 🖥️ Front-end (UI/UX)
- [ ] Criado componente de `FeedbackModal.js`.
- [ ] Integração com o novo endpoint de `/api/v1/orders`.
- [ ] Tratamento de estados de erro (400, 401, 500) para o usuário.

### ⚙️ Back-end (API)
- [ ] Criado `OrderController` e `CreateOrderService`.
- [ ] Implementada validação de schema com Zod/Joi.
- [ ] Adicionado middleware de autenticação JWT.

### 🗄️ Database (Persistence)
- [ ] Nova Migration: `create_orders_table`.
- [ ] Atualização do Schema do Prisma/Eloquent.
- [ ] Indexação na coluna `user_id` para otimização de busca.

---

## 🧪 Plano de Testes (Crucial)
1. **Setup:** Rode `npm install`, `docker-compose up` e `npx prisma migrate dev`.
2. **Teste de Sucesso:** Tente finalizar uma compra com o carrinho cheio. Verifique se o registro aparece no banco (`SELECT * FROM orders`).
3. **Teste de Erro:** Tente finalizar uma compra sem estar logado. O sistema deve retornar `401 Unauthorized`.
4. **Logs:** Verifique se o log de erro foi registrado no console/banco em caso de falha.

---

## 📸 Evidências Visuais
| Desktop | Mobile |
| :--- | :--- |
| !(URL_AQUI) | !

[Imagem Mobile]
(URL_AQUI) |

---

## 🚨 Checklist de Segurança e Qualidade
- [ ] **Variáveis de Ambiente:** Não subi arquivos `.env` ou chaves de API expostas.
- [ ] **Migrations:** Testei o `rollback` da migration e ela funciona sem perda de dados críticos.
- [ ] **Performance:** Verifiquei se não há N+1 queries no carregamento da lista.
- [ ] **Linting:** O comando `npm run lint` ou `composer lint` passou com sucesso.
- [ ] **Documentação:** O Swagger/README foi atualizado com os novos campos.

---
**Task ID:** #12345
**Reviewers Sugeridos:** @dev-backend-senior, @ui-ux-lead