---
{"dg-publish":true,"permalink":"/continuous-variable-in-ml/","created":"2026-10-10T16:17:51.892+01:00","updated":"2026-10-10T17:28:33.718+01:00","dg-note-properties":{}}
---

#ml 
 **Continuous variables are highly relevant in ML, but the  calculus is mostly just notational. You will rarely, if ever, have to solve a calculus integral by hand in this course.**

### 1. What is a Continuous Variable, really?

A **Discrete** variable is _countable_. You can list the outcomes: "0 clicks, 1 click, 2 clicks." Or "Cat, Dog, Bird." There are gaps between the values.

A **Continuous** variable is _measurable_. It can take any value in an interval. Examples: Height, weight, time, temperature, or the probability output of a model (0.8734...).  

The tricky part: **The probability of getting exactly one specific value is zero.**  
If I ask "What is the probability that a randomly chosen person is exactly 1.800000000 meters tall?" the answer is 0. Instead, we ask: "What is the probability they are between 1.75m and 1.85m?"

Because of this, we use a **Probability Density Function (PDF)**, f(x). The probability is the **area under the curve** between two points.

### 2. The Calculus Demystified

You saw this:

![Pasted image ٢٠٢٦١٠١٠١٦٢٢٠١.png\|299](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A1%D9%A0%D9%A1%D9%A6%D9%A2%D9%A2%D9%A0%D9%A1.png)

**In ML, you almost never actually compute these integrals manually.**  
Why? Because the math gets impossibly hard for complex models. Instead, we use:

- **Libraries (like SciPy):** They compute the area numerically.
    
- **Known properties:** If we know the data follows a specific distribution (like the Normal/Gaussian distribution), we already know the formulas for its mean and variance. We just plug in the numbers.
    

### 3. The Missing Continuous Example (Expectation & Variance)

: **The Normal (Gaussian) Distribution**.

 the formula for it:

![Pasted image ٢٠٢٦١٠١٠١٦٢٤١٧.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A1%D9%A0%D9%A1%D9%A6%D9%A2%D9%A4%D9%A1%D9%A7.png)

Don't let the formula scare you. It's just a bell curve defined by two parameters:

- μ (Mu): The mean (Expectation).
    
- σ2 (Sigma squared): The variance.
    

**If a variable X follows a Normal distribution:**

- **Expectation E[X]=μ.** The peak of the bell curve. If we are modeling the weights of a neural network, E[X]is the average weight.
    
- **Variance Var(X)=σ2** The width of the bell curve. A small variance means all the weights are tightly clustered around the mean. A large variance means they are spread out.
    

If you ever see ![Pasted image ٢٠٢٦١٠١٠١٦٢٨٠٣.png\|132](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A1%D9%A0%D9%A1%D9%A6%D9%A2%D9%A8%D9%A0%D9%A3.png) for a Normal distribution. You just say, "Ah, it's a Normal distribution, so the Expectation is just μ."

### 4. Where in ML?

.** Here is where you will see them:

1. **Features📄:** Height📏, weight, income💰️, temperature🌡️ are all continuous.
    
2. **Model Weights:** When you initialize a neural network, the weights are drawn from a continuous Normal distribution.
    
3. **Noise🔊❎:** Real-world data has continuous noise (e.g., sensor error). We model this as y=f(x)+ϵy=f(x)+ϵ, where ϵϵ is a continuous random variable.
    
4. **Probabilities:** The output of a logistic regression or softmax is a continuous value between 0 and 1.
    

### TLDR


- **Conceptually:** Discrete = counting, Continuous = measuring. Probability for continuous is an _area under a curve_.
    
- **Practically:** In ML, we use continuous variables constantly, but we handle the math using **known formulas** or **software libraries**.
***
⏭️Next: [[Joint Random Variables\|Joint Random Variables]]