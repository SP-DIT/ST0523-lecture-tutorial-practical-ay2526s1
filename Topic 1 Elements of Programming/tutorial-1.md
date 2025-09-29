# Tutorial 1

In this tutorial, we will experience for ourselves the application of the 3 key elements:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

## 1.1 Strings

In the lesson materials, we have already seen `numbers` as one form of primitive expression, in this tutorial we will introduce another form of primitive expression, the `string` primitive expression.

A string primitive expression, also known as string literals, is written by encapsulating characters within a quotation mark (`'` or `"`).

```js
'hello world';
```

One such `operator combination` possible with `strings` is the `+` operator, which combines two string together into a single string:

```js
'hello' + 'world';
```

'helloworld'

## 1.1.1 Escape character

Within a string literal, most characters can be entered literally. Sometimes, you would want a character to be interpreted differently. For example, if I want to display the following message:

> The movie name is 'Lion King'

The following code would not work correctly:

```js
'The movie name is 'Lion King''
```

It would produce the following error instead:

```js
'The movie name is 'Lion King''
                    ^^^^

Uncaught SyntaxError: Unexpected identifier 'Lion'
```

What happened is that the second `'` right before the word Lion is treated as the closing quotation of the first `'` at the start of the string.

The error `SyntaxError: Unexpected identifier 'Lion'` suggest that the word `Lion` is processed as an separate identifier and not part of the string. The identifier is unexpected because it is not a valid means of combination for combining strings.

So instead, we need a mechanism instead to signal to the program to treat the quotation around Lion King differently.

We would hence use the backslash `\` (Not to be confused with the forward-slash `/` character) to create an escape sequence.

<!-- prettier-ignore -->
```js
'The movie name is \'Lion King\'';
```

The following are other escape sequence useful for building more complex strings, try them out to see the effect for yourself:

| escape sequence | purpose             | example                     |
| --------------- | ------------------- | --------------------------- |
| `\n`            | Break line          | `'first line\nsecond line'` |
| `\t`            | tab                 | `'first\tsecond'`           |
| `\\`            | Display a backslash | `'3\\5'`                    |

Try creating a string to create the following pattern:

```
 ____
/.  .\
| \/ |
\____/
```

## 1.2 Variables and Functions

We have so far seen another example of a primitive express and how they can be combined using the `+` operator. Let's now focus on the means of abstraction through variables and functions.

Like with numbers, we can declare a constant with a constant declaration:

```js
const movie = 'Lion King';
```

The above would associate the value `'Lion King'` with the name `movie`, and we can then reference it in subsequent expressions:

<!-- prettier-ignore -->
```js
const movie = 'Lion King';

'The movie name is \'' + movie + '\'';
```

The above could similarly be abstracted through the use of a function like the following:

<!-- prettier-ignore -->
```js
function createMessage(movie) {
    const message = 'The movie name is \'' + movie + '\'';
    return message;
}

createMessage('Lion King');
```

## 1.3 Try it out!

### 1.3.1 Menu item

Complete the following function to achieve the expected output:

```js
function menuItem(number, message) {}

console.log(menuItem(1, 'apple'));
console.log(menuItem(2, 'orange'));
console.log(menuItem(3, 'pear'));
```

Expected output:

```
1. apple
2. orange
3. pear
```

### 1.3.2 Menu item

Complete the following function to print out the menu items

> Make use of `menuItem` to complete the task

```js
function generateMenu(item1, item2, item3) {}

console.log(generateMenu('apple', 'orange', 'pear'));
console.log(generateMenu('basketball', 'volleyball', 'soccer'));
console.log(generateMenu('FED', 'FOP', 'FOC'));
```

Expected output:

```
1. apple
2. orange
3. pear

1. basketball
2. volleyball
3. soccer

1. FED
2. FOP
3. FOC
```

## 1.4 Operator Overloading: Using the `+` operator on number and strings

So far, we have seen that the `+` can be used for numbers and strings, e.g.:

```js
1 + 2;

'hello' + 'world';
```

What happens when you combine values of different types? e.g.:

```js
1 + 'hello';
```

This is called `overloading`, where an operator or function can be used for different combination of value types. When using operators on different types, do test and check the behavior.

For the `+` operator, the rule is simple:

1. If one side is a string, the other side would also be converted to a string.
2. Otherwise, both side is converted to numbers.

Which explains why the above code would be evaluated to `1hello`.

That is, as the right-hand-side is a string, the left-hand-side is also converted to a string (i.e. `1` is converted to `'1'`). The two strings are then combined together.

### 1.4.1 Try it out

For the following:

1. Guess the outcome first
2. Tests it out
3. Develop your own explanation for the behavior

```js
1 + 'hello' + 2;
```

```js
'hello' + 1 + 2;
```

```js
1 + 2 + 'hello';
```

## 1.X Summary

In this tutorial, we explored the application of the 3 key elements:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

We also introduced `string` another primitive expression for representing a sequence of characters.
