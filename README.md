# Javascript Built-In Methods
Referat about JavaScript Built-In Methods

#### Understanding and Using JavaScript Built-in Methods 
Built-in methods are available for various data types, including arrays, strings, numbers, and objects.
There are also methods for mathematical operations and Date formatting.
One of the biggest advantages of using built-in methods is that they are highly optimized, so they are often faster and more efficient than writing custom code.
In this Referat, we will learn basics and explore the various built-in methods available in JavaScript, including their syntax, usage, and practical examples.

### ***Number Methods***
### 1. The Number.isFinite() method determines the passed number is an finite or not. 
It takes one argument 'any integer' and returns  'true' or 'false'.
Here are some examples. 
```javascript
Number.isFinite(Infinity); // false
Number.isFinite(NaN); // false
Number.isFinite(-Infinity); // false

Number.isFinite(0); // true
Number.isFinite(2e64); // true
```

Javascript also have an isFinite() global function. Difference between Number.isFinite() and isFinite() is type conversion. Number.isFinite() only works with integer numbers not strings. We can see that in following example
```javascript
Number.isFinite('0'); // false because '0' is a string not an number
```
### 2. The Number.isInteger() static method determines whether the passed value is an integer.
It takes one argument 'any value' and returns 'true' or 'false'.
Here are some examples.
```javascript
Number.isInteger(0); // true
Number.isInteger(1); // true
Number.isInteger(-100000); // true
Number.isInteger(99999999999999999999999); // true

Number.isInteger(0.1); // false
Number.isInteger(Math.PI); // false

Number.isInteger(NaN); // false
Number.isInteger(Infinity); // false
Number.isInteger(-Infinity); // false
Number.isInteger("10"); // false
Number.isInteger(true); // false
Number.isInteger(false); // false
Number.isInteger([1]); // false
```

Note that some number literals, while looking like non-integers, actually represent integers — due to the precision limit of ECMAScript floating-point number encoding (IEEE-754). For example.
```js
Number.isInteger(5.0); // true
Number.isInteger(5.000000000000001); // false
Number.isInteger(5.0000000000000001); // true, because of loss of precision
Number.isInteger(4500000000000000.1); // true, because of loss of precision
```
### 3. The Number.isNaN() static method determines whether the passed value is the number value NaN, and returns false if the input is not of the Number type.
Here are some examples.
```js
Number.isNaN(NaN); // true
Number.isNaN(Number.NaN); // true
Number.isNaN(0 / 0); // true
Number.isNaN(37); // false
```
Javascript also have an isNaN() global function.The difference between Number.isNan() and isNaN() is type conversion.The Number.isNaN() only works with integer type values,if argument is an string, the method will always return false. **Number.isNaN() method**
```js
Number.isNaN("NaN"); // false => string
Number.isNaN(undefined); // false => undefined
Number.isNaN({}); // false => object
Number.isNaN("blabla"); // false => string
```
**isNaN() global function**
```js
isNaN("NaN"); // true => NaN == NaN
isNaN(undefined); // true => 
isNaN({}); // true
isNaN("blabla"); // true
```
### 4. **The Number.isSafeInteger() static method determines whether the provided value is a number that is a safe integer.** 
The safe integers consist of all integers from -(253 - 1) to 253 - 1, inclusive (±9,007,199,254,740,991).Here are some examples
```js
Number.isSafeInteger(3); // true
Number.isSafeInteger(2 ** 53); // false
Number.isSafeInteger(2 ** 53 - 1); // true
Number.isSafeInteger(NaN); // false
Number.isSafeInteger(Infinity); // false
Number.isSafeInteger("3"); // false
Number.isSafeInteger(3.1); // false
Number.isSafeInteger(3.0); // true
```
### 5. The Number.parseFloat() static method parses an argument and returns a floating point number. 
If a number cannot be parsed from the argument, it returns NaN.
It takes as an argument string.
```js
Number.parseFloat("123.1"); // 123.1 
Number.parseFloat("123"); // 123 
Number.parseFloat("12.345e6"); // 1234500 
Number.parseFloat("hello world"); // NaN
```
### 6. The Number.parseInt() method in JavaScript is used to convert a string representation of a number to an integer.
Here's the syntax for the Number.parseInt() method:
```js
Number.parseInt(string [, radix])
```
where string is the string representation of the number you want to convert, and radix is an optional argument specifying the base of the number to be converted. The default value of radix is 10.

