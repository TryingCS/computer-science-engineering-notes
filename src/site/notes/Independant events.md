---
{"dg-publish":true,"permalink":"/independant-events/","created":"2026-10-08T21:01:54.720+01:00","updated":"2026-10-08T21:14:21.798+01:00","dg-note-properties":{}}
---

#ml 
• Two events A and B are independent if:
P(A∩B) =P(A)P(B)  or P(A∣B )=P(A)
***
###  Common Mix-Up:

- **Disjoint🆚:** A and B cannot happen at the same time. 
- P(A∩B)=0.
- **Independent🆓:** Knowing A happened doesn't change the probability of B 
- P(A∩B)=P(A)P(B).
    

In fact, if two events are disjoint and both have a probability greater than 0, they are **highly dependent** (not independent). If I tell you event A happened, you _know_ event B didn't happen. That's dependence!

### Why  this is useful for ML

It simplifies computations in **Naive Bayes**.  
In Naive Bayes, calculating the joint probability of 100 different words appearing in an email would normally require a massive table of every possible combination of words.  
But by **assuming** the words are independent _given the class_, we can just multiply their individual probabilities together. It's a "naive" assumption (because words actually _are_ correlated in real life), but it makes the math computationally tractable and works  well in practice.