# Reprodução Parcial: Late Fusion of Transformers for Sentiment Analysis of Code-Switched Data

Este repositório contém a reprodução parcial do artigo **"Late Fusion of Transformers for Sentiment Analysis of Code-Switched Data"** (Sharma, Chinmay & Sharma, EMNLP 2023). 

O projeto implementa um pipeline completo utilizando **PyTorch**, **Hugging Face Transformers** e **Scikit-Learn** focado na análise de sentimentos em textos bilíngues (*Code-Switched* Inglês-Espanhol do benchmark GLUECoS).

---

## 🔍 Escopo da Reprodução
* **Dataset:** `Huggmachas/GLuecos_Sentiment_EN_ES` (via Hugging Face Datasets).
* **Modelos Individuais:** 
  * `mBERT` (`bert-base-multilingual-cased`)
  * `XLM-R` (`xlm-roberta-base`)
* **Late Fusion:** Um classificador MLP (`MLPClassifier`) treinado sobre os logits concatenados dos dois modelos base.
* **Métrica Alvo:** F1-Score ponderado em comparação com os resultados da Tabela 5 do artigo original.

---

## ⚠️ Adaptação Metodológica Importante
Como o split `test` público disponível no mirror do Hugging Face possui rótulos de espaço reservado (*placeholders* ocultos destinados originalmente ao leaderboard oficial via GitHub Actions), foi necessário reorganizar o protocolo de avaliação:
1. O conjunto de validação (`dev`) foi dividido de forma estratificada.
2. Criou-se um subset de ajuste (`dev_fit`) para o fine-tuning e treinamento da fusão.
3. Criou-se um subset de holdout (`dev_holdout`) isolado estritamente para a avaliação final comparativa.

---

## 📊 Principais Descobertas
* **Modelos Individuais:** Reproduziram com alta fidelidade e consistência os resultados do artigo original (`XLM-R` superando consistentemente o `mBERT`).
* **Late Fusion:** A vantagem da fusão tardia reportada no paper não se sustentou de forma estável na média de múltiplas execuções, apontando para a alta sensibilidade do modelo de fusão frente à redução do tamanho efetivo do dataset adaptado.

---

## 🚀 Como Executar
O projeto foi desenvolvido para ser executado de forma interativa. 
1. Faça o upload do Jupyter Notebook para o **Google Colab** (recomenda-se a utilização de uma aba com suporte a **GPU T4**).
2. Execute as células sequencialmente. As dependências e o dataset serão baixados e configurados de forma automatizada no início do script.

---

## 📂 Estrutura do Repositório
```text
├── late_fusion_code_switched.ipynb       # Jupyter Notebook completo da reprodução
├── LICENSE                               # Arquivo de licença do projeto
└── README.md                             # Documentação do projeto
```

---
## 📜 Licença
Desenvolvido para fins acadêmicos e educacionais sob a licença MIT.
