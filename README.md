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









