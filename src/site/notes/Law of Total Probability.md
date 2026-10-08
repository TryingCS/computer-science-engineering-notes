---
{"dg-publish":true,"permalink":"/law-of-total-probability/","created":"2026-10-08T19:02:54.007+01:00","updated":"2026-10-08T19:24:36.977+01:00","dg-note-properties":{}}
---

#ml 

tldr just add the slices.🍕
**"What is the overall probability of an event when it can happen in several different ways?"**
![Pasted image ٢٠٢٦١٠٠٨١٩٠٥٣٢.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A0%D9%A5%D9%A3%D9%A2.png)
In this medical example:
*   **\(B\) is the event:** "The test is positive" (\(T+\)).
*   **The ways \(B\) can happen are the causes:** A patient can be Healthy (\(A_1\)), Mildly ill (\(A_2\)), or Severely ill (\(A_3\)). 

Every single person in the population falls into exactly ONE of those three categories. They are disjoint (no overlap) and they make up the whole population ("partition" of the sample space). **This is crucial.**

### Breaking Down the Formula

The formula is:
![Pasted image ٢٠٢٦١٠٠٨١٩٠٧٠٧.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A0%D9%A7%D9%A0%D9%A7.png)

Here is the translation:
*   \(P(A_i)\): How common is this group in the population? (e.g., 90% of people are healthy).
*   \(P(B | A_i)\): If someone is in this group, how likely is the event \(B\)? (e.g., If healthy, 2% chance of a positive test).
*   (P(B | A_i)P(A_i)): The probability of **being in that group AND having event \(B\) happen**.
*   The Sum : We add up the "AND" probabilities for all possible groups to get the total probability of (B).

### The Step-by-Step Medical Example

Let's calculate \(P(T^+)\), the overall probability that a **random** person tests positive.

**Group 1: Healthy (\(A_1\))**
*   Probability of being in this group: \(P(A_1) = 0.90\)
*   Probability of testing positive if you're in this group: \(P(T^+ | A_1) = 0.02\)
*   Probability of being healthy **AND** testing positive: \(0.90 \times 0.02 = 0.018\) (This is 1.8% of the total population).

**Group 2: Mildly ill (\(A_2\))**
*   Probability of being in this group: \(P(A_2) = 0.08\)
*   Probability of testing positive if you're in this group: \(P(T^+ | A_2) = 0.80\)
*   Probability of being mildly ill **AND** testing positive: \(0.08 \times 0.80 = 0.064\) (This is 6.4% of the total population).

**Group 3: Severely ill (\(A_3\))**
*   Probability of being in this group: \(P(A_3) = 0.02\)
*   Probability of testing positive if you're in this group: \(P(T^+ | A_3) = 0.99\)
*   Probability of being severely ill **AND** testing positive: \(0.02 \times 0.99 = 0.0198\) (This is 1.98% of the total population).

**The Total:**
If you add those up, you get the total probability of a positive test:

0.018 + 0.064 + 0.0198 = 0.1018

So, **10.18% of the entire population will test positive.**


 It  means: if you grab a random person off the street, there is a 10.18% chance they test positive. It doesn't tell you *why* they tested positive (they could be healthy with a false positive, or sick with a true positive). It just gives you the overall rate of positive tests.

### Why in ML ? 
This is the mathematical engine behind **Naive Bayes** and many other probabilistic models. 

Imagine you are building an ML model to predict if a user will click on an ad (Event \(B\)).
*   The "causes" (\(A_i\)) could be different user types: "New User", "Returning User", "Premium User".
*   You know how common each user type is: \(P(A_i)\).
*   You know how likely each user type is to click: \(P(B | A_i)\).
*   Using the Law of Total Probability, you can calculate the overall probability of *anyone* clicking the ad: \(P(B)\).

It allows you to compute the denominator in [[Bayes’ Theorem\|Bayes’ Theorem]]. 

 The key is realizing that ==🔴P(T+ | A_i) * P(A_i))== is just calculating the probability of a specific "slice" of the population.