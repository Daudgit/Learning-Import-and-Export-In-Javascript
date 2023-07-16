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
functon sayHi(user){
alert(`Hello, ${user}`);
}

functon sayBye(user){
alert(`Bye, ${user}`);
}

  export {sayHi,sayBye};

```
__***Node That these are comes under named export not default export as we learnt in leasson 1__

