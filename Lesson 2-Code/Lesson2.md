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

# `Import*`
Usually, we put a list of what to import in curly braces `import {...}`, like this:
```javascript
//📁 main.js
import {sayHi, sayBye} from './say.js';
sayHi('John'); // Hello, John!
sayBye('John'); // Bye, John!
```
But if there’s a lot to import, we can import everything as an object using `import * as <obj>`, for instance:
```javascript
// 📁 main.js
import * as say from './say.js';

say.sayHi('John');
say.sayBye('John');
```
But here you can see where i am importing everything using `*` then it is quiet difficult for me to understand.At first sight, “import everything” seems such a cool thing, short to write.

_But why should we ever explicitly list what we need to import?_
Well, there are few reasons.
- Explicitly listing what to import gives shorter names: `sayHi()` instead of `say.sayHi()`.
- Explicit list of imports gives better overview of the code structure: what is used and where. It makes code support and refactoring easier.

# `Import as` and `Export as`
## `Import as`
we can also use `as` to import under different names.
For instance, let’s import `sayHi` into the local variable as `hi` , and import `sayBye` as `bye`:
```javascript
// 📁 main.js
import {sayHi as hi, sayBye as bye} from './say.js';

hi('John'); // Hello, John!
bye('John'); // Bye, John!
```

## `Export as`
The similar syntax exists for `export`.

Let’s export functions as `hi` and `bye`:
```javascript
// 📁 say.js
...
export {sayHi as hi, sayBye as bye};
```
Now `hi` and `bye` are official names for outsiders, to be used in imports:
```javascript
// 📁 main.js
import * as say from './say.js';

say.hi('John'); // Hello, John!
say.bye('John'); // Bye, John!
```

# Export default
In practice, there are mainly two kinds of modules.
- Modules that contain a library, pack of functions, like `say.js` above.
- Modules that declare a single entity, e.g. a module `user.js` exports only `class User`.

Mostly, the second approach is preferred, so that every “thing” resides in its own module.

Naturally, that requires a lot of files, as everything wants its own module, but that’s not a problem at all. Actually, code navigation becomes easier if files are well-named and structured into folders.

Modules provide a special `export default` (“the default export”) syntax to make the “one thing per module” way look better.

Put `export default` before the entity to export:
```javascript
// 📁 user.js
export default class User { // just add "default"
  constructor(name) {
    this.name = name;
  }
}
```
There may be only one export default per file.

…And then import it without curly braces:
```javascript
// 📁 main.js
import User from './user.js'; // not {User}, just User

new User('John');
```

| Named export                | Default export                    |
| --------------------------- | --------------------------------- |
| `export class User {...}`    | `export default class User {...}` |
| `import {User} from ...`     | `import User from ...`            |

Technically, we may have both default and named exports in a single module, but in practice people usually don’t mix them. A module has either named exports or the default one.

As there may be at most one default export per file, the exported entity may have no name.

For instance, these are all perfectly valid default exports:
```javascript
export default class { // no class name
  constructor() { ... }
}
```

```javascript
export default function(user) { // no function name
  alert(`Hello, ${user}!`);
}
```

```javascript
// export a single value, without making a variable
export default ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
```

__Not giving a name is fine__, because there is only one `export default` per file, so `import` without curly braces knows what to import.

But, Without default, such an export would give an error:
```javascript
export class { // Error! (non-default export needs a name)
  constructor() {}
}
```

__*** So, be carefull when you export one entity per file and don't give any name then you should export it as a `default`__

### The “default” name
In some situations the `default` keyword is used to reference the default export.

For example, to export a function separately from its definition:
```javascript
function sayHi(user) {
  alert(`Hello, ${user}!`);
}

// same as if we added "export default" before the function
export {sayHi as default};
```
Or, another situation, let’s say a module `user.js` exports one main `“default”` thing, and a few `named ones` (rarely the case, but it happens):
```javascript
// 📁 user.js
export default class User {
  constructor(name) {
    this.name = name;
  }
}

export function sayHi(user) {
  alert(`Hello, ${user}!`);
}
```

Here’s how to import the default export along with a named one:

```javascript
import {default as User, sayHi} from './user.js'
new User('John')
```
And, finally, if importing everything `*` as an object, then the `default` property is exactly the default export:
```javascript
// 📁 main.js
import * as user from './user.js';

let User = user.default; // the default export
new User('John');
```

### A Interesting thing to remember between named and default
Named exports are `explicit`. They exactly name what they import, so we have that information from them; that’s a good thing.

Named exports force us to use exactly the right name to import:

```javascript
import {User} from './user.js';
// import {MyUser} won't work, the name must be {User}
```

…While for a default export, we always `choose the name when importing`:
```javascript
import User from './user.js'; // works
import MyUser from './user.js'; // works too
// could be import Anything... and it'll still work
```

__So team members may use different names to import the same thing, and that’s not good.

Usually, to avoid that and keep the code consistent, there’s a rule that imported variables should correspond to file names, e.g:__
```javascript
import User from './user.js';
import LoginForm from './loginForm.js';
import func from '/path/to/func.js';
...
```

Still, some teams consider it a serious drawback of default exports. So they prefer to always use named exports. Even if only a single thing is exported, it’s still exported under a name, without default.

That also makes re-export (see below) a little bit easier.








