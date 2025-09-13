# AMA 

## What is a list in Python?

A list in Python is a built-in data structure that allows you to store an ordered collection of items. Lists are mutable, meaning you can change their content after creation. They can hold items of different data types, including integers, strings, and even other lists.

## What is Open/Close in SOLID?

The Open/Close Principle is one of the five SOLID principles of object-oriented design. It states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code, which helps to reduce the risk of introducing bugs and makes the system more maintainable.

## What is a primary key in SQL?

A primary key in SQL is a unique identifier for each record in a database table. It ensures that each record can be uniquely identified and accessed. A primary key must contain unique values and cannot contain NULL values. It is often used to establish relationships between tables in a relational database.

## Difference between <id> and <class>?

In HTML, the `<id>` and `<class>` attributes are used to identify and style elements, but they serve different purposes:
- `<id>`: The `id` attribute is used to uniquely identify a single element on a page. An `id` must be unique within the HTML document, meaning no two elements can have the same `id`.
- `<class>`: The `class` attribute is used to classify elements into groups. Multiple elements can share the same class, allowing you to apply the same styles or behaviors to multiple elements at once.

## Python is an interpreted language. Why?

Python is considered an interpreted language because the code you write is not compiled into machine-level instructions before execution. Instead, Python code is executed line by line by the Python interpreter. When you run a Python script, it is first converted into bytecode and then executed by the Python Virtual Machine (PVM).

## What is a set in Python?

A set in Python is a built-in data structure that represents an unordered collection of unique items. Sets are mutable, meaning you can add or remove items after creation, but they do not allow duplicate values. Sets are commonly used for membership testing, removing duplicates from a list, and performing mathematical set operations like union, intersection, and difference.

```python
s = set([True,0,1,False])
print(s)  # Output: {0, 1}
```
In this example, the set `s` contains only the unique values `0` and `1`, as `True` and `False` are considered equivalent to `1` and `0`, respectively.