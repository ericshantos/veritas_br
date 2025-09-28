[🇬🇧] [Read in English](README.md)

# Sistema de Classificação de Notícias Falsas

Este repositório contém um modelo de machine learning treinado para detectar fake news em português, utilizando o dataset [Fake.br-Corpus](https://github.com/roneysco/Fake.br-Corpus). O objetivo é criar uma rede neural capaz de distinguir notícias falsas de verdadeiras, auxiliando no combate à desinformação.

## 📌 Tecnologias Utilizadas
- Python
- Pandas
- TensorFlow/Keras
- Scikit-learn
- SpaCy
- Unidecode
- Google Colab

## 📂 Estrutura do Projeto
```
/
├── br_fake_news_predict_model.ipynb  # Notebook principal
├── br_fake_news_predict_model.keras  # Modelo treinado salvo
└── Fake.br-Corpus/                   # Dataset utilizado
```

## 🔍 Como Executar o Projeto

1. **Clone o repositório e instale as dependências:**
```bash
!git clone https://github.com/ericshantos/br_fake_news_detector_model.git
```

2. **Baixe o dataset Fake.br-Corpus:**

> Ao execultar a primeira célula do caderno, é possível fazer o download do dataset

```bash
!git clone https://github.com/roneysco/Fake.br-Corpus
```

1. **Execute o Jupyter Notebook no Google Colab ou localmente:**
   - Google Colab: [Executar no Colab](https://colab.research.google.com/github/ericshantos/br_fake_news_detector_model/blob/main/br_fake_news_detector_model.ipynb)
   - Localmente: `jupyter notebook br_fake_news_predict_model.ipynb`

## 🗂️ Preparação dos Dados

O dataset Fake.br-Corpus possui notícias reais e falsas em português, organizadas em arquivos de texto. O script realiza:
- **Leitura e extração das notícias** (fake e reais)
- **Limpeza dos textos** (remoção de stopwords, pontuação e acentuação)
- **Tokenização** para transformar palavras em números
- **Divisão do dataset** em treinamento (80%) e teste (20%)

## 📊 Construção do Modelo

A rede neural implementada utiliza:
- **Camada de Embedding** para transformar palavras em vetores densos
- **Três camadas LSTM** para aprendizado de padrões textuais
- **Camadas de Dropout** para evitar overfitting
- **Camada densa com ativação sigmoid** para classificação binária

## ⚙️ Treinamento e Avaliação

O modelo foi treinado com os seguintes parâmetros:
- **Épocas**: 5
- **Batch size**: 128
- **Otimização**: Adam
- **Loss function**: Binary Crossentropy

### 🎯 Resultados
Após o treinamento, o modelo atingiu uma precisão satisfatória ao classificar notícias reais e falsas. Alcançando o valor de acurácia de 93% sobre o conjunto de teste:

![](./assets/result.png)

## 💾 Salvando o Modelo
O modelo treinado é salvo no formato Keras para ser reutilizado em outras aplicações:
```python
model.save("br_fake_news_predict_model.keras")
```

## 💐 Agradecimentos

Dedico a construção deste modelo a todos os meus professores do Ensino Médio, dos quais, de todos os ensinamentos que me transmitiram, o senso crítico foi primordial para fundamentar esta aplicação.

Uma menção especial à professora Winola Cunha, que, por diversas vezes, me instruiu a prestar atenção na aula de morfossintaxe, pois eu precisaria disso um dia.

## 📜 Licença

Este projeto está licenciado sob a MIT License. Consulte o arquivo LICENSE para mais detalhes.

---
**Criado por [Eric dos Santos](https://github.com/ericshantos)** 🚀