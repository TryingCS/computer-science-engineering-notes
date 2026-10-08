---
{"dg-publish":true,"permalink":"/random-variables-and-distributions/","created":"2026-10-08T22:19:20.110+01:00","updated":"2026-10-08T22:58:24.298+01:00","dg-note-properties":{}}
---

#ml 
### Definitons
A random variable is a mapping:
X: Ω → R
that maps each outcome ω of the sample space
to a real value X ω .
• Two main types exist:

| Type                          | Description                                                | ML Examples                                            |
| ----------------------------- | ---------------------------------------------------------- | ------------------------------------------------------ |
| Discrete random<br>variable   | Takes a finite or countable<br>number of values            | Number of clicks,<br>classes of a model                |
| Continuous<br>random variable | Can take an infinite<br>number of values on an<br>interval | Weight, height,<br>probability predicted<br>by a model |

• The law of a random variable describes the
distribution of probabilities over its possible
values.
### Discrete variable
• It is characterized by a probability mass function
(Probability mass function, PMF):
P (X = xi )= pi , with $\sum$pi = 1

### Continuous variable
![Pasted image ٢٠٢٦١٠٠٨٢٢٣٨١١.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A2%D9%A2%D9%A3%D9%A8%D9%A1%D9%A1.png)

### Expectation and Variance
![Pasted image ٢٠٢٦١٠٠٨٢٢٥٧٢٢.png](/img/user/Pasted%20image%20%D9%A2%D9%A0%D9%A2%D9%A6%D9%A1%D9%A0%D9%A0%D9%A8%D9%A2%D9%A2%D9%A5%D9%A7%D9%A2%D9%A2.png)• Examples:
• The expectation of the average loss over a
dataset : E [Loss] .
• The variance measures the stability of the
model :
– low variance → robust model;
– high variance → overfitting.