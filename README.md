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
isFinite('0'); // true
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
Number.parseInt("14", 8); // 12
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
We can see another example to understand method toLocaleString()
```js
number.toLocaleString('ar-EG'); // → ١٢٣٤٥٦٫٧٨٩
```
It outputs 3500 in Arabic language
### 10. The toPrecision() method in JavaScript is used to format a number by specifying the number of significant digits to display. 
Here's an example of using the toPrecision() method:
```js
(123.456).toPrecision(2); //  "1.2e+2"
(123.456).toPrecision(5); //  "123.46"
```
In this example, the toPrecision() method is called on a number and is passed a number of significant digits to display. The method returns a string representation of the number, formatted with the specified number of significant digits. The string may include scientific notation, depending on the number and the number of significant digits specified.
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

### ***Boolean Methods***

In JavaScript, there are several built-in methods that return a Boolean value (true or false). Some of the most commonly used ones are
### 1. The Array.includes() returns true if an array includes a certain element, and false otherwise.
```js
let fruits = ['apple', 'banana', 'cherry'];

// Check if an array includes a certain element Example 1
fruits.includes('apple');  // true
fruits.includes('pear');   // false


// Check if an array includes an element with a specific index Example 2
fruits.includes('banana', 1);   // true
fruits.includes('banana', 2);   // false
```
In the example, we create an array of fruits and use the includes() method to check if the array includes the elements 'apple' and 'pear'. In the second example, we also use the includes() method but with a second argument that specifies the index at which to start the search.

### 2. The includes() method in JavaScript is used to check if a given string contains a specified substring or not. 
It returns a boolean value (true if the substring is present, false otherwise). Here are some examples to demonstrate its usage:
```js
let str = "Hello, World!";

// Check if the string contains the substring "Hello"
console.log(str.includes("Hello")); // true

// Check if the string contains the substring "Goodbye"
console.log(str.includes("Goodbye")); // false

// Check if the string contains the substring "World" starting from index 7
console.log(str.includes("World", 7)); // true

// Check if the string contains the substring "world" (case sensitive)
console.log(str.includes("world")); // false
```
You can also use the includes() method with arrays to check if an array contains a specified element. For example:
```js
let arr = [1, 2, 3, 4, 5];

// Check if the array contains the element 3
console.log(arr.includes(3)); // true

// Check if the array contains the element 6
console.log(arr.includes(6)); // false
```

### ***String Methods***
### 1. The charAt() method in JavaScript is used to get the character at a specified index in a string. 
Here's an example to demonstrate its usage:
```js
let str = "Hello World!";

str.charAt(0); // H
```
The square bracket notation and this Method is equivalent
```js
str[0]; // H
```
### 2. The charCodeAt() method in JavaScript is used to get the Unicode code of the character at a specified index in a string. 
The Unicode code is a numerical representation of a character, and it ranges from 0 to 65535.
```js
let str = "Hello, World!";

// Get the Unicode code of the character at index 0
str.charCodeAt(0); // 72

// Get the Unicode code of the character at index 7
str.charCodeAt(7); // 87

// Get the Unicode code of the character at index 100 (beyond the length of the string)
str.charCodeAt(100); // NaN
```
### 3. The concat() method in JavaScript is used to concatenate two or more strings together into a single string. 
Here's an example to demonstrate its usage:
```js
let str1 = "Hello";
let str2 = "Methods";

// Concatenate str1 and str2
let result = str1.concat(" ", str2, "!");
result // "Hello Methods!"
```
We can also concatenate strings using the + operator
```js
let str1 = "Hello";
let str2 = "Methods";

// Concatenate str1 and str2
let result = str1 + " " + str2 + "!";
result; // "Hello Methods!"
```
### 4. The indexOf() method in JavaScript is used to search for a specified substring in a string, and returns the index of the first occurrence of the substring. 
If the substring is not found, indexOf() returns -1. Here's an example to demonstrate its usage:
```js
let str = "Hello World!";

str.indexOf("Hello"); // 0
str.indexOf("world"); // -1
```
### 5. The lastIndexOf() method in JavaScript is used to search for a specified substring in a string, starting from the end of the string, and returns the index of the last occurrence of the substring. 
If the substring is not found, lastIndexOf() returns -1. Here's an example to demonstrate its usage:
```js
let str = "developer";

str.lastIndexOf("e"); // 7
```
### 6. The localeCompare() method in JavaScript is used to compare two strings in the current locale and returns a number indicating their relative order. 
The returned value is:

