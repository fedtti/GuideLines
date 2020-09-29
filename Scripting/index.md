## JAVASCRIPT

#### Best Practices
* **Always add comment describing the function and its signature** before creating a new function, add a comments explaining what the function is used for, which params will recieve in input and what output will produce

```js
/**
 * This function will return the sum of the arguments recieved in input.
 *
 * @param {number} param1 the first argument of the sum
 * @param {number} param2 the second argument of the sum
 * @return {number} the sum of the arguments
 *
 */
example(param1, param2) {
    return param1 + param2;
}
```
* **Comment the main steps of the function** add some comments inside the function describing its main steps

```js
/**
 * This function will return the quotient of the arguments recieved in input.
 *
 * @param {number} param1 the first argument of the division
 * @param {number} param2 the second argument of the division
 * @return {number} the quotient of the arguments if param2 different from 0
 *
 */
example(param1, param2) {
    // If param2 is equal to 0 return 0. Check needed because we cant divide a number by 0
    if (param2 === 0) return 0;

    return param1/param2;
}
```

* **The variable name should be in camelCase**

Bad
```js
const variable_name = 0;
```

Good
```js
const variableName = 0;
```

* **Const variables should be UPPERCASE**
* **Give variable descriptive names** when creating a variable give it a descriptive name. This will help you and, if done right, no comments will be needed for that variable. For boolean variable use 'is' and 'has' prefix.

Bad
```js
// Checking if the element height is more than 100px
if (height > 100) {...}
```

Good
```js
const hasRequiredHeight = heightInPx > 100;
if (hasRequiredHeight) {...}
```

* **If a string is used in more than one place, store it in some CONST variable** this will prevent typos and also will make code more readable

* **Use arrow function when possibile** use arrow function whenever is possible to prevent errors in the function scope

* **Avoid large number of function params** when creating a function, avoid passing too much params in input. If possible, use an object instead. This will make the code more readable and prevent from having to pass every function param value even if thery are not necessary.

Bad
```js
/**
 * As you can see, when arg4 is true we don't need arg1, arg2, arg3 to be passed because they are not used
 */
function test(arg1, arg2, arg3, arg4) {
    if (arg4) return '';

    return arg1 + arg2 + arg3;
}

test('', '', '', true);
```

Good
```js
/**
 * As you can see, using an object we don't need to pass every single param.
 */
function test({ arg1, arg2, arg3, arg4 }) {
    if (arg4) return '';

    return arg1 + arg2 + arg3;
}

test({ arg4: true });
```

* **Use destructuring** thanks to object destructuring we can extract properties from an object and bind them to variables. The cool thing is that we can extract more then one prop at time

Bad
```js
const hero = {
  name: 'Batman',
  realName: 'Bruce Wayne'
};

const name     = hero.name;
const realName = hero.realName;

name;     // => 'Batman',
realName; // => 'Bruce Wayne'
```

Good
```js
const hero = {
  name: 'Batman',
  realName: 'Bruce Wayne'
};

const { name, realName } = hero;

name;     // => 'Batman',
realName; // => 'Bruce Wayne'
```

* **Prevent having line codes larger than 100 characters**
* **Use const when declaring unmutable variable, otherwise use let**
* **Object clone** when you need to clone an object follows this rules:
    * Spread operator/Object.assign() will perform a shallow copy (prefer spread operator over Object.assign());
    * JSON.stringify() ---> JSON.parse() will perform a deep copy;
* **Prevent function with too much logic** a function should be as small as possible. If the function become too much large it means that it's handling more than one task. Maybe the better solution will be splitting it into sub functions
* **Prefer async/await over promises**
* **Utils file - helpers functions** create an utils.js file in which you can store functions used over the whole application. Stop copying/pasting the same code in different functions
* **Don't overuse if/else** if a function has different possible outcome based on some value, prevent creating a list of if/else statement. Use switch instead, the code will be clearer.

Bad
```js
function test(value) {
    const text = 'Hello';
    if(value === 1) {
        text = `${text} World`;
    } else if (value === 2) {
        text = `${text} World!`;
    } else if (value === 3) {
        text = `${text} World! Guys`;
    } else {
        text = `No hello for you!`;
    }

    return text;
}
```

Good
```js
function test(value) {
    let text = 'Hello';

    switch(value) {
        case 1:
            text = `${text} World`;
            break;
        case 2:
            text = `${text} World!`;
            break;
        case 3:
            text = `${text} World! Guys`;
            break;
        default:
           text = `No hello for you!`;
            break;
        
    return text;
}
```
* **Prefer string template over string concatenation** the code will be more readable and easy to understand and easy to format. You can also use tagged template literals to make some transformation over the string

Bad
```js
const string1 = 'Hello';
const string2 = 'World';
const string3 = '!';

const string4 = string1 + ' ' + string2 + ' ' + string3;
```

Good
```js
const string1 = 'Hello';
const string2 = 'World';
const string3 = '!';

const string4 = `${string1} ${string2} ${string3}`;
```
* **Create a file for global constants** if different functions uses the same constants values, store them in a 'constants.js' file
* **Add linters to your code** to help you keep your code formatting style, add some linters plugin to help you formatting the code (ex.: es-lint)
* **Use === comparizion** using only == will make js convert the variables to match the type. Using === instead, will compare both values and types
* **Don't declare unecessary variables** If a variable is used only once, don't create it
* **Use shorcut notation** when possible, use shortcut notation instead:
    * replace if...else with **ternary operator**
    * replace if with **short-circuit evaluation**

Bad
```js
let level = false;
if (a === 1) {
    level = true;
} else {
    level = false;
}

let greetings = '';
if (level) greetings = 'Hello World!'
```

Good
```js
let level = a === 1;

let greetings = level && 'Hello World!';
```

* **Don't use console.log** don't push code with console.log inside. Remove all of them and use the browser console debugging function instead
