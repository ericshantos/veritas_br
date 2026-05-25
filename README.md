[🇧🇷] [Leia em Português](README.pt.md)

# 🧠 Fake News Classification System (PT-BR)

VeritasBR is a hybrid deep learning system for fake news detection in Portuguese, combining the semantic power of BERT with the sequential modeling capabilities of BiLSTM networks.

The project was developed with the goal of combating misinformation in Portuguese using modern Natural Language Processing (NLP) techniques and Transformer-based architectures.

---

## 🤗 Model on Hugging Face

The trained model is publicly available on the Hugging Face Hub:

👉 [https://huggingface.co/ericshantos/veritasseq/](https://huggingface.co/ericshantos/veritasseq)

---

# 🚀 Objective

To develop an automatic news classification system capable of identifying whether a news article is **true** or **false** in Portuguese.

The project focuses on:

* Semantic textual understanding.
* Sequential contextual analysis.
* Robust generalization through dataset expansion.
* Real-world applicability against misinformation.

---

# 🧪 Technologies Used

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

# 📈 Evolution of the VeritasBR Project

VeritasBR has gone through several architectural evolutions during development, continuously seeking improvements in contextual and semantic understanding for fake news classification.

## 🥇 Phase 1 — Traditional LSTM

The first versions of the project used traditional LSTM (Long Short-Term Memory) networks.

The initial objective was to validate whether recurrent architectures could effectively learn linguistic patterns in Portuguese fake news.

### Characteristics

* Sequential text processing.
* Contextual learning through recurrent memory.
* Embedding-based textual representation.
* Lightweight and computationally efficient architecture.

### Limitations

Despite achieving good results, traditional recurrent architectures still struggled with:

* Deep semantic understanding.
* Long-range contextual dependencies.
* Linguistic ambiguities.
* Richer contextual representations.

---

## 🥈 Phase 2 — Transformer-Based BERT

To overcome the limitations of traditional recurrent networks, VeritasBR evolved toward Transformer architectures using BERTimbau.

The introduction of BERT represented a major leap in semantic understanding capabilities.

### Improvements Achieved

* Bidirectional contextual embeddings.
* Deep semantic representation.
* Better interpretation of ambiguous language.
* Stronger contextual awareness.

### Why BERT?

Unlike traditional embeddings, BERT generates dynamic representations for each token according to the sentence context.

This allowed VeritasBR to better understand linguistic structures present in fake news and subtle patterns of textual manipulation.

---

## 🥉 Phase 3 — Hybrid BERT + BiLSTM Architecture

The current version of VeritasBR adopts a hybrid architecture combining:

* BERTimbau for semantic encoding.
* BiLSTM (Bidirectional LSTM) for sequential refinement.

The motivation behind this approach is that, although BERT captures semantic context extremely well, BiLSTM layers can still improve temporal dependencies and sequential relationships.

This combination allows the model to:

* Preserve rich Transformer-generated embeddings.
* Improve sequential contextual memory.
* Increase classification consistency.
* Model subtle misinformation patterns.

The hybrid architecture currently represents the most advanced stage of the project.

---

# 📂 Dataset Expansion

The current version of VeritasBR uses a consolidated dataset composed of three major Portuguese fake news datasets:

| Source         | Description                                               |
| -------------- | --------------------------------------------------------- |
| Fake.br-Corpus | Reference dataset containing real and fake news articles. |
| FakeTrue.Br    | Complementary Portuguese fake news dataset.               |
| FakeRecogna    | Expanded dataset with greater thematic diversity.         |

## 📊 Statistics

* Total volume: ~22,684 news articles.
* Stratified split:

  * 90% training
  * 10% testing

This expansion significantly improved the model's semantic generalization capability.

---

# 🧠 Model Architecture — BERT + BiLSTM

VeritasBR uses a hybrid architecture composed of:

* BERTimbau for deep semantic extraction.
* BiLSTM layers for sequential contextual refinement.

## 🔍 Architecture Flow

```text
Input Text
        ↓
BERT Tokenizer
        ↓
BERTimbau Encoder
        ↓
Contextual Embeddings
        ↓
BiLSTM Layer
        ↓
Pooling / Dense Layers
        ↓
Binary Classification
```

## ⚙️ Components

### Encoder

* `neuralmind/bert-base-portuguese-cased`

### Sequential Layer

* Bidirectional LSTM (BiLSTM)
* Captures long-range dependencies in both directions.

### Classification Head

* Dense layers.
* GELU activation.
* Dropout regularization.
* Binary output.

### Optimization

* Adam Optimizer.
* Supervised fine-tuning.
* Binary Cross Entropy Loss.

---

# ⚙️ Data Pipeline

The project implements a modular extraction and preprocessing pipeline.

## 📥 Extraction

Custom extractors process:

* `.txt` (Fake.br-Corpus)
* `.csv` (FakeTrue.Br)
* `.xlsx` (FakeRecogna)

## 🧹 Preprocessing

* Null value removal.
* Label normalization.
* Text standardization.

## 🔤 Tokenization

* BERT WordPiece Tokenizer.
* Maximum length: `256` tokens.

## 🚚 DataLoader Optimizations

* `pin_memory=True`
* `prefetch_factor`
* GPU-optimized loading strategies.

---

# 🏋️ Training

## 📌 Fine-Tuning Configuration

| Hyperparameter | Value                |
| -------------- | -------------------- |
| Learning Rate  | ~2e-5                |
| Batch Size     | 32                   |
| Optimizer      | Adam                 |
| Loss Function  | Binary Cross Entropy |
| GPU            | Recommended          |

---

# 📊 Results

The hybrid BERT + BiLSTM architecture significantly improves contextual understanding compared to traditional LSTM-only approaches.

## ✨ Improvements Achieved

* Better semantic understanding.
* Bidirectional sequential refinement.
* Greater contextual consistency.
* More robust classification.

Traditional LSTM architectures remain efficient, but integration with BERT significantly enhances linguistic representation.

![Result](./assets/result.png)

---

# 🚀 How to Use the Model

The trained VeritasBR hybrid model is publicly available on the Hugging Face Hub in `.pth` format.

## 📥 Download the Weights

Download the model weights from:

👉 [https://huggingface.co/ericshantos/veritasseq](https://huggingface.co/ericshantos/veritasseq?utm_source=chatgpt.com)

Weight file:

```text
veritasseq_v3_0.pth
```

---

## 🐍 Creating a Conda Environment (Native Machine)

If you are running the project locally, it is recommended to create an isolated Conda environment.

### 1️⃣ Create the environment

```bash
conda create -n veritas python=3.11
```

### 2️⃣ Activate the environment

```bash
conda activate veritas
```

### 3️⃣ Install dependencies

```bash
conda install torch matplotlib numpy pytorch sklearn
```

---

# ▶️ Running the Project

## 1️⃣ Clone the repository

```bash
git clone https://github.com/ericshantos/veritasBR.git
```

## 2️⃣ Create and activate the Conda environment

```bash
conda create -n veritas python=3.11
conda activate veritas
```

## 3️⃣ Active the virtual environment

```bash
conda activate veritas
```

## 4️⃣ Download the model weights

Download:

```text
veritasseq_v3_0.pth
```

from the Hugging Face Hub and place the file inside the project directory.

## 5️⃣ Open the training notebook

```bash
jupyter notebook veritasBR.ipynb
```

---

# 💡 Research Insights

## 🔹 Why combine BERT and BiLSTM?

Although BERT already captures deep contextual information, BiLSTM layers can further refine sequential dependencies and improve classification consistency.

This hybrid approach is especially effective for:

* Long textual sequences.
* Linguistically ambiguous news.
* Fake news with subtle semantic manipulation.

## 🔹 Main Advantages

* Better semantic representation.
* Bidirectional sequential analysis.
* Stronger contextual memory.
* Greater overall robustness.

---

# 🔬 Future Improvements

Possible future evolutions include:

* Multi-task Learning.
* Semantic enrichment.
* Explainable AI techniques.
* Attention visualization.
* Knowledge graph integration.
* Reinforcement learning-based misinformation filtering.

---

# 💐 Acknowledgments

I dedicate this project to the teachers and mentors who contributed to my development in technology, critical thinking, and scientific research.

Special thanks to everyone who encouraged curiosity, questioning, and the pursuit of knowledge.

---

# 📜 License

This project is licensed under the MIT License.

See the `LICENSE` file for more details.

---

# 👨‍💻 Author

Developed by Eric dos Santos 🚀
