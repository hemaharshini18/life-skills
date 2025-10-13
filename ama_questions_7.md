# AMA Questions

### 1. How do `.gitattributes` and `.gitignore` differ in usage?
`.gitignore` tells Git which files or directories to completely ignore — such as temporary files, build outputs, or environment settings — so they aren’t tracked in commits. It prevents unnecessary or system-specific files from cluttering the repository.  
`.gitattributes`, on the other hand, manages how Git treats tracked files. It can define text normalization, binary file handling, diff behavior, and merge strategies.  
While `.gitignore` focuses on what **not** to track, `.gitattributes` focuses on **how** tracked files are handled and processed. Both files improve collaboration and consistency in multi-developer projects.


### 2. What are dataclasses, and how are they different from regular classes?
Dataclasses in Python (introduced in version 3.7) simplify class creation by automatically generating special methods like `__init__`, `__repr__`, and `__eq__`.  
They are declared using the `@dataclass` decorator and are ideal for classes that primarily store data rather than behavior.  
Unlike regular classes, developers don’t need to manually write repetitive initialization or comparison code.  
Dataclasses also support features like default values, immutability (`frozen=True`), and type hints for better clarity and error detection.  
They are commonly used in data modeling, configuration handling, and serialization tasks.


### 3. What is a materialized view, and how does it differ from a regular view?
A materialized view is a precomputed and stored result of a SQL query, which physically saves the data on disk.  
Unlike regular views that always query live data from tables, materialized views enhance performance by avoiding repeated computation of complex joins or aggregations.  
However, they need manual or scheduled refreshing to stay in sync with the underlying data.  
Regular views always display the latest data but can be slower for heavy queries.  
Materialized views are useful in data warehousing or analytics where read speed matters more than real-time accuracy.


### 4. How do CSS variables (`--var`) work and what are their advantages?
CSS variables (custom properties) are reusable values defined with a `--` prefix and accessed via the `var()` function.  
They can be declared globally in the `:root` selector or locally within specific elements.  
This allows developers to define design tokens like colors, fonts, or spacing values once and reuse them consistently.  
Unlike preprocessor variables (e.g., in Sass), CSS variables are dynamic — they can be updated at runtime using JavaScript.  
They improve maintainability, make theming easier, and help avoid redundancy across stylesheets.


### 5. What is JSON?
JSON (JavaScript Object Notation) is a lightweight, human-readable format used for storing and exchanging data between systems.  
It represents data as key–value pairs and supports nested structures like arrays and objects.  
Because of its simplicity and compatibility with many languages, JSON is widely used in web APIs, configurations, and data serialization.  
It’s language-independent but closely aligned with JavaScript’s syntax, making it easy to parse and generate.  
In modern development, JSON plays a critical role in RESTful APIs, where it acts as the communication medium between the frontend and backend.


### 6. What is the difference between `Form` and `ModelForm` in Django?
A Django `Form` is manually defined by the developer and can represent any kind of data, independent of database models.  
A `ModelForm`, however, automatically generates form fields based on the attributes of a Django model.  
This makes it ideal for creating or updating database records directly through forms.  
Using `ModelForm` simplifies data validation and saves time by linking the form’s fields directly to the model structure.  
While `Form` offers flexibility for custom use cases, `ModelForm` provides rapid development for model-related operations.


### 7. What’s the purpose of `csrf_token`, and how does Django protect against CSRF attacks?
Django’s `csrf_token` is part of its built-in Cross-Site Request Forgery (CSRF) protection mechanism.  
It generates a unique, session-specific token for every form rendered to the user.  
When a form is submitted, Django checks whether the token in the request matches the one stored in the user’s session.  
If it doesn’t match, Django blocks the request, preventing unauthorized commands from being executed on behalf of the user.  
This ensures that only legitimate, user-initiated form submissions are processed, protecting sensitive actions like logins and payments.


### 8. How does the browser’s re-render cycle get triggered?
The browser’s rendering cycle is triggered whenever changes occur to the DOM or CSSOM.  
Actions like updating text, changing styles, resizing the window, or modifying layout properties can start a re-render.  
The process involves recalculating styles, performing layout (reflow), and repainting the visual elements on screen.  
To optimize performance, browsers batch small changes together and execute them efficiently.  
Poorly managed reflows — like frequent DOM manipulations in loops — can cause performance issues, so developers often use techniques like `documentFragment` or virtual DOM to minimize them.
