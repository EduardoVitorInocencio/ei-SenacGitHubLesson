# 🤖 Pull Request: [Automação / Implementação de Modelo]

## 📝 Resumo do Processo
Ex: "Automação de extração de faturas com classificação de intenção via GPT-4o e armazenamento em Data Lake."

## 🧩 Arquitetura da Solução

### ⚙️ Core RPA (Python)
- [ ] **Seletores/Interação:** Uso de seletores robustos (Xpath/ID) ou Visão Computacional?
- [ ] **Orquestração:** Implementação de `Wait` dinâmico para evitar quebras por lentidão do sistema.
- [ ] **Cleanup:** Garantia de fechamento de instâncias (Browsers/Drivers) após erro ou sucesso.

### 🧠 AI & LLM Layer
- [ ] **Prompt Engineering:** O prompt foi versionado? Existe controle de `temperature` e `max_tokens`?
- [ ] **Token Usage:** Estimativa de custo por execução da automação.
- [ ] **Fallback:** O que acontece se a API de IA estiver fora do ar ou o JSON vier malformatado?

### 🛡️ Tratamento de Erros (Error Handling)
- [ ] **Screenshots de Erro:** O robô tira print da tela antes de encerrar em caso de falha?
- [ ] **Logs de Negócio:** Log de "Fatura não encontrada" vs "Erro de Sistema".
- [ ] **Retry Logic:** Estratégia de re-tentativa para erros de rede.

---

## 📊 Métricas de Validação (Acurácia)
| Cenário de Teste | Resultado Esperado | Resultado Obtido | Status |
| :--- | :--- | :--- | :--- |
| PDF Legível | Extração 100% | Extração 100% | ✅ |
| PDF Digitalizado (Ruído) | Extração > 90% | Extração 92% | ✅ |
| Documento Inválido | Rejeição/Erro | Rejeição | ✅ |

---

## 🧪 Como o Revisor deve Validar?

1. **Venv:** Ative o ambiente virtual e instale as `requirements.txt`.
2. **Secrets:** Configure as chaves de API (OpenAI/Anthropic) no seu `.env` local.
3. **Mock Data:** Use os arquivos de teste na pasta `/tests/samples/`.
4. **Execução:** Rode `python main.py --debug` e observe o log do SQLite/Console.

---

## 🚨 Checklist de Auditoria (Compliance)
- [ ] **Dados Sensíveis:** Garanti que PII (Dados Pessoais) não estão sendo enviados para a IA sem anonimização?
- [ ] **Performance:** O tempo médio de execução está dentro do SLA (ex: < 30s por documento)?
- [ ] **Estabilidade:** Testei o robô com a resolução de tela alterada (Headless vs Headful)?

---
**Bot ID:** `RPA-INV-001`
**AI Model:** `gpt-4o-mini`