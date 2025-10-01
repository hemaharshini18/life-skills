# AMA 

### Q1: What are First-Class Functions in JavaScript?
Functions in JavaScript are treated as first-class citizens, meaning they can be assigned to variables, passed as arguments, or returned from other functions. This enables higher-order functions, callbacks, and modular code design. First-class functions make code flexible and reusable.

### Q2: Explain the concept of Currying in JavaScript
Currying is the process of converting a function with multiple arguments into a series of functions that each take a single argument. It allows partial application and improves code reusability. Currying is widely used in functional programming for cleaner code.

### Q3: What is the difference between Pure and Impure Functions?
Pure functions always return the same output for the same input and do not produce side effects. Impure functions may depend on or modify external states, making them unpredictable. Pure functions are easier to test and debug.

### Q4: How does JavaScript handle Hoisting for variables and functions?
Hoisting moves declarations to the top of their scope. Function declarations are fully hoisted, while variables declared with var are hoisted and initialized with undefined. Let and const are hoisted but stay in a temporal dead zone until defined.

### Q5: What is the difference between Function Declarations and Function Expressions?
Function declarations are hoisted and can be called before definition. Function expressions are stored in variables and must be defined before use. Expressions are commonly used for callbacks and modular coding.

### Q6: What are IIFEs (Immediately Invoked Function Expressions) in JavaScript?
IIFEs are functions that run immediately after being defined. They create a private scope and prevent polluting the global namespace. IIFEs are used to encapsulate logic and maintain variable privacy.

