---
{"dg-publish":true,"permalink":"/joint-random-variables/","created":"2026-10-10T16:39:17.910+01:00","updated":"2026-10-10T17:10:29.584+01:00","dg-note-properties":{}}
---

#ml 
**"Let's look at two different random variables at the exact same time and see how they interact."**

combination of : **[[Common Probability Distributions\|Common Probability Distributions]]** + **[[Conditional probability\|Conditional probability]]**.

***
### "Two variables X and Y can be related."

In ML, we almost never look at a single variable in isolation. We look at features (X) and try to predict a target (Y). We want to know: _If X takes a certain value, what happens to Y?_

To do this, we need three different ways of looking at their probabilities:

### 1. Joint Distribution: P(X=xi,Y=yi)

- **Translation:** The probability that X is a specific value **AND** Y is a specific value at the same time.
    
- **Example:** Let X = "Weather" (Sunny☀️, Rainy🌧️) and YY = "Umbrella☂️" (Yes, No). The joint distribution asks: "What is the probability it is Sunny **AND** I bring an Umbrella?" (Probably low).
    
- **Math:** It's just the probability of the **intersection:** P(X∩Y).
    
### 2. Marginal Distribution: P(X=xi)=∑jP(X=xi,Y=yj)

- **Translation:** The probability of X happening, **ignoring** Y.
    
- **How to get it:** You add up all the possibilities of Y.
    
- **Example:** What is the probability it is Sunny (regardless of whether I bring an umbrella)? You add up P(Sunny, Umbrella)+P(Sunny, No Umbrella)P(Sunny, Umbrella)+P(Sunny, No Umbrella).
    

### 3. Conditional Distribution: P(Y=yj∣X=xi)

- **Translation:** The probability of Y, given that we already know X.
    
- **Formula:** ![Pasted image ٢٠٢٦١٠١٠١٧٠١٤٧.png\|366](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A1%D9%A0%D9%A1%D9%A7%D9%A0%D9%A1%D9%A4%D9%A7.png)
- **Aha moment:** This is literally the conditional probability formula from earlier!
    
    - Numerator = Joint probability (A∩B)
        
    - Denominator = Marginal probability (B)
        
- **Example:** What is the probability I bring an umbrella, **given that** it is Sunny? 
	- ![Pasted image ٢٠٢٦١٠١٠١٧٠١٠٥.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A1%D9%A0%D9%A1%D9%A7%D9%A0%D9%A1%D9%A0%D9%A5.png)

### "X can represent the features and Y the class to predict."

From MATH tio ML:

1. **X is your data📊.** (Features: pixels in an image, words in an email, age and income of a user).
    
2. **Y is your label🏷️.** (Class: Cat/Dog)
    
3. **P(X,Y) is the joint distribution of the entire dataset.** It describes how the features and labels appear together in the real world.
    
4. **P(Y∣X)is what your model is trying to learn!** It's the probability of the class, given the features.
    
### ML Connection

When you train a model, you are trying to approximate P(Y∣X).

- _Generative models_ ⚗️ try to model the full joint distribution P(X,Y) and then use Bayes' theorem to get P(Y∣X).
    
- _Discriminative models_ ⚡️skip the joint distribution and try to learn P(Y∣X) directly.
    
***
vocab:
Joint = AND🤝, Marginal = IGNORE THE OTHER✖️, Conditional = GIVEN✅.
***
⏭️Next: [[Common Probability Distributions\|Common Probability Distributions]]