Less than 0 if the first string comes before the second string in the current locale's sort order.
0 if the two strings are equal in the current locale's sort order.
Greater than 0 if the first string comes after the second string in the current locale's sort order.
Here's an example to demonstrate its usage:
```js
let str1 = "ä";
let str2 = "z";

// Compare the two strings in the current locale
console.log(str1.localeCompare(str2)); // -1

let str3 = "a";
let str4 = "z";

// Compare the two strings in the current locale
console.log(str3.localeCompare(str4)); // -1
```
In the example above, localeCompare(str2) returns -1, indicating that the first string "ä" comes before the second string "z" in the current locale's sort order. Similarly, localeCompare(str4) returns -1, indicating that the first string "a" comes before the second string "z" in the current locale's sort order.
### 7. The length property in JavaScript is used to determine the number of elements in an object. 
This property is commonly used with arrays and strings.

For example, you can use the length property to find the number of elements in an array:
```js
let arr = ["push","pop","shift","unshift"];

arr.length; // 4
```
We can delete last element using length property
```js 
arr.length = arr.length - 1;
arr.length; // 3
arr // ["push","pop","shift"]
```
If we call length in string it will output the count of characters
```js
let name = "John Doe";
name.length; // 8
```
### 8. The match() method in JavaScript is used to search a string for a match against a regular expression and returns the matching result as an array.

Here's an example of using the match() method to search for a pattern in a string:
```js
let str = "Understanding and Using Built In Javascript methods";
let pattern = /[A-Z]/g;
let matches = str.match(pattern);
matches // ['U','U','B','I','J']
```
In this example, the match() method searches the string str for any uppercase letters and returns the matching characters in an array. The /[A-Z]/g regular expression specifies that we want to match uppercase letters, and the g flag indicates that we want to search for multiple occurrences of the pattern in the string.
***If there are no matches, the match() method returns null.***
```js
str.match(/[1-10]/g) // null
```
In JavaScript, flags are used in regular expressions to modify the behavior of the match() method and other regular expression methods.
1) g (global) flag: When the g flag is used, the match() method will return all matches in the string, not just the first one. For example:
```js
let str = "The quick brown fox jumps over the lazy dog.";
let pattern = /the/gi;
let matches = str.match(pattern);
matches; // Output: ["The", "the"]
```
2) i (ignore case) flag: When the i flag is used, the match() method will perform a case-insensitive match. For example:
```js
let str = "The quick brown FOX jumps over the lazy dog.";
let pattern = /fox/i;
let matches = str.match(pattern);
matches; // ["FOX"]
```
3) m (multiline) flag: When the m flag is used, the ^ and $ symbols in the regular expression will match the beginning and end of each line, respectively, in a multiline string. For example:
```js
let str = "The quick\nbrown fox\njumps over\nthe lazy dog.";
let pattern = /^the/gm;
let matches = str.match(pattern);
matches; // Output: ["The", "the"]
```
### 9. The replace() method in JavaScript is used to search and replace a string with another string. 
It can be used to change all occurrences of a specific pattern in a string, or just the first occurrence.

Here's an example of using the replace() method to replace all occurrences of a pattern in a string:
```js
let str = "Understanding and Using Built in functions";
let pattern = /functions/gi;
let newStr = str.replace(pattern, "methods");
newStr; //  "Understanding and Using Built in methods"
```
In this example, the replace() method searches the string str for all occurrences of the pattern the, and replaces them with the string "a". 
The /the/gi regular expression specifies that we want to match the string "the" in a case-insensitive manner, and the g flag indicates that we want to replace all occurrences of the pattern in the string.
### 10. The search() method in JavaScript is used to search for a specified pattern in a string and returns the position of the first occurrence of the pattern.

Here's an example of using the search() method to find the first occurrence of a pattern in a string:
```js
let str = "The quick brown fox jumps over the lazy dog.";
let pattern = /the/i;
let position = str.search(pattern);
console.log(position); // Output: 0
```
In this example, the search() method searches the string str for the first occurrence of the pattern the. The /the/i regular expression specifies that we want to match the string "the" in a case-insensitive manner.

