# 📦 OmniCart API – High-Performance E-commerce Backend

## 📌 Visão Geral

A **OmniCart API** é uma solução de backend robusta para e-commerce, construída com foco em **Domain-Driven Design (DDD)** e **Clean Architecture**. A API gerencia desde o catálogo complexo de produtos até o processamento de pedidos e integração com gateways de pagamento, garantindo consistência de dados através de transações ACID no PostgreSQL.

### 🎯 Diferenciais de Engenharia:

* **Camada de Abstração de Dados:** Uso de **Repository Pattern** para desacoplar a lógica de negócio do banco de dados.
* **Segurança:** Autenticação via **JWT (JSON Web Tokens)** com renovação por *Refresh Tokens* e criptografia de senhas com **Argon2**.
* **Gerenciamento de Banco:** Controle total de versão de esquema via **Prisma Migrations**.
* **Escalabilidade:** Preparado para ambiente de containers com Docker e Docker Compose.

---

## 🏗️ Arquitetura do Sistema

O projeto segue os princípios da **Clean Architecture**, dividindo-se em:

1. **Domain:** Regras de negócio puras e entidades (independente de frameworks).
2. **Application:** Casos de uso (Use Cases) como `CreateOrder`, `AuthenticateUser`.
3. **Infrastructure:** Implementações técnicas (Persistência com Prisma, Envio de E-mail, Gateways de Pagamento).
4. **Interface (Web):** Controladores Express e Middlewares de validação.

---

## 🧱 Stack Tecnológica

* **Runtime:** Node.js v20 (LTS)
* **Framework:** Express.js
* **Linguagem:** TypeScript (Tipagem estrita para evitar erros em runtime)
* **ORM:** Prisma (Type-safe query builder)
* **Banco de Dados:** PostgreSQL 15
* **Validação:** Zod (Schema validation para requisições)
* **Documentação:** Swagger/OpenAPI

---

## 📁 Estrutura de Diretórios

```text
.
├── prisma/               # Esquema do banco e Migrations
├── src/
│   ├── @types/           # Definições de tipos globais
│   ├── core/             # Erros customizados e classes base
│   ├── domain/           # Entidades e Interfaces (Contracts)
│   ├── use-cases/        # Lógica de negócio (Regras)
│   ├── infra/            # Repositórios, DB e Implementações externas
│   └── http/             # Controllers, Routes e Middlewares
├── tests/                # Testes Unitários e Integração (Vitest)
├── docker-compose.yml    # Orquestração Node + Postgres + Redis
└── .env.example          # Template de variáveis de ambiente

```

---

## ⚙️ Setup de Desenvolvimento

Este projeto utiliza **Docker** para garantir que o ambiente seja idêntico em qualquer máquina.

1. **Clone e Instale:**
```bash
git clone https://github.com/seu-usuario/omnicart-backend.git
npm install

```


2. **Levante os containers (DB & Cache):**
```bash
docker-compose up -d

```


3. **Rode as Migrations:**
```bash
npx prisma migrate dev

```


4. **Inicie o servidor:**
```bash
npm run dev

```



---

## 📝 Governança e Qualidade de Código

### Fluxo de Commits (Semantic Commits)

Obrigatório o uso do padrão **Conventional Commits**. O Husky impedirá commits que não sigam a regra:

* `feat(order): adiciona suporte a cupons de desconto`
* `fix(auth): corrige vazamento de memória no middleware de JWT`
* `refactor(db): otimiza query de listagem de produtos`

### Pull Requests & CI/CD

* **Linting:** `npm run lint` deve retornar zero erros.
* **Tests:** Pelo menos 80% de cobertura de código em Use Cases.
* **Review:** Mínimo de 2 aprovações de outros desenvolvedores para merge na `main`.

