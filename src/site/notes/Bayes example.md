---
{"dg-publish":true,"permalink":"/bayes-example/","created":"2026-10-08T20:47:52.630+01:00","updated":"2026-10-08T21:01:00.375+01:00","dg-note-properties":{}}
---

#ml 
### The Setup 🧫

You are building an ML model to filter emails. The model has been trained on a dataset of past emails, so it already knows some statistics:

**The Classes (The Causes):**

- A1A1​ = "Spam"
    
- A2A2​ = "Not Spam" (Legitimate email)
    

**The Data (The Observation):** 🔍️

- BB = "The email contains the word 'Promotion'"
    

### What We Know from Training Data

From analyzing past emails 📨, we know:

1. **Priors (How common is each class overall?):**
    
    - P(Spam)=0.2 (20% of all emails are spam)
        
    - P(Not Spam)=0.8 (80% are legitimate)
        
2. **Likelihoods (If we know the class, how likely is the word?):**
    
    - P("Promotion"∣Spam)=0.9 (90% of spam emails contain the word "Promotion")
        
    - P("Promotion"∣Not Spam)=0.1 (10% of legitimate emails contain the word "Promotion" — maybe a newsletter or a sale from a trusted brand)
        

### What We Want to Know 

A new email arrives. It contains the word "Promotion".  
We want to know: **What is the probability that this email is Spam?**  
We want to find: P(Spam∣"Promotion")

### Step 1: The Numerator (Prior × Likelihood)

This is the probability of "It's Spam" **AND** "It contains Promotion".

P(Spam)×P("Promotion"∣Spam)=0.2×0.9=0.18

### Step 2: The Denominator (The Total Probability of the Data)

This is the overall probability of _any_ email containing the word "Promotion", whether it's spam or not.

P("Promotion")=P("Promotion"∣Spam)P(Spam)+P("Promotion"∣Not Spam)P(Not Spam)=(0.9×0.2)+(0.1×0.8)=(0.9×0.2)+(0.1×0.8)=0.18+0.08=0.26=0.18+0.08=0.26

So, 26% of all your emails contain the word "Promotion".

### Step 3: The Final Calculation (Bayes' Theorem)

P(Spam∣"Promotion")=0.180.26≈0.692P(Spam∣"Promotion")=0.260.18​≈0.692

### The "Aha!" Moment

Before seeing the word "Promotion", your prior belief was that there was a **20% chance** the email was spam.  
After seeing the word "Promotion", your updated belief (the posterior) is that there is a **69.2% chance** it is spam.

**But notice it's not 100%.** Even though 90% of spam emails contain "Promotion", there is still a 30.8% chance it's a legitimate email. This is because "Promotion" is a fairly common word in legitimate marketing emails too, and because spam isn't overwhelmingly common in the first place.

### The Jump to Machine Learning (Naive Bayes)

In real ML, an email has _many_ words, not just one. Let's say the email contains "Promotion", "Free", and "Offer".

Instead of just looking at one word BB, we look at a set of words B1,B2,B3​.  
This is where the **Naive Bayes** classifier comes in. It makes the "naive" assumption that these words are **conditionally independent given the class**.

Mathematically, this means we just multiply their likelihoods:

Score for Spam=P(Spam)×P("Promotion"∣Spam)×P("Free"∣Spam)×P("Offer"∣Spam)Score for Spam=P(Spam)×P("Promotion"∣Spam)×P("Free"∣Spam)×P("Offer"∣Spam)

Then we do the same for "Not Spam". Whichever score is higher is the class the model predicts.

_(Note: In practice, we often drop the denominator because it's the same for both classes. We just compare the numerators to see which class is more likely. This is why you'll often see Bayes' theorem written as a proportionality: P(A∣B)∝P(A)P(B∣A).


### Why this is powerful

This is how your email inbox works . It doesn't "know" that an email is spam. It calculates a probability based on prior knowledge (how common spam is) and evidence (words in the email), and then makes a decision based on a threshold (e.g., if P(Spam)>0.5 send to spam folder).

