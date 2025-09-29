# 2. Conditions

> "In mathematics we are usually concerned with declarative (what is) descriptions, whereas in computer science we are usually concerned with imperative (how to) descriptions." (SICP, 2022)

Previously, we explored the elements of primitive expressions, means of combination, and means of abstraction through operators, names, and functions.

While they are powerful by itself, if we are to specific the how-to of solving more complex problems, it is still very limited at this point.

Take for example, we cannot declare a function that computes the absolute value of a number by first testing whether the number is a positive or negative number, then taking certain actions accordingly. That is, the absolute number is defined as:

$$
\begin{equation}
       absolute(x) =
        \begin{cases}
            x & \text{if $x \geq 0 $} \\
            -x & \text{otherwise}
        \end{cases}
    \end{equation}
$$

To achieve such a behavior, we will need to introduce a new set of primitives and mechanisms. Let's dive in!

## 2.1 Boolean

In the previous chapter, we focused solely on numbers. In this chapter, we will introduce a new type of primitive known as Boolean, which very simply has only 2 possible value: `true` and `false` (case-sensitive). Example:

```js
true;
```

### 2.1.1 Comparison Operators

Like the equation above, there may be times where we want to compare 2 numbers, to test if perhaps one is greater than the other. Apart from the usual arithmetic operators (`+`, `-`, `*`, `/`, etc...), which produces another number. There is also a set of operators known as Comparison Operators, and these operators produces Booleans.

| operator | name                | purpose                                                                      | example             |
| -------- | ------------------- | ---------------------------------------------------------------------------- | ------------------- |
| `===`    | Strict Equality     | Tests whether the left and right values are identical to one another         | `5 === 3` (`false`) |
| `!==`    | Strict Non-Equality | Tests whether the left and right values are **not** identical to one another | `8 !== 7` (`true`)  |
| `<`      | Less Than           | Tests whether the left value is smaller than the right one.                  | `5 < 12` (`true`)   |
| `>`      | Greater Than        | Tests whether the left value is greater than the right one.                  | `5 > 5` (`false`)   |
| `<=`     | Less Than           | Tests whether the left value is smaller than or equal to the right one.      | `12 <= 12` (`true`) |
| `>=`     | Greater Than        | Tests whether the left value is greater than or equal to the right one.      | `5 >= 13` (`false`) |

## 2.2 Conditional Statements

The Boolean values become especially useful when used with Conditional Statements to control the flow of the program. Take the equation specified at the top, with Comparison Operator, we are now able to test whether a number is greater or equal to (`>=`) 0. Pair this with Conditional Statements, and we can now control the flow of the program.

```js
function absolute(x) {
    if (x >= 0) {
        return x;
    } else {
        return -x;
    }
}
```

More formally, a Conditional Statement can be understood to have the following:

```
if1️⃣ (condition2️⃣) {
    consequent-statements3️⃣;
} else4️⃣ {
    alternative-statements5️⃣;
}
```

1. The conditional statement start with the keyword `if`
2. It contains with the parenthesis the condition, a boolean.
3. If the condition is true, it will then evaluate the consequent-statements
4. The alternative flow is demarcated by the `else` keyword
5. If the condition is false, it will then evaluate the alternative statements

So, if we execute the following function application expression:

```js
absolute(4);
```

When the function is evaluated it goes through the following procedure:

1. Set the parameter `x` to `4`.
2. Test if `x >= 0` returns `true`.
    1. First, we evaluate the left-hand-side of the operator, substituting `x` with the associated value of `4`.
    2. Secondly, we evaluate the right-hand-side, which is just 0.
    3. Then, we apply the operator to the values, which check if the left hand side is greater or equal to the right hand side, giving us: `4 >= 0` → `true`
3. Since the condition evaluates to `true`, we will execute the `consequent-statements`.
    1. Which simply `returns x`, where `x` is `4`.
4. Note that it will skip the `alternative-statements`, regardless whether it was a return statement or not.

