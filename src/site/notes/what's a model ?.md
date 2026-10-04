---
{"dg-publish":true,"permalink":"/what-s-a-model/","dg-note-properties":{}}
---

#ml 
A **model** in machine learning is :

> **the learned function/artifact that takes new input data and produces an output (prediction, category, value, decision, etc.).**

é
![Pasted image ٢٠٢٦١٠٠٣٢٢١٥٢١.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A3%D9%A2%D9%A2%D9%A1%D9%A5%D9%A2%D9%A1.png)
### Traditional programming
- You provide: **Data** + **Handcrafted model**
- The “handcrafted model” means the rules/logic are written by a human programmer.
- The computer applies those rules to the data and produces a **Result**.
- Example:  
  `if email contains "free money" → spam`  
  That rule was written by a human.

### Machine learning
- You provide: **Sample data** + **Expected result** (labels)
- The computer uses a learning algorithm to produce a [[model artifact\|model artifact]].
- Then, in the prediction phase, you provide: **New data** + **Model**
- The computer produces a **Result**.
- The model is not written by hand; it is **learned from examples**.

So the model is the **intermediate learned thing** that replaces the handcrafted rules.

---

### What does a model actually contain?

It depends on the algorithm, but usually it contains:

1. **A structure/form** — e.g. a linear equation, a decision tree, a neural network.
2. **Learned parameters** — e.g. weights, coefficients, thresholds, split rules.
3. **A prediction function** — how to turn input features into an output.

For example:

- **Linear regression model:**  
  \[
  y = 50000 + 3000 \times \text{size}
  \]  
  The numbers `50000` and `3000` are learned from data. This model predicts a price.

- **Decision tree model:**  
  Actual `if-then` rules learned from data, e.g.  
  `if income > 50k and age < 30 → class A`

- **Neural network model:**  
  A large set of weights and biases arranged in layers. It doesn’t look like human-readable rules, but it still maps inputs to outputs.

- **Spam classifier model:**  
  Takes features of an email and outputs `spam` or `not spam`.

So it’s not necessarily a simple set of rules. It’s a **mathematical/statistical representation** that has been tuned to make good predictions.

---

### Model vs Algorithm

A useful distinction:

- **Algorithm** = the learning procedure.  
  Example: “train a logistic regression using gradient descent.”
- **Model** = the result of that procedure.  
  Example: the specific logistic regression equation with specific weights learned from your data.

In the ML diagram on page 13:
- `Sample Data + Expected Result → Computer → Model`
- The computer here is running a **learning algorithm**.
- The output is the **model**.

Then later:
- `New Data + Model → Computer → Result`
- The computer is now doing **inference/prediction** using the learned model.

---

### Simple analogy

- **Traditional programming:** You write a recipe for a cake. The computer follows it.
- **Machine learning:** You show the computer many examples of cakes and their ingredients. The computer infers a recipe. That inferred recipe is the **model**.

The model is what allows the system to **generalise** to new, unseen data — which is why page 10 says generalisation is essential.

So when you see “model” in these slides, read it as:

> **the learned mapping from input features to output predictions, produced by training on data, and used to make decisions on new data.**

For classification, it makes categorising decisions.  🗄️
For regression, it predicts numerical values. 🔢
For clustering, it assigns groups. 
For reinforcement learning, it may be a policy.  
 in all cases, it’s the learned thing that guides future outputs.
