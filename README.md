# JS-Advanced-JavaScript
You will learn how to write JavaScript in a professional environment using the new 
JavaScript syntax in ES6, how to leverage JavaScript's asynchronous nature using 
callbacks and promises, and how to set up test suites and test your code. You will 
be introduced to JavaScript's functional programming style and you will apply 
everything you learn to build a simple application in various JavaScript frameworks 
and libraries for backend and frontend development

## Advanced JavaScript - Covering Scope, Variables, Arrow Functions, Classes &amp; Modules, Transpilation, Iterators &amp; Generators

## Learning Objectives;
  - Examine major features in ES6 and implement those features to build applications
  - Create promise and callback handlers to work with asynchronous processes
  - Develop asynchronous flows using Promise chaining and async/await syntax
  - Manipulate the DOM with JavaScript
  - Handle JavaScript browser events
  - Explore Test Driven Development and build code tests with JavaScript code testing frameworks.
  - List the benefits and drawbacks of functional programming compared to other styles
  - Construct applications with the Node.js backend framework and the React frontend framework

<a href="https://github.com/TrainingByPackt/Advanced-JavaScript">Code Bundles for Advanced JS</a>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
### Scope;
Understanding Scope
In computer science, scope is the region of a computer program where the binding or
association of a name to an entity, such as a variable or function, is valid. JavaScript has
the following two distinct types of scope:
• Function scope
• Block scope
Until ES6, function scope was the only form of scope in JavaScript; all variable and
function declarations followed function scope rules. Block scope was introduced in ES6
and is used only by the variables declared with the new variable declaration keywords
let and const. These keywords are discussed in detail in the Declaring Variables section.

Function Scope
Function scope in JavaScript is created inside functions. When a function is declared, a
new scope block is created inside the body of that function. Variables that are declared
inside the new function scope cannot be accessed from the parent scope; however, the
function scope has access to variables in the parent scope.
To create a variable with function scope, we must declare the variable with the var
keyword. For example:
```
var example = 5;
The following snippet provides an example of function scope:
var example = 5;
function test() {
  var testVariable = 10;
  console.log( example ); // Expect output: 5
  console.log( testVariable ); // Expect output: 10
}
test();
console.log( testVariable ); // Expect reference error
```

Snippet 1.1: Function Scope
Parent scope is simply the scope of the section of code that the function was defined
in. This is usually the global scope; however, in some cases, it may be useful to define a
function inside a function. In that case, the nested function's parent scope would be the
function in which it is defined. In the preceding snippet, the function scope is the scope
that was created inside the function test. The parent scope is the global scope, that is,
where the function is defined.
Note
Parent scope is the block of code, which the function is defined in. It is not the
block of code in which the function is called.

Function Scope Hoisting
When a variable is created with function scope, it's declaration automatically gets
hoisted to the top of the scope. Hoisting means that the interpreter moves the
instantiation of an entity to the top of the scope it was declared in, regardless of where
in the scope block it is defined. Functions and variables declared using var are hoisted
in JavaScript; that is, a function or a variable can be used before it has been declared.

The following code demonstrates this, as follows:
```
example = 5; // Assign value
console.log( example ); // Expect output: 5
var example; // Declare variable
Snippet 1.2: Function Scope Hoisting
```

Note
Since a hoisted variable that's been declared with var can be used before it
is declared, we have to be careful to not use that variable before it has been
assigned a value. If a variable is accessed before it has been assigned a value, it will
return the value as undefined, which can cause problems, especially if variables
are used in the global scope.

Block Scope
A new block scope in JavaScript is created with curly braces ({}). A pair of curly braces
can be placed anywhere in the code to define a new scope block. If statements, loops,
functions, and any other curly brace pairs will have their own block scope. This includes
floating curly brace pairs not associated with a keyword (if, for, etc). The code in the
following snippet is an example of the block scope rules:
```
// Top level scope
function scopeExample() {
  // Scope block 1
  for ( let i = 0; i < 10; i++ ){ /* Scope block 2 */ }
  if ( true ) { /* Scope block 3 */ } else { /* Scope block 4 */ }
  // Braces without keywords create scope blocks
  { /* Scope block 5 */ }
  // Scope block 1
  Understanding Scope | 5
}
```

Snippet 1.3: Block Scope
Variables declared with the keywords let and const have block scope. When a variable
is declared with block scope, it does NOT have the same variable hoisting as variables
that are created in function scope. Block scoped variables are not hoisted to the top of
the scope and therefore cannot be accessed until they are declared. This means that
variables that are created with block scope are subject to the Temporal Dead Zone
(TDZ). The TDZ is the period between when a scope is entered and when a variable
is declared. It ends when the variable is declared rather than assigned. The following
example demonstrates the TDZ:
```
// console.log( example ); // Would throw ReferenceError
let example;
console.log( example ); // Expected output: undefined
example = 5;
console.log( example ); // Expected output: 5
```

Note
If a variable is accessed inside the Temporal Dead Zone, then a runtime error will
be thrown. This is important because it allows our code to be built more robustly
with fewer semantic errors arising from variable declaration.
To get a better understanding of scope blocks, refer to the following table:
Figure 1.1: Function Scope versus Block Scope
In summary, scope provides us with a way to separate variables and restrict access
between blocks of code. Variable identifier names can be reused between blocks
of scope. All new scope blocks that are created can access the parent scope, or the
scope in which they were created or defined. JavaScript has two types of scope.
A new function scope is created for each function defined. Variables can be added to
function scope with the var keyword, and these variables are hoisted to the top of the
scope. Block scope is a new ES6 feature. A new block scope is created for each set of
curly braces. Variables are added to block scope with the let and const keywords. The
variables that are added are not hoisted and are subject to the TDZ.

