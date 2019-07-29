# Operators
Equality Operators
Unary Operators
Logical Operators
Relational Operators
Conditional Operator
Assignment Operator
Operator Precedence 

Equality Operators
`if (var1 == var2) {}`
This will do type conversion. 
`if (var1 === var2) {}` 
Strict equality operator. Best practice is to use ===.
`if (var1 != var2) {}`
tries to convert types to the same
`if(var1 !== var2) {}` 
types must be the same. 
`console.log(1==true`) \\true`
`console.log(1===true) \\false`
`console.log(if == "123"); \\true`
`console.log(if === "123"); \\false`
`console.log(if != "123"); \\false`
`console.log(if !== "123"); \\true`

Unary Operators
Operate on a single variable
`++var1` var1 incremented before used in expression 
`var1++`
`--var1`
`var1--`
`+var` can convert string into a numeric type
`-var` changes sign of numeric variable. 

```
let year = 1967;
console.log(++year);
\\1968
```
```
let year = 1967;
console.log(year++);
\\1967
console.log(year);
\\1968
```
Operator becomes before or after variable. 
```
let year = "1967";
console.log(typeof(+year)); \\number
``` 
+ symbol does not make it positive. 
Negate a variable is -
```
let year = "-1967";
console.log(-year); 
\\1967
```

Logical (Boolean) Operators
`if (var1 > 5 && var2 < 100) {} ` <br/>
`if (var1 > 5 || var2 < 100) {} ` <br/>
`if (var1 > 5 || var2 < 100 && var3 === 5) {} `
AND symbol has higher precedence 
var2 < 100 && var3 === 5 evaluate first before or symbol.
If you intended OR operator to kick in first: 
`if ((var1 > 5 || var2 < 100) && var3 === 5) {} `
!var1 convert var1 into boolean value and flip it. 
```
if (5 === 5 && 6 === 7) {
  console.log(true);
}
else {
  console.log(false);
}  
```
```
if (5 === 3 && 6 === 3) {
  console.log(true);
}
else {
  console.log(false);
}  
\\false 
```
```
let userSettings = null;
let defaultSettings = {name: 'Default'}; 
console.log( userSettings || defaultSettings);
\\ {name: "Default"}
```
```
let userSettings = {name: 'Joe'};
let defaultSettings = {name: 'Default'}; 
console.log( userSettings || defaultSettings);
\\ {name: "Joe"}
```
```
let userSettings = {name: 'Joe'};
let defaultSettings = {name: 'Default'}; 
console.log( userSettings && defaultSettings);
\\ {name: "Default"}
```
```
let car = null; \\on its own, it is false
console.log(!car);
\\true
```

Relational Operators
// >  <  >=   <= 
uppercase letters are considered less than lowercase characters
`"Zoo" < "alphabet" \\true `
Compared by ASCII value.
```
let s1 = 'Zoo';
let s2 = 'alphabet';
if (s1 < s2) {
  console.log(true);
} 
else {
  console.log(false);
}
\\true
```
```
let s1 = 'Zoo';
let s2 = 'alphabet';
if (s1.toUpperCase() < s2.toUpperCase()) {
  console.log(true);
} 
else {
  console.log(false);
}
\\false - alphabet comes before zoo when both uppercase 
```

Conditional Operator
`var result = (foo > 5) ? true : false; `
() are optional here. 
`console.log( (5>4) ? 'yes' : 'no' );  \\yes`
Spacing is optional as well.

Assignment Operators
`var1 += 10` 
`var1 -= 10;
`var1 /= 10`
`var1 *= 10`
`var1 %= 10`
modulus operator
var << 1 shift left operator shift bits to left by one bit, not bery common.
var >> 1 shift to right. 
var2 >>>= 1; keeps sign 
```
let year = 1964;
year += 10;
console.log( year );
\\ 1974
```
```
let year = 1964;
year -= 10;
console.log( year );
\\ 1954
```
```
let year = 1964;
year >>= 1;  \\shift right one bit. 
console.log( year );
\\982 - this is equivalent to dividing it by 2. 
```
```
let year = 1964;
year <<= 1;  \\shift left by one bit. 
console.log( year );
\\same as multiplying by 2 - 3928 
```
Exclusive OR operators - check out Mozzila

Operator Precedence
Order in which operators get executed. 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table

Summary
Equality
== === != !==

Unary
- ++ -- + -(flips sign on number)

Logical 
&& || !

Relational 
- Capital letters before lowercase letters

Conditional
- (condition) ? true=value : false-value

Assignment 
+= -= *= /= %= 
shift bits with <<= >>= 

Operator Precedence 










