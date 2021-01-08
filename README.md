# JS Notes

## Closures
A closure is a function defined inside another function (called the parent function), and has access to variables that are declared and defined in the parent function scope.

```
foo() // undefined
bar() // 'bar
// Defined at run-time
var foo = function(){ 
    return 'foo'
}; 
// Defined at parse time
function bar(){ 
     return 'bar'
};

```

## Hoisting
In the execution context variables declared using the `var` keyword or functions declared using the `function` keyword will have their declarations moved to the top of their scope, the global scope.  
>Global scope for: Browser (`window`) and Node (`global`)
>Declaring a variable with `let` or `const` does not add it to the global object.
```
foo() // undefined
bar() // 'bar
oop() // ReferenceError: Cannot access 'oop' before initialization
var foo = function(){ 
    return 'foo'
}; 
function bar(){ 
     return 'bar'
};
const oop = () => 'oop';
```
Above `var foo` will be processed and a reference to `foo` will be created in memory with `undefined`

## Strict Mode

>The short and most important answer here is that use strict is a way to voluntarily enforce stricter parsing and error handling on your JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. In general, it is a good practice.

- Makes debugging easier. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions, alerting you sooner to problems in your code and directing you more quickly to their source.
- Prevents accidental globals. Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. 
- Eliminates `this` coercion. Without strict mode, a reference to a `this` value of null or undefined is automatically coerced to the global. In strict mode, referencing a a this value of null or undefined throws an error.
- Disallows duplicate parameter values. Strict mode throws an error when it detects a duplicate named argument for a function (e.g., function foo(val1, val2, val1){}), thereby catching what is almost certainly a bug in your code that you might otherwise have wasted lots of time tracking down.
-Makes eval() safer. There are some differences in the way `eval()` behaves in strict mode and in non-strict mode. Most significantly, in strict mode, variables and functions declared inside of an eval() statement are not created in the containing scope (they are created in the containing scope in non-strict mode, which can also be a common source of problems).
- Throws error on invalid usage of `delete`.  

## Misc
### Associativity rule 

Operators with the same precedence are processed based on the associativity property of the operator. The associativity of the assignment operator is Right to Left.

Number + Number -> Addition
Boolean + Number -> Addition
Boolean + Boolean -> Addition
Number + String -> Concatenation
String + Boolean -> Concatenation
String + String -> Concatenation

###  Check if object is array
 Object.prototype.toString.call()
 Array.isArray
 ### Get Modulus of negative
 ```
 function mod(n, m) {
  return ((n % m) + m) % m;
}
 ```

this
bind
call
apply
generator
eval
prototype
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY1NjI0OTQ3NSw2MDI2NjgyLDMyMzkyMj
c4MiwyMjU0MjI0MjMsNTQyMjE5MDczLDE0ODYzMzI2OTVdfQ==

-->