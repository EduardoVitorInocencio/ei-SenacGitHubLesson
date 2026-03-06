# 🐘 LumaCommerce – Enterprise Laravel API

## 📌 Visão Geral

O **LumaCommerce** é um ecossistema de e-commerce de alto desempenho, desenvolvido com **Laravel 11**. O projeto utiliza uma arquitetura orientada a serviços (**Service Layer Pattern**) para garantir que a lógica de negócio seja independente dos controladores, facilitando testes unitários e manutenção a longo prazo.

### 🎯 Diferenciais Técnicos:

* **Service Layer & Repositories:** Desacoplamento total da lógica de checkout e cálculo de impostos.
* **Processamento Assíncrono:** Uso de **Laravel Queues** com Redis para envio de e-mails de confirmação e processamento de notas fiscais sem travar o usuário.
* **Segurança Avançada:** Implementação de **Laravel Sanctum** para autenticação de SPA e Mobile, com proteção contra CSRF e XSS.
* **Observabilidade:** Logs estruturados e monitoramento de performance com **Laravel Telescope**.

---

## 🏗️ Estrutura do Ecossistema

O projeto é organizado seguindo os padrões do Eloquent ORM e injeção de dependência nativa do Laravel:

1. **Models:** Entidades ricas com relacionamentos mapeados (`belongsTo`, `hasMany`).
2. **Services:** Onde reside a "mágica". Ex: `CheckoutService`, `InventoryService`.
3. **Jobs:** Tarefas em segundo plano (Filas).
4. **Observers:** Gatilhos automáticos (ex: baixar estoque assim que um pedido for pago).

---

## 📁 Arquitetura de Pastas (Laravel Way)

```text
.
├── app/
│   ├── Http/Controllers/  # Controladores enxutos (Lean Controllers)
│   ├── Models/            # Entidades do banco de dados
│   ├── Providers/         # Registro de serviços e bindings
│   └── Services/          # [Pasta Custom] Lógica de negócio pesada
├── database/
│   ├── factories/         # Geração de dados fakes para testes
│   ├── migrations/        # Versionamento do banco de dados (Git-driven)
│   └── seeders/           # Dados iniciais do sistema
├── tests/
│   ├── Feature/           # Testes de ponta a ponta (API endpoints)
│   └── Unit/              # Testes de lógica isolada
├── docker-compose.yml     # Setup com Laravel Sail (PHP, MySQL, Redis, Mailpit)
└── artisan                # CLI do Laravel para automação

```

---

## ⚙️ Setup de Desenvolvimento (Laravel Sail)

Este projeto utiliza o **Laravel Sail**, uma interface de linha de comando leve para interagir com o ambiente Docker padrão do Laravel.

1. **Instalação:**
```bash
git clone https://github.com/seu-usuario/lumacommerce-api.git
composer install

```


2. **Subir o Ambiente (Docker):**
```bash
./vendor/bin/sail up -d

```


3. **Gerar Chave e Migrar Banco:**
```bash
./vendor/bin/sail artisan key:generate
./vendor/bin/sail artisan migrate --seed

```



---

## 📝 Governança e Qualidade (Git Workflow)

### Padrão de Commits

Seguimos o **Conventional Commits**. O uso de Git Hooks garante que nenhuma migração de banco suba sem teste:

* `feat(order): implementar integração com API do Melhor Envio`
* `fix(cart): corrigir cálculo de ICMS em produtos importados`
* `chore(deps): atualizar laravel/framework para v11.1`

### Fluxo de Merge

1. Branches devem seguir o padrão `feature/` ou `hotfix/`.
2. **Obrigatório:** `php artisan test` deve passar com 100% de sucesso.
3. **Code Review:** Pelo menos uma aprovação de um par é necessária para merge na branch `develop`.

---