Exercise 1: Implementing Block Scope
To implement block scope principles with variables, perform the following steps:
1. Create a function called fn1 as shown (function fn1()).
2. Log the string as scope 1.
3. Create a variable called scope with the value of 5.
4. Log the value of the variable called scope.
5. Create a new block scope inside of the function with curly braces ({}).
6. Inside the new scope block, log the string called scope 2.
7. Create a new variable called scope, inside the scope block and assign the value
different scope.
8. Log the value variable scope inside our block scope (scope 2).
9. Outside of the block scope defined in step 5 (scope 2), create a new block scope
(use curly braces).
10. Log the string called scope 3.
11. Create a variable inside the scope block (scope 3) with the same name as the
variables (call it scope) and assign it the value a third scope.
12. Log the new variable's value.
13. Call fn1 and observe its output Code
index.js:
```
function fn1(){
  console.log('Scope 1');
    let scope = 5;
    console.log(scope);
  {
    console.log('Scope 2');
    let scope = 'different scope';
    console.log(scope);
  }
  {
    console.log('Scope 3');
    let scope = 'a third scope';
    console.log(scope);
  }
}
```
// fn1();
// https://bit.ly/2RoOotW

Snippet 1.5: Block implementation output
Outcome

Figure 1.2: Scope outputs
You have successfully implemented block scope in JavaScript.
In this section, we covered the two types of JavaScript scope, function and block scope,
and the differences between them. We demonstrated how a new instance of function
scope was created inside each function and how block scope was created inside each
set of curly braces. We discussed the variable declaration keywords for each type of
scope, var for function scope and let/const for block scope. Finally, we covered the
basics of hoisting with both function and block scope.
Declaring Variables
Basic JavaScript uses the keyword var for variable declaration. ECMAScript 6
introduced two new keywords to declare variables; they are let and const. In the world
of Professional JavaScript variable declaration, var is now the weakest link. In this topic,
we will go over the new keywords, let and const, and explain why they are better than
var.
The three ways to declare variables in JavaScript are by using var, let, and const. All
function in slightly different ways. The key differences between the three variable
declaration keywords are the way they handle variable reassignment, variable scope,
and variable hoisting. These three features can be explained briefly as follows:
Variable reassignment: The ability to change or reassign the variable's value at
any time.
Variable scope: The extent or area of the code from which the variable may
be accessed.
Variable hoisting: The variable instantiation and assignment time in relation to
the variable's declaration. Some variables can be used before they are declared.
The var keyword is the older variable declaration keyword that's used to declare
variables in JavaScript. All variables created with var can be reassigned, have function
scope, and have variable hoisting. This means that variables created with var are hoisted
to the top of the scope block, where they are defined and can be accessed before
declaration. The following snippet demonstrates this, as follows:
```
// Referenced before declaration
console.log( example ); // Expect output: undefined
var example = 'example';
```

Snippet 1.6: Variables created using var are hoisted
Since variables that are created with the keyword var are not constants, they can be
created, assigned, and reassigned a value at will. The following code demonstrates this
aspect of the functionality of var:
```
// Declared and assigned
var example = { prop1: 'test' };
console.log( 'example:', example );
// Expect output: example: {prop1: "test"}
// Value reassigned
example = 5;

console.log( example ); // Expect output: 5
```

Snippet 1.7: Variables created using var are not constant
Variables created with var can be reassigned at any time and once the variable is
created, it can be accessed from anywhere in the function, even before the original
declaration point.
The let keyword functions similar to the keyword var. As expected, the keyword let
allows us to declare a variable that can be reassigned at any time. This is shown in the
following code:
```
// Declared and initialized
let example = { prop1: 'test' };
console.log( 'example:', example );
// Expect output: example: {prop1: 'test"}
// Value reassigned
example = 5;
console.log( example ); // Expect output: 5
```

Snippet 1.8: Variables created with let are not constant
There are two significant differences between let and var. Where let and var differ is
their scoping and variable hoisting properties. Variables declared with let are scoped
at the block level; that is, they are only defined in the block of code contained within a
matching pair of curly braces ({}).
Variables declared with let are not subject to variable hoisting. This means that
accessing a variable declared with let before the assignment will throw a runtime error.
As discussed earlier, this is the Temporal Dead Zone. An example of this is shown in the
following code:
```
// Referenced before declaration
console.log( example );
// Expect ReferenceError because example is not defined
let example = 'example';
```

Snippet 1.9: Variables created with let are not hoisted

The last variable declaration keyword is const. The const keyword has the same scoping
and variable hoisting rules as the let keyword; variables declared with const have block
scoping and do not get hoisted to the top of the scope. This is shown in the following
code:
```
// Referenced before declaration
console.log( example );
// Expect ReferenceError because example is not defined
const example = 'example';
```

Snippet 1.10: Variables created with const are not hoisted
The key difference between const and let is that const signifies that the identifier will
not be reassigned. The const identifier signifies a read-only reference to a value. In
other words, the value written in a const variable cannot be changed. If the value of a
variable initialized with const is changed, a TypeError will be thrown.
Even though variables created with const cannot be reassigned, this does not mean
that they are immutable. If an array or object is stored in a variable declared with const,
the value of the variable cannot be overwritten. However, the array content or object
properties can be changed. The contents of an array can be modified with functions
such as push(), pop(), or map() and object properties can be added, removed, or
updated. This is shown in the following code:
```
// Declared and initialized
const example = { prop1: 'test' };
// Variable reassigned
example = 5;
// Expect TypeError error because variable was declared with const
// Object property updated
example.prop1 = 5;
// Expect no error because subproperty was modified
```

Snippet 1.11: Variables created with const are constant but not immutable
To understand the different keywords in more detail, refer to the following table:

Figure 1.3: Differences between var, let, and const
Now that we understand the nuances among var, let, and const, we can decide on
which one to use. In the professional world, we should always use let and const,
because they provide all the functionality of var and allow the programmer to be
specific and restrictive with the variable scope and usage.
In summary, var, let, and const all function similarly. The key differences are in the
nature of const, the scope, and the hoisting. Var is function scoped, not constant, and
hoisted to the top of the scope block. let and const are both block-scoped and not
hoisted. let is not constant, while, const is constant but immutable.