Here are a few examples to demonstrate how the Number.parseInt() method can be used:
```js
Number.parseInt("123"); // 123
Number.parseInt("1011", 2); // 11
Number.parseInt("12", 8); // 14
Number.parseInt("JavaScript"); // NaN
```
### 7. The toExponential() method returns a string representing the Number object in exponential notation
Here's the syntax for the toExponential() method:
```js
toExponential()
toExponential(fractionDigits)
```
A string representing the given Number object in exponential notation with one digit before the decimal point, rounded to fractionDigits digits after the decimal point.
```js
const numObj = 77.1234;

console.log(numObj.toExponential()); // 7.71234e+1
console.log(numObj.toExponential(4)); // 7.7123e+1
console.log(numObj.toExponential(2)); // 7.71e+1
console.log(77.1234.toExponential()); // 7.71234e+1
console.log((77).toExponential()); // 7.7e+1
```

### 8. The toFixed() method formats a number using fixed-point notation.
Here's the syntax
```js
toFixed()
toFixed(digits)
```
The toFixed() method returns a string representation of numObj that does not use exponential notation and has exactly digits digits after the decimal place. The number is rounded if necessary, and the fractional part is padded with zeros if necessary so that it has the specified length.
```js
const numObj = 12345.6789;

numObj.toFixed(); // '12346'; rounding, no fractional part
numObj.toFixed(1); // '12345.7'; it rounds up
numObj.toFixed(6); // '12345.678900'; additional zeros
(1.23e+20).toFixed(2); // '123000000000000000000.00'
(1.23e-10).toFixed(2); // '0.00'
2.34.toFixed(1); // '2.3'
2.35.toFixed(1); // '2.4'; it rounds up
2.55.toFixed(1); // '2.5'
// it rounds down as it can't be represented exactly by a float and the
// closest representable float is lower
2.449999999999999999.toFixed(1); // '2.5'
// it rounds up as it's less than NUMBER.EPSILON away from 2.45.
// This literal actually encodes the same number value as 2.45

(6.02 * 10 ** 23).toFixed(50); // 6.019999999999999e+23; large numbers still use exponential notation
```
### 9. The toLocaleString() method returns a string with a language-sensitive representation of this number. 
Here's the syntax
```js
toLocaleString()
toLocaleString(locales)
toLocaleString(locales, options)
```
The locales and options parameters customize the behavior of the function and let applications specify the language whose formatting conventions should be used.
```js
const number = 3500;

console.log(number.toLocaleString()); // "3,500" if in U.S. English locale
```
### 10. The toPrecision() method is used to format a number to a specified number of significant figures.
```js
(123.456).toPrecision(2); //  "1.2e+2"
(123.456).toPrecision(5); //  "123.46"
```
### 11. The toString() method in JavaScript is a method that is used to convert a number to a string. 
The general syntax for using the toString() method is:
```js
number.toString([radix]);
```
where number is a number value and radix is an optional parameter that specifies the base to use for representing the number as a string. The radix can be an integer between 2 and 36. If radix is not specified, it defaults to 10.

Here are some examples of using the toString() method in JavaScript:
```js
(123).toString()); // "123"
(123).toString(2); // "1111011"
(123).toString(16); // "7b" 
```
### 12. The valueOf() method in JavaScript is a method that is inherent to all JavaScript objects. 
It returns the primitive value of the object. For most objects, the default implementation of the valueOf() method returns the object itself, which is not very useful. However, for certain built-in objects, such as Number, Boolean, and Date, the valueOf() method returns a primitive value that represents the object.

For example:
```js
let num = 123;
num.valueOf(); // 123

let bool = true;
bool.valueOf(); // true

let date = new Date();
date.valueOf(); // the number of milliseconds since January 1, 1970, 00:00:00 UTC
```