The search() method returns the position of the first occurrence of the pattern in the string. If the pattern is not found, the method returns -1.

It's worth noting that the search() method is similar to the indexOf() method in JavaScript, but the search() method takes a regular expression as its argument, whereas the indexOf() method takes a string.

### 11. The slice() method in JavaScript is used to extract a part of an array or a string and return a new array or a string, respectively. 
Here's an example of using the slice() method with an array:
```js
const fruits = ['apple', 'banana', 'kiwi', 'mango'];

const slicedFruits = fruits.slice(1, 3);
slicedFruits; // ['banana', 'kiwi']
```
In this example, the slice() method is used to extract elements from the fruits array starting from the index 1 (inclusive) and ending at index 3 (exclusive), and return a new array slicedFruits containing the extracted elements ['banana', 'kiwi'].

Here's an example of using the slice() method with a string:
```js
const sentence = "Hello, World!";

const slicedSentence = sentence.slice(7, 12);
slicedSentence; // 'World'
```
In this example, the slice() method is used to extract characters from the sentence string starting from the index 7 (inclusive) and ending at index 12 (exclusive), and return a new string slicedSentence containing the extracted characters 'World'.
### 12. The split() method in JavaScript is used to split a string into an array of substrings based on a specified separator. 
Here's an example of using the split() method:
```js
let sentence = "Hello, World!";
let words = sentence.split(" ");
words; // ['Hello,', 'World!']
```
Here's another example of using the split() method with a different separator:
```js
let birthday = "17-03-2005";
let birtharr = birthday.split("-");
birtharr; // ['17','03','2005']
```
### 13. The substr() method in JavaScript is used to extract a part of a string and return a new string. 
Here's an example of using the substr() method:
```js
const sentence = "Hello, World!";

const subSentence = sentence.substr(7, 5);
subSentence; // 'World'
```
In this example, the substr() method is used to extract a part of the sentence string starting from the index 7 and containing 5 characters. The method returns a new string subSentence containing the extracted characters 'World'.

```js
const message = "Good morning!";

const subMessage = message.substr(5, 8);
subMessage; // 'morning'
```
In this example, the substr() method is used to extract a part of the message string starting from the index 5 and containing 8 characters. The method returns a new string subMessage containing the extracted characters 'morning'.

Javascript also have a ***substring()*** method.There are some differences between the two methods:
1. Starting and ending indices: The substr() method takes two arguments: the starting index and the length of the substring to extract. The substring() method takes two arguments: the starting index and the ending index (exclusive).

2. Negative arguments: If either argument to substr() is negative, it is treated as zero. If either argument to substring() is negative, it is treated as the length of the string plus the argument (i.e. a negative argument counts from the end of the string).

Here's an example to demonstrate the difference:
```js 
const message = "Good morning!";

const substrMessage = message.substr(5, 8);
const substringMessage = message.substring(5, 13);
console.log(substrMessage); // 'morning'
console.log(substringMessage); // 'morning'
```
In this example, both the substr() and substring() methods extract a part of the message string. The substr() method takes two arguments: 5 (the starting index) and 8 (the length of the substring to extract). The method returns the 'morning' substring. The substring() method takes two arguments: 5 (the starting index) and 13 (the ending index). The method also returns the 'morning' substring.
If we change the ending index in the substring() method to a number greater than the length of the string, it will automatically adjust the ending index to the length of the string:
```js 
const substringMessage = message.substring(5, 20);
console.log(substringMessage); // 'morning!'
```
In this example, the substring() method takes two arguments: 5 (the starting index) and 20 (the ending index). Since the string message has a length of only 12, the ending index is automatically adjusted to 12, so the method returns the substring 'morning!'.
### 14. The toLocaleLowerCase() method in JavaScript is used to convert a string to lowercase based on the locale. 
Here are some examples of how to use this method:
```js
let msg = "Javascript Methods";
let lower_msg = msg.toLocaleLowerCase();
lower_msg // "javascript methods"
```
In this example, the toLocaleLowerCase() method is used to convert the message string to lowercase. The resulting string is "javascript methods".
```js
let msg = "HÄLLO WÖRLD";
let lower_msg = msg.toLocaleLowerCase();
lower_msg // "hällo wörld"
```
In this example, the toLocaleLowerCase() method is used to convert a string with uppercase characters with diacritical marks. The resulting string is 'hällo wörld'.

