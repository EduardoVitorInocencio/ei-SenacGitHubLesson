# 🐛 Bug Report: Falha na Persistência do Carrinho (Guest User)
### Tipo
Bug | Prioridade: 🔴 Alta (Bloqueador de Conversão)

## Descrição do Problema
Usuários não autenticados (Visitantes) perdem todos os itens adicionados ao carrinho ao atualizar a página (F5) ou navegar entre categorias. O sistema não está persistindo o estado no localStorage ou os dados estão sendo sobrescritos pelo estado inicial da aplicação.

## Passos para Reproduzir
Acesse a página inicial da loja sem fazer login.

Adicione 3 produtos diferentes à vitrine clicando em "Adicionar ao Carrinho".

Clique no ícone do carrinho e verifique se os 3 itens aparecem (OK).

Pressione F5 (Refresh) no navegador.

Verifique o ícone do carrinho novamente.

## Comportamento Esperado
O carrinho deveria manter os 3 produtos armazenados, recuperando os dados do localStorage ou de um Cookie de sessão durante a reinicialização da aplicação.

## Comportamento Atual
O contador do carrinho volta para 0 (zero) e a lista de itens aparece vazia após o carregamento da página.

## Evidências
Console Log do Browser (F12):
Uncaught TypeError: Cannot read properties of undefined (reading 'cartItems') at App.js:42

Snapshot do LocalStorage:
key: 'aura_cart' | value: [] (O array está sendo resetado para vazio no hook useEffect).

## Critérios de Aceitação
[ ] O estado do carrinho deve ser persistido e recuperado com sucesso após o refresh.

[ ] O Bug deve ser corrigido sem exigir que o usuário esteja logado.

[ ] Testado em ambiente de desenvolvimento (Chrome e Firefox).

[ ] Validado que a correção não gera regressões no fluxo de checkout de usuários logados.