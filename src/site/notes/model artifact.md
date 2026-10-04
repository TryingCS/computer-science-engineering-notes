---
{"dg-publish":true,"permalink":"/model-artifact/","dg-note-properties":{}}
---

#ml 
the learning algorithm does not typically create literal source code like `if x then y`.** It produces a **model artifact** — usually a set of numbers, parameters, or a data structure — that a separate prediction program knows how to interpret.

Let’s break it down.

---

### 1. What the learning algorithm actually outputs

Depending on the algorithm, the “model” might be:

| Algorithm | What the model actually is |
|-----------|----------------------------|
| **Linear regression** | A list of coefficients (e.g. `y = 50000 + 3000 * size`) |
| **Decision tree** | A tree data structure: nodes with feature thresholds, leaves with class labels |
| **K-Nearest Neighbors** | The entire training dataset (it just stores it) |
| **SVM** | A set of support vectors and their weights |
| **Neural network** | Millions of weights and biases arranged in layers |

None of these are source code. They are **data**.  
The learning algorithm adjusts these numbers or builds this structure to minimise error on the training data.

So when the slide says “the computer produces a Model”, it means it outputs something like a file (`.pkl`, `.h5`, `.json`) containing those learned parameters.

---

### 2. How the model is used later

You have two separate programs:

- **Training program**: takes data + labels → runs learning algorithm → saves model file.
- **Prediction program**: takes new data + loads model file → computes output.

The prediction program contains the *logic* to interpret the model.  
For example, if the model is a decision tree, the prediction program knows how to traverse the tree.  
If the model is a linear regression, it knows to multiply features by coefficients and sum them.

So the model itself is not “if x then y” code. It’s the **data** that the prediction program uses to make decisions.

---

### 3. But some models *are* human-readable

 Black-box models exist, but not all models are black boxes.

- **Decision tree** (small one): You can literally read the tree and see rules like  
  `if income > 50k and age < 30 → class A`.  
  It’s not written as Python code, but it’s easily interpretable.

- **Linear regression**: You can look at the coefficients and understand the effect of each feature.

- **K-Nearest Neighbors**: The “model” is just the training data. You can inspect it, but it’s not a set of rules.

- **SVM**: Harder to interpret, especially with non-linear kernels.

- **Random Forest**: Hundreds of trees — practically a black box.

- **Neural network**: Millions of weights — very much a black box.

So **black box** means: even though we have the model parameters, we can’t easily explain *why* it made a specific prediction. It’s not about whether it’s code; it’s about **interpretability**.

---

### 4. Could you convert a model to if-then code?

Yes, sometimes.  
For a decision tree, you *could* write a program that converts the tree into nested `if-else` statements. Some tools do this for deployment.  
But that’s a **conversion** — the original model was still a tree data structure, not code.

For a neural network, you can’t meaningfully convert it to simple if-then rules. The best you can do is write code that performs the matrix multiplications.

---

### 5. Analogy

Think of a model like a **recipe**:

- The learning algorithm is like a chef who tastes many cakes and figures out the recipe.
- The model is the recipe written down as **ingredient amounts and steps** — not as a story in English.
- The prediction program is the cook who reads the recipe and bakes a new cake.

The recipe isn’t “code” it’s a set of instructions stored in a structured way. Some recipes are simple and readable; some are complex molecular gastronomy that only a machine can follow.

---

### Summary

- **Model ≠ literal code.** It’s a learned representation: parameters, trees, weights, etc.
- A separate prediction program interprets the model to produce outputs.
- Some models are human-readable (linear regression, small decision trees), some are black boxes (neural nets, random forests).
- “Black box” refers to difficulty in explaining predictions, not to whether it’s code.
- The learning algorithm doesn’t write `if x then y`; it finds numbers/structure that best map inputs to outputs.
