---
{"dg-publish":true,"permalink":"/uncertain/","dg-note-properties":{}}
---

#ml 

“Uncertain” is the **umbrella term**. “Incomplete” and “noisy” are **specific causes/forms** of uncertainty.

- **Uncertain** = “something is wrong with the data / we are not sure.”
- **Incomplete** = “some information is missing.”
- **Noisy** = “some information is distorted, erroneous, or random.”

The three terms tell you **why** it is uncertain, and therefore **which tools** to use.

| Term             | Meaning                                                        | ML example                                            | Typical handling                                           |
| ---------------- | -------------------------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------- |
| **Uncertain**👀  | General lack of certainty; umbrella concept                    | Model says \(P(\text{spam})=0.87\)                    | Probabilistic models, Bayes, distributions                 |
| **Incomplete**🫗 | Missing values, partial observations, unobserved variables     | Missing age, missing label, only partial user history | Imputation, EM, missing-data likelihood, marginalization   |
| **Noisy** 🔊     | Measurement error, random fluctuations, label errors, outliers | Typos in emails, sensor noise, mislabeled images      | Robust statistics, noise models, regularization, denoising |

### Does probability vs statistics handle them differently?

Not exactly. Probability and statistics are **complementary lenses**, not two separate toolboxes where one handles “noisy” and the other handles “incomplete.”

- **Probability** = forward reasoning.  ⏩️
  Given a model/parameters, compute the probability of data or events.  
  Example: if x and y compute via Bayes.

- **Statistics** = inverse reasoning.  ⏪️
  Given data, estimate parameters, summarize, validate, and quantify uncertainty.  
  Example: from a sample, estimate average time = \(12.3 \pm 2.1\) minutes.

Both are used for all three issues:

- **Incomplete data**🫗: probability models the missingness mechanism; statistics does imputation, EM, maximum likelihood with missing data.
- **Noisy data**🔊: probability models the noise distribution; statistics estimates noise variance, uses robust estimators, filters outliers.
- **General uncertainty**👀: probability gives the language; statistics gives the inference and evaluation methods.

### Why not just say “real data is uncertain”?

Because “uncertain” is a **symptom**, not a **diagnosis**.  
Different causes require different treatments:

- If data is **incomplete**, you may need imputation or missing-data models.
- If data is **noisy**, you may need robust loss functions, regularization, or denoising.
- If data is simply **uncertain**, you may need probabilistic predictions instead of hard labels.
