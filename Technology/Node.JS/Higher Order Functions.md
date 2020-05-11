# Higher-Order Functions

> "There are two ways of constructing a software design: One way is to make it so simple that there are no deficiencies, and the other way is to make it so complicated that there are no obvious deficiencies." 
> 
> -C.A.R. Hoare, 1980 ACM Turing Award Lecture

  As Hoare said, it's impossible to build a program without any flaws, so the goal we can strive for is to develop a program without any obvious deficiencies.

> A large program is a costly program, and not just because of the time, it takes to build. Size almost always involves complexity, and complexity confuses programmers. Confused programmers, in turn, introduce mistakes (bugs) into programs.

```js
function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// → true
```
A closure is a good way to reconstruct funtions which are alike.

funny func...

```js
function repeat(n, action) {
  for (let i = 0; i < n; i++) {
    action(i);
  }
}

function unless(test, then) {
  if (!test) then();
}

repeat(3, n => {
  unless(n % 2 == 1, () => {
    console.log(n, "is even");
  });
});
// → 0 is even
// → 2 is even
```
use high order function to make program more abstract.


## Nothing enlightening else...
