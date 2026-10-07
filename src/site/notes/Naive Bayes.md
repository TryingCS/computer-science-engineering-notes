---
{"dg-publish":true,"permalink":"/naive-bayes/","created":"2026-10-07T08:10:50.481+01:00","updated":"2026-10-07T08:19:56.102+01:00","dg-note-properties":{}}
---

#ml 
In Naive Bayes we want to calculate this:
![Pasted image ٢٠٢٦١٠٠٧٠٨٠٩٢٩.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A7%D9%A0%D9%A8%D9%A0%D9%A9%D9%A2%D9%A9.png)
Which means: *"Given that the email contains these words, what is the probability it is Spam?"*

To calculate that, Bayes' theorem flips it around. We need to calculate:
![Pasted image ٢٠٢٦١٠٠٧٠٨١٠٠٤.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A7%D9%A0%D9%A8%D9%A1%D9%A0%D9%A0%D9%A4.png)
Which means: **"Given that the class is Spam**, what is the probability that it contains these words?"

This is where the "Naive" part comes in. 

### The "Naive" Assumption of Independence
In reality, words in an email are not independent. If an email contains "Offer", it's probably also likely to contain "Free". They are correlated.

But calculating the exact joint probability of "Offer" AND "Free" AND "Promotion" appearing together in a spam email is computationally expensive. You would need a massive dataset of every single possible combination of words.

So, Naive Bayes makes a **naive assumption**:
> "Let's assume that **given that the email is Spam**, the words appear independently of each other."

Mathematically, this turns an impossible calculation into a simple multiplication:

P("Offer", "Free", "Promotion"∣Spam)≈P("Offer"∣Spam)×P("Free"∣Spam)×P("Promotion"∣Spam)

In Naive Bayes, we are NOT assuming the words are disjoint. An email can absolutely contain both "Offer" and "Free" at the same time. We are assuming they are **conditionally independent given the class**. 

### A Concrete Example
Imagine we have a dataset of emails.
*   **Class 1: Spam**
*   **Class 2: Not Spam**

We look at the Spam emails and calculate:
- P("Offer"∣Spam)=0.8 (80% of spam emails contain "Offer")
- P("Free"∣Spam)=0.7P("Free"∣Spam)=0.7 (70% of spam emails contain "Free")
Now a new email arrives with both words. Because we assume they are independent *given the class*, the probability of seeing both words in a Spam email is \(0.8 \times 0.7 = 0.56\).

Then we do the same for the Not Spam class, and compare the two numbers to make our prediction. 