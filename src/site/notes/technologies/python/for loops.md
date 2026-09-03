---
{"dg-publish":true,"permalink":"/technologies/python/for-loops/","dg-note-properties":{}}
---

#python 
`range(3)`**
creates a sequence of 3 numbers: `0, 1, 2`. (Think of it like 0 km, 1 km, 2 km).

**3. `in`**
In a loop, `in` means "grab the next item from the sequence". 
* Loop 1: `i` grabs `0`.
* Loop 2: `i` grabs `1`.
* Loop 3: `i` grabs `2`.

**4. `f` and `{}` (f-strings)**
The `f` stands for "format". It lets you inject variables directly into text. 
The `{}` is an empty box. You put the variable name inside the box, and Python replaces the box with the variable's value.

```python
i = 5
# Without f-string:
print("Step " + str(i)) 

# With f-string (much cleaner):
print(f"Step {i}") 
```
