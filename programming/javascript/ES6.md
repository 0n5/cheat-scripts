JavaScript ES6
==============

ES6 code is transpiled into syntax that can be read by any browser via Babel

Transpiling at runtime is very slow and should be only used in dev

#### Variables

``` javascript
const = SOME_VARIABLE
// constant variable that cannot be changed

```

``` javascript
let = SOME_VARIABLE
// variable that provides lexical block scoping to JS functions
// a variable declared outside of the code block will not be overwritten inside

```

#### Template Literals

``` javascript
`${A_VARIABLE}, {B_VARIABLE}` 
// Provides concatenation that honors whitespace

```

#### Destructuring 

objects

``` javascript

var cats = {
    Felix: "Tabby",
    Heathcliff: "Calico",
    Snowball: "Russian Blue"
}

var {Felix, Heathcliff} = shelter_cats
// pulls 2 keys out of the object and stores them in their own variable

```

arrays

``` javascript
var [firstCat] = ["Felix", "Heathcliff", "Snowball"]
// stores Felix, the first cat in the array in its own variable

var [,,thirdCat] = ["Felix", "Heathcliff", "Snowball"]
// stores Snowball the third cat in the array in its own variable

```

#### Object Literal Enhancement


``` javascript

var name = "Bob"
var position = "Developer"

var employee = {name, position}
takes two variables and turns them into an object

```

### Spread Operator

arrays

``` javascript

var cats = ["Felix", "Jose", "Tom"]
var tomCats = ["Josie", "Rosie"]

var allCats = [...cats, ...tomCats]
// combines both arrays into one
// does not mutate the original array such as with join()

```

function arguments

```
function instructions(...args) {
    // do some things
}
// spread operator collects the arguments as an array
// can be used in the function block

```

#### Classes

``` javascript

class Cat {
    constructor(cat_type, gender) {
        cat_type,
        gender
    }
    meow() {
        // some method 
    }
    
}

```

Create new instance of Classes

``` javascript

const pet = new Cat("Calico", "Female");


```

Extend Classes

``` javascript

class Pet extends Cat {
    constructor(name, declawed) {
        super(name,declawed)
    }
    // sub class inherits properties of the superclass
}

```

#### Modules

exporting

``` javascript

export { myFunction }; 
// export function already named

export const foo = Math.sqrt(2);
// exporting constant

export default class {}
// export's only one variable (can also be function or object) 

```

importing

``` javascript

import { Test, Testing } from ./Testing.js
// module with multiple exports, can be destructured

import Testing from ./SingleTest.js
// modules using export default importing as single variable
```

scoping modules

``` javascript

import { Test as t } from ./Testing.js

t(someFileToTest)
// using the module variable in code

````

