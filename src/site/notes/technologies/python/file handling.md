---
{"dg-publish":true,"permalink":"/technologies/python/file-handling/","dg-note-properties":{}}
---

#python 
Think of a file like a physical notebook. You must **open** 📖 it, **read/write** in it, and **close** it. 🗝️

In Python, the safest way to do this is using the `with` statement. It automatically closes the file for you, even if your code crashes.

**1. Text Files (`.txt`)**
```python
# Writing to a file ('w' means write. It overwrites existing content)
with open("notes.txt", "w") as file:
    file.write("Distance: 10 km\n")
    file.write("Weight: 75 kg\n")

# Reading from a file ('r' means read)
with open("notes.txt", "r") as file:
    content = file.read()
    print(content)

# Appending to a file ('a' means add to the end, keeps old content)
with open("notes.txt", "a") as file:
    file.write("Speed: 50 km/h\n")
```

**2. JSON Files (`.json`)**
JSON is just a text file formatted like a Python dictionary. It is the standard way APIs and web apps share data.
```python
import json

data = {"name": "Sensor_1", "temp_c": 22.5, "active": True}

# Write dictionary to a JSON file
with open("data.json", "w") as file:
    json.dump(data, file, indent=4) # indent=4 makes it pretty and readable

# Read JSON file back into a dictionary
with open("data.json", "r") as file:
    loaded_data = json.load(file)
    print(loaded_data["temp_c"]) # Prints 22.5
```

**3. CSV Files (`.csv`)** 
CSV (Comma-Separated Values) is like a simple Excel spreadsheet. 
*While Python has a built-in `csv` module, in real-world data science (Semester 7+), you will almost exclusively use **Pandas** for this:*
```python
import pandas as pd

# Write to CSV
df = pd.DataFrame({"distance_km": [10, 20], "weight_kg": [50, 60]})
df.to_csv("measurements.csv", index=False)

# Read from CSV
new_df = pd.read_csv("measurements.csv")
print(new_df)
```

***

**Summary of Modes:**
* `"r"` = Read (Default, file must exist)
* `"w"` = Write (Creates new file or **erases** old one)
* `"a"` = Append (Adds to the end of existing file)
