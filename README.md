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

### Scope;
Understanding Scope
In computer science, scope is the region of a computer program where the binding or
association of a name to an entity, such as a variable or function, is valid. JavaScript has
the following two distinct types of scope:
• Function scope
• Block scope
Understanding Scope | 3
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
var example = 5;
The following snippet provides an example of function scope:
var example = 5;
function test() {
var testVariable = 10;
console.log( example ); // Expect output: 5
console.log( testVariable ); // Expect output: 10
}
test();
console.log( testVariable ); // Expect reference erro


### Variable types;
var, let, const;

### Arrow Functions;

### Classes &amp; Modules;

### Transpilation;

### Iterators &amp; Generators;


### Hoisting;