Exercise 2: Utilizing Variables
To utilize the var, const, and let variable declaration keywords for variable hoisting and
reassignment properties, perform the following steps:
1. Log the string Hoisted before assignment: and the value of the hoisted variable.
2. Define a variable called hoisted with the keyword var and assign it the value this
got hoisted.
3. Log the string hoisted after assignment: and the value of the hoisted variable.
4. Create a try-catch block.
5. Inside the try block, log the value of the variable called notHoisted1.
6. Inside the catch block, give the catch block the err parameter, then log the string
Not hoisted1 with error: and the value of err.message.
7. After the try-catch block, create the notHoisted1 variable with the let keyword
and assign the value 5.
8. Log the string notHoisted1 after assignment and the value of notHoisted1.
9. Create another try-catch block.
10. Inside the try block, log the value of the notHoisted2 variable.
12 | Introducing ECMAScript 6
11. Inside the catch block, give the catch block the err parameter, then log the string
Not hoisted2 with error: and the value of err.message.
12. After the second try-catch block, create the notHoisted2 variable with the keyword
const and assign the value [1,2,3].
13. Log the string notHoisted2 after assignment and the value of notHoisted2.
14. Define a final try catch block.
15. Inside the try block, reassign notHoisted2 to the new value string.
16. Inside the catch block, give the catch block the err parameter, then log the string
Not hoisted 2 was not able to be changed.
17. After the try-catch block, push the value 5 onto the array in notHoisted2.
18. Log the string notHoisted2 updated. Now is: and the value of notHoisted2.

Code
index.js:
```
var hoisted = 'this got hoisted';
try{
  console.log(notHoisted1);
} catch(err){}
  let notHoisted1 = 5;
try{
  console.log(notHoisted2);
} catch(err){}
  const notHoisted2 = [1,2,3];
try{
  notHoisted2 = 'new value';
} catch(err){}
  notHoisted2.push(5);
```

Snippet 1.12: Updating the contents of the object
https://bit.ly/2RDEynv
Outcome
Figure 1.4: Hoisting the variables
You have successfully utilized keywords to declare variables.
In this section, we discussed variable declaration in ES6 and the benefits of using the
let and const variable declaration keywords over the var variable declaration keyword.
We discussed each keywords variable reassignment properties, variable scoping, and
variable hoisting properties. The keywords let and const are both create variables in
the block scope where var creates a variable in the function scope. Variables created
with var and let can be reassigned at will. However, variables created with const cannot
be reassigned. Finally, variables created with the keyword var are hoisted to the top of
the scope block in which they were defined. Variables created with let and const are
not hoisted.

Introducing Arrow Functions
Arrow functions, or Fat arrow functions, are a new way to create functions in
ECMAScript 6. Arrow functions simplify function syntax. They are called fat arrow
functions because they are denoted with the characters =>, which, when put together
look like a fat arrow. Arrow functions in JavaScript are frequently used in callback
chains, promise chains, array methods, in any situation where unregistered functions
would be useful.
The key difference between arrow functions and normal functions in JavaScript is that
arrow functions are anonymous. Arrow functions are not named and not bound to an
identifier. This means that an arrow function is created dynamically and is not given a
name like normal functions. Arrow functions can however be assigned to a variable to
allow for reuse.

When creating an arrow function, all we need to do is remove the function keyword and
place an arrow between the function arguments and function body. Arrow functions are
denoted with the following syntax:
```
( arg1, arg2, ..., argn ) => { /* Do function stuff here */ }
```

Snippet 1.13: Arrow function syntax
As you can see from the preceding syntax, arrow functions are a more concise way of
writing functions in JavaScript. They can make our code more concise and easier to
read.
Arrow function syntax can also vary, depending on several factors. Syntax can vary
slightly depending on the number of arguments passed in to the function, and the
number of lines of code in the function body. The special syntax conditions are outlined
briefly in the following list:
• Single input argument
• No input arguments
• Single line function body
• Single expression broken over multiple lines
• Object literal return value
Exercise 3: Converting Arrow Functions
To demonstrate the simplified syntax by converting a standard function into an arrow
function, perform the following steps:
1. Create a function that takes in parameters and returns the sum of the two
parameters. Save the function into a variable called fn1.
2. Convert the function you just created to an arrow function and save into another
variable called fn2.
To convert the function, remove the function keyword. Next, place an arrow
between the function arguments and the function body.
3. Call both functions and compare the output.
Code
index.js:
```
const fn1 = function( a, b ) { return a + b; };
const fn2 = ( a, b ) => { return a + b; };
Introducing Arrow Functions | 15
console.log( fn1( 3 ,5 ), fn2( 3, 5 ) );
```

Snippet 1.14: Calling the functions
https://bit.ly/2M6uKwN
Outcome
Figure 1.5: Comparing the function's output
You have successfully converted normal functions into arrow functions.

Arrow Function Syntax
If there are multiple arguments being passed in to the function, then we create the
function with the parentheses around the arguments as normal. If we only have a single
argument to pass to the function, we do not need to include the parentheses around
the argument.
There is one exception to this rule, and that is if the parameter is anything other than
a simple identifier. If we include a default value or perform operations in the function
arguments, then we must include the parentheses. For example, if we include a default
parameter, then we will need the parentheses around the arguments. These two rules
are shown in the following code:
```
// Single argument arrow function
arg1 => { /* Do function stuff here */ }
// Non simple identifier function argument
( arg1 = 10 ) => { /* Do function stuff here */ }
```

Snippet 1.15: Single argument arrow function
If we create an arrow function with no arguments, then we need to include the
parentheses, but they will be empty. This is shown in the following code:
```
// No arguments passed into the function
( ) => { /* Do function stuff here */ }
```

Snippet 1.16: No argument
Arrow functions can also have varied syntax, depending on the body of the function. As
expected, if the body of the function is multiline, then we must surround it with curly
braces. However, if the body of the function is a single line, then we do not need to
include the curly braces around the body of the function. This is shown in the following
code:
```
// Multiple line body arrow function
( arg1, arg2 ) => {
console.log( `This is arg1: ${arg1}` );
console.log( `This is arg2: ${arg2}` );
/* Many more lines of code can go here */
}
// Single line body arrow function
( arg1, arg2 ) => console.log( `This is arg1: ${arg1}` )
```

Snippet 1.17: Single line body
When using arrow functions, we may also exclude the return keyword if the function
is a single line. The arrow function automatically returns the resolved value of the
expression on that line. This syntax is shown in the following code:
```
// With return keyword - not necessary
( num1, num2 ) => { return ( num1 + num2 ) }
// If called with arguments num1 = 5 and num2 = 5, expected output is 10
// Without return keyword or braces
( num1, num2 ) => num1 + num2
// If called with arguments num1 = 5 and num2 = 5, expected output is 10
```

