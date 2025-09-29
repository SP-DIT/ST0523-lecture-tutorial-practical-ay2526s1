# Tutorial 2

In this tutorial, we will expand further on the following:

1. Boolean and comparison operators
2. Conditional Statements
3. Logical Composition operators

## 2.1 Boolean and comparison operators

In the lecture, a new type of primitive was introduced: Boolean (`true` and `false`).

Along which, comparison operators (`>`, `<`, `>=`, `<=`, `===`, and `!==`) were introduced. These operators compares the two values on the left and right-hand-side and produce a boolean.

For example:

```js
9 < 3;
```

would produce the boolean `false`.

### 2.1.1 `==` vs `===`

In JavaScript, the `==` (equality) and `===` (strict equality) operator both checks for equality by one is "stricter" than the other. It is stricter in the sense that the `===` immediately returns `false` if the type of the values are different, but `==` would first try to convert the two value to the same type before comparing.

Example:

```js
1 == '1';
```

The above would return `true` as the `==` operator would first convert both values to string before comparison. Whereas:

```js
1 === '1';
```

Would return `false`, as the `===` would immediate return `false` given that the two types are different (one is a string, and one is a number).

### 2.1.2 String comparison

While it may be intuitive to compare numbers, comparing Strings might be less intuitive.

```js
'abc' < 'def';
```

would return `true` whereas

```js
'aaa' < 'aa';
```

would return `false`.

What happens is that JavaScript would compare the characters at each position using their UTF-16 code.

Hence when comparing `'abc'` against `'def'`, the program would first compare `'a'` against `'d'`, and `'a'` would have a smaller UTF-16 code than `d`, hence `abc` is considered less than `def`.

Take another example:

```js
'abc' < 'abd';
```

The program would first compare `'a'` against `'a'`, since they are the same, it would then compare `'b'` against `'b'`, and finally, `'c'` against `'d'`. At this point `'c'`'s UTF-16 code is smaller than `'d'` hence `'abc'` is deemed less than `'abd'` and hence evaluates to `true`

## 2.2 Conditional Statements

The boolean values would serve as a key mechanism to help control the flow of a program. In the lecture, an example of computing absolute value was given.

The basic structure of a conditional statement is as follows:

```
if (condition1) {
    consequent-statements1;
} else if (condition2) {
    consequent-statements2;
} else if (condition3) {
    consequent-statements3;
} else if ...
...
} else {
    final-alternative-statements;
}
```

### 2.2.1 Try it out

Implement the following function that compares two value `a` and `b` of the same type, and returns 1 if `a` is greater than `b`, `-1` if `a` is smaller than `b`, and `0` if `a` is equal to `b`;

```js
function compare(a, b) {}

compare(1, 2);
compare(2, 1);
compare(2, 2);
compare('a', 'b');
compare('b', 'a');
compare('x', 'x');
```

the above should return:

```
1
-1
0
1
-1
0
```

### 2.2.2 If-in-a-If: Try-it-out

The `consequent-statements` can indeed be another set of `If-statements`:

```js
if (1 > 0) {
    if (2 < 3) {
        ...
    } else {
        ...
    }
} else {
    ...
}
```

Using the above strategy, implement the following function that compares 3 different values `a`, `b`, and `c` of the same type. That if `a` is the smallest, return `0`, else, if `b` is the smallest, return `1`, otherwise, return `2` indicating that `c` is the smallest.

```js
function compareThreeValues(a, b, c) {}

console.log(compareThreeValues(1, 2, 3));
console.log(compareThreeValues(1, 3, 2));
console.log(compareThreeValues(2, 1, 3));
console.log(compareThreeValues(3, 1, 2));
console.log(compareThreeValues(2, 3, 1));
console.log(compareThreeValues(3, 2, 1));
```

Expected output:

```
0
0
1
1
2
2
```

## 2.3 Logical Composition Operator

Just as how numbers have `+`, `-`, `*`, `/` to combine multiple numbers, boolean too have their own set of operators to combine them together:

| operator                       | name | purpose                                                                                        | example                    |
| ------------------------------ | ---- | ---------------------------------------------------------------------------------------------- | -------------------------- |
| $operand_1$ `&&` $operand_2$   | AND  | `true` if both $operand_1$ AND $operand_2$ are `true`. Otherwise, evaluates to `false`         | `true && false` (`false`)  |
| $operand_1$ `\|\|` $operand_2$ | OR   | `true` as long as one of $operand_1$ OR $operand_2$ is `true`. Otherwise, evaluates to `false` | `true \|\| false` (`true`) |
| `!` $operand_1$                | NOT  | Inverts the boolean value. `true` if $operand_1$ is `false`. `false` otherwise.                | `!false` (`true`)          |

### 2.3.1 Try it out

Implement `compareThreeValue` again, but instead of using if-in-a-if, use logical composition operators instead.

That is, `a` can be considered smallest if the following is true: `a` is lesser than `b` AND `a` is lesser than `c`.
