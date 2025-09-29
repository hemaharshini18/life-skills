# JavaScript Fundamentals

## 1. Introduction to JavaScript Data Types

JavaScript is dynamically typed, meaning variables can hold values of any type without explicit declaration. The language supports two categories of data types: primitive and non-primitive (reference types).

### 1.1 Primitive Data Types
- **Number**: Represents both integers and floating-point numbers, e.g., `42` or `3.14`. Special values include `NaN` (Not-a-Number) and `Infinity`.
- **String**: Sequences of characters enclosed in single quotes, double quotes, or backticks, e.g., `'hello'`.
- **Boolean**: Logical values `true` or `false`.
- **Undefined**: A variable declared but not assigned a value.
- **Null**: Intentionally represents "no value" or "empty object pointer".
- **Symbol**: Unique, immutable primitives introduced in ES6, often used for object property keys.
- **BigInt**: For integers beyond the safe range of Number (beyond ±2^53 - 1), e.g., `123n`.

### 1.2 Non-Primitive Data Types
- **Object**: Collections of key-value pairs, including arrays, functions, and dates. Objects are mutable and passed by reference.

Understanding these types is crucial for type coercion and operations, as JavaScript often implicitly converts types during comparisons or arithmetic.

## 2. Variable Declarations: let, var, const

JavaScript offers three keywords for declaring variables, each with distinct scoping and mutability rules.

- **var**: Function-scoped or globally scoped if declared outside functions. It allows redeclaration and reassignment. Hoisting occurs, where declarations are moved to the top of their scope, but initializations are not.
- **let**: Block-scoped (e.g., within `{}` blocks like if-statements or loops). It allows reassignment but not redeclaration in the same scope. Hoisted but not initialized, leading to a Temporal Dead Zone (TDZ) if accessed before declaration.
- **const**: Also block-scoped, but variables cannot be reassigned after initialization. However, for objects or arrays, properties or elements can still be mutated.

### 2.1 Why Avoid Using var
Using `var` is discouraged in modern JavaScript due to its function-scoping, which can lead to unexpected behavior in block contexts. For instance, a `var` declared inside a loop is accessible outside it, potentially causing bugs. It also permits redeclarations, increasing the risk of overwriting variables unintentionally. ES6 introduced `let` and `const` to provide safer, more predictable scoping aligned with other languages.

### 2.2 Dangers of Global Variables
Global variables, often declared without keywords or using `var` outside functions, pollute the global namespace (e.g., `window` in browsers). This leads to naming conflicts, especially in large codebases or when integrating third-party libraries. They persist throughout the application's lifecycle, consuming memory unnecessarily. Best practices advocate modular code with local scopes to encapsulate variables, reducing side effects and improving maintainability.

## 3. Truthy and Falsy Values

In JavaScript, values are coerced to booleans in conditional contexts (e.g., if-statements). Falsy values evaluate to `false`: `false`, `0`, `-0`, `0n` (BigInt zero), `''` (empty string), `null`, `undefined`, `NaN`. All other values are truthy, including non-empty strings, non-zero numbers, objects, arrays (even empty ones), and functions.

This behavior enables concise conditions but can introduce bugs if not handled carefully, such as treating `0` as falsy when it might be a valid value.

## 4. Functions in JavaScript

Functions are first-class citizens, treatable as variables.

### 4.1 Function Hoisting
Function declarations are hoisted entirely (declaration and body), allowing invocation before declaration in code. However, function expressions (e.g., assigned to variables) are not hoisted beyond their variable declaration, leading to TDZ errors if using `let` or `const`.

### 4.2 Default Return Behavior
If a function lacks a `return` statement, it implicitly returns `undefined`. This is useful for side-effect functions but can surprise developers expecting explicit values.

### 4.3 Ways to Declare Functions
- **Function Declaration**: `function add(a, b) { return a + b; }` – Hoisted.
- **Function Expression**: `const add = function(a, b) { return a + b; };` – Named or anonymous; not fully hoisted.
- **Arrow Function**: `const add = (a, b) => a + b;` – Concise, no own `this` or `arguments`.
- **Immediately Invoked Function Expression (IIFE)**: `(function() { ... })();` – For encapsulation.

### 4.4 Named vs. Anonymous Functions
Named functions (e.g., `function greet() {}`) aid debugging via stack traces showing the name. Anonymous functions (e.g., in expressions) lack this, making errors harder to trace but useful for one-off callbacks.

### 4.5 Passing Functions and Variable Arguments
Functions can be passed as arguments, enabling higher-order functions like callbacks: `function execute(cb) { cb(); }`. For variable arguments, use the `arguments` object (array-like) in regular functions or rest parameters (`...args`) in ES6: `function sum(...numbers) { return numbers.reduce((a, b) => a + b); }`.

### 4.6 Arrow vs. Regular Functions
Arrow functions lack their own `this` (lexical binding from enclosing scope), `arguments`, `super`, or `new.target`. They cannot be constructors (no `new`). Regular functions bind `this` dynamically, useful for methods but error-prone in callbacks.

### 4.7 Closures
A closure is a function that retains access to its lexical scope even when executed outside it. Example: `function outer() { let count = 0; return () => count++; }` – The inner function "closes over" `count`, enabling private state.

## 5. Pass by Value vs. Pass by Reference

Primitives are passed by value: a copy is made, so modifications inside functions do not affect originals. Objects (including arrays) are passed by reference: the reference is copied, so mutations affect the original, but reassigning the parameter does not.

