---
{"dg-publish":true,"permalink":"/misc/","created":"2026-10-07T08:07:31.051+01:00","updated":"2026-10-07T08:36:06.698+01:00","dg-note-properties":{}}
---

#ml 



**"class"** is the **target label** you are trying to predict. 
If you are building a spam filter, the classes are **Spam** and **Not Spam**. 
The words in the email ("Offer", "Free", "Meeting") are called **features** or **attributes**, not classes.

### What does "Given the class" mean?
It means we are **conditioning** on the target label. We are pretending, "What if we already knew for a fact this email was Spam?" 
***
*   **Disjoint:** Two events cannot happen at the same time. (Rolling a 1 and rolling a 2 on a single die).
*   **Independent:** Two events don't affect each other's probability. (Rolling a 1 on Die 1 and rolling a 6 on Die 2).
***


**Valid probability measure=> follows the  three Kolmogorov axioms (Non-negativity, Normalization, Additivity)

"Make up a whole"**
This means the events are **exhaustive**—they cover every single possible outcome within the new universe. 
(In math terms, they are a **partition** of \(B\). They don't overlap, and together they cover all of \(B\).)
These classes are disjoint (an image is exactly one of them) and they "make up a whole" (those are the only options)

 the **Normalization Axiom** applied to a new conditional universe. 
When we condition on \(B\), \(B\) becomes our new (Omega). The probabilities of all the disjoint pieces that make up \(B\) must still sum to exactly 1.
### Why in ML?
This is the absolute core of classification models (like logistic regression or neural networks).


Because of this property, your model must output:
		P(Cat∣Image)+P(Dog∣Image)+P(Bird∣Image)=1

This is exactly why the [[Softmax\|Softmax]] function (from a few slides ago) exists! It forces the model's outputs to satisfy this property. 
***

