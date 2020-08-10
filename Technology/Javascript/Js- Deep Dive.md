# Js: Deep Dive


Some notes of reading the list of articles in [33 concepts in JS](https://github.com/leonardomso/33-js-concepts?utm_source=gold_browser_extension). Maybe trivial, but useful.

## Currying, Composition of functions and Pipe

Actually, I don't know something about function composition before. But after read the first article in the list, I find I have realized it in my code already.

### Pure functions

The functions below are defined as impure functions:
 
 - Use non-local variables.
 - Cause mutations to the arguments passed on to it.
 - Return different results with same arguments.
 - Cause side effect like output to I/O device eg.`console.log()`.

**Function composition** is the act of pipelining the result of one function, to the input of another, creating an entirely new function.

**currying** is a process of converting a <n> arguments function into a chained sequence of <n> functions each with one argument.

```js
function add(a, b){
   return a+b;
}
add(1,2); //3

function curriedAdd(a){
   return function(b){
      return a+b;
   }
}
curriedAdd(1)(2); //3
```

