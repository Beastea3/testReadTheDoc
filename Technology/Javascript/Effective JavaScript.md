# Effective JavaScript



## ‘use strict’
There are two solutions to write robust code with `use strict`:

1. Do not connect two js files which one is in strict mode, but the other one is not.
2. Define the function and encapsulate in an immediately-executed function.

## Float in JavaScript
It's so Tricky when we use JS to process the values. in my one experience, I usually went crazy when I calculate the values in JS.

JS has this problem is as expected because it has only one number value, all `typeof` results of numbers are number, no matter what it is, an integer or float. All numbers in JS are **double-precision** float. 
Precision sometimes goes run when we use float, one solution in this book provides is to convert the float to integer, which will not have the precision issues.

## Hidden Forcible Convert

Just view the code below:

```JavaScript
var x = NaN;
x === NaN // false
```

To check if a var is an NaN, we must use `isNaN()`;
but when the var is obj or other var types, `isNaN()` also returns true.
Then we can use `a !== a;` to check whether the var is NaN or not.

## Prefer original Object

ust view the code below:

```JavaScript
var s = new String('hello'); 
typeof s; // 'object'
```
## Type Converting in `===`

arg1 | arg2 | Converting
----|---|----
null | undefined | return true default
null or undefined | types other than null and undefined | return false default
original types | Date obj | convert original type to number then Date.toString then Date.valueOf
original types | Objs other than Date | convert original type to number then obj.valueOf then obj.toString
original types | Original types | convert original type to number


## When U do not need the semicolon
1. A new line in js file;
2. When the code behind can not be parsed;
    
    ```
    a = b
    (f())
    
    ```
    these codes can be executed successfully since JS compiler will not insert `;` between then. Just equal to `a = b(f())`.
3. Lines have a `return` or `break` etc.


## How about the Unicode? 

Unicode matched integer 0 to 1114111 to each character,
 
Unicode符号范围 (十六进制)  |   UTF-8编码方式（二进制）
------| ---------------------------------------------
0000 0000-0000 007F | 0xxxxxxx
0000 0080-0000 07FF | 110xxxxx 10xxxxxx
0000 0800-0000 FFFF | 1110xxxx 10xxxxxx 10xxxxxx
0001 0000-0010 FFFF | 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx

So UTF-8 Code could require 1 to 4 bytes to store.

In JS, string.length could return something unexpected, just like

```
// to-do
```

## Try use global variables LESS

Its common sense that global variables will pollute the variables in your block or functions.

## Always Define Local Variables

When uses an undefined variable, the variable will hiddenly convert to a global variable. About this, lint syntax checker is an effective solution.

## Avoid using with

Nothing to say about it, never use it.

## About the Closure

Basic features which allow the closure happens:

1. Allow the current function use the variables defined outside it.

    ```
    function makeSandwitch() {
        var magicIngredient = 'peanut butter';
        function make(filling) {
            return magicIngredient + ' and ' + filling;
        }
        return make('jelly');
    }
    makeSandwitch() // 'peanut butter and jelly' 
    ```
    function make has the access to the var magicIngredient;

2. Allow the current function use the variables defined in outer function although the outer function has returned.

    ```
    function sandwitchMaker() {
        var magicIngredient = 'peanut butter';
        function make(filling) {
            return magicIngredient + ' and ' + filling;
        }
        return make;
    }
    var f = sandwitchMaker();
    f('jelly') // “peanut butter and jelly”
    f('bananas') // "peanut butetr and bananas"
    ```
    We can see that f has still the access to the variable which defined in a returned func makeSandwitch()

    Then we can take advantage of this feature and has codes below:
    
    ```
    function sandwitchMaker(magicIngredient) {
        function make(filling) {
            return magicIngredient + ' and ' + filling;
        }
        return make;
    }
    var hamAnd = sandwitchMaker('ham');
    hamAnd('cheese'); // "ham and cheese"
    ```
    This is basical usage of closure, but I can even not use it in my work, should pay more attention in the future developing.
3. Closure can update the value of a outer variable
    
    ```
    function box() {
        var val = undefined;
        return {
            set: function(newVal) { val = newVal },
            get: function() { return val },
            type: function() { return typeof val }
        };
    }
    var b = box();
    b.type;// "undefined"
    b.set(98.9);
    b.get; 98.9
    ```
    the set func update the val in box();

## Variable hoisting
 The confusing issue is that the declaration of variables in JS will hoist to the top of the function.
 Hence, there is a way to avoid these confusions, manually hoist the variables in the function...Which I think is not a smart choice, In my own coding preference, just keep it in mind and coding as no hoisting with it is good enough.
 
##Use immediately invoked function expressions(IIFEs) to create local variables

This is efficient when we intend to keep some variables scoped in a block only.

View this buggy code below:

```
// BUGGY CODE
function wrapElements(a) {
    var result = [], i, n;
    for (i = 0, n = a.length; i < n; i++) {
        result[i] = function() { return a[i]; };
    }
    return result;
}
var wrapped = wrapElements([10, 20, 30, 40, 50]);
var f = wrapped[0];
f(); // undefined


// CORRECT CODE WITH IIFE
function wrapElements(a) {
    var result = [];
    for (var i = 0, n = a.length; i < n; i++) {
        (function(j) {
            result[i] = function() { return a[j]; };
        })(i);
    }
    return result;
}
var wrapped = wrapElements([10, 20, 30, 40, 50]);
var f = wrapped[0];
f(); // 10

```

## Prefer Named functions...

## When uses eval to create new variables, wrap them in nested functions to avoid scope pollution.

What's more, prefer indirect eval to direct eval...

## Differences between functions, methods, constructor calls.

functions are simple... methods, in my opinion, they are functions which belong to an object, and they can use this to call the object.
And constructor is to create a new object a new this.


## Try to use High-order functions more

High order function means the function which has a callback as a parameter. There are many original High-order functions in JS. I often use them when I process arrays. But these functions can be used in many scenarios, I should be careful about the possibility of using them in future developing.

## Arguments: which makes arguments variable...

arguments can process the arguments into an array of arguments...

```
function average() {
    for (var i = 0, sum = 0, n = arguments.length;
        i < n;
        i++) {
            sum += arguments[i];
        }
    return sum / n;
}

average(1,2,3) // 2
```
