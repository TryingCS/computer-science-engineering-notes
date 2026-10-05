---
{"dg-publish":true,"permalink":"/semi-vs-self/","dg-note-properties":{}}
---

#ml 
## Why can unlabeled data help in semi-supervised learning?

The key idea:

> **Unlabeled data tells you about the *structure* of the data — where the points lie, how they cluster, what the boundaries might be — even though it doesn't tell you the correct labels.**

Knowing the structure helps you place decision boundaries better, especially when you have very few labeled points.

### Concrete example

Imagine you're classifying emails as spam / not spam. You have:

- **10 labeled emails** (5 spam, 5 not spam)
- **10,000 unlabeled emails**

Now, if you only use the 10 labeled emails, you might draw a decision boundary that seems okay but is actually wrong — because 10 points is too few to see the true shape of the data.

But the 10,000 unlabeled emails tell you:
- What the data distribution looks like.
- Which emails are similar to each other.
- Where the natural clusters are.

For instance, if the unlabeled data forms two clear clusters, and your labeled spam examples fall mostly in one cluster, you can infer that the other cluster is probably “not spam” — even without labels for those points.

### Visual intuition

Think of two classes as two islands in a sea of data points. With only a few labeled points, you don't know where the shorelines are. But if you see thousands of unlabeled points, you can see the shape of the islands. The unlabeled points don't tell you which island is “spam” and which is “not spam”, but they tell you **where the islands are**. That helps you draw a much better boundary.


### So yes — semi-supervised learning says:

> **A small amount of labeled data + a large amount of unlabeled data can outperform a small amount of labeled data alone.**

Because the unlabeled data provides structural information that the labeled data alone cannot.

It’s not that unlabeled data is “better” than labeled data. It’s that **unlabeled data is cheap and plentiful**, and when combined with a little labeled data, it can dramatically improve performance.

### Common semi-supervised techniques

1. **Self-training:** Train on labeled data, predict on unlabeled data, add the most confident predictions as new labeled examples, retrain. Repeat.
2. **Co-training:** Train two models on different views of the data; each labels examples for the other.
3. **Graph-based methods:** Build a similarity graph over all data (labeled + unlabeled); propagate labels through the graph.
4. **Semi-supervised SVM:** Find a boundary that separates labeled points AND avoids dense regions of unlabeled points.

---

## But then what's self-supervised learning?

This is where it gets confusing, because both use unlabeled data. The difference is in **what the goal is**.

| | Semi-supervised | Self-supervised |
|---|---|---|
| **Labels** | A few human labels | No human labels at all |
| **Goal** | Solve a specific task (e.g., spam classification) | Learn general representations/features |
| **How unlabeled data is used** | To improve the decision boundary for the task | To create a *pretext task* whose labels come from the data itself |
| **Example** | 100 labeled emails + 10,000 unlabeled → better spam classifier | Mask a word in a sentence, predict it; repeat billions of times → learn language representations |

### Self-supervised in more detail

In self-supervised learning, you don't have a downstream task in mind (or at least, not directly). Instead, you **invent a task from the data itself**:

- Take a sentence: “The cat sat on the ___.”
- Hide the last word.
- Ask the model to predict it.
- The correct answer is “mat” — and you got that label **for free** from the data, no human annotation needed.

Do this billions of times on raw text, and the model learns grammar, facts, reasoning patterns, etc. This is how BERT and GPT are pre-trained.

After pre-training, you can **fine-tune** the model on a small labeled dataset for a specific task (e.g., sentiment analysis). That fine-tuning step is supervised, but it requires far fewer labels because the model already understands language.

### So the hierarchy is:

1. **Supervised:** Lots of labeled data → learn task directly.
2. **Semi-supervised:** Few labeled + lots unlabeled → learn task directly, using unlabeled data as a guide.
3. **Self-supervised:** No labels → learn general representations from a pretext task, then optionally fine-tune on a small labeled dataset.

---

## Why the confusion?

Both semi-supervised and self-supervised use unlabeled data. The difference is:

- **Semi-supervised:** You have a specific task. You have a few labels for that task. Unlabeled data helps you do *that task* better.
- **Self-supervised:** You don't have labels. You create a fake task from the data. The goal is to learn *general features* that can later be used for many tasks.

Another way to think about it:

- **Semi-supervised** = “I have a little supervision, help me make the most of it with unlabeled data.”
- **Self-supervised** = “I have no supervision, so I'll supervise myself using the data's own structure.”

---

## A concrete comparison

**Semi-supervised spam classification:**
- You have 100 labeled emails (spam/not spam).
- You have 10,000 unlabeled emails.
- You use the unlabeled emails to understand the distribution of email content.
- You train a classifier that separates spam from not spam, using both.
- Result: better spam classifier than using 100 labeled emails alone.

**Self-supervised language model:**
- You have billions of sentences, no labels.
- You create a task: predict the next word.
- You train a huge model on this task.
- Result: a model that understands language structure.
- Later, you fine-tune it on 100 labeled sentiment examples to build a sentiment classifier.

---

## Summary

- **Semi-supervised:** Unlabeled data helps because it reveals the structure of the data distribution, which helps you place better decision boundaries when labels are scarce.
- **Self-supervised:** No labels at all; you create a pretext task from the data itself to learn general representations, which can then be fine-tuned on a small labeled dataset.
- Both exploit unlabeled data, but semi-supervised is task-specific with a few labels, while self-supervised is task-agnostic with zero human labels.

unlabeled data, if used correctly, can be more valuable than a tiny labeled dataset. But self-supervised takes it further — it doesn't even need a task or any labels; it creates its own supervision from the data.