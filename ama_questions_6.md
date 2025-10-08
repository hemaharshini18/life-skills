# AMA Answers

### 1. What’s the difference between `&&` and `;` in command chaining?
In command-line interfaces, the `&&` operator executes the second command only if the first one succeeds, meaning it has an exit status of zero. On the other hand, the semicolon (`;`) simply separates commands, allowing the next command to execute regardless of whether the previous one fails or succeeds. This makes `&&` useful for dependent operations, while `;` is ideal for sequential independent commands.

### 2. How does `git cherry-pick` differ from `git revert`?
The `git cherry-pick` command is used to apply a specific commit from one branch onto another branch, effectively copying the changes. In contrast, `git revert` creates a new commit that undoes the changes introduced by a previous commit, preserving history. Cherry-picking moves changes across branches, while revert safely reverses changes within the same branch.

### 3. What are decorators and how do they work internally?
In Python, decorators are functions that modify the behavior of another function or class without changing its code directly. They work by taking a function as input, wrapping it inside another function, and returning the modified version. Internally, this is achieved using closures that preserve the original function’s context while extending its functionality, making decorators powerful tools for logging, authentication, and more.

### 4. What is a CTE (Common Table Expression), and when should it be used?
A Common Table Expression (CTE) is a temporary result set in SQL that can be referenced within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. Defined using the `WITH` clause, CTEs make complex queries more readable and reusable. They are particularly useful for recursive queries or when you need to break down a complex query into logical parts without creating a permanent view.

### 5. What is the purpose of the `defer` and `async` attributes in `<script>` tags?
The `defer` and `async` attributes control how external JavaScript files are loaded and executed. Scripts with `defer` are downloaded in parallel but executed only after the HTML is fully parsed, preserving order. Scripts with `async` are downloaded and executed as soon as they are ready, potentially out of order. These attributes improve page load performance by preventing scripts from blocking rendering.

### 6. What are pseudo-elements and pseudo-classes?
Pseudo-elements and pseudo-classes are CSS selectors that help style elements in specific states or parts. Pseudo-classes, like `:hover` or `:focus`, target elements based on user interaction or state. Pseudo-elements, like `::before` and `::after`, allow developers to style specific parts of an element’s content. Together, they enhance design flexibility without modifying HTML structure.

### 7. What is event delegation, and why is it useful?
Event delegation is a technique in JavaScript where a single event listener on a parent element handles events triggered by its child elements. Instead of attaching multiple listeners to each child, the event bubbles up to the parent, which identifies the source using `event.target`. This improves performance, reduces memory usage, and simplifies handling dynamically added elements.

### 8. What are Django middleware and their uses?
In Django, middleware are lightweight components that process requests and responses globally before they reach views or after they leave them. They sit between the web server and the application, handling tasks such as authentication, session management, request logging, and security filtering. Middleware enhances modularity and allows developers to apply cross-cutting concerns efficiently.