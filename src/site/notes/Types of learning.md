---
{"dg-publish":true,"permalink":"/types-of-learning/","created":"2026-10-05T18:14:36.479+01:00","updated":"2026-10-05T19:53:41.105+01:00","dg-note-properties":{}}
---

#ml 
First, a tiny bit of shared vocabulary:

- **Features** = the input information. E.g., age, income, pixels of an image.
- **Label** = the desired output/answer. E.g., “spam”, “cat”, “price = $300k”.
- **Model** = the learned thing that maps features to outputs.
- **Training** = the process of learning the model from data.
- **Prediction/Inference** = using the model on new data.

Now, the learning types differ mainly in **what kind of experience the algorithm gets** and **what it’s trying to achieve**.

---

## 1. Supervised Learning 🤝

**Intuition:**  
You learn from examples where the correct answer is already known. Like studying with flashcards that have the answer on the back. 

**Data:**  
Every training example has:
- features (inputs)
- a label (the correct output)

Example:

| Size (m²) | Rooms | Price |
|-----------|-------|-------|
| 50        | 2     | 150k  |
| 80        | 3     | 250k  |
| 120       | 4     | 400k  |

Here, `Size` and `Rooms` are features, `Price` is the label.

**Objective:**  
Learn a function that predicts the label from the features, and **generalises** to new, unseen examples.

**Two main sub-types:**
- **Regression:** predict a continuous number (e.g., price, temperature).
- **Classification:** predict a category (e.g., spam/not spam, cat/dog , pizza 🍕 or not pizza💔).

**Examples:**
- Predicting apartment prices (regression).
- Classifying emails as spam or not spam (classification).
- Medical diagnosis from symptoms.

**Typical algorithms:**
- Linear Regression
- Logistic Regression
- Decision Trees
- Support Vector Machines (SVM)
- Neural Networks

**Key point:**  
Supervised learning needs labeled data. The quality and quantity of labels matter a lot. If labels are wrong, the model learns wrong things.

---

## 2. Unsupervised Learning 🛞

**Intuition:**  
You’re given a pile of objects with no labels, and you’re asked to find patterns or group similar ones. Like organising a messy room without being told what the categories are. 👕📕 🗄️

**Data:**  
Only features. No labels.

Example:

| Age | Income | Purchases/month |
|-----|--------|-----------------|
| 25  | 40k    | 3               |
| 45  | 80k    | 1               |
| 32  | 55k    | 5               |

There’s no “correct answer” column.

**Objective:**  
Discover hidden structure in the data. Common goals:
- **Clustering:** group similar points together.
- **Dimensionality reduction:** compress many features into fewer meaningful ones.
- **Density estimation:** understand how data is distributed.

**Examples:**
- Segmenting customers into groups based on buying behaviour.
- Reducing image dimensions with PCA.
- Finding anomalies or outliers.

**Typical algorithms:**
- K-means
- DBSCAN
- Hierarchical clustering
- PCA (Principal Component Analysis)
- t-SNE

**Key point:**  
There is no label to predict, so evaluation is harder. You often need domain knowledge to interpret the discovered structure.

---

## 3. Semi-Supervised Learning

**Intuition:**  
A mix of the previous two. You have a **small amount of labeled data** and a **large amount of unlabeled data**. Like a teacher giving you answers for only a few flashcards, but you have thousands of unlabeled ones.

**Data:**  
- A few examples with labels.
- Many examples without labels.

**Objective:**  
Use the unlabeled data to improve learning, because labeling is often expensive💸, slow❄️, or requires experts👓️.

**Why it helps:**  
The unlabeled data can reveal the underlying structure of the data distribution. For example, if you know that certain points are close together, a label for one can help infer labels for its neighbours.

**Examples:**
- Medical imaging: only a few images are annotated by doctors, thousands are not.
- Spam detection: a few labeled emails, many unlabeled.
- Speech recognition.

**Typical algorithms:**
- Semi-supervised SVM
- Generative models (e.g., Gaussian mixtures with some labels)
- Self-training (model labels unlabeled data, then retrains)

**Key point:**  
It’s not “unsupervised with a bit of supervision” — it’s a deliberate blend. The unlabeled data is used as a guide, not as a source of direct answers.

---

## 4. [[Reinforcement Learning\|Reinforcement Learning]] (RL)

**Intuition:**  
An agent learns by interacting with an environment. It takes actions, receives rewards or penalties, and sees the new state. Like training a dog with treats: good behaviour gets a treat, bad behaviour gets nothing.

**Data:**  
Not a fixed dataset. Instead, the agent generates its own experience through trial and error.

Key elements:
- **Agent:** the learner/decision maker.
- **Environment:** the world it interacts with.
- **State:** current situation.
- **Action:** what the agent can do.
- **Reward:** feedback signal (positive/negative).
- **Policy:** the strategy mapping states to actions.

**Objective:**  
Learn an optimal policy that maximises cumulative reward over time.

**Examples:**
- Playing video games (AlphaGo, Atari, Mario).
- Robot walking.
- Traffic light control.
- Resource management (energy, logistics).

**Typical algorithms:**
- Q-learning
- SARSA
- Policy Gradient
- Deep Q-Networks (DQN)

**Key point:**  
There’s no labeled “correct action” at each step. The agent must explore and learn from delayed rewards. It’s about sequential decision making.

---

## 5. Self-Learning / Self-Supervised Learning

**Intuition:**  
The model learns from raw data by **creating its own labels** from the data itself. No human labels are needed. It’s like reading a book and covering up some words, then trying to predict the missing words.

**Data:**  
Raw data (text, images, audio) with no human-provided labels.

**Objective:**  
Learn useful representations or features by solving an auxiliary task (called a **pretext task**) where the labels are automatically generated from the data.

**Examples of pretext tasks:**
- Predict the next word in a sentence (used by GPT).
- Fill in missing words (used by BERT).
- Predict whether two image patches come from the same image (contrastive learning).
- Colourise a grayscale image.

**Why it’s powerful:**  
It allows models to learn from massive amounts of unlabeled data (e.g., all of Wikipedia, billions of images). This is how modern large language models are pre-trained.

**Typical algorithms:**
- Transformers (BERT, GPT)
- Contrastive learning (SimCLR)
- Autoencoders

**Key point:**  
Different from semi-supervised: here, **no human labels at all**. The supervision comes from the data’s own structure. After pre-training, the model can be fine-tuned on a small labeled dataset for a specific task.

---

## Quick comparison table

| Type            | Labels?                         | Goal                   | Example               |
| --------------- | ------------------------------- | ---------------------- | --------------------- |
| Supervised      | All labeled                     | Predict output         | Spam classification   |
| Unsupervised    | None                            | Find structure         | Customer segmentation |
| Semi-supervised | Few labeled + many unlabeled    | Improve with unlabeled | Medical imaging       |
| Reinforcement   | No labels, rewards              | Learn optimal policy   | Game playing          |
| Self-supervised | No human labels, self-generated | Learn representations  | BERT, GPT             |
[[semi vs self\|semi vs self]]
[[Unsupervised vs Self-supervised\|Unsupervised vs Self-supervised]]

---

## How to think about them

- **Supervised** = learning with an answer key.
- **Unsupervised** = learning without an answer key, just patterns.
- **Semi-supervised** = a few answers, many questions.
- **Reinforcement** = learning by doing, with rewards.
- **Self-supervised** = making your own answer key from the data.

Each type has its own strengths and is suited to different problems. The choice depends on what data you have and what you want to achieve.

