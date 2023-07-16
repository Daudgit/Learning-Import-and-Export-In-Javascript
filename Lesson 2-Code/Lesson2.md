# `Export` before declaration V/S `Export` Apart From Declaration
we can label any declaration by placing `export` before it also we can put `export` separately
## `Export` before declaration
```javascript
// export an array
export let month = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
//export a constant
export const pi = 3.14159265359
//export a class
export class User{
constructor(name){
  this.name = name;
}
}
// export a function
export function sayHi(user) {
  alert(`Hello, ${user}!`);
}
// and also keep it in mind no semicolon is required after the function or class declaration.
```
## `Export` Apart from declaration
here we are exporting the variables, constant, class and functions after the declaration.
```javascript
//📁say.js

functon sayHi(user){
alert(`Hello, ${user}`);
}

functon sayBye(user){
alert(`Bye, ${user}`);
}

export {sayHi,sayBye};

```
__***Node That these are comes under named export not default export as we learnt in leasson 1__

## `Import*`
Usually, we put a list of what to import in curly braces `import {...}`, like this:
```javascript
//📁 main.js
import {sayHi, sayBye} from './say.js';
sayHi('John'); // Hello, John!
sayBye('John'); // Bye, John!
```
But if there’s a lot to import, we can import everything as an object using `import * as <obj>`, for instance:



