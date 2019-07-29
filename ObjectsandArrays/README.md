# Objects and Arrays
Constructor Functions 
Prototypes 
Expanding Objects using Prototypes
JS Object Notation
Array Iteration

Constructor Functions
Used to instantiate new objects.
```
function Car(id) {
   this.carId = id;
}

let car = new Car(123);
console.log(car.carId);
\\123
```
this in a constructor function will be empty object. 
Method:
```
function Car(id) {
  this.carId = id;
  this.start = function () {
     console.log('start: ' + this.carId);
   };
}

let car = new Car(123);
car.start();
//start: 123
```
The value of this is set to the global window object.
```
function Car() {
   console.log(this);
}
Car(); 
```
Need new keyword on constructor funcction car. 
```
function Car() {
   console.log(this);
}
let vehicle = new Car(); 
```

Prototypes
without prototypes
```
function Car(id) {
  this.carId = id;
  this.start = function () {
     console.log('start: ' + this.carId);
   };
}

let car = new Car(123);
car.start();
//start: 123
```
with prototype
```
function Car(id) {  //constructor function. 
  this.carId = id;
}

Car.prototype.start = function () {  //property prototype 
     console.log('start: ' + this.carId); //still need to work with functions context - this. 
   };

let car = new Car(123);
car.start();
//start: 123
```
Can add our methods directly and use on any object. 

Expanding Objects using Prototypes
Polyfill. 
String.prototype
```
String.prototype.hello = function() {
   return this.toString() + ' Hello';
}

console.log('foo'.hello()); //foo Hello
```
Take functionality to our own objects or built in objects.

JSON - JS Object Notation
```
let car = {
   id: 123,
   style: 'convertible'
};
console.log(JSON.stringify(car));
// {"id":123, "style": "convertible"}
```
Looks much like object literal. Can pass string onto some api. 
Convert Array to JSON
```
let carIds = [
  { carId: 123 },
  { carId: 456 },
  { carId: 789 }
];
console.log( JSON.stringify(carIds));
// [{"carId": 123}, {"carId":456}, {"carId":789}]
```
Parsing JSON
```
let jsonIn = 
`
 [
  {"carId" : 123},
  {"carId" : 456},
  {"carId" : 789}
]
`;
let carIds = JSON.parse(jsonIn);
console.log(JSON.stringify(carIds));
```
Property names need to be in "" for JSON content. 
without json.stringify:
{carId: 123}
{carId: 456}
{carId: 789}
with json.stringify
[{"carId": 123}
{"carId": 456}
{"carId": 789}]

Array Iteration
```
let carIds = [
  {carId: 123, style: 'sedan'},
  {carId: 456, style: 'convertible'},
  {carId: 789, style: 'sedan'}
]
carIds.forEach(car => console.log(car));
carIds.forEach((car,index) => console.log(car,index));
```
forEach method calls a function on each element on each array.
Results from above:
 {carId: 123, style: "sedan"}
  {carId: 456, style: "convertible"}
  {carId: 789, style: "sedan"}
```
let carIds = [
  {carId: 123, style: 'sedan'},
  {carId: 456, style: 'convertible'},
  {carId: 789, style: 'sedan'}
]
let convertibles = carIds.filter(
   car => car.style === 'convertible'
);
console.log(convertibles);
```
Array Testing
```
let carIds = [
  {carId: 123, style: 'sedan'},
  {carId: 456, style: 'convertible'},
  {carId: 789, style: 'sedan'}
]
let result = carIds.every(
   car => car.carId > 0
);
console.log(result);
```
Locate the First Match - find method 
```
let carIds = [
  {carId: 123, style: 'sedan'},
  {carId: 456, style: 'convertible'},
  {carId: 789, style: 'sedan'}
]
let car = carIds.find(
  car => car.carId > 500
);
console.log(car);
``

Summary
Constructor Functions 
  new Car()
  creates new this value
Prototypes
  property of constructor function
Expanding Objects using Prototypes
JS Object Notation - JSON 
Array Iteration
  -forEach, filter, every, find



