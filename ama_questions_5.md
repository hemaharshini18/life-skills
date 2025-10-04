# AMA

### Q1: How does Python implement closures and how do they interact with scopes?
Closures in Python are functions that remember variables from their enclosing scope. They allow inner functions to access outer variables even after the outer function has finished execution. This works with the LEGB rule (Local → Enclosing → Global → Built-in) for variable lookup. Closures are commonly used in decorators and factory functions.

### Q2: What is a window function in SQL, and how does it differ from GROUP BY?
Window functions perform calculations across a set of table rows related to the current row, without collapsing the rows. Examples include ROW_NUMBER() and AVG() OVER(). Unlike GROUP BY, which aggregates rows into a single output per group, window functions keep all rows visible while adding computed values.

### Q3: What is the difference between <picture> and <img> tags for responsive images?
The <img> tag displays a single image source, while <picture> allows multiple sources for different conditions like screen size or image format. The browser chooses the most appropriate source in <picture>, improving performance and responsiveness. <img> is simpler but less flexible for responsive needs.

### Q4: Explain the difference between stacking context and z-index.
A stacking context is a local environment where elements are layered according to rules. Properties like position, opacity, or transform create a new stacking context. z-index controls the order of elements inside the same stacking context. An element with high z-index may not appear above another if they belong to different stacking contexts.

### Q5: How does JavaScript’s this behave differently in arrow functions, normal functions, and object methods?
In normal functions, this is dynamic and depends on how the function is called. In object methods, this refers to the object itself. Arrow functions inherit this from their surrounding scope (lexical binding) and do not have their own this. This makes arrow functions useful for callbacks but unsuitable for methods requiring dynamic this.

### Q6: Difference between append() and appendChild()?
appendChild() inserts a single Node as the last child and only accepts Node objects. append() can insert multiple items (Nodes or strings) and is more flexible. appendChild() returns the inserted node, while append() does not. append() is newer and versatile; appendChild() is older and stricter.