Snippet 1.18: Single line body when value is returned
Since arrow functions with single expression bodies can be defined without the curly
braces, we need special syntax to allow us to split the single expression over multiple
lines. To do this, we can wrap the multi-line expression in parentheses. The JavaScript
interpreter sees that the line are wrapped in parentheses and treats it as if it were a
single line of code. This is shown in the following code:
```
// Arrow function with a single line body
// Assume numArray is an array of numbers
( numArray ) => numArray.filter( n => n > 5).map( n => n - 1 ).every( n => n
< 10 )
// Arrow function with a single line body broken into multiple lines
// Assume numArray is an array of numbers
( numArray ) => (
numArray.filter( n => n > 5)
.map( n => n - 1 )
.every( n => n < 10 )
)
```

Snippet 1.19: Single line expression broken into multiple lines
If we have a single line arrow function returning an object literal, we will need special
syntax. In ES6, scope blocks, function bodies, and object literals are all defined with
curly braces. Since single line arrow functions do not need curly braces, we must use
the special syntax to prevent the object literal's curly braces from being interpreted as
either function body curly braces or scope block curly braces. To do this, we surround
the returned object literal with parentheses. This instructs the JavaScript engine to
interpret curly braces inside the parentheses as an expression instead of a function
body or scope block declaration. This is shown in the following code:
```
// Arrow function with an object literal in the body
( num1, num2 ) => ( { prop1: num1, prop2: num2 } ) // Returns an object
```

Snippet 1.20: Object literal return value
When using arrow functions, we must be careful of the scope that these functions are
called in. Arrow functions follow normal scoping rules in JavaScript, with the exception
of the this scope. Recall that in basic JavaScript, each function is assigned a scope, that
is, the this scope. Arrow functions are not assigned a this scope. They inherit their
parent's this scope and cannot have a new this scope bound to them. This means
that, as expected, arrow functions have access to the scope of the parent function, and
subsequently, the variables in that scope, but the scope of this cannot be changed in
an arrow function. Using the .apply(), .call(), or .bind() function modifiers will NOT
change the scope of an arrow function's this property. If you are in a situation where
you must bind this to another scope, then you must use a normal JavaScript function.

In summary, arrow functions provide us with a way to simplify the syntax of anonymous
functions. To write an arrow function, simply omit the function keyword and add an
arrow between the arguments and function body.
Special syntax can then be applied to the function arguments and body to simplify the
arrow function even more. If the function has a single input argument, then we can
omit the parentheses around it. If the function body has a single line, we can omit the
return keyword and the curly braces around it. However, single-line functions that
return an object literal must be surrounded with parentheses.
We can also use parentheses around the function body to break a single line body into
multiple lines for readability.

Exercise 4: Upgrading Arrow Functions
To utilize the ES6 arrow function syntax to write functions, perform the following steps:
1. Refer to the exercises/exercise4/exercise.js file and perform the updates in this
file.
2. Convert fn1 with basic ES6 syntax.
Remove the function keyword before the function arguments. Add an arrow
between the function arguments and function body.
3. Convert fn2 with single statement function body syntax.
Remove the function keyword before the function arguments. Add an arrow
between the function arguments and function body.
Remove the curly braces ({}) around the function body. Remove the return
keyword.
4. Convert fn3 with Single input argument syntax.
Remove the function keyword before the function arguments. Add an arrow
between the function arguments and function body.
Remove the parentheses around the function input argument.
5. Convert fn4 with no input argument syntax.
Remove the function keyword before the function arguments. Add an arrow
between the function arguments and function body.
6. Convert fn5 with object literal syntax.
Remove the function keyword before the function arguments. Add an arrow
between the function arguments and function body.
Remove the curly braces ({}) around the function body. Remove the return
keyword.
Surround the returned object with parentheses.
Code
index.js:
```
let fn1 = ( a, b ) => { … };
let fn2 = ( a, b ) => a * b;
let fn3 = a => { … };
let fn4 = () => { … };
let fn5 = ( a ) => ( … );
```

Snippet 1.21: Arrow function conversion
https://bit.ly/2M6qSfg
Outcome
Figure 1.6: Converting the function's output
You have successfully utilized the ES6 arrow function syntax to write functions.
In this section, we introduced arrow functions and demonstrated how they can be used
to greatly simplify function declaration in JavaScript. First, we covered the basic syntax
for arrow functions: ( arg1, arg2, argn ) => { /* function body */ }. We proceeded
to cover the five special syntax cases for advanced arrow functions, as outlined in the
following list:
• Single input argument: arg1 => { /* function body */ }
• No input arguments: ( ) => { /* function body */ }
• Single line function body: ( arg1, arg2, argn ) => /* single line */
• Single expression broken over multiple lines: ( arg1, arg2, argn ) => ( /* multi
line single expression */ )
• Object literal return value: ( arg1, arg2, argn ) => ( { /* object literal */ }
)

Learning Template Literals
Template literals are a new form of string that was introduced in ECMAScript 6. They
are enclosed by the backtick symbol (``) instead of the usual single or double quotes.
Template literals allow you to embed expressions in the string that are evaluated
at runtime. Thus, we can easily create dynamic strings from variables and variable
expressions. These expressions are denoted with the dollar sign and curly braces (${
expression }). The template literal syntax is shown in the following code:
```
const example = "pretty";
console.log( `Template literals are ${ example } useful!!!` );
// Expected output: Template literals are pretty useful!!!
```

Snippet 1.22: Template literal basic syntax
Template literals are escaped like other strings in JavaScript. To escape a template
literal, simply use a backslash (\) character. For example, the following equalities
evaluate to true: `\`` === "`",`\t` === "\t", and `\n\r` === "\n\r".
Template literals allow for multiline strings. Any newline characters that are inserted
into the source are part of the template literal and will result in a line break in the
output. In simpler terms, inside a template literal, we can press the Enter key on the
keyboard and split it on to two lines. This newline character in the source code will
be parsed as part of the template literal and will result in a newline in the output. To
replicate this with normal strings, we would have to use the \n character to generate a
new line. With template literals, we can break the line in the template literal source and
achieve the same expected output. An example of this is shown in the following code:
```
// Using normal strings
console.log( 'This is line 1\nThis is line 2' );
// Expected output: This is line 1
// This is line 2
// Using template literals
console.log( `This is line 1
This is line 2` );
// Expected output: This is line 1
// This is line 2
```

