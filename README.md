# JavascriptFundamentals_Pluralsight

Intro and Setup
JS Language Features
Operators
Functions and Scope 
Objects and Arrays
Classes and Modules
Programming the BOM and DOM
Promises and Error Handling
Data Access Using HTTP
Forms
Security
Building for Production 
`npm run dev`
localhost:1337

History
Created in 1995 by Brandon Eich
1997 - ECMA Standard, ECMAScript
ECMAScript = Javascript
2015 - ECMAScript 2015 (ES6) - mast majority of updates
>2015 - Yearly Updates

Node JS
VSC
https://webpack.js.org/ (will be installed by npm)
https://github.com/wbkd/webpack-starter

VS Code
CTRL + `
Extensions: Marketplace
`ext:git`

babel-loader converts to earlier version of JS. we don't want that. 
In webpack.config.dev.js:
  test: /\.(js)$/,
        include: Path.resolve(__dirname, '../src'),
        loader: 'babel-loader'
babel only converts 70% to ES5.

Constants, let and var, Rest Parameters, Destructuring, Spread Syntax, typeof()
const carId = 42; 
constants must be initialized (with value) 
const carId = 42;
carId = 100; //ERROR! Constant cannot be changed.
const carId; //error unexpected token.

let and var for variable Declarations
C, C++, Java 

```
if (true) {
   var foo = 9;
}
console.log(foo); //9
```
```
if (true) {
   let foo = 9; //let has block scoping 
}
console.log(foo); //error - program execution leaves block. 
```

Let has block scoping and var does not. 
Best practice using let over var.
Let helps you catch errors earlier because compiler will complain earlier. 

Rest parameters
```
function sendCars(...allCarIds) {
   allCarIds.forEach ( id => console.log(id));
}
sendCars(100, 200, 555);
//100 200 555
allCarIds will be an array.
```
```
function sendCars(day, ...allCarIds) {
   allCarIds.forEach( id => console.log(id));
}
sendCars('Monday',100,200,555);
// 100 200 555
```
You can mix normal and rest parameters but you always need to call rest parameter last. 
Comma is not permitted after rest parameter.

Destructuing Arrays
Easily assign values within array to variables. Can also destructure objects. 
```
let carIds = [1,2,5];
let [car1, car2, car3] = carIds; //destructuring syntax 
console.log(car1, car2, car3);
// 1 2 5
```
Taking array and assigning it to variables.

```
let carIds = [1,2,5]
let car1, remainingCars;
[car1, ... remainingCars] = carIds; //destructuring and then rest parameter syntax 
console.log(car1, remainingCars);
// 1 [2,5]
```

```
let carIds = [1,2,5];
let remainingCars;
[, ... remainingCars] = carIds; // destructuring syntax starts with , to skip first. remaining array elements in remainingCars.
console.log(remainingCars);
// [2,5]
```
```
let carIds = [100, 200, 300];
let[car1,car2] = carIds;
console.log(car1,car2); \\100 200
```
```
let carIds = [100,200,300];
let car1,car2,theRest;
[car1, car2, ...theRest] = carIds;
console.log(car1, car2, theRest);
```
```
let carIds = [100,200,300];
let car1,car2,theRest;
[, car2, ...theRest] = carIds; 
console.log(car1, car2, theRest); \\undefined 200 300
```
Quick way to assign array elements to variables - destructing 

Destructuring Objects
```
let car = {id: 5000, style: 'convertible'};
let {id, style} = car;  \\destructuring for objects. 
console.log(id, style);
//5000 convertible
```
Destucturing arrays [] objects {}
```
let car = {id: 5000, style: 'convertible'};
let id, style;
{id, style} = car; //error! curly brace also used for code blocks. 
console.log(id, style);
```
```
let car = {id: 5000, style: 'convertible'};
let id, style;
({id, style}) = car; 
console.log(id, style);
//5000 convertible
```

Spread Syntax 
Take an array and spread out its elements
```
function startCars(car1, car2, car3) {
   console.log(car1, car2, car3);
}

let carIds = [100,300, 500];
startCars(...carIds); 
\\100 300 500
```
function startCars(car1, car2, car3) {
   console.log(car1, car2, car3);
}
let carIds = [100, 300, 500];
startCars(...carIds);
//100 300 500
```

Taking into an array and breaking it out into car1, car2, car3
Rest parameter collects elements and stores them in an array. 
Spread takes array and spreads it out into various parameters.

```
function startCars(car1, car2, car3) {
   console.log(car1, car2, car3);
}
let carCodes = 'abc';
startCars(...carCodes);
//a b c
```
Both strings and arrays are called iterables in JS.
```
function startCars(car1, car2, car3, ...rest) {
   console.log(rest);
}
let carIds = [1,2,3,4,5,6];
startCars(...carIds);
//[4,5,6]
```
Can use spread and rest at the same time.


typeof()
built in function ins JS
`typeof(1); //number`
`typeof('Hello'; //string`
`typeof(function() {}); //function`
`typeof(true); //boolean`
Valuable for API
`typeof({}); //object`
`typeof(null); //object` c and c++ days null of object
`typeof(undefined) //undefined`
`typeof(NaN); //number //some type of numeric operation went bad.`

Common Type Expressions
// convert to string
foo.toString();

// convert string to integer
Number.parseInt('55'); //55 as a number

// convert string to number
Number.parseFloat('55.99'); //55.99 as a number

`console.log( typeof(Number.parseInt('55'))); //number`

 `console.log( Number.parseInt('55ABC')); //55`
stop parsing at chars
 `console.log( Number.parseFloat('55.88ABC')); //55.55`
 `console.log( Number.parseFloat('ABC55.88ABC')); //NaN`

When doing parseint or parseFloat, needs to start as a number, doesn't need to end in number.

Controlling Loops
Can leave initialization out but do need to leave ; in there. 
```
let i=0;
for (; i<12; i++) {
  if (i===8) {
    break;
  }
}
console.log(i); //8
```
break allows to exit loop. 

```
for (let i=0; i<4; i++) {
  if (i === 2) {
     continue;
  }
  console.log(i);
} 
// 0 1 3
``` 
continue allows to continue the loop.
```
for (let i=0; i<5; i++) {
   console.log(i);
   if (i === 3)
      break;
 }  \\0 1 2 3
```

Summary
Constants
-const

let and var
Rest Parameters
 - ...theRest

Destructuing
 - arrays: [a,b] = arr;
 - objects: ({a,b} = obj); 
 
Spread Syntax 
 - fn(...arr) 

typeof() 

Common Type Conversion
 - toString()
 - Number.parseInt()
 - Number.parseFloat()

Controlling Loops
 - break
 - continue






























