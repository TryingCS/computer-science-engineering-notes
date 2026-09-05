---
{"dg-publish":true,"permalink":"/python-roadmap/","dg-note-properties":{}}
---


#python 
## Python prerequisites

### Must know before #S7 

| Topic | What you should know |
|---|---|
| Basic syntax | Variables, loops, `if`, functions, error handling |
| Data structures | Lists, dictionaries, tuples, sets |
| File handling | Read/write text, CSV, JSON files |
| OOP basics | Classes, objects, methods, inheritance |
| Virtual environments | `python -m venv`, `pip install`, `requirements.txt` |
| Jupyter / Colab | Running notebooks, installing libraries |
| NumPy basics | Arrays, indexing, slicing, vectorized operations |
| Pandas basics | `DataFrame`, filtering, grouping, cleaning missing values |
| Matplotlib basics | Simple plots: line, bar, scatter, histogram |
| Debugging | Print debugging, basic use of exceptions |

### Should know before Semester 8

| Topic | Why |
|---|---|
| NumPy broadcasting | Needed for ML, Deep Learning, image processing |
| Pandas pipelines | Needed for NLP, Big Data, BI, visualization |
| Matplotlib / Seaborn | Needed for results and dashboards |
| Scikit-learn basics | Train/test split, fit/predict, metrics |
| API usage | `requests`, JSON, Hugging Face models |
| Linux terminal basics | Running scripts, installing packages, using Docker |
| Basic SQL from Python | SQLite / PostgreSQL / Pandas-SQL workflows |

---

## Concepts learned through the courses

| Course | Python concepts / libraries learned |
|---|---|
| Machine Learning | `scikit-learn`, model pipelines, preprocessing, metrics, XGBoost, clustering, PCA |
| Modeling & Simulation | Simulation scripts, random generation, queues, `SimPy`-style logic |
| Operational Research | Optimization scripts, `PuLP` / OR-Tools style modeling |
| Knowledge Representation | Graphs, ontologies, Bayesian networks, `pgmpy`-style reasoning |
| NLP | Text preprocessing, tokenization, embeddings, Hugging Face, transformers |
| Deep Learning | PyTorch or TensorFlow, tensors, training loops, autograd, DataLoader, GPU training |
| Image Processing | OpenCV, `scikit-image`, filters, convolution, segmentation |
| Computer Vision | OpenCV, 3D reconstruction, camera geometry, object detection |
| Generative AI | Hugging Face, LLM APIs, prompt pipelines, LangChain-style apps, Gradio/Streamlit demos |
| Big Data | PySpark, distributed DataFrames, basic Kafka/Spark workflows |
| Data Visualization | Plotly, Bokeh, Dash, Folium, NetworkX |
| Blockchain | `web3.py`, smart contract interaction |
| Security / Adversarial ML | Scripting, cryptography libraries, adversarial attacks on models |

---

## Minimum checklist before Semester 7

You should be able to do this without help:

```python
import pandas as pd
import numpy as np

df = pd.read_csv("data.csv")
df = df.dropna()

x = df[["feature1", "feature2"]].values
y = df["target"].values
```

And this:

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

X_train, X_test, y_train, y_test = train_test_split(x, y, test_size=0.2)

model = LogisticRegression()
model.fit(X_train, y_train)

pred = model.predict(X_test)
print(accuracy_score(y_test, pred))
```

## Bottom line

Before Semester 7: focus on **Python + NumPy + Pandas + Matplotlib + scikit-learn basics**.

During Semesters 8 and 9: the courses will push you into **PyTorch, Hugging Face, OpenCV, PySpark, Dashboards, and Web3**.