Snippet 1.23: Template literal multi-line syntax

Exercise 5: Converting to Template Literals

To convert standard string objects to template literals to demonstrate the power of
template literal expressions, perform the following steps:
1. Create two variables, a and b, and save numbers into them.
2. Log the sum of a and b in the format a + b is equal to <result> using normal
strings.
3. Log the sum of a and b in the format a + b is equal to <result> using a single
template literal.
Code
index.js:
```
let a = 5, b = 10;
console.log( a + ' + ' + b + ' is equal to ' + ( a + b ) );
console.log( `${a} + ${b} is equal to ${a + b}` );
```

Snippet 1.24: Template literal and string comparison
https://bit.ly/2RD5jbC
Outcome

Figure 1.7: Logging the sum of the variable's output
You have successfully converted standard string objects to template literals.
Template literals allow for expression nesting, that is, new template literals can be put
inside the expression of a template literal. Since the nested template literal is part of
the expression, it will be parsed as a new template literal and will not interfere with
the external template literal. In some cases, nesting a template literal is the easiest and
most readable way to create a string. An example of template literal nesting is shown in
the following code:
```
function javascriptOrCPlusPlus() { return 'JavaScript'; }
const outputLiteral = `We are learning about ${ `Professional ${
javascriptOrCPlusPlus() }` }`
```

Snippet 1.25: Template literal nesting
A more advanced form of template literals are tagged template literals. Tagged
template literals can be parsed with a special function called tag functions, and can
return a manipulated string or any other value. The first input argument of a tag
function is an array containing string values. The string values represent the parts of
the input string, broken at each template expression. The remaining arguments are the
values of the template expressions in the string. Tag functions are not called like normal
functions. To call a tag function, we omit the parentheses and any whitespace around
the template literal argument. This syntax is shown in the following code:
```
// Define the tag function
function tagFunction( strings, numExp, fruitExp ) {
const str0 = strings[0]; // "We have"
const str1 = strings[1]; // " of "
const quantity = numExp < 10 ? 'very few' : 'a lot';
return str0 + quantity + str1 + fruitExp + str2;
}
const fruit = 'apple', num = 8;
// Note: lack of parenthesis or whitespace when calling tag function
const output = tagFunction`We have ${num} of ${fruit}. Exciting!`
console.log( output )
// Expected output: We have very few of apples. Exciting!!
```

Snippet 1.26: Tagged template literal example
A special property named raw is available for the first argument of a tagged template.
This property returns an array that contains the raw, unescaped, versions of each part
of the split template literal. This is shown in the following code:
```
function tagFunction( strings ){ console.log( strings.raw[0] ); }
tagFunction`This is line 1. \n This is line 2.`
// Expected output: "This is line 1. \n This is line 2." The characters
//'\' and 'n' are not parsed into a newline character
```
Snippet 1.27: Tagged template raw property
In summary, template literals allow for the simplification of complicated string
expressions. Template literals allow you to embed variables and complicated
expressions into strings. Template literals can even be nested into the expression
fields of other template literals. If a template literal is broken into multiple lines in the
source code, the interpreter will interpret that as a new line in the string and insert one
accordingly. Template literals also provide a new way to parse and manipulate strings
with the tagged template function. These functions give you a way to perform complex
string manipulation via a special function. The tagged template functions also give
access to the raw strings as they were entered, ignoring any escape sequences.
Exercise 6: Template Literal Conversion
You are building a website for a real estate company. You must build a function that
takes in an object with property information and returns a formatted string that states
the property owner, where the property is located (address), and how much they are
selling it for (price). Consider the following object as input:
```
{
address: '123 Main St, San Francisco CA, USA',
floors: 2,
price: 5000000,
owner: 'John Doe'
}
```

