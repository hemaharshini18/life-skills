# Asynchronous JavaScript

## 1. JavaScript Code Execution

JavaScript is single-threaded, executing code in a synchronous, blocking manner by default. The engine processes code line-by-line using a call stack, where functions are pushed and popped as they are called and return. Global code executes first, followed by function invocations.

When encountering asynchronous operations (e.g., timers, network requests), JavaScript offloads them to Web APIs, allowing the main thread to continue. Completed async tasks are queued in the task queue, and the event loop pushes them back to the call stack when it's empty.

## 2. Synchronous vs. Asynchronous Code

- **Synchronous Code**: Executes sequentially; each statement blocks until completion. Ideal for simple computations but can freeze the UI for long tasks.
- **Asynchronous Code**: Allows non-blocking execution; code continues while waiting for operations like I/O. This maintains responsiveness, crucial for user interfaces.

Key Difference: Sync code waits for results immediately, potentially halting execution; async defers results via callbacks or promises, enabling concurrency simulation in a single thread.

## 3. Ways to Make Code Asynchronous

- **Callbacks**: Pass functions to be invoked upon completion, e.g., `setTimeout(callback, delay)`.
- **Promises**: Objects representing eventual completion/failure, created with `new Promise()`.
- **Async/Await**: Syntactic sugar over promises for readable async code.
- **Events**: Use event listeners like `addEventListener` for DOM events.
- **Web Workers**: Offload heavy computations to background threads.

## 4. Web Browser APIs

Web Browser APIs (e.g., DOM, XMLHttpRequest, Fetch, Timers like setTimeout/setInterval) provide asynchronous capabilities. These are not part of core JavaScript but implemented by the browser environment. When called, they register callbacks and handle operations outside the JS engine, queuing tasks for the event loop upon completion.

## 5. The Event Loop

The event loop manages asynchronous execution in JavaScript's concurrency model. It continuously checks the call stack and task queues:

- **Call Stack**: Executes synchronous code.
- **Task Queue**: Holds completed async callbacks (macrotasks: setTimeout, I/O).
- **Microtask Queue**: Higher priority for promises, MutationObserver.

Process: If the stack is empty, the loop dequeues microtasks first, then macrotasks, ensuring non-blocking behavior.

## 6. Callbacks and Related Issues

### 6.1 Callback Hell
Callback hell refers to deeply nested callbacks in asynchronous code, leading to pyramid-like structures that are hard to read and maintain. Example:
```javascript
fs.readFile('file1.txt', (err, data1) => {
  if (err) return;
  fs.readFile('file2.txt', (err, data2) => {
    if (err) return;
    // More nesting...
  });
});
```
This increases error proneness and debugging difficulty.

### 6.2 Inversion of Control in Callbacks
In callbacks, control is handed to the called function, which invokes your callback. This loss of control can lead to issues like unhandled errors or unexpected invocation timing/order, reducing predictability.

## 7. Promises

### 7.1 What is a Promise?
A Promise is an object representing the eventual completion or failure of an asynchronous operation and its resulting value. It avoids callback nesting by providing a chainable API.

### 7.2 Creating a New Promise
```javascript
const promise = new Promise((resolve, reject) => {
  // Async operation
  if (success) resolve(value);
  else reject(error);
});
```

### 7.3 States of a Promise
- **Pending**: Initial state, neither fulfilled nor rejected.
- **Fulfilled**: Operation completed successfully (resolved).
- **Rejected**: Operation failed.

Promises are settled once fulfilled or rejected, immutable thereafter.

### 7.4 Consuming an Existing Promise
Use `.then(onFulfilled, onRejected)` or `.catch(onRejected)` to handle results/errors.

## 8. Promise Chaining

### 8.1 Chaining with .then
Chain multiple `.then` for sequential async operations:
```javascript
promise
  .then(result => transform(result))
  .then(nextResult => console.log(nextResult));
```
Each `.then` returns a new promise.

### 8.2 Handling Errors with .catch
Append `.catch(error => handle(error))` to catch rejections from the chain.

### 8.3 Finally Block
`.finally(() => cleanup())` executes regardless of fulfillment/rejection, useful for cleanup.

### 8.4 Errors in .then with .catch
If an error is thrown in `.then`, it's caught by subsequent `.catch`, rejecting the chain.

### 8.5 Errors in .then without .catch
Unhandled errors propagate as unhandled promise rejections, potentially crashing Node.js or logging warnings in browsers.

### 8.6 Placement of .catch
Place `.catch` at the end to handle errors from any preceding promise in the chain, ensuring comprehensive error management.

### 8.7 Consuming Multiple Promises
- **Chaining**: Sequence them via successive `.then`.
- **Promise.all**: `Promise.all([p1, p2])` resolves when all fulfill, rejects on first rejection.

## 9. Error Handling in Promises

Use `.catch` for rejections and try-catch with async/await. Always handle errors to prevent silent failures.

### 9.1 Importance of Error Handling
Errors are inevitable in async ops (e.g., network failures). Proper handling prevents crashes, provides user feedback, and maintains app stability—critical for reliability.

## 10. Promisifying Asynchronous Functions

Convert callback-based functions to promises:
```javascript
function promisify(fn) {
  return (...args) => new Promise((resolve, reject) => {
    fn(...args, (err, result) => {
      if (err) reject(err);
      else resolve(result);
    });
  });
}
const readFilePromise = promisify(fs.readFile);
```
For setTimeout: `new Promise(resolve => setTimeout(resolve, delay))`.

## 11. Promise Utility Functions

- **Promise.resolve(value)**: Returns a fulfilled promise with the value.
- **Promise.reject(reason)**: Returns a rejected promise with the reason.
- **Promise.all(iterable)**: Fulfills with array of values when all resolve; rejects on first rejection.
- **Promise.allSettled(iterable)**: Fulfills with array of outcomes (fulfilled/rejected) when all settle.
- **Promise.any(iterable)**: Fulfills with first resolved value; rejects if all reject.
- **Promise.race(iterable)**: Settles with the outcome of the first to settle (resolve or reject).
