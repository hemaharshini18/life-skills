# AMA 

## What is the difference between __init__ and __new__ methods in Python?

- __new__ creates a new object of a class. It’s like building the skeleton of the object.
- __init__ sets up the object by giving it initial values, like adding details to the skeleton.
- __new__ runs first and returns the new object; then __init__ fills in the details.
- __new__ is used for special cases, like controlling how objects are made (e.g., ensuring only one instance exists).
- If __new__ doesn’t return an object, __init__ won’t run.

## What are arrow functions in JavaScript and how are they different from normal functions?

- Arrow functions are a short way to write functions in JavaScript, like () => {}.
- They don’t have their own this; they use the this from the surrounding code.
- You can’t use arrow functions to create objects with new.
- They’re great for quick tasks like callbacks or event handlers.
- Normal functions are better when you need a separate this or want to create objects.


## Explain hoisting in JavaScript with an example.

- Hoisting is when JavaScript moves variable and function declarations to the top of their scope before running the code.
- Functions declared with function can be used before they’re written in the code.
- Variables with var are hoisted but start as undefined.
- Variables with let or const are hoisted but can’t be used until declared.


## What is the difference between isinstance() and type() in Python?

- type() tells you the exact class of an object.
- isinstance() checks if an object is an instance of a class or any class it inherits from.
- isinstance() is more flexible because it works with subclasses.
- Example: If Dog inherits from Animal, isinstance(dog, Animal) is True, but type(dog) == Animal is False.
- Use isinstance() for most real-world checks.

## What are JavaScript objects and how are they different from arrays?

- Objects store data as key-value pairs, like { name: "Alice", age: 25 }.
- Arrays store data in order, like [1, 2, 3], with number indices.
- Objects are for structured data (e.g., a person’s details); arrays are for lists (e.g., a list of numbers).
- Arrays have built-in methods like map or filter; objects use keys to access values.

## Explain the difference between for...of and for...in loops.

- for...in loops over the keys (property names) of an object.
- for...of loops over the values of things like arrays or strings.
- Use for...in for objects, like { a: 1, b: 2 } to get a, b.
- Use for...of for arrays, like [1, 2, 3] to get 1, 2, 3.
- Avoid for...in for arrays since it gives indices, not values.

## What is duck typing in Python?

- Duck typing means Python cares about what an object can do, not what it is.
- If an object has the right methods, it can be used, no matter its class.
- Example: If an object has a quack() method, it’s treated like a duck, even if it’s not a Duck class.
- It makes code flexible but can cause errors if the object doesn’t behave as expected.

## Difference between setTimeout and setInterval?

- setTimeout runs a function once after a delay, like setTimeout(myFunction, 1000) for 1 second.
- setInterval runs a function repeatedly every set time, like setInterval(myFunction, 1000) every 1 second.
- Both are used for timing in JavaScript and don’t block other code.
- Use setTimeout for one-time delays and setInterval for repeated actions.