It's important to note that the behavior of toLocaleLowerCase() may vary based on the locale and the platform.
### 15. The toLocaleUpperCase() method in JavaScript is used to convert a string to uppercase based on the locale. 
Here are some examples of how to use this method:
```js
const message = "Hello World";
const upperCaseMessage = message.toLocaleUpperCase();
upperCaseMessage; // 'HELLO WORLD'
```
toLocaleUpperCase() method like an toLocaleLowerCase() have vary behavior based on the locale and the platform.
### 16. The toLowerCase() method in JavaScript is used to convert a string to lowercase. 
Here's an example of how to use this method:
```js
const message = "Hello World";
const lowerCaseMessage = message.toLowerCase();
lowerCaseMessage; // 'hello world'
```
In this example, the toLowerCase() method is used to convert the message string to lowercase. The resulting string is 'hello world'.

***Note that message string is not changing. The method toLowerCase() creates new string. Because string is immutable type.***
### 17. The toUpperCase() method in JavaScript is used to convert a string to uppercase. 
Here's an example of how to use this method:
```js
const message = "Hello World";
const upperCaseMessage = message.toUpperCase();
upperCaseMessage; // 'HELLO WORLD'
```
In this example, the toUpperCase() method is used to convert the message string to uppercase. The resulting string is 'HELLO WORLD'.

***Note that message string is not changing. The method toUpperCase() creates new string. Because string is immutable type.***
### 18. The toString() method in JavaScript is used to convert a value to a string. 
Here are some examples of using the toString() method:
```js
(123).toString(); // '123'
(true).toString(); // 'true'
```
In addition to its basic use for converting values to strings, the toString() method also has some additional capabilities. For example, when used with numbers, it can be used to convert a number to a binary, octal, or hexadecimal string representation:
```js
(10).toString(2); // '1010'
(10).toString(8); // '12'
(10).toString(16).toUpperCase(); // 'A'
```
In these examples, the toString() method is passed a radix (the base of the number system), and the resulting string representation is in binary, octal, or hexadecimal, respectively.
### 19. The endsWith() method in JavaScript checks if a string ends with the specified characters. 
Here's an syntax of endsWith()
```js
endsWith(searchString)
endsWith(searchString, endPosition)
```
Here's an example of how you can use it:
```js
let str = "Hello, World!";
let endsWithWorld = str.endsWith("World!");

endsWithWorld; // true
```
In this example, the endsWith() method is used to check if the string str ends with the characters "World!". The result of this method will be a Boolean value that indicates whether the string ends with the specified characters or not. In this case, endsWithWorld will be true, since str does end with "World!".

You can also specify the starting index for the search using the second parameter of the endsWith() method:
```js
let str = "Hello, World!";
let endsWithHello = str.endsWith("Hello", 5);

endsWithHello; // false
```
In this example, the endsWith() method is used to check if the string str ends with the characters "Hello" starting from the index 5. The result of this method will be false, since the characters "Hello" do not appear at the end of the string when starting the search from the index 5.
### 20. The String.fromCharCode() method in JavaScript allows you to convert a sequence of Unicode code points into a string. 
Here's an example of how you can use it:
```js
let string = String.fromCharCode(74,97,118,97);
string; // "Java"
```
In this example, the String.fromCharCode() method is used to convert the Unicode code points 74, 97, 118 and 97 into a string. The result will be the string "Java".

You can also use the String.fromCharCode() method to convert multiple code points into a string:
```js
let string = String.fromCharCode(74,97,118,97,115,99,114,105,112,116);
string; // "Javascript"
```
In this example, the String.fromCharCode() method is used to convert the sequence of code points into the string "Javascript".

***Note that the String.fromCharCode() method is a static method, meaning that you call it directly on the String object, rather than on an instance of a string.***
### 21. The String.fromCodePoint() method in JavaScript is similar to String.fromCharCode() 
but it can handle a wider range of Unicode code points, including those that are greater than 65,535. 
Here's an example of how you can use it:
```js
let string = String.fromCodePoint(74,97,118,97,115,99,114,105,112,116);
string; // "Javascript"
```
In this example, the String.fromCodePoint() method is used to convert the code points 74,97,118,97,115,99,114,105,112 and 116 into a string. The result will be the string "Javascript".

