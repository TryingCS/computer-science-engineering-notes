---
{"dg-publish":true,"permalink":"/multi-class-classification/","dg-note-properties":{}}
---

#ml 
In ML, when we say **"multi-class classification,"** we specifically mean **more than two classes**. 

Yes, linguistically it sounds weird because "multi" just means "many" (and 2 is many), but in ML jargon, it's a strict distinction:

1. **Binary Classification:** Exactly **2** classes. 
   * *Examples:* Spam / Not Spam. Fraud / Not Fraud. Cat / Dog. 
   * The probabilities sum to 1: \(P(\text{Spam}) + P(\text{Not Spam}) = 1\).

2. **Multi-class Classification:** **3 or more** classes.
   * *Examples:* Classifying an image as Cat / Dog / Bird. Classifying a digit as 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9.
   * The probabilities sum to 1: \(P(\text{Cat}) + P(\text{Dog}) + P(\text{Bird}) = 1\).

3. **Multi-label Classification (Bonus):** An image can have *multiple* labels at the same time.
   * *Example:* A movie poster is tagged as "Action", "Sci-Fi", AND "Comedy". 
   * Here, the probabilities **do not** sum to 1. (The model is answering "yes/no" for each tag independently).

**So why did the slide say "multi-class"?**
Because the slide was specifically showing an example of [[Softmax\|Softmax]] In neural networks, Softmax is the specific mathematical function used when you have **more than two** mutually exclusive classes. If you only have two classes, you use a different function called "Sigmoid," and you only need to calculate one probability (because the other is just \(1 - p\)).

**The takeaway:**
Whether it's binary or multi-class, the Kolmogorov **Normalization axiom** ((P(Omega) = 1)) still applies. The probabilities of all possible *mutually exclusive* outcomes must sum to 1. 