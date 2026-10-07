---
{"dg-publish":true,"permalink":"/conditional-probability/","created":"2026-10-07T07:16:34.794+01:00","updated":"2026-10-07T11:23:17.218+01:00","dg-note-properties":{}}
---

#ml 


![Pasted image ٢٠٢٦١٠٠٧٠٧١٧٣٤.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A7%D9%A0%D9%A7%D9%A1%D9%A7%D9%A3%D9%A4.png)
### 1. Why is conditional probability calculated like that?

just dividing the size of the overlap by the size of the new universe (\(B\)). It scales the probability because the "given" event \(B\) is now our new 100% (our new 1.0).

### 2. The Additivity axiom

![Pasted image ٢٠٢٦١٠٠٧٠٧٢٤٠٨.png\|90](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A7%D9%A0%D9%A7%D9%A2%D9%A4%D9%A0%D9%A8.png)
![Pasted image ٢٠٢٦١٠٠٧٠٧٢٢٢٧.png\|308](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A7%D9%A0%D9%A7%D9%A2%D9%A2%D9%A2%D9%A7.png)


says: **The Additivity axiom still works in a conditional universe.**

 If two events are disjoint then the probability of \(A\) **OR** \(C\) is the sum of their probabilities.
This property says: "If we know \(B\) happened, and \(A\) and \(C\) are disjoint, then the probability of \(A\) OR \(C\) given \(B\) is just the probability of \(A\) given \(B\) plus the probability of \(C\) given \(B\)."

**Why in ML?**
This is the mathematical foundation of things like **Naive Bayes**: 
eg:
calculate the probability of a document being spam given that it contains word 1, word 2, etc. We assume those words are disjoint/independent given the class, and we just *sum* (or multiply) their conditional probabilities to get the final answer. 