You can also use the String.fromCodePoint() method to convert code points into a string, even if they are greater than 65,535:
```js
let string = String.fromCodePoint(128512);

string // "😀"
```
In this example, the String.fromCodePoint() method is used to convert the code point 128512 into a string. The result will be the string representation of the Unicode character "😀" (a smiling face with open mouth and tightly-closed eyes).

***Note that the String.fromCodePoint() method is a static method, meaning that you call it directly on the String object, rather than on an instance of a string.***
### 22. The indexOf() method in JavaScript is used to find the first occurrence of a specified value in a string. 
Here's an example of how you can use it:
```js
let str = "Hello, World!";
let indexOfWorld = str.indexOf("World");

indexOfWorld; // 7
```
In this example, the indexOf() method is used to find the first occurrence of the string "World" in the string str. The result of this method will be the index of the first occurrence of the specified value in the string, or -1 if the value is not found. 
In this case, indexOfWorld will be 7, since the first occurrence of "World" in str starts at index 7.

You can also specify the starting index for the search using the second parameter of the indexOf() method:
```js
let str = "Hello, World!";
let indexOfHello = str.indexOf("Hello", 5);
indexOfHello; // -1
```
In this example, the indexOf() method is used to find the first occurrence of the string "Hello" in the string str starting from the index 5. The result of this method will be -1, since the characters "Hello" do not appear in the string str when starting the search from the index 5.
### 23. The lastIndexOf() method in JavaScript is used to find the last occurrence of a specified value in a string. 
Here's an example of how you can use it:

```js
let str = "Hello, World! Hello, World!";
let lastIndexOfHello = str.lastIndexOf("Hello");
lastIndexOfHello; // 13
```
In this example, the lastIndexOf() method is used to find the last occurrence of the string "Hello" in the string str. The result of this method will be the index of the last occurrence of the specified value in the string, or -1 if the value is not found. In this case, lastIndexOfHello will be 13, since the last occurrence of "Hello" in str starts at index 13.

You can also specify the starting index for the search using the second parameter of the lastIndexOf() method:

```js
let str = "Hello, World! Hello, World!";
let lastIndexOfHello = str.lastIndexOf("Hello", 5);
lastIndexOfHello; // 0
```
In this example, the lastIndexOf() method is used to find the last occurrence of the string "Hello" in the string str starting from the index 5. The result of this method will be 0, since the characters "Hello" first appear in the string str starting from the index 0, and when starting the search from the index 5, it finds the first occurrence of the string "Hello".
### 24. The matchAll() method in JavaScript is used to find all occurrences of a specified regular expression in a string. 
This method returns an iterator that provides access to the individual matches of the regular expression in the string. 
Here's an example of how you can use it:

```js
let str = "Hello, World! Hello, World!";
let regex = /l/g;

let matches = str.matchAll(regex);

for (let match of matches) {
    console.log(match[0]); 'l' appears 6 times
}
``` 
In this example, the matchAll() method is used to find all occurrences of the regular expression /Hello/g in the string str. The result of this method will be an iterator that provides access to the individual matches of the regular expression in the string. In this case, the loop will log "l" 6 times, since "l" appears 6 times in the string str.

Note that the matchAll() method is a relatively new addition to the JavaScript language and may not be supported by older browsers. It's also worth noting that this method requires the g (global) flag to be set on the regular expression in order to find all occurrences of the pattern in the string.
### 25. The normalize() method in JavaScript is used to normalize a string representation of a Unicode character sequence, such that it can be compared in a case-insensitive manner. 
This method returns a new string that represents the same character sequence as the original string, but with the characters in a standardized form that is appropriate for comparison. 
Here's an example of how you can use it:

```js
let str = "m\u00e9dical";
let normalized = str.normalize();

console.log(normalized); // "médical"
```

In this example, the normalize() method is used to normalize the string str, which contains the character é (U+00E9) encoded as a combining character sequence. The result of this method will be a new string that represents the same character sequence as the original string, but with the characters in a standardized form. In this case, the value of normalized will be "médical".