## 2.3 Nested Conditional Statements

Suppose you now want to implement a function that compares two value and returns either 1, 0, or -1 depending on whether the first value is greater, equal, or smaller. That is:

$$
\begin{equation}
       compare(x, y) =
        \begin{cases}
            1 & \text{if $x \gt y $} \\
            0 & \text{if $x = y $} \\
            -1 & \text{otherwise}
        \end{cases}
    \end{equation}
$$

Using the above conditional statement we could implement it the following way:

```js
function compare(x, y) {
    if (x > y) {
        return 1;
    } else {
        if (x === y) {
            return 0;
        } else {
            return -1;
        }
    }
}
```

An alternative way is to use the `else if` keyword as in the following:

```js
function compare(x, y) {
    if (x > y) {
        return 1;
    } else if (x === y) {
        return 0;
    } else {
        return -1;
    }
}
```

More formally,

```
if (condition1) {
    consequent-statements1;
} else if1️⃣ (condition2)2️⃣ {
    consequent-statements23️⃣;
} else if (condition3) {
    consequent-statements3;
} else if ...
...
} else {
    final-alternative-statements4️⃣;
}
```

1. The additional conditional statement start with the keyword `else if`.
2. Like the first If-block, It contains with the parenthesis the condition, a boolean.
3. If any of the condition is true, it will then evaluate the corresponding consequent-statements
4. If all conditions evaluates to false, it will then evaluate the final-alternative-statements.

## 2.4 Logical Composition Operators

Apart from comparison operators, there is another set of operators called the Logical Composition Operators which enable us to construct compound boolean expressions. The three most frequently used are:

| operator                       | name | purpose                                                                                        | example                    |
| ------------------------------ | ---- | ---------------------------------------------------------------------------------------------- | -------------------------- |
| $operand_1$ `&&` $operand_2$   | AND  | `true` if both $operand_1$ AND $operand_2$ are `true`. Otherwise, evaluates to `false`         | `true && false` (`false`)  |
| $operand_1$ `\|\|` $operand_2$ | OR   | `true` as long as one of $operand_1$ OR $operand_2$ is `true`. Otherwise, evaluates to `false` | `true \|\| false` (`true`) |
| `!` $operand_1$                | NOT  | Inverts the boolean value. `true` if $operand_1$ is `false`. `false` otherwise.                | `!false` (`true`)          |

As a trivial example, we can revisit the `absolute(x)` function, rewriting the condition with logical composition operators:

```js
function absolute(x) {
    if (x > 0 && x === 0) {
        return x;
    } else {
        return -x;
    }
}
```

## 2.5 Truth Table

The following a some popular outcomes that may come in handy:

| x     | y     | x && y | x \|\| y | !x    |
| ----- | ----- | ------ | -------- | ----- |
| true  | true  | true   | true     | false |
| true  | false | false  | true     | false |
| false | true  | false  | true     | true  |
| false | false | false  | false    | true  |

If we consider `true` as $1$ and `false` as $0$, we can also consider the `&&` operator as multiplication, and the `||` operator as addition.

| x   | y   | x && y           | x \|\| y    |
| --- | --- | ---------------- | ----------- |
| $1$ | $1$ | $1 \times 1 = 1$ | $1 + 1 = 1$ |
| $1$ | $0$ | $1 \times 0 = 0$ | $1 + 0 = 1$ |
| $0$ | $1$ | $0 \times 1 = 0$ | $0 + 1 = 1$ |
| $0$ | $0$ | $0 \times 0 = 0$ | $0 + 0 = 0$ |

## 2.X Summary

We started with the problem where with only functions and variables, we are limited to a linear, sequential manner of executing the program. With the introduction of Boolean, Conditional Statements, and Logical Composition Operators, we now have the tools to take different actions based on different conditions.

In the next topic, we will look at how we can make use of other mechanisms that would allow the repetition of code.