Snippet 1.28: Object Input
To utilize a template literal to pretty-print an object, perform the following steps:
1. Create a function called parseHouse that takes in an object.
2. Return a template literal from the function. Using expressions, embed the owner,
address, and price in the format <Owner> is selling the property at <address>
for <price>.
3. Create a variable called house and save the following object into it: { address: "123
Main St, San Francisco CA, USA", floors: 2, price: 5000000, owner: "John
Doe" }
4. Call the parseHouse function and pass in the house variable.
5. Log the output.
Code
index.js:
```
function parseHouse( property ) {
return `${property.owner} is selling the property at ${property.address}
for ${property.price} USD`
}
const house = {
address: "123 Main St, San Francisco CA, USA",
floors: 2,
price: 5000000,
owner: "John Doe"
};
console.log( parseHouse( house ) );
```

Snippet 1.29: Template literal using expressions
https://bit.ly/2RklKKH

Outcome

Figure 1.8: Template literal output
You have successfully utilized a template literal to pretty-print an object.
In this section, we covered template literals. Template literals upgrade strings by
allowing us to nest expressions inside them that are parsed at runtime. Expressions
are inserted with the following syntax: `${ expression }`. We then showed you how
to escape special characters in template literals and discussed how in-editor newline
characters in template literals are parsed as newline characters in the output. Finally,
we covered template literal tagging and tagging functions, which allow us to perform
more complex template literal parsing and creation.

Enhanced Object Properties
ECMAScript 6 added several enhancements to object literals as part of the ES6
syntactic sugar. ES6 added three ways to simplify the creation of object literals. These
simplifications include a more concise syntax for initializing object properties from
variables, a more concise syntax for defining function methods, and computed object
property names.

Note

Syntactic sugar is a syntax that is designed to make expressions easier to read and
express. It makes the syntax "sweeter" because code can be expressed concisely.
Object Properties
The shorthand for initializing object properties allows you to make more concise
objects. In ES5, we needed to define the object properties with a key name and a value,
as shown in the following code:
```
function getPersionES5( name, age, height ) {
return {
name: name,
age: age,
height: height
};
}
getPersionES5( 'Zachary', 23, 195 )
// Expected output: { name: 'Zachary', age: 23, height: 195 }
```

Snippet 1.30: ES5 object properties
Notice the repetition in the object literal returned by the function. We name the
property in the object after variable name causing duplication (<code>name: name</
code>). In ES6, we can shorthand each property and remove the repetition. In ES6, we
can simply state the variable in the object literal declaration and it will create a property
with a key that matches the variable name and a value that matches the variable value.
This is shown in the following code:
```
function getPersionES6( name, age, height ) {
return {
Enhanced Object Properties | 27
name,
age,
height
};
}
getPersionES6( 'Zachary', 23, 195 )
// Expected output: { name: 'Zachary', age: 23, height: 195 }
```

Snippet 1.31: ES6 object properties
As you can see, both the ES5 and ES6 examples output the exact same object. However,
in a large object literal declaration, we can save a lot of space and repetition by using
this new shorthand.

Function Declarations

ES6 also added a shorthand for declaring function methods inside objects. In ES5,
we had to state the property name, then define it as a function. This is shown in the
following example:
```
function getPersonES5( name, age, height ) {
return {
name: name,
height: height,
getAge: function(){ return age; }
};
}
getPersonES5( 'Zachary', 23, 195 ).getAge()
// Expected output: 23
```

Snippet 1.32: ES5 function properties

In ES6, we can define a function but with much less work. As with the property
declaration, we don't need a key and value pair to create the function. The function
name becomes the key name. This is shown in the following code:
```
function getPersionES6( name, age, height ) {
return {
name,
height,
getAge(){ return age; }
};
}
getPersionES6( 'Zachary', 23, 195 ).getAge()
// Expected output: 23
```

Snippet 1.33: ES6 function properties
Notice the difference in the function declaration. We omit the function keyword and
the colon after the property key name. Once again, this saves us a bit of space and
simplifies things a little.
Computed Properties
ES6 also added a new, efficient way to create property names from variables. This is
through computed property notation. As we already know, in ES5, there is only one
way to create a dynamic property whose name is specified by a variable; this is through
bracket notation, that is, : obj[ expression ] = 'value' . In ES6, we can use this same
type of notation during the object literal's declaration. This is shown in the following
example:
```
const varName = 'firstName';
const person = {
[ varName ] = 'John',
lastName: 'Smith'
};
console.log( person.firstName ); // Expected output: John
```
Snippet 1.34: ES6 Computed property

As we can see from the preceding snippet, the property name of varName was
computed to be firstName. When accessing the property, we simply reference it as
person.firstName. When creating computed properties in object literals, the value
that's computed in the brackets does not need to be a variable; it can be almost any
expression, even a function. An example of this is shown in the following code:
```
const varName = 'first';
function computeNameType( type ) {
return type + 'Name';
}
const person = {
[ varName + 'Name' ] = 'John',
[ computeNameType( 'last' ) ]: 'Smith'
};
console.log( person.firstName ); // Expected output: John
console.log( person.lastName ); // Expected output: Smith
```

Snippet 1.35: Computed property from function
In the example shown in the preceding snippet, we created two variables. The first
contains the string first and the second contains a function that returns a string.
We then created an object and used computed property notation to create dynamic
object key names. The first key name is equal to firstName. When person.firstName is
accessed, the value that was saved will be returned. The second key name is equal to
lastName. When person.lastName is accessed, the value that was saved will be returned.
In summary, ES6 added three ways to simplify the declaration of object literals, that is,
property notation, function notation, and computed properties. To simplify property
creation in objects, when properties are created from variables, we can omit the key
name and the colon. The name property that's created is set to the variable name and
the value is set to the value of the variable. To add a function as a property to an object,
we can omit the colon and function keyword. The name of the property that's created is
set to the function name and the value of the property is the function itself. Finally, we
can create property names from computed expressions during the declaration of the
object literal. We simply replace the key name with the expression in brackets. These
three simplifications can save us space in our code and make object literal creation
easier to read.

Exercise 7: Implementing Enhanced Object Properties

You are building a simple JavaScript math package to publish to Node Package Manager
(NPM). Your module will export an object that contains several constants and functions.
Using ES6 syntax, create the export object with the following functions and values: the
value of pi, the ratio to convert inches to feet, a function that sums two arguments, and
a function that subtracts two arguments. Log the object after it has been created.
To create objects using ES6 enhanced object properties and demonstrate the simplified
syntax, perform the following steps:
1. Create an object and save it into the exportObject variable.
2. Create a variable called PI that contains the value of pi (3.1415).
3. Create a variable called INCHES_TO_FEET and save the value of the inches to feet
conversion ratio (0.083333).
Using ES6 enhanced property notation, add a property called PI from the variable
PI. Add a property called INCHES_TO_FEET from the INCHES_TO_FEET variable, which
contains the inches to feet conversion ratio.
Add a function property called sum that takes in two input arguments and returns
the sum of the two input arguments.
Add a function property called subtract that takes in two input arguments and
returns the subtraction of the two input arguments.
4. Log the object exportObject.
Code
index.js:
```
const PI = 3.1415;
const INCHES_TO_FEET = 0.083333;
const exportObject = {
PI,
INCHES_TO_FEET,
sum( n1, n2 ) {
return n1 + n2;
},
subtract( n1, n2 ) {
return n1 - n2;
Destructuring Assignment | 31
}
};
console.log( exportObject );
```

Snippet 1.36: Enhanced object properties
https://bit.ly/2RLdHWk

Outcome

Figure 1.9: Enhanced object properties output
You have successfully created objects using ES6 enhanced object properties.
In this section, we showed you enhanced object properties, a syntactic sugar to help
condense object property creation into fewer characters. We covered the shorthand for
initializing object properties from variables and functions, and we covered the advanced
features of computed object properties, that is, a way to create an object property name
from a computed value, inline, while defining the object.

Destructuring Assignment
Destructuring assignment is syntax in JavaScript that allows you to unpack values
from arrays or properties from objects, and save them into variables. It is a very handy
feature because we can extract data directly from arrays and objects to save into
variables, all on a single line of code. It is powerful because it enables us to extract
multiple array elements or object properties in the same expression.

Array Destructuring
Array destructuring allows us to extract multiple array elements and save them into
variables. In ES5, we do this by defining each variable with its array value, one variable
at a time. This makes the code lengthy and increases the time required to write it.

In ES6, to destructure an array, we simply create an array containing the variable to
assign data into, and set it equal to the data array being destructured. The values in the
array are unpacked and assigned to the variables in the left-hand side array from left to
right, one variable per array value. An example of basic array destructuring is shown in
the following code:
```
let names = [ 'John', 'Michael' ];
let [ name1, name2 ] = names;
console.log( name1 ); // Expected output: 'John'
console.log( name2 ); // Expected output: 'Michael'
```

Snippet 1.37: Basic array destructuring
As can be seen in this example, we have an array of names and we want to destructure
it into two variables, name1 and name2. We simply surround the variables name1 and
name2 with brackets and set that expression equal to the data array names, and then
JavaScript will destructure the names array, saving data into each of the variables.
The data is destructured from the input array into the variables from left to right, in
the order of array items. The first index variable will always be assigned the first index
array item. This leads to the question, what do we do if we have more array items than
variables? If there are more array items than variables, then the remaining array items
will be discarded and will not be destructured into variables. The destructuring is a one
to one mapping in array order.
What about if there are more variables than array items? If we attempt to destructure
an array into an array that contains more variables than the total number of array
elements in the data array, some of the variables will be set to undefined. The array
is destructured from left to right. Accessing a non-existent element in a JavaScript
array results in an undefined value to be returned. This undefined value is saved to the
leftover variables in the variable array. An example of this is shown in the following
code:
```
let names = [ 'John', 'Michael' ];
let [ name1 ] = names
let [ name2, name3, name4 ] = names;
console.log( name1 ); // Expected output: 'John'
console.log( name2 ); // Expected output: 'John'
console.log( name3 ); // Expected output: 'Michael'
console.log( name4 ); // Expected output: undefined
```

Snippet 1.38: Array destructuring with mismatched variable and array items

Note
We must be careful when destructuring arrays to make sure that we don't
unintentionally assume that a variable will contain a value. The value of the
variable could be set to undefined if the array is not long enough.
ES6 array destructuring allows for skipping array elements. If we have an array of values
and we only care about the first and third values, we can still destructure the array.
To ignore a value, simply omit the variable identifier for that array index in the left-
hand side of the expression. This syntax can be used to ignore a single item, multiple
items, or even all the items in an array. Two examples of this are shown in the following
snippet:
```
let names = [ 'John', 'Michael', 'Jessica', 'Susan' ];
let [ name1,, name3 ] = names;
// Note the missing variable name for the second array item
let [ ,,, ] = names; // Ignores all items in the array
console.log( name1 ); // Expected output: 'John'
console.log( name3 ); // Expected output: 'Jessica'
```
Snippet 1.39: Array destructuring with skipped values

Another very useful feature of array destructuring is the ability to set default values for
variables that are created with destructuring. When we want to add a default value, we
simply need to set the variable equal to the desired default value in the left-hand side of
the destructuring expression. If what we are destructuring does not contain an index to
assign to the variable, then the default value will be used instead. An example of this is
shown in the following code:
```
let [ a = 1, b = 2, c = 3 ] = [ 'cat', null ];
console.log( a ); // Expected output: 'cat'
console.log( b ); // Expected output: null
console.log( c ); // Expected output: 3
```

Snippet 1.40: Array destructuring with skipped values
Finally, array destructuring can be used to easily swap values of variables. If we wish to
swap the value of two variables, we can simply destructure an array into the reversed
array. We can create an array containing the variables we want to reverse and set
it equal to the same array, but with the variable order changed. This will cause the
references to be swapped. This is shown in the following code:
let a = 10;
let b = 5;
[ a, b ] = [ b, a ];
console.log( a ); // Expected output: 5
console.log( b ); // Expected output: 10

Snippet 1.41: Array destructuring with skipped values
Exercise 8: Array Destructuring
To extract values from an array using array destructuring assignment, perform the
following steps:
1. Create an array with three values, 1, 2, and 3, and save it into a variable called data.
2. Destructure the array created with a single expression.
Destructure the first array value into a variable called a. Skip the second value of
the array.
Destructure the third value into a variable called b. Attempt to destructure a
fourth value into a variable called c and provide a default value of 4.
3. Log the value of all of the variables.
Code
index.js:
const data = [ 1, 2, 3 ];
const [ a, , b, c = 4 ] = data;
console.log( a, b, c );

Snippet 1.42: Array destructuring
https://bit.ly/2D2Hm5g
Outcome
Figure 1.10: Destructured variable's output
You have successfully applied an array destructuring assignment to extract values from
an array.
In summary, array destructuring allows us to quickly extract values from arrays and
save them into variables. Variables are assigned to array values, item by item, from
left to right. If the number of variables exceeds the number of array items, then the
variables are set to undefined, or the default value if specified. We can skip an array
index in the destructuring by leaving a hole in the variables array. Finally, we can use
destructuring assignment to quickly swap the values of two or more variables in a single
line of code.

Rest and Spread Operators
ES6 also introduces two new operators for arrays called rest and spread. The rest and
spread operators are both denoted with three ellipses or periods before an identifier (
...array1 ). The rest operator is used to represent an infinite number of arguments as
an array. The spread operator is used to allow an iterable object to be expanded into
multiple arguments. To identify which is being used, we must look at the item that
the argument is being applied to. If the operator is applied to an iterable object (array,
object, and so on), then it is the spread operator. If the operator is applied to function
arguments, then it is the rest operator.
Note
In JavaScript, something considered iterable if something (generally values or key/
value pairs) can be stepped through one at a time. For example, an array is iterable
because the items in the array can be stepped through one at a time. Objects are
considered iterable because the key/value pairs can be stepped through one at a
time.
The rest operator is used to represent an indefinite number of arguments as an array.
When the last parameter of a function is prefixed with the three ellipses, it becomes
an array. The array elements are supplied by the actual arguments that are passed into
the function, excluding the arguments that already have been given a separate name in
the formal declaration of the function. An example of rest destructuring is shown in the
following code:
```
function fn( num1, num2, ...args ) {
// Destructures an indefinite number of function parameters into the
//array args, excluding the first two arguments passed in.
console.log( num1 );
console.log( num2 );
console.log( args );
}
```

Destructuring Assignment | 37
```
fn( 1, 2, 3, 4, 5, 6 );
// Expected output
// 1
// 2
// [ 3, 4, 5, 6 ]
```
Snippet 1.43: Array destructuring with skipped values
Similar to the arguments object of a JavaScript function, the rest operator contains a
list of function arguments. However, the rest operator has three distinct differences
from the arguments object. As we already know, the arguments object is an array-like
object that contains each argument that's passed into the function. The differences
are as follows. First, the rest operator contains only the input parameters that have not
been given a separate formal declaration in the function expression.
Second, the arguments object is not an instance of an Array object. The rest parameter
is an instance of an array, which means that array functions like sort(), map(), and
forEach() can be applied to them directly.
Lastly, the arguments object has special functionality that the rest parameter does not
have. For example, the caller property exists on the arguments object.
The rest parameter can be destructured similar to how we destructure an array. Instead
of putting a single variable name inside before the ellipses, we can replace it with
an array of variables we want to fill. The arguments passed into the function will be
destructured as expected for an array. This is shown in the following code:
```
function fn( ...[ n1, n2, n3 ] ) {
// Destructures an indefinite number of function parameters into the
// array args, which is destructured into 3 variables
console.log( n1, n2, n3 );
}
fn( 1, 2 ); // Expected output: 1, 2, undefined
```

Snippet 1.44: Destructured rest operator
The spread operator allows an iterable object such as an array or string to be expanded
into multiple arguments (for function calls), array elements (for array literals), or
key-value pairs (for object expressions). This essentially means that we can expand
an array into arguments for creating another array, object, or calling a function. An
example of spread syntax is shown in the following code:
```
function fn( n1, n2, n3 ) {
console.log( n1, n2, n3 );
}
const values = [ 1, 2, 3 ];
fn( ...values ); // Expected output: 1, 2, 3
```

Snippet 1.45: Spread operator
In the preceding example, we created a simple function that takes in three inputs
and logs them to the console. We created an array with three values, then called the
function using the spread operator to destructure the array of values into three input
parameters for the function.
The rest operator can be used in destructuring objects and arrays. When destructuring
an array, if we have more array elements than variables, we can use the rest operator to
capture, or catch, all of the additional array elements during destructuring. When using
the rest operator, it must be the last parameter in the array destructuring or function
arguments list. This is shown in the following code:
const [ n1, n2, n3, ...remaining ] = [ 1, 2, 3, 4, 5, 6 ];
console.log( n1 ); // Expected output: 1
console.log( n2 ); // Expected output: 2
console.log( n3 ); // Expected output: 3
console.log( remaining ); // Expected output: [ 4, 5, 6 ]

Snippet 1.46: Spread operator
In the preceding snippet, we destructured the first three array elements into three
variables, n1, n2, and n3. We then captured the remaining array elements with the rest
operator and destructured them into the variable that remained.

In summary, the rest and spread operators allow iterable entities to be expanded into
many arguments. They are denoted with three ellipses before the identifier name.
This allows us to capture arrays of arguments in functions or unused items when
destructuring entities. When we use the rest and spread operators, they must be the
last arguments that are passed into the expression they are being used in.

Object Destructuring
Object destructuring is used in a very similar way to array destructuring. Object
destructuring is used to extract data from an object and assign the values to new
variables. In ES6, we can do this in a single JavaScript expression. To destructure an
object, we surround the variables we want to destructure with curly braces ({}), and
set that expression equal to the object we are destructuring. A basic example of object
destructuring is shown in the following code:
```
const obj = { firstName: 'Bob', lastName: 'Smith' };
const { firstName, lastName } = obj;
console.log( firstName ); // Expected output: 'Bob'
console.log( lastName ); // Expected output: 'Smith'
```

Snippet 1.47: Object destructuring
In the preceding example, we created an object with the keys firstName and lastName.
We then destructured this object into the variables firstName and lastName. Notice
that the names of the variables and the object parameters match. This is shown in the
following example:
Note
When doing basic object destructuring, the name of the parameter in the object
and the name of the variable we are assigning it to must match. If there is no
matching parameter for a variable we are trying to destructure, then the variable
will be set to undefined.
```
const obj = { firstName: 'Bob', lastName: 'Smith' };
const { firstName, middleName } = obj;
console.log( firstName ); // Expected output: 'Bob'
console.log( middleName ); // Expected output: undefined
```

Snippet 1.48: Object destructuring with no defined key
As we saw, the middleName key does not exist in the object. When we try to destructure
the key and save it into the variable, it is unable to find a value and the variable is set to
undefined.
With advanced object destructuring syntax, we can save the key that's extracted into
a variable with a different name. This is done by adding a colon and the new variable
name after the key name in the destructuring notation. This is shown in the following
code:
```
const obj = { firstName: 'Bob', lastName: 'Smith' };
const { firstName: first, lastName } = obj;
console.log( first ); // Expected output: 'Bob'
console.log( lastName ); // Expected output: 'Smith'
```
Snippet 1.49: Object destructuring into new variable
In the preceding example, we could clearly see that we are destructuring the firstname
key from the object and saving it into the new variable, called first. The lastName key is
being destructured normally and is saved into a variable called lastName.
Much like with array destructuring, we can destructure an object and provide a default
value. If a default value is provided and the key we are attempting to destructure does
not exist in the object, then the variable will be set to the default value instead of
undefined. This is shown in the following code:
```
const obj = { firstName: 'Bob', lastName: 'Smith' };
const { firstName = 'Samantha', middleName = 'Chris' } = obj;
console.log( firstName ); // Expected output: 'Bob'
console.log( middleName ); // Expected output: 'Chris'
```

Snippet 1.50: Object destructuring with default values
Destructuring Assignment | 41
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->

### Variable types;
var, let, const;

### Arrow Functions;

### Classes &amp; Modules;

### Transpilation;

### Iterators &amp; Generators;


### Hoisting;


