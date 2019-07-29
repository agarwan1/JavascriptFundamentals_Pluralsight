# Functions and Scope
Function and Block Scope
IIFE's (immediately invoked function expressions)
Closures (functions and context kept around in memory)
The this keyword (every function - function context)
call(), apply() and bind() - have to do with this keyword
Arrow Functions
Default Parameters 

Function Scope
Lifetime of these variables
let message inside function - outside of function message is no longer available. 
```
function startCar(carId) {
  let message = 'Starting...';
  let startFn = function turnKey () {  //nested function.
      console.log(message); //'Starting...'
  };
  startFn()
}
startCar(123);
```
Function can't find var, looks at parent function. Doesn't matter how deeply you have the functions nested. 
```
function startCar(carId) {
  let message = 'Starting...';
  let startFn = function turnKey () {  //nested function.
      let message = 'Override';
  };
  startFn()
  console.log(message); //'Starting...'
}
startCar(123);
```
Nested function uses same variable name, legal but will go out of scope. 
This function will give reference error due to out of scope:
```
function startCar(carId) {
   let message = 'Starting...'
}
startCar(123);
console.log(message); //Error - message is not defined. 
```

Block Scope 
Code in between {} 
Lifetime of variables within {} other than a function
```
if (5 === 5) {
   let message = 'Equal'
}
console.log(message); //Error
```
Message went out of scope.
```
let message = 'Outside';
if (5 === 5) {
   let message = 'Equal'
   console.log(message);  //Equal
}
console.log(message);  //Outside 
```
Temporarily override outside variable. 
If we used var, it would get hoisted. Behave as if top of file.
```
if (5 === 5) {
   var message = 'Equal'
}
console.log(message); \\Equal
```
```
var message = 'Outside';
if (5 === 5) {
   var message = 'Equal'
   console.log(message);  //Equal
}
console.log(message);  //Equal
```
Block scope only applied to let. 

IIFE's 
We have modules in JS. Before modules, we needed a way to group code and work in isolation. 
IIFE = Immediately Invoked Function Expression
```
(function () {
   console.log('in function');
 })();
```
```
let app = (function() {
   let carId = 123;
   console.log('in function');
   return {};
}) ();
\\in function
\\{}
```
iife can hold onto var when creating closure.
iife is used as a closure and can access functions within that module --real value
iife is related to app - standard name is app.

Closures
```
let app = (function() {
   let carId = 123;
   let getId = function() {
      return carId;
    };
   return {            \\CLOSURE
      getId : getId    
   };
}) ();
console.log(app.getId());
\\ 123
```
Usually we see property and function name as the same - doesn't have to be.
We reference the function getId so IIFE will persist. Parent function will persist along with all of parent variables. 
Return a reference within the function. 

The this keyword
this refers to an object. Context for function - special object.
```
let fn = function() {
   console.log(this === window);
};
fn(); //true
```
this is a keyword that exists within functions.
not in strict mode. outside of strict mode - this keyword equals global object. usually working with objects with this.
```
let 0 = {
   carId: 123,
   getId: function() {
       console.log(this); \\{carId: 123, getId: f..}
       return this.carId;
   }
};
console.log(o.getId()); //123
```
Every function gets associated with this object. 
Functions in JS can be moved from object to object. 

call and apply
Change the value of this.
```
let o = {
   carId: 123,
   getId: function() {
       return this.carId;
   }
};
let newCar = {carId: 456};
console.log(o.getId.call(newCar)); 
//456
```
We can take a function and change its context. 
Apply is similiar to call. Only diff with apply, you can pass arguments.
```
let o = {
   carId: 123,
   getId: function(prefix) {
       return prefix + this.carId;
   }
};
let newCar = {carId: 456};
console.log(o.getId.apply(newCar, ['ID: '])); 
//ID: 456
```
Apply accepts array of arguments. Only difference with call.
call and apply change the value of this. 

Bind
Sometimes make a copy of function and also change the this value. 
```
let o = {
   carId: 123,
   getId: function(prefix) {
       return prefix + this.carId;
   }
};
let newCar = {carId: 456};
let newFn = o.getId.bind(newCar);
console.log(newFn()); 
//456
```

Arrow Functions
Traditionally we defined functions with function keyword. With ECMAScript now more concise.
```
let getId = () => 123; 
console.log(getId()); 
//123 
```
Looks cryptic and tricky. 
```
let getId = prefix => prefix + 123;
console.log(getId('ID: ')); //ID: 123
```
This example has two parameters:
```
let getId = (prefix, suffix) => prefix + 123 + suffix;
console.log(getId('ID: ', '!')); 
//ID: 123!
```
If arrow function has 2 or more functions we do need ().
We can specify opening and closing {}.
```
let getId = (prefix, suffix) => {
   return prefix + 123 + suffix;
};
console.log(getId('ID: ', '!')); 
//ID: 123!
```
Here, we do need the return keyword.
No curly braces and no return statement. 
No parameters - we still need ()
_ signifies a variable and may or may not be used within a function. It is a convention (instead of `()`). 
```
let getId = _ => 123;
console.log(getId());
```
*Arrow functions do not have their own "this" value. "this" refers to the enclosing context.*
Get around problems with this value. 
Good idea to use arrow functions for methods. 

Default Parameters
ES2015
```
let trackCar = function(carId, city='NY') {
   console.log(`Tracking ${carId} in ${city}.`)  //Interpolation. 
};
console.log(trackCar(123));
//Tracking 123 in NY.
console.log(trackCar(123,'Chicago'));
//Tracking 123 in Chicago.
```
The city = 'NY' is default parameter and it is used if nothing is specified.
It makes logical sense that you wouldn't have default parameter first.

Summary
Function and Block Scope 
IIFE's
Closures
The this keyword
call(), apply() and bind() 
call - call a function. apply - pass an array an arguments. bind - makes a copy of function resetting this keyword
Arrow Functions - does not have its own this value
Default Parameters


``