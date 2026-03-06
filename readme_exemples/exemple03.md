# Python ETL Enterprise: Medallion Architecture & Observability

## Sobre o Projeto

Este pipeline realiza a ingestão de dados de fontes heterogêneas (CSV, TXT, API), processando-os através da **Arquitetura Medalhão**. O grande diferencial é o seu **Core de Governança**, que utiliza um banco **SQLite** para registrar o status de cada execução, volumetria de dados e tratamento de exceções em tempo real.

## 🏗️ Arquitetura do Sistema

O pipeline é dividido em módulos especializados para garantir alta coesão e baixo acoplamento:

1. **Extractor:** Responsável pela conexão e coleta (Requests para API, IO para local).
2. **Medallion Processor:** Scripts dedicados para as camadas Bronze (Raw), Silver (Clean) e Gold (Business).
3. **ErrorHandler:** Centralizador de exceções que decide se o pipeline deve parar ou continuar (Retry Logic).
4. **Metadata Logger (SQLite):** Banco de dados técnico que armazena:
* `run_id`: Identificador único da execução.
* `status`: (STARTED, SUCCESS, FAILED).
* `row_count`: Quantidade de registros processados por camada.
* `error_msg`: Traceback detalhado em caso de falha.



---

## 🧱 Stack Tecnológica

* **Linguagem:** Python 3.10+
* **Dados:** Pandas (Transformação) & SQLAlchemy (Interface com SQLite).
* **API:** Requests com suporte a *Backoff/Retry*.
* **Reports:** XlsxWriter com formatação de KPIs.

---

## 📁 Estrutura de Pastas (Refatorada)

```text
.
├── data/
│   ├── 1_bronze/         # Ingestão raw (imutável).
│   ├── 2_silver/         # Dados limpos e normalizados.
│   └── 3_gold/           # Reports finais em .xlsx.
├── database/
│   └── pipeline_logs.db  # SQLite para auditoria e logs.
├── src/
│   ├── core/
│   │   ├── extractor.py  # Abstração de coleta de dados.
│   │   ├── handler.py    # Gerenciador de erros e retentativas.
│   │   └── logger.py     # Interface de escrita no SQLite.
│   ├── stages/
│   │   ├── bronze.py     # Validação de schema inicial.
│   │   ├── silver.py     # Limpeza e deduplicação.
│   │   └── gold.py       # Agregação de negócio.
├── main.py               # Orquestrador principal do fluxo.
└── .env                  # Configurações e chaves de API.

```

---

## Fluxo de Execução e Monitoramento

Para garantir a rastreabilidade, cada execução segue o fluxo:

1. **Init:** O `logger.py` cria um registro no SQLite com status `STARTED`.
2. **Extract:** O `extractor.py` busca os dados. Se a API falhar, o `handler.py` tenta 3 vezes antes de marcar como `FAILED`.
3. **Process:** As camadas Medalhão processam os dados. A cada passo, o SQLite é atualizado com o `row_count` atual.
4. **Finalize:** O report Excel é gerado e o status final é gravado no banco.

**Exemplo de consulta de logs:**

```sql
SELECT run_id, status, row_count, timestamp 
FROM pipeline_execution_logs 
ORDER BY timestamp DESC LIMIT 5;

```

---

## 📝 Boas Práticas e Contribuição

* **Commits:** Use o padrão semântico (ex: `feat(api): adicionar retry logic no extractor`).
* **Erros:** Nunca use `try/except: pass`. Todo erro deve ser enviado ao `ErrorHandler`.
* **Revisão:** PRs que alteram a camada **Gold** exigem validação de esquema de dados.

---