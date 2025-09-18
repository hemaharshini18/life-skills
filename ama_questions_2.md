# AMA Questions

---

## 1. Explain about `append()` and `extend()` in Python
- In Python, both `append()` and `extend()` are used with lists, but they work differently.  
- `append()` adds a single element (object) to the end of the list, even if that element is another list.  
- `extend()` takes an iterable (like a list, tuple, or set) and adds each element individually to the list.  

Example:  
```python
a = [1, 2]
a.append([3, 4])   # [1, 2, [3, 4]]
a.extend([5, 6])   # [1, 2, [3, 4], 5, 6]
```  
- Use `append()` when you want to add a single item, and `extend()` when you want to merge another iterable.

---

## 2. What are CSS selectors?
- CSS selectors are patterns used to select and style specific elements in an HTML document.  
- They allow developers to apply styles to elements based on tag name, class, id, attributes, or relationships.  

Types of selectors include:  
- **Element Selector** → `p { color: red; }`  
- **Class Selector** → `.highlight { background: yellow; }`  
- **ID Selector** → `#header { font-size: 20px; }`  
- **Attribute Selector** → `input[type="text"] { border: 1px solid black; }`  
- **Combinators** → `div p { ... }` (descendant)  

Selectors help target elements efficiently and maintain clean CSS.

---

## 3. What is Monkey Patching?
- Monkey patching is the practice of dynamically modifying a class or module at runtime.  
- It allows you to add, modify, or override behavior of code without altering the original source.  

Example:  
```python
class A:
    def greet(self):
        return "Hello"

def new_greet(self):
    return "Hi from patched method!"

A.greet = new_greet   # Monkey patching
print(A().greet())    # Hi from patched method!
```  
- While powerful, monkey patching should be used carefully as it can lead to maintenance issues.

---

## 4. Explain recursion with example
- Recursion is a technique where a function calls itself to solve smaller instances of a problem.  
- Every recursive function has two parts:
  1. **Base case** – stops recursion.  
  2. **Recursive case** – function calls itself with a smaller input.  

Example (factorial):  
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # 120
```  
- Recursion is useful for problems like factorial, Fibonacci, and tree traversal.

---

## 5. What is local and global variable?
- A **local variable** is declared inside a function and can only be accessed within that function.  
- A **global variable** is declared outside all functions and is accessible throughout the program.  

Example:  
```python
x = 10  # global variable
def func():
    y = 5  # local variable
    print(y, x)

func()
```  
- If you want to modify a global variable inside a function, you must use the `global` keyword.  

---

## 6. What is metadata?
- Metadata is “data about data.” It describes and provides information about other data, making it easier to understand and manage.  
- In databases, metadata includes information like table names, column names, data types, and constraints.  
- In files, metadata can include file size, creation date, and author details.  
- Example: In an image file, metadata might store resolution, camera settings, and geolocation.  
- Metadata is crucial for data organization, search, and retrieval.  

---

## 7. Can you explain `map()`, `filter()`, `reduce()`?
- These are functional programming tools in Python for processing iterables.  

**`map()`** → applies a function to every element in an iterable.  
```python
nums = [1, 2, 3]
print(list(map(lambda x: x*2, nums)))  # [2, 4, 6]
```

**`filter()`** → selects elements based on a condition.  
```python
nums = [1, 2, 3, 4]
print(list(filter(lambda x: x%2==0, nums)))  # [2, 4]
```

**`reduce()`** → applies a rolling computation to items.  
```python
from functools import reduce
nums = [1, 2, 3, 4]
print(reduce(lambda x, y: x+y, nums))  # 10
```

- Together, they provide a concise way to transform, filter, and aggregate data.

---

## 8. What is file handling?
- File handling in Python refers to reading from and writing to files.  
- The built-in `open()` function is used to access files with different modes like:  
  - `"r"` → read, `"w"` → write, `"a"` → append, `"b"` → binary.  
- Example:  
```python
f = open("test.txt", "w")
f.write("Hello World")
f.close()
```  
- Always close files after use, or use `with open()` which auto-closes files.  
- File handling is crucial for working with persistent storage like logs, configs, or datasets.  

---

## 9. What is exception handling?
- Exception handling is a mechanism to manage errors that occur during program execution.  
- Instead of crashing, Python allows handling exceptions using `try-except` blocks.  
- Example:  
```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```  
- We can also use `finally` (for cleanup) and `else` (if no error occurs).  
- Proper exception handling makes programs more reliable and user-friendly.  

---
