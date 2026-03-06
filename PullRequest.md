# 🚀 Pull Request: Integração de Cálculo de Frete (Logística v1)

## 📝 Resumo da Alteração

Implementação do módulo de logística para cálculo dinâmico de frete baseado no CEP do usuário. Esta alteração conecta o Front-end ao novo serviço de cotação no Back-end, utilizando o banco de dados para cache de faixas de CEP comuns.

## 🛠️ Mudanças por Camada

### 🖥️ Front-end (UI/UX)

* [x] Criado o componente `ShippingCalculator.jsx` com validação de máscara de CEP.
* [x] Adicionado *Skeleton Loader* enquanto a API processa a cotação.
* [x] Exibição de mensagens de erro amigáveis para CEPs não atendidos.

### ⚙️ Back-end (API)

* [x] Criado o endpoint `POST /api/v1/shipping/calculate`.
* [x] Implementada integração com a API dos Correios/Melhor Envio.
* [x] Adicionada lógica de *fallback*: se a API externa cair, utiliza uma tabela de preços fixa (contingência).

### 🗄️ Database (Persistence)

* [x] Nova Migration: `20240520_create_shipping_rates_table`.
* [x] Armazenamento de logs de consultas para análise de densidade de pedidos por região.

---

## 🧪 Plano de Testes

Para validar esta PR, siga os passos abaixo:

1. **Setup:** Execute `npm install` e `npx prisma migrate dev`.
2. **Teste de Sucesso:** No carrinho, insira o CEP `01001-000`. O valor retornado deve ser **R$ 12,50** (conforme mock de teste).
3. **Teste de Erro:** Insira o CEP `99999-999`. O sistema deve exibir a mensagem: *"Desculpe, ainda não entregamos nesta região."*
4. **Persistência:** Verifique se após o cálculo, o valor do frete é somado corretamente ao total do pedido no banco de dados.

---

## 📸 Evidências Visuais

| Estado de Carregamento | Resultado do Cálculo |
| --- | --- |
|  |  |

---

## 🚨 Checklist de Segurança e Qualidade

* [x] **Variáveis de Ambiente:** A chave da API de logística foi movida para o `.env` (não está no código).
* [x] **Performance:** Implementado cache de 1 hora para consultas de um mesmo CEP para evitar chamadas excessivas à API externa.
* [x] **Linting:** `npm run lint` executado sem erros.
* [x] **Documentação:** Swagger atualizado com o novo endpoint de frete.

---

**Task ID:** #EC-782
**Reviewers Sugeridos:** @backend-lead, @qa-engineer

