---
{"dg-publish":true,"permalink":"/softmax/","created":"2026-10-06T19:43:07.978+01:00","updated":"2026-10-06T20:26:35.410+01:00","dg-note-properties":{}}
---

#misc 
 fancy word, but it's just a specific *function* used in neural networks. 


just to make sense of the slide:

-   **What it is:** Softmax is a function used at the end of a multi-class classification model (like a neural network trying to classify an image as a cat, dog, or bird).
-   **What it does:** It takes the raw, messy outputs of the network (which could be any numbers, like 5.2, -1.3, 0.8) and squashes them into a valid probability distribution.
-   **Why it was in the slide:** The slide was showing an example of the **Normalization** axiom ((P(Omega) = 1)). Because the model is classifying an image into exactly one of three classes, Softmax ensures that  (P(cat) + P(dog) + P(bird}) = 1). 

**Why you can skip it:**
You don't need to know how Softmax calculates it (it involves exponentials) to understand the Kolmogorov axioms. The slide is just saying: *"Here is a real-world ML example where the Normalization axiom holds."*

**When you will actually learn it:**
You'll likely cover Softmax in detail in **Chapter 2 (Logistic Regression)** for binary classification, or in a future Deep Learning course. 

**Recommendation:**
Just replace the word "softmax" with "some neural network function" in your head for now. The takeaway is just: *In [[multi-class classification\|multi-class classification]], the probabilities of all classes must sum to 1.* 
