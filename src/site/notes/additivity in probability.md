---
{"dg-publish":true,"permalink":"/additivity-in-probability/","created":"2026-10-06T19:33:55.070+01:00","updated":"2026-10-06T19:57:01.420+01:00","dg-note-properties":{}}
---


#ml 
Additivity simply means: **If two or more events cannot happen at the same time, the probability that *any one of them* happens is just the sum of their individual probabilities.**

Tthe mathematical formalization of saying "OR" when the options are mutually exclusive.

### Decoding the Symbols

![Pasted image ٢٠٢٦١٠٠٦١٩٣٥٠٤.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A6%D9%A1%D9%A9%D9%A3%D9%A5%D9%A0%D9%A4.png)
**1. \(A_i\)**
This represents a collection of events. The little \(i\) is just an index (like 1, 2, 3...). So \(A_1, A_2, A_3\), etc., are different events.

**2. "for disjoint events \(A_i\)"**
*   **Disjoint** (also called mutually exclusive) means the events have no overlap. If one happens, the others *cannot* happen.

**
*   The  **U** symbol is the **Union** symbol.
*   In probability, "Union" translates to the word **"OR"**.
*   So \(\bigcup_i A_i\) means "Event 1 **OR** Event 2 **OR** Event 3... happens."
*   Therefore, the whole left side is: *"The probability that at least one of these disjoint events happens."*

**
*   The symbol \(\sum\) is the **Summation** symbol (Sigma). It means "add up everything that follows."
*   So this is simply: *"The probability of Event 1 + the probability of Event 2 + the probability of Event 3..."*

### A Concrete Example

Imagine rolling a fair 6-sided die.
The sample space is \(\Omega = \{1, 2, 3, 4, 5, 6\}\).

Let's define:
*   \(A_1\) = "Roll a 1" (Probability = 1/6)
*   \(A_2\) = "Roll a 2" (Probability = 1/6)

These are **disjoint** (you can't roll a 1 AND a 2 at the same time).
If you want to know the probability of rolling a 1 **OR** a 2:
*   Left side: \(P({1 OR 2}) = 2/6\)
*   Right side: \(P(1) + P(2) = 1/6 + 1/6 = 2/6\)

They match. That's the axiom.

### Why is the word "disjoint" so important here?

If the events are **NOT** disjoint, you cannot just add them up, because you would double-count the overlap.

*Example of non-disjoint:* \(A_1\) = "Roll an even number" (2, 4, 6), \(A_2\) = "Roll a number greater than 3" (4, 5, 6).
*   \(P(A_1) = 3/6\)
*   \(P(A_2) = 3/6\)
*   If you just add them: \(3/6 + 3/6 = 6/6 = 1\).
*   But the probability of rolling an even number OR a number > 3 is not 1. (You could roll a 1, which is neither). 
*   The overlap is rolling a 4 or 6. Because those are in both sets, adding them counts them twice. 

That's why the axiom explicitly says **"for disjoint events"**. If they aren't disjoint, you have to subtract the intersection (the overlap) — which is the next thing you'll usually learn in probability.

###  for Machine Learning?
In ML, especially in classification (like a neural network with a [[Softmax\|Softmax]] output), the model outputs probabilities for each class. If the classes are disjoint (an image is either a cat, a dog, or a bird—never both), then the sum of the probabilities of all classes must equal 1. That's the Additivity and Normalization axioms working together! 