## 6. Loops and Iteration

### 6.1 Types of For Loops
- **Traditional for**: `for (let i = 0; i < arr.length; i++) {}` – Ideal for index-based access with numbers.
- **for...in**: Iterates over enumerable properties of objects: `for (let key in obj) {}` – Not recommended for arrays due to prototype pollution risks.
- **for...of**: Iterates over iterable values (e.g., arrays, strings): `for (let value of arr) {}` – Cleaner for values without indices.
- **forEach**: Array method: `arr.forEach((value, index) => {})` – Executes a callback per element; cannot break early.

Use `forEach` for simple side effects; prefer `map`, `filter`, `reduce` for transformations (see Section 8).

## 7. Utilizing MDN Web Docs

The Mozilla Developer Network (MDN) is the premier resource for JavaScript documentation. Search via "MDN [topic]", e.g., "MDN Array.prototype.map". It provides syntax, examples, browser compatibility, and polyfills. Regularly consulting MDN ensures accurate, up-to-date knowledge.

## 8. Utility Methods

### 8.1 Popular Array Methods
- `push/pop/shift/unshift`: Add/remove elements (mutable).
- `slice/splice`: Extract or modify portions (slice immutable, splice mutable).
- `concat/join`: Combine arrays or convert to strings (immutable).
- `indexOf/lastIndexOf/includes`: Search for elements.
- `sort/reverse`: Reorder (mutable).
- `map/filter/reduce/find/some/every`: Functional operations.

### 8.2 Popular String Methods
- `charAt/indexOf/lastIndexOf/includes/startsWith/endsWith`: Searching.
- `slice/substring/substr`: Extraction (immutable).
- `toUpperCase/toLowerCase/trim/replace/split`: Manipulation.
- `concat/repeat/padStart/padEnd`: Building strings.

### 8.3 Popular Object Methods
- `Object.keys/values/entries`: Retrieve keys, values, or pairs.
- `Object.assign`: Shallow merge (mutable target).
- `Object.freeze/seal`: Prevent modifications.
- `hasOwnProperty`: Check direct properties.

### 8.4 Mutable vs. Immutable Methods
Mutable methods (e.g., `push`, `sort`) alter the original; immutable (e.g., `map`, `slice`) return new instances, promoting functional programming and reducing side effects.

### 8.5 When to Use forEach vs. map/filter/reduce
Use `forEach` for iterations with side effects (e.g., logging). Opt for `map` to transform (new array), `filter` to select subsets, `reduce` to accumulate (e.g., sum). These are immutable and chainable: `arr.filter(x => x > 0).map(x => x * 2).reduce((a, b) => a + b)`.

## 9. Error Handling

### 9.1 Try-Catch
Wrap risky code in `try { ... } catch (error) { ... } finally { ... }`. `catch` handles thrown errors; `finally` executes regardless.

### 9.2 Throwing Errors
Use `throw new Error('Message')` for Error objects with stack traces. `throw 'Message'` throws a string, lacking trace info—less useful for debugging.

### 9.3 Reading Errors and Stack Traces
Error messages detail type (e.g., TypeError) and message. Stack traces show call sequences (file:line). Practice daily for two weeks: Intentionally cause errors (e.g., undefined access, division by zero) in varied scenarios, analyze traces to trace issues back to source lines.

### 9.4 Importance of Catch Block
Without `catch`, unhandled errors crash the program or propagate. It allows graceful recovery, logging, or user feedback, enhancing robustness.

## 10. Modern Features

- **Spread Operator (`...`)**: Expands iterables/objects: `[...arr1, ...arr2]` or `{...obj1, ...obj2}` for shallow copies.
- **Template Literals**: Backtick strings for interpolation: `` `Hello, ${name}!` ``; multiline support.
- **Default Parameters**: `function greet(name = 'World') {}` – Fallback values.
- **Destructuring**: Extract values: `const {a, b} = obj;` or `[x, y] = arr;`.
- **=== vs. ==**: Strict equality (`===`) checks value and type; loose (`==`) coerces types (e.g., `'1' == 1` is true).
- **value === undefined vs. !value**: The former checks specifically for `undefined`; `!value` treats all falsy as true, potentially missing cases like `null` or `0`.
- **null vs. undefined**: `null` is intentional absence; `undefined` is uninitialized or missing.
- **Console Methods**: `console.log` (general), `.error` (red errors), `.warn` (warnings), `.info` (info), `.table` (tabular), `.time/.timeEnd` (timing).

## 11. Modules: Importing and Exporting

In CommonJS (Node.js): Export with `module.exports = { fn };` or `exports.fn = ...;`. Import: `const { fn } = require('./module');`. ES Modules use `export`/`import` for browsers/modern Node.

## 12. Best Practices

- **Indentation**: Use 2-4 spaces consistently; avoid tabs for cross-editor compatibility.
- **Variable Naming**: CamelCase for variables/functions (e.g., `userName`); UPPER_SNAKE for constants (e.g., `MAX_VALUE`); descriptive names.
- **Loop Variables**: Use meaningful names like `index` or `item`; avoid single letters except for simple counters.
- **Other**: Avoid globals; use strict mode (`'use strict';`); lint with ESLint; comment sparingly but meaningfully; prefer const over let/var.
- **Error Handling**: Always handle potential errors; avoid empty catch blocks.