SmartAnswer — Answer Sentence Selection on WikiQA

📌 Project Overview

SmartAnswer is a Natural Language Processing project for Answer Sentence Selection (ASS).

Given a question and a set of candidate sentences, the system ranks the candidate sentences and identifies the sentence most likely to correctly answer the question.

The project compares classical Machine Learning approaches with a Siamese LSTM model using the WikiQA dataset.

---

🎯 Problem Statement

For a given question, multiple candidate sentences may be available. The goal is to determine which sentence is the most relevant answer.

This can be useful in:

- Question answering systems
- Search and information retrieval
- Technical knowledge retrieval
- FAQ systems
- Enterprise document search
- Customer and engineering support systems

---

📊 Dataset

Dataset: WikiQA

After preprocessing:

- 29,208 question-sentence rows
- 3,044 unique questions
- Binary labels:
  - "1" → Correct answer sentence
  - "0" → Incorrect answer sentence

The dataset is highly imbalanced, with incorrect candidate sentences greatly outnumbering correct ones.

---

🔬 Approach

The project follows this pipeline:

WikiQA Dataset
      ↓
Data Cleaning & Preprocessing
      ↓
Question-Level Train/Dev/Test Split
      ↓
Feature Engineering
      ↓
Machine Learning Models
      ↓
Ranking & Evaluation

The train/dev/test split is performed at the question level to reduce the risk of information leakage between datasets.

---

🏗️ Project Architecture

                  ┌─────────────────────┐
                  │     WikiQA Dataset  │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Data Preprocessing   │
                  │ & Cleaning           │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Question-Level      │
                  │ Train/Dev/Test Split│
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Feature Engineering │
                  │                     │
                  │ TF-IDF              │
                  │ BM25                │
                  │ Jaccard             │
                  │ Word Overlap        │
                  │ Entity Overlap      │
                  │ Length Features     │
                  │ Question Type       │
                  └──────────┬──────────┘
                             │
                             ▼
              ┌──────────────────────────────┐
              │     ML Ranking Models       │
              │                              │
              │ Logistic Regression         │
              │ Random Forest               │
              │ Gradient Boosting           │
              │ SVM                         │
              │ MLP                         │
              └──────────────┬───────────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Siamese LSTM        │
                  │ Comparison          │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Ranking Evaluation  │
                  │                     │
                  │ MAP                 │
                  │ MRR                 │
                  │ Precision@1         │
                  └─────────────────────┘

🔄 End-to-End Workflow

1. Load and clean the WikiQA dataset.
2. Remove duplicate question-sentence pairs.
3. Split data at the question level to reduce data leakage.
4. Generate lexical and statistical features.
5. Train multiple classical ML models.
6. Train a Siamese LSTM for comparison.
7. Rank candidate sentences for each question.
8. Evaluate ranking quality using MAP, MRR and Precision@1.
9. Compare the performance of all evaluated models.

---

⚙️ Feature Engineering

The classical ML models use 16 engineered features, including:

Similarity Features

- TF-IDF Cosine Similarity
- Word Overlap
- Jaccard Similarity
- BM25 Score
- Entity Overlap

Length Features

- Question Length
- Sentence Length
- Length Ratio

Question-Type Features

- Who
- What
- When
- Where
- Why
- How
- Which
- Other

---

🤖 Models Evaluated

The project evaluates:

- Logistic Regression
- Random Forest
- Gradient Boosting
- SVM
- MLP
- Siamese LSTM

The Siamese LSTM uses shared weights to encode the question and candidate sentence into comparable representations.

---

📈 Results

Model| MAP| MRR| Precision@1
MLP| 0.6176| 0.6277| 0.4659
Gradient Boosting| 0.6087| 0.6201| 0.4578
SVM| 0.5972| 0.6056| 0.4337
Logistic Regression| 0.5947| 0.6049| 0.4337
Random Forest| 0.5908| 0.6025| 0.4257
Siamese LSTM| 0.5400| 0.5471| 0.3494

The MLP achieved the best reported performance among the evaluated models.

---

📏 Evaluation Metrics

Mean Reciprocal Rank (MRR)

Measures how highly the first correct answer appears in the ranked results.

Mean Average Precision (MAP)

Measures ranking quality across multiple relevant answers.

Precision@1

Measures how often the top-ranked candidate sentence is actually correct.

---

🛠️ Technology Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- TensorFlow / Keras
- NLTK
- TF-IDF
- BM25
- Jupyter Notebook

---

🌍 Real-World Applications

The answer-ranking approach can be extended to enterprise knowledge retrieval systems.

For example, in an industrial organization, it could help retrieve relevant information from:

- Technical manuals
- Product documentation
- Troubleshooting guides
- Engineering FAQs
- Internal knowledge bases
- Customer support documentation

A production system could extend this architecture with semantic embeddings, vector search, reranking and an LLM to generate grounded answers with source references.

---

🚀 Future Improvements

Possible improvements include:

- Semantic embedding-based retrieval
- Transformer/BERT-based ranking
- Vector databases
- Hybrid lexical + semantic search
- RAG-based question answering
- Confidence/answerability thresholds
- Source citation
- Human escalation for low-confidence answers
- Domain-specific enterprise datasets

---

📁 Repository Structure

SmartAnswer-WikiQA/
│
├── Notebook.ipynb
├── WikiQA.csv
├── SmartAnswer_Full_Project.pptx
├── .gitignore
└── README.md

---

👩‍💻 Project

SmartAnswer — Answer Sentence Selection on WikiQA

Developed as an NLP / Information Retrieval project focused on ranking candidate answer sentences.
