---
{"dg-publish":true,"permalink":"/bayes-theorem/","created":"2026-10-08T19:21:06.293+01:00","updated":"2026-10-08T20:47:49.899+01:00","dg-note-properties":{}}
---

#ml 
Bayes' theorem is the bridge that takes us from the easy thing to calculate P(B|A) to the useful thing we want to predict P(A|B) by combining the [[Conditional probability\|Conditional probability]] formula and the [[Law of Total Probability\|Law of Total Probability]].
![Pasted image ٢٠٢٦١٠٠٨١٩٣٤٢٤.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A3%D9%A4%D9%A2%D9%A4.png)
### Step 1: Define th (The Symbols)

- **Ai​ (The Causes):**  mutually exclusive groups
    
- **B (The Data ):** what we observe.
    
- **The Partition statement:** "Let partition be a partition of the sample space: {A1,A2,…,An}{A1​,A2​,…,An​} such that ⋃iAi=Ω⋃i​Ai​=Ω and Ai∩Aj=∅Ai​∩Aj​=∅ for i≠ji=j."
    
    - _math speak for: "The causes cover everyone  and no one belongs to two groups at once (∩=∅∩=∅)."

### Step 2: The Formula (Left to Right)

The formula is:
![Pasted image ٢٠٢٦١٠٠٨١٩٣٤٢٤.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A3%D9%A4%D9%A2%D9%A4.png)
**The Left Side: P(Ai∣B)P(Ai​∣B)**

- **Meaning:** The probability that a patient belongs to group Ai, _given that_ they tested positive (B).
    
  - **ML Terminology:** This is called the **Posterior**. It's what we want to know after we see the data. 
    

**The Numerator (Top): P(Ai)P(B∣Ai)P(Ai​)P(B∣Ai​)**

- P(Ai): The probability of being in group Ai​ before any test. (Called the **Prior**).
    
- P(B∣Ai) The probability of testing positive if you are in group Ai​. (Called the **Likelihood**).
    
- _Multiplying them together_ gives the probability of "being in group Ai​ **AND** testing positive."
    

**The Denominator (Bottom): ∑jP(Aj)P(B∣Aj)∑j​P(Aj​)P(B∣Aj​)**

- This is the **[[Law of Total Probability\|Law of Total Probability]]** 
    
- It is the overall probability of testing positive, P(B)P(B), across the entire population. (Called the **Evidence** or marginal likelihood).

### Step 3: Let's calculate it with the Medical Example

Let's calculate the probability that a patient is **severely ill (\(A_3\))** given a **positive test (\(B\))**. 

We want: \(P(A_3 | B)\)

**Numerator:**
*   \(P(A_3)\) = 0.02 (2% of the population is severely ill)
*   \(P(B | A_3)\) = 0.99 (99% of severely ill people test positive)
*   Numerator = \(0.02 \times 0.99 = 0.0198\)

**Denominator:**
*   We calculated this on the previous slide! It's the total probability of a positive test: \(0.1018\)
So, if you test positive, there is only a **19.4% chance** you are severely ill. (This is because the disease is so rare in the first place—the "Prior" \(P(A_3) = 0.02\) heavily drags the probability down).

### Why do we use Bayes?
Look at what we knew before:

- We knew P(Positive Test∣Severely Ill)=0.99P(Positive Test∣Severely Ill)=0.99. (The doctor knows how the test behaves if you're sick).
    

Look at what Bayes' Theorem lets us find:

- P(Severely Ill∣Positive Test)P(Severely Ill∣Positive Test). (The patient wants to know: "I tested positive, am I sick?").
    

**Bayes' Theorem is a time machine that lets you flip the condition.**

In Machine Learning, we use this _constantly_:

- We know P(Email contains "Free"∣Spam)P(Email contains "Free"∣Spam)—it's easy to count how many spam emails have the word "Free".
    
- But we want P(Spam∣Email contains "Free")P(Spam∣Email contains "Free")—"Given this email has the word 'Free', is it spam?"
    

![Pasted image ٢٠٢٦١٠٠٨١٩٥٢١٨.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A5%D9%A2%D9%A1%D9%A8.png)
***




![Pasted image ٢٠٢٦١٠٠٨١٩٥٩٥٧.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A5%D9%A9%D9%A5%D9%A7.png)






• pss it is a reformulation of the definition of
[[Conditional probability\|Conditional probability]]:
![Pasted image ٢٠٢٦١٠٠٨١٩٢٣٠٣.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A1%D9%A9%D9%A2%D9%A3%D9%A0%D9%A3.png)

[[Bayes example\|Bayes example]]