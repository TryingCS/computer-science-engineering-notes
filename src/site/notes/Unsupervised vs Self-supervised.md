---
{"dg-publish":true,"permalink":"/unsupervised-vs-self-supervised/","dg-note-properties":{}}
---

#ml
Both use **unlabeled data**. But they are different in **goal**, **training signal**, and **what the model learns**.

---

## The core difference in one sentence

- **Unsupervised learning** tries to **discover hidden structure** in the data (e.g., groups, patterns, compressed representations) **without any labels**.
- **Self-supervised learning** tries to **learn useful representations** by **creating its own labels** from the data and solving a **prediction task** — it’s like ==supervised learning, but the labels are generated automatically==.

So:  
**Unsupervised = find structure.  
Self-supervised = solve a fake prediction task to learn features.**

---

## 1. Unsupervised learning

**Goal:** Explore the data, find patterns, group similar points, reduce dimensions, estimate densities.

**Training signal:** No labels at all. The algorithm optimises an internal objective like:
- Minimise distance within clusters (K-means)
- Maximise variance captured (PCA)
- Maximise likelihood of the data (density estimation)

**Typical tasks:**
- Clustering (K-means, DBSCAN, hierarchical)
- Dimensionality reduction (PCA, t-SNE)
- Anomaly detection
- Association rules

**Output:** Usually a structure: cluster assignments, principal components, a lower-dimensional embedding.

**Example:**  
You have customer data (age, income, purchases). You run K-means and get 3 groups. You don’t know what the groups mean, but you can inspect them and label them later (e.g., “young spenders”, “older savers”). The algorithm never predicted anything; it just grouped.

**Analogy:**  
You’re given a box of mixed Lego pieces and asked to sort them into piles. No one tells you what the piles should be. You just group similar pieces together.

---

## 2. Self-supervised learning

**Goal:** Learn **general-purpose representations** (features) that can later be used for many downstream tasks.

**Training signal:** No human labels, but the algorithm **creates labels automatically** from the data. It solves a **pretext task** — a fake supervised problem.

**Common pretext tasks:**
- **Masked language modeling:** hide a word in a sentence, predict it. (BERT)
- **Next word prediction:** predict the next token. (GPT)
- **Image rotation prediction:** rotate an image by 0°, 90°, 180°, 270°; predict the rotation.
- **Contrastive learning:** given two augmented views of the same image, learn to recognise they are similar; different images are dissimilar. (SimCLR)
- **Colorisation:** turn grayscale into color.

**Output:** A pre-trained model (e.g., a neural network) that has learned rich features. You then **fine-tune** it on a small labeled dataset for a specific task (e.g., sentiment classification, object detection).

**Example:**  
You take billions of sentences. You hide 15% of words and train a model to predict them. After training, the model understands grammar, facts, and some reasoning. Then you fine-tune it on 1000 labeled movie reviews to classify sentiment. The self-supervised step gave it a huge head start.

**Analogy:**  
You’re given a huge book with some words blanked out. Your task is to fill in the blanks. By doing this millions of times, you learn the language deeply. Later, you can use that knowledge to answer questions or write essays.

---

## 3. Key differences in a table

| Aspect | Unsupervised | Self-supervised |
|--------|-------------|-----------------|
| **Labels** | None | None from humans, but automatically generated from data |
| **Training objective** | Find structure (clusters, components) | Solve a prediction task (masked word, next token, rotation) |
| **Output** | Structure (clusters, embeddings) | A pre-trained model (representations) |
| **Typical algorithms** | K-means, PCA, DBSCAN, t-SNE | BERT, GPT, SimCLR, autoencoders (some) |
| **Evaluation** | Hard; often needs domain knowledge | Can measure pretext task accuracy; downstream tasks show quality |
| **Goal** | Explore data | Learn features for transfer learning |
| **Is it supervised?** | No | No human labels, but the setup mimics supervised learning |

---

## 4. Why self-supervised is not just unsupervised

In unsupervised learning, there is **no prediction**. You’re not trying to guess anything; you’re just finding patterns.

In self-supervised learning, you **do predict something** — a masked word, a rotation angle, whether two images match. The labels are free, but they are labels. So the training loop looks exactly like supervised learning: input → prediction → loss → update. The only difference is that the labels come from the data itself, not from a human annotator.

So self-supervised is sometimes called **“supervised learning with free labels”** or **“self-supervision”**. It sits between unsupervised and supervised: it uses unlabeled data, but it learns by solving a supervised-like task.

---

## 5. Examples to cement the difference

**Unsupervised:**  
You have 10,000 images of handwritten digits. You run PCA to reduce them to 2D. You see clusters but you don’t know which digit each cluster represents. You never predicted anything.

**Self-supervised:**  
You have 10,000 images of handwritten digits. You create a task: take each image, rotate it by a random angle, and train a model to predict the rotation. After training, the model has learned useful features of digits. Then you fine-tune it on a few labeled digits to classify 0–9. The rotation prediction was the pretext task; it gave the model a good starting point.

---

## 6. Why it matters

- **Unsupervised** is great for exploration and when you have no labels at all and just want to understand your data.
- **Self-supervised** is the engine behind modern large models (BERT, GPT, CLIP). It allows models to learn from massive unlabeled data (text, images, audio) and then be adapted to many tasks with little labeled data.

In short:

> **Unsupervised** = “I have no labels. Let me find structure.”  
> **Self-supervised** = “I have no labels, but I can create a fake prediction task to learn useful features.”

Both use unlabeled data, but self-supervised turns it into a supervised-like problem to learn representations.
