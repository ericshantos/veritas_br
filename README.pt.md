[🇬🇧] [Read in English](README.md)

# 🧠 Sistema de Classificação de Notícias Falsas (PT-BR)

O VeritasBR é um sistema híbrido de deep learning para detecção de fake news em português, combinando o poder semântico do BERT com a modelagem sequencial das redes BiLSTM.

O projeto foi desenvolvido com o objetivo de combater a desinformação em língua portuguesa utilizando técnicas modernas de Processamento de Linguagem Natural (PLN) e arquiteturas baseadas em Transformers.

---

## 🤗 Modelo no Hugging Face

O modelo treinado está disponível publicamente no Hugging Face Hub:

👉 [https://huggingface.co/ericshantos/veritasseq/](https://huggingface.co/ericshantos/veritasseq/)

---

# 🚀 Objetivo

Desenvolver um sistema automático de classificação de notícias capaz de identificar se uma notícia é **verdadeira** ou **falsa** em português.

O projeto possui foco em:

* Compreensão semântica textual.
* Análise contextual sequencial.
* Generalização robusta através da expansão de dados.
* Aplicabilidade real no combate à desinformação.

---

# 🧪 Tecnologias Utilizadas

* Python
* PyTorch
* Pandas
* NumPy
* Scikit-learn
* Hugging Face Transformers
* Jupyter Notebook
* BERTimbau
* BiLSTM

---

# 📈 Evolução do Projeto VeritasBR

O VeritasBR passou por diversas evoluções arquiteturais ao longo do desenvolvimento, buscando melhorar continuamente a compreensão contextual e semântica na classificação de fake news.

## 🥇 Fase 1 — LSTM Tradicional

As primeiras versões do projeto utilizavam redes LSTM (Long Short-Term Memory).

O objetivo inicial era validar se arquiteturas recorrentes seriam capazes de aprender padrões linguísticos em notícias falsas em português.

### Características

* Processamento sequencial do texto.
* Aprendizado contextual através de memória recorrente.
* Representação textual baseada em embeddings.
* Arquitetura leve e computacionalmente eficiente.

### Limitações

Apesar dos bons resultados obtidos, arquiteturas recorrentes tradicionais ainda apresentavam dificuldades em:

* Compreensão semântica profunda.
* Dependências contextuais de longa distância.
* Ambiguidades linguísticas.
* Representações contextuais mais ricas.

---

## 🥈 Fase 2 — BERT Baseado em Transformers

Para superar as limitações das redes recorrentes tradicionais, o VeritasBR evoluiu para arquiteturas Transformer utilizando o BERTimbau.

A introdução do BERT representou um grande salto na capacidade de compreensão semântica.

### Melhorias Obtidas

* Embeddings contextuais bidirecionais.
* Representação semântica profunda.
* Melhor interpretação de linguagem ambígua.
* Maior percepção contextual.

### Por que BERT?

Diferentemente de embeddings tradicionais, o BERT gera representações dinâmicas para cada token de acordo com o contexto da sentença.

Isso permitiu que o VeritasBR compreendesse melhor estruturas linguísticas presentes em fake news e padrões sutis de manipulação textual.

---

## 🥉 Fase 3 — Arquitetura Híbrida BERT + BiLSTM

A versão atual do VeritasBR adota uma arquitetura híbrida que combina:

* BERTimbau para codificação semântica.
* BiLSTM (Bidirectional LSTM) para refinamento sequencial.

A motivação dessa abordagem é que, embora o BERT capture contexto semântico de forma extremamente eficiente, camadas BiLSTM ainda podem aprimorar dependências temporais e relações sequenciais.

Essa combinação permite:

* Preservar embeddings ricos gerados pelo Transformer.
* Melhorar a memória contextual sequencial.
* Aumentar a consistência da classificação.
* Modelar padrões sutis de desinformação.

A arquitetura híbrida representa atualmente o estado mais avançado do projeto.

---

# 📂 Expansão do Dataset

A versão atual do VeritasBR utiliza uma base consolidada composta por três grandes datasets de fake news em português:

| Fonte          | Descrição                                               |
| -------------- | ------------------------------------------------------- |
| Fake.br-Corpus | Dataset de referência contendo notícias reais e falsas. |
| FakeTrue.Br    | Base complementar de notícias falsas em português.      |
| FakeRecogna    | Dataset expandido com maior diversidade temática.       |

## 📊 Estatísticas

* Volume total: ~22.684 notícias.
* Divisão estratificada:

  * 90% treino
  * 10% teste

Essa expansão aumentou significativamente a capacidade de generalização semântica do modelo.

---

# 🧠 Arquitetura do Modelo — BERT + BiLSTM

O VeritasBR utiliza uma arquitetura híbrida composta por:

* BERTimbau para extração semântica profunda.
* Camadas BiLSTM para refinamento contextual sequencial.

## 🔍 Fluxo da Arquitetura

```text
Texto de Entrada
        ↓
Tokenizador BERT
        ↓
Encoder BERTimbau
        ↓
Embeddings Contextuais
        ↓
Camada BiLSTM
        ↓
Pooling / Camadas Densas
        ↓
Classificação Binária
```

## ⚙️ Componentes

### Encoder

* `neuralmind/bert-base-portuguese-cased`

### Camada Sequencial

* Bidirectional LSTM (BiLSTM)
* Captura dependências de longo alcance em ambas as direções.

### Cabeça de Classificação

* Camadas densas.
* Ativação GELU.
* Regularização com Dropout.
* Saída binária.

### Otimização

* Adam Optimizer.
* Fine-tuning supervisionado.
* Binary Cross Entropy Loss.

---

# ⚙️ Pipeline de Dados

O projeto implementa um pipeline modular de extração e pré-processamento.

## 📥 Extração

Extratores personalizados processam:

* `.txt` (Fake.br-Corpus)
* `.csv` (FakeTrue.Br)
* `.xlsx` (FakeRecogna)

## 🧹 Pré-processamento

* Remoção de valores nulos.
* Normalização de labels.
* Padronização textual.

## 🔤 Tokenização

* WordPiece Tokenizer do BERT.
* Comprimento máximo: `256` tokens.

## 🚚 Otimizações do DataLoader

* `pin_memory=True`
* `prefetch_factor`
* Estratégias otimizadas para GPU.

---

# 🏋️ Treinamento

## 📌 Configuração de Fine-Tuning

| Hiperparâmetro  | Valor                |
| --------------- | -------------------- |
| Learning Rate   | ~2e-5                |
| Batch Size      | 32                   |
| Otimizador      | Adam                 |
| Função de Perda | Binary Cross Entropy |
| GPU             | Recomendado          |

---

# 📊 Resultados

A arquitetura híbrida BERT + BiLSTM melhora significativamente a compreensão contextual em comparação com abordagens tradicionais baseadas apenas em LSTM.

## ✨ Melhorias Obtidas

* Melhor compreensão semântica.
* Refinamento sequencial bidirecional.
* Maior consistência contextual.
* Classificação mais robusta.

Arquiteturas LSTM tradicionais continuam eficientes, porém a integração com BERT amplia significativamente a representação linguística.

![Result](./assets/result.png)

---

# 🚀 Como Utilizar o Modelo

O modelo híbrido treinado do VeritasBR está disponível publicamente no Hugging Face Hub no formato `.pth`.

## 📥 Download dos Pesos

Baixe os pesos do modelo em:

👉 [https://huggingface.co/ericshantos/veritasseq](https://huggingface.co/ericshantos/veritasseq)

Arquivo de pesos:

```text
veritasseq_v3_0.pth
```

---

## 🐍 Criando um Ambiente Conda (Máquina Nativa)

Caso esteja executando o projeto localmente, recomenda-se criar um ambiente isolado utilizando Conda.

### 1️⃣ Criar o ambiente

```bash
conda create -n veritas python=3.11
```

### 2️⃣ Ativar o ambiente

```bash
conda activate veritas
```

### 3️⃣ Instalar as dependências

```bash
conda install torch matplotlib numpy pytorch sklearn
```

---

# ▶️ Executando o Projeto

## 1️⃣ Clone o repositório

```bash
git clone https://github.com/ericshantos/veritasBR.git
```

## 2️⃣ Crie e ative o ambiente Conda

```bash
conda create -n veritas python=3.11
conda activate veritas
```

## 3️⃣ Ative o ambiente virtual

```bash
conda activate veritas
```

## 4️⃣ Baixe os pesos do modelo

Baixe:

```text
veritasseq_v3_0.pth
```

no Hugging Face Hub e coloque o arquivo dentro do diretório do projeto.

## 5️⃣ Abra o notebook de treinamento

```bash
jupyter notebook veritasBR.ipynb
```

---

# 💡 Insights da Pesquisa

## 🔹 Por que combinar BERT e BiLSTM?

Embora o BERT já capture informações contextuais profundas, camadas BiLSTM conseguem refinar dependências sequenciais e melhorar a consistência da classificação.

Essa abordagem híbrida é especialmente eficiente para:

* Sequências textuais longas.
* Notícias linguisticamente ambíguas.
* Fake news com manipulações semânticas sutis.

## 🔹 Principais Vantagens

* Melhor representação semântica.
* Análise sequencial bidirecional.
* Memória contextual mais robusta.
* Maior robustez geral.

---

# 🔬 Melhorias Futuras

Possíveis evoluções futuras incluem:

* Multi-task Learning.
* Enriquecimento semântico.
* Técnicas de Explainable AI.
* Visualização de atenção.
* Integração com grafos de conhecimento.
* Filtragem de desinformação baseada em reinforcement learning.

---

# 💐 Agradecimentos

Dedico este projeto aos professores e mentores que contribuíram para minha formação em tecnologia, pensamento crítico e pesquisa científica.

Agradeço especialmente às pessoas que incentivaram a curiosidade, o questionamento e a busca pelo conhecimento.

---

# 📜 Licença

Este projeto está licenciado sob a licença MIT.

Veja o arquivo `LICENSE` para mais detalhes.

---

# 👨‍💻 Autor

Desenvolvido por Eric dos Santos 🚀
