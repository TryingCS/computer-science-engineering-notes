---
{"dg-publish":true,"permalink":"/technologies/python/data-structures/","dg-note-properties":{}}
---

#python 

| Operation                    | Syntax           | List `[]` | Dict `{}`            | Tuple `()`    | Set `{}` |
| ---------------------------- | ---------------- | --------- | -------------------- | ------------- | -------- |
| **Create**                   | `x = [...]`      | ✅         | ✅                    | ✅             | ✅        |
| **Get length**               | `len(x)`         | ✅         | ✅                    | ✅             | ✅        |
| **Check if item exists**     | `5 in x`         | ✅         | ✅ (checks keys)      | ✅             | ✅        |
| **Access by position**       | `x[0]`           | ✅         | ❌                    | ✅             | ❌        |
| **Access by key**            | `x["name"]`      | ❌         | ✅                    | ❌             | ❌        |
| **Slice (get a range)**      | `x[1:3]`         | ✅         | ❌                    | ✅             | ❌        |
| **Add one item**             | `x.append(5)`    | ✅         | ❌                    | ❌             | ❌        |
| **Add one item**             | `x.add(5)`       | ❌         | ❌                    | ❌             | ✅        |
| **Add key-value**            | `x["k"] = v`     | ❌         | ✅                    | ❌             | ❌        |
| **Insert at position**       | `x.insert(1, 5)` | ✅         | ❌                    | ❌             | ❌        |
| **Merge two together**       | `x.extend(y)`    | ✅         | ❌                    | ❌             | ❌        |
| **Merge two together**       | `x.update(y)`    | ❌         | ✅                    | ❌             | ✅        |
| **Remove last item**         | `x.pop()`        | ✅         | ✅ (removes last key) | ❌             | ✅        |
| **Remove specific item**     | `x.remove(5)`    | ✅         | ❌                    | ❌             | ✅        |
| **Remove by key**            | `del x["k"]`     | ❌         | ✅                    | ❌             | ❌        |
| **Remove safely (no crash)** | `x.discard(5)`   | ❌         | ❌                    | ❌             | ✅        |
| **Find position of item**    | `x.index(5)`     | ✅         | ❌                    | ✅             | ❌        |
| **Count occurrences**        | `x.count(5)`     | ✅         | ❌                    | ✅             | ❌        |
| **Sort in place**            | `x.sort()`       | ✅         | ❌                    | ❌             | ❌        |
| **Reverse**                  | `x.reverse()`    | ✅         | ❌                    | ❌             | ❌        |
| **Loop through**             | `for i in x:`    | ✅         | ✅ (loops keys)       | ✅             | ✅        |
| **Clear all items**          | `x.clear()`      | ✅         | ✅                    | ❌             | ✅        |
| **Copy**                     | `x.copy()`       | ✅         | ✅                    | ❌ (immutable) | ✅        |

**Key takeaways:**
- **Lists** are the most flexible. They can do almost everything.
- **Dicts** are special because they use keys, not positions.
- **Tuples** are read-only. You can look at them but never change them.
- **Sets** are for uniqueness. No positions, no keys, no duplicates.