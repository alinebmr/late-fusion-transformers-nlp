# Reprodução Parcial: Late Fusion of Transformers for Sentiment Analysis of Code-Switched Data

Este repositório contém a reprodução parcial do artigo **"Late Fusion of Transformers for Sentiment Analysis of Code-Switched Data"** (Sharma, Chinmay & Sharma, EMNLP 2023). 

O projeto implementa um pipeline completo utilizando **PyTorch**, **Hugging Face Transformers** e **Scikit-Learn** focado na análise de sentimentos em textos bilíngues (*Code-Switched* Inglês-Espanhol do benchmark GLUECoS)[cite: 2].

---

## 🔍 Escopo da Reprodução
* **Dataset:** `Huggmachas/GLuecos_Sentiment_EN_ES` (via Hugging Face Datasets)[cite: 2].
* **Modelos Individuais:** 
  * `mBERT` (`bert-base-multilingual-cased`)[cite: 2]
  * `XLM-R` (`xlm-roberta-base`)[cite: 2]
* **Late Fusion:** Um classificador MLP (`MLPClassifier`) treinado sobre os logits concatenados dos dois modelos base[cite: 2].
* **Métrica Alvo:** F1-Score ponderado em comparação com os resultados da Tabela 5 do artigo original[cite: 2].

---

## ⚠️ Adaptação Metodológica Importante
Como o split `test` público disponível no mirror do Hugging Face possui rótulos de espaço reservado (*placeholders* ocultos destinados originalmente ao leaderboard oficial via GitHub Actions), foi necessário reorganizar o protocolo de avaliação[cite: 2]:
1. O conjunto de validação (`dev`) foi dividido de forma estratificada[cite: 2].
2. Criou-se um subset de ajuste (`dev_fit`) para o fine-tuning e treinamento da fusão[cite: 2].
3. Criou-se um subset de holdout (`dev_holdout`) isolado estritamente para a avaliação final comparativa[cite: 2].

---

## 📊 Principais Descobertas
* **Modelos Individuais:** Reproduziram com alta fidelidade e consistência os resultados do artigo original (`XLM-R` superando consistentemente o `mBERT`)[cite: 2].
* **Late Fusion:** A vantagem da fusão tardia reportada no paper não se sustentou de forma estável na média de múltiplas execuções, apontando para a alta sensibilidade do modelo de fusão frente à redução do tamanho efetivo do dataset adaptado[cite: 2].

---

## 🚀 Como Executar
O projeto foi desenvolvido para ser executado de forma interativa. 
1. Faça o upload do Jupyter Notebook para o **Google Colab** (recomenda-se a utilização de uma aba com suporte a **GPU T4**)[cite: 2].
2. Execute as células sequencialmente. As dependências e o dataset serão baixados e configurados de forma automatizada no início do script[cite: 2].

---

## 📂 Estrutura do Repositório
```text
├── late_fusion_code_switched.ipynb       # Jupyter Notebook completo da reprodução
├── LICENSE                               # Arquivo de licença do projeto
└── README.md                             # Documentação do projeto