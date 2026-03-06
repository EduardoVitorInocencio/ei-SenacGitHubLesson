# 🛍️ Aura Store – E-commerce SPA (Single Page Application)

## 📌 Visão Geral do Projeto

A **Aura Store** é uma aplicação de e-commerce de ponta a ponta (Front-end), construída **exclusivamente com Vanilla JavaScript, HTML5 e CSS3**. O objetivo deste projeto é demonstrar a capacidade de escalar uma aplicação sem frameworks, utilizando padrões de design avançados para garantir performance, manutenibilidade e uma experiência de usuário (UX) fluida.

### 🎯 Principais Desafios Técnicos Resolvidos:

* **Roteamento Client-Side:** Navegação sem recarregamento de página (SPA) usando a `History API` nativa do navegador.
* **Gerenciamento de Estado Reativo:** Implementação de uma *Store* customizada usando o padrão **Publisher/Subscriber (Pub/Sub)**, conectando o carrinho, o checkout e a vitrine.
* **Integração com API REST:** Consumo assíncrono de dados (`Fetch API`) com tratamento robusto de erros, *loading states* e *skeleton screens*.
* **Performance Mágica:** Carregamento otimizado com *Lazy Loading* de imagens, *Code Splitting* via Vite e pontuação máxima no Google Lighthouse.

---

## 🏗️ Arquitetura e Padrões (Design Patterns)

Para manter o código Vanilla escalável, adotamos as seguintes práticas:

1. **Padrão MVC (Model-View-Controller):** Separação estrita entre a lógica de negócios (Models/Services), a interface (Views/Components) e os intermediários (Controllers).
2. **CSS com Metodologia BEM:** (Block, Element, Modifier) para evitar vazamento de estilos e escopo global.
3. **Web Components Autônomos:** Criação de componentes modulares baseados em classes ES6.

---

## 🧱 Stack Tecnológica

* **Core:** HTML5 Semântico, CSS3 (Variáveis Globais) e JavaScript (ES6+ Modules).
* **Bundler & Dev Server:** Vite (para Hot Module Replacement ultra-rápido e build otimizado).
* **Testes:** Vitest (Testes Unitários) e Cypress (Testes End-to-End).
* **Linting & Code Quality:** ESLint, Prettier e Husky (Gatilhos de pré-commit).

---

## 📁 Estrutura de Diretórios (Deep Dive)

A árvore do projeto foi desenhada para suportar crescimento contínuo:

```text
.
├── .husky/               # Hooks do Git (pre-commit, commit-msg)
├── src/
│   ├── assets/           # Imagens, fontes e ícones SVG
│   ├── components/       # Componentes reutilizáveis (UI)
│   │   ├── Button/       # Ex: Button.js, Button.css
│   │   └── ProductCard/  
│   ├── core/             # Lógica central da aplicação
│   │   ├── Router.js     # Roteador SPA customizado
│   │   └── Store.js      # Gerenciamento de estado (Pub/Sub)
│   ├── pages/            # Páginas montadas (Home, Cart, Checkout)
│   ├── services/         # Integrações com APIs externas e Mock Service Worker
│   ├── styles/           # CSS Global, variáveis de design tokens e resets
│   └── utils/            # Funções auxiliares (formatadores de moeda, validadores)
├── index.html            # Ponto de entrada (Entry point)
├── main.js               # Inicialização da aplicação
├── package.json          # Dependências e scripts npm
└── vite.config.js        # Configuração do empacotador

```

---

## ⚙️ Como Rodar o Projeto Localmente

Certifique-se de ter o **Node.js (v18+)** instalado em sua máquina.

1. **Clone o repositório:**
```bash
git clone https://github.com/seu-usuario/aura-store-vanilla.git
cd aura-store-vanilla

```


2. **Instale as dependências de desenvolvimento:**
```bash
npm install

```


3. **Inicie o servidor de desenvolvimento (Vite):**
```bash
npm run dev

```


4. **Para gerar o Build de Produção:**
```bash
npm run build

```



---

## 🔄 Fluxo de Contribuição e Git Flow

Este repositório simula um ambiente corporativo. Todas as contribuições devem passar por nossa esteira de CI/CD (GitHub Actions).

### Regras de Commit (Semantic Commits)

Nosso projeto usa o **Commitlint** e **Husky**. Commits fora do padrão serão rejeitados automaticamente.

* `feat(cart): implementa cálculo dinâmico de frete`
* `fix(ui): corrige desalinhamento do header no mobile`
* `test(store): adiciona testes unitários para o gerenciador de estado`

### Processo de Pull Request (PR)

1. Crie uma branch seguindo o padrão: `feature/nome-da-feature` ou `bugfix/nome-do-bug`.
2. Assegure-se de que a cobertura de testes (Coverage) não caia (mínimo de 85%).
3. Execute `npm run lint` antes de abrir o PR.
4. O merge na branch `main` só ocorre após a aprovação de pelo menos 1 revisor (Code Review).

---
