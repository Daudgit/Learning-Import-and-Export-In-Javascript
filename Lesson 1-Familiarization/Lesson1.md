Sure! Here's the content in a Markdown (`.md`) file format:

```markdown
# JavaScript Export and Import Directives

In JavaScript, the `export` and `import` directives are used for working with modules. Modules help organize code into separate files, allowing you to split your codebase into manageable, reusable pieces. Here's a breakdown of these directives and their usage:

## `export`

The `export` directive is used to expose functionalities from a module that can be accessed by other modules. It can be used in two ways:

### Named Exports

You can export specific variables, functions, or classes individually by using the `export` keyword before their declaration.

```javascript
// Exporting individual functionalities
export const myVariable = 42;
export function myFunction() {
  // ...
}
export class MyClass {
  // ...
}
```

### Default Export

You can export a default functionality from a module by using the `export default` syntax. A module can have only one default export.

```javascript
// Exporting a default functionality
const myVariable = 42;
export default myVariable;

// Alternatively, you can export default directly on declaration
export default function myFunction() {
  // ...
}
```

## `import`

The `import` directive is used to import functionalities from other modules into the current module. It allows you to use functionalities exported from other modules as if they were defined locally. You can import functionalities in several ways:

### Named Imports

Import specific functionalities by using their names. This requires the same named export from the source module.

```javascript
// Importing specific functionalities
import { myVariable, myFunction, MyClass } from './myModule';
```

### Default Import

Import the default functionality from a module by specifying a name of your choice. This requires the default export from the source module.

```javascript
// Importing default functionality
import myVariable from './myModule';

// Alternatively, you can specify the default import on declaration
import myFunction from './myModule';
```

### Mixed Imports

You can combine named and default imports in a single statement.

```javascript
// Importing a mix of named and default functionalities
import myVariable, { myFunction, MyClass } from './myModule';
```

The `export` and `import` directives allow you to create modular JavaScript codebases, enabling better organization, code reuse, and encapsulation. By exporting and importing functionalities, you can use them across multiple files and build more maintainable and scalable applications.
```
Please note that Markdown files do not execute JavaScript code. This file format is used for documentation purposes and can be rendered as HTML for better readability.