You can also specify the normalization form to be used by passing an optional argument to the normalize() method. For example, you can use normalize("NFD") to normalize the string using the Normalization Form Canonical Decomposition (NFD) algorithm, or normalize("NFC") to normalize the string using the Normalization Form Canonical Composition (NFC) algorithm.
### 26. The padEnd() method in JavaScript is used to pad a string with a specified character or set of characters so that the string reaches a specified length. 
Here's an example of how you can use it:

```js
let str = "Hello";
let padded = str.padEnd(10, "!");

console.log(padded); //  "Hello!!!!!!".

```
In this example, the padEnd() method is used to pad the string str with the character ! so that the resulting string reaches a length of 10 characters. The result of this method will be a new string that represents the original string with the specified padding characters added to the end. In this case, the value of padded will be "Hello!!!!!!".

If the original string already exceeds the specified length, then the padEnd() method will not add any padding characters, and the original string will be returned unchanged. If no padding character is specified, then the default padding character is the space character (" ").
### 27. The padStart() method in JavaScript is used to pad a string with a specified character or set of characters so that the string reaches a specified length. 
This method adds the padding characters to the start of the string, rather than the end as in the case of padEnd(). 
Here's an example of how you can use it:

```js
let str = "Hello";
let padded = str.padStart(10, "!");

console.log(padded); // "!!!!!Hello"
```
In this example, the padStart() method is used to pad the string str with the character ! so that the resulting string reaches a length of 10 characters. The result of this method will be a new string that represents the original string with the specified padding characters added to the start. In this case, the value of padded will be "!!!!!Hello".

If the original string already exceeds the specified length, then the padStart() method will not add any padding characters, and the original string will be returned unchanged. If no padding character is specified, then the default padding character is the space character (" ").
### 28. The repeat() method in JavaScript is used to repeat a string a specified number of times to create a new string. 
Here's an example of how you can use it:
```javascript

let str = "Hello";
let repeated = str.repeat(3);

console.log(repeated); // "HelloHelloHello"
```
In this example, the repeat() method is used to repeat the string str three times to create a new string. The result of this method will be a new string that consists of the original string repeated the specified number of times. In this case, the value of repeated will be "HelloHelloHello".

The repeat() method will accept a non-negative integer as an argument, and if the argument is not a positive integer, it will return an empty string. If the argument is zero, the original string will be returned unchanged.
### 29. The trim() method in JavaScript is used to remove whitespace characters from the beginning and end of a string. 
Here's an example of how you can use it:

```javascript

let str = "   Hello World!   ";
let trimmed = str.trim();

console.log(trimmed); "Hello World!"
```
In this example, the trim() method is used to remove any whitespace characters from the beginning and end of the string str. The result of this method will be a new string that has all leading and trailing whitespace characters removed. In this case, the value of trimmed will be "Hello World!".

The trim() method removes all leading and trailing whitespace characters, including spaces, tabs, and line breaks. If you need to remove whitespace characters only from one side of the string, you can use the trimStart() method to remove only leading whitespace characters, or the trimEnd() method to remove only trailing whitespace characters.
### 30. The trimEnd() method in JavaScript is used to remove whitespace characters from the end of a string. 
Here's an example of how you can use it:

```javascript
let str = "   Hello World!   ";
let trimmed = str.trimEnd();

console.log(trimmed); // " Hello World!"
```
In this example, the trimEnd() method is used to remove any whitespace characters from the end of the string str. The result of this method will be a new string that has all trailing whitespace characters removed. In this case, the value of trimmed will be " Hello World!".

The trimEnd() method removes all trailing whitespace characters, including spaces, tabs, and line breaks. If you need to remove whitespace characters only from the start of the string, you can use the trimStart() method. If you need to remove whitespace characters from both the start and end of the string, you can use the trim() method.
### 31. The trimStart() method in JavaScript is used to remove whitespace characters from the beginning of a string. 
Here's an example of how you can use it:

```javascript
let str = "   Hello World!   ";
let trimmed = str.trimStart();

console.log(trimmed); // "Hello World! "
```
In this example, the trimStart() method is used to remove any whitespace characters from the beginning of the string str. The result of this method will be a new string that has all leading whitespace characters removed. In this case, the value of trimmed will be "Hello World! ".

The trimStart() method removes all leading whitespace characters, including spaces, tabs, and line breaks. If you need to remove whitespace characters only from the end of the string, you can use the trimEnd() method. If you need to remove whitespace characters from both the start and end of the string, you can use the trim() method.
