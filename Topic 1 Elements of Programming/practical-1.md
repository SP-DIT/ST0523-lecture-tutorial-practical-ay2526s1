# Practical 1

## 1. Make a message

Given the name, year of birth, and current year, return a message indicating the person's name and age.

```js
function makeMessage(name, yearOfBirth, currentYear) {}

console.log(makeMessage('John', 1994, 2025)); // "John (31)"
```

## 2. Make 3 messages

Given the name and the year of birth of 3 different person, along with the current year, return a message listing the name and age of the 3 person, each separated by a comma.

> Hint: You should reuse your code from the previous question

```js
function makeMessage(name, yearOfBirth, currentYear) {}

function make3Messages(name1, yearOfBirth1, name2, yearOfBirth2, name3, yearOfBirth3, currentYear) {}

console.log(make3Messages('John', 1994, 'Mary', 1999, 'Tom', 1986, 2025)); // "John (31), Mary (26), Tom (39)"
```

## 3. Calculate $a^2 - b^2$

> Hint: $a \times a = a^2$

```js
function aSquareMinusBSquare(a, b) {}

console.log(aSquareMinusBSquare(10, 1)); // 99
```

## 4. Calculate $(a^2 - b^2)^2 - (c^2 - d^2)^2$

> Hint: Reuse `aSquareMinusBSquare`

```js
function aSquareMinusBSquare(a, b) {}

function multipleSquareMinusSquare(a, b, c, d) {}

console.log(multipleSquareMinusSquare(4, 3, 2, 1)); // 40
```

## 5. Multiple wrapper

Implement a function `wrapper(a, b, c, message)` that returns a string which wraps the message in a specific pattern of characters.

`a`, `b`, and `c` are single-character strings used as wrapping characters.

The output string should be constructed as follows:

1. The string starts with three repetitions of character `a`.
2. This is followed by two repetitions of character `b`.
3. Then a single instance of character `c`.
4. Next comes the original `message` string.
5. After the message, repeat character `c` once again.
6. Then repeat character `b` twice.
7. Finally, end the string with three repetitions of character `a`.

Example 1:

```js
wrapper('#', '%', '*', 'message');
```

Output 1:

```js
###%%*message*%%###
```

Example 2:

```js
wrapper('@', 'B', '(', 'message');
```

Output 2:

```
@@@BB(message(BB@@@
```

Code

```js
function wrapper(a, b, c, message) {}

console.log(wrapper('#', '%', '*', 'message')); // "###%%*message*%%###"
```

## 6. Challenge

Same question as 5, but using as little `+` operator in the entire program as possible.

You can use as many variables and functions as you want, and you cannot use anything else not taught in the module so far.

i.e. Apart from creating variables and functions, you can't use things like:

1. for-loop
2. template literals (e.g. `${a}${a}${a}`)
3. String methods (e.g. `'a'.repeat(3)`)
4. Or any other mechanisms not taught in the module.

> Hint: It is possible to achieve this with just 1 `+` operator. You can use new functions and variables to recreate the above behaviors.
