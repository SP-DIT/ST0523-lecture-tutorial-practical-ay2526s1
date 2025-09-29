# 1. The elements of Programming

## 1.1 What is a program?

> Script --> Computer --> Action

One way to understand a program, is the conversion of a script, written in a programming language, by a computer to perform some action. In modern computer, what the computer does is to use an existing software (either a compiler or an interpreter), to process the script, break it down into individual steps, and executes them.

The script that is to be processed by the computer, hence have to contain instructions, written in a specific ways in which the computer can understand, and sequenced in a manner than bring the computer to achieve the desirable outcome.

The following is an example of a script written using a specific language, with instructions sequences a specific manner, to have the computer compute the average score of a course:

```js
function calculateAverage(scores) {
    if (scores.length === 0) return 0;

    let sum = 0;
    for (let i = 0; i < scores.length; i++) {
        sum = sum + scores[i];
    }

    return sum / scores.length;
}

const average = calculateAverage([78, 82, 61, 94, 66, 54, 83]);
console.log(average);
```

> "A powerful programming language is more than just a means for instructing a computer to perform tasks. The language also serves as a framework within which we organize our ideas about processes." (SICP, 2022)

Thus, in any programming language, it would provide us with means to combine simple ideas to build more complex ideas. That is, every programming language would provide:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

We will seek to build up the understanding of each of the 3 mechanism to one day return to the script above to understand how they all piece together.

## 1.2 Expressions

### 1.2.1 Expression Statement

A script (like the one above), is made up of several statements, and one type of statement is called a **expression statement**.

The following is one such expression statement:

```js
123;
```

Where the statement is composed of an `expression` and a semi-colon (which indicates the end of the statement). In this case, the number `123` is an example of a `primitive expression`, defined by the language to be a number in base 10.

### 1.2.2 Operator Combination

We can combine a few of these primitive expressions (e.g. `123`), together with other primitive expressions through the use of `operators`. Also known as `operator combination`. The value of an `operator combination` is obtained by applying the function specified by the operator to the arguments that are the values of the operands. for e.g.:

```js
123 + 234;
```

The above combines 2 `primitive expressions` (`123`, and `234`) and the value of this operator combination is the sum (`+`) of `123` and `234`, giving us `369`

More examples:

```js
99 - 12;
```

Value: 87

```js
2 * 9;
```

Value: 18

```js
22 / 11;
```

Value: 2

### 1.2.3 Syntax Error

In the above example, one of the rule is that the `operator` has to be in the middle of two `expressions`, for example, the following would not be valid:

```js
2 + * 3;
```

As the operator `+` would expect the left-hand-side and the right-hand to be `expressions` rather than another operator. When the program executes this expression, it would then produce the following error:

```
> 2 + * 3
2 + * 3
    ^

Uncaught SyntaxError: Unexpected token '*'
```

The above state that there is an `SyntaxError`, indicating that you have violated a rule of the language (a.k.a the syntax), where the `+` operator did not expect to see `*` on it's right-hand-side.

### 1.2.4 Nested operator combination

As briefly mentioned, each operator expects `expressions` on its left and right. We've seen the use of `primitive expressions`. It can also be _nested_, that the left and right hand side can also be other `operator combination`

```js
(1 + 2) * (3 + 4);
```

Parentheses (round brackets) here serves to avoid confusion of which operator combination to be evaluated first. But JavaScript also allow the omission of round brackets. It follows 2 rules to determine the order of which the various operator combinations are evaluated.

1. Order of precedence
2. left or right-associative

Take the following expression as an example:

```js
1 - (5 / 2) * 4 + 3;
```

By following the rules of order-of-precedence, and left or right-associative, the program would evaluate the expression in the following order:

```js
1 - (5 / 2) * 4 + 3;
```

1. Operators `/` and `*` have a higher weight than `+` and `-`, hence they would be the first to be evaluated.
2. Between `/` and `*`, since these operators are `left-associative`, they are hence evaluated from left-to-right

Let's see an example of a right-associative operator:

```js
2 ** (3 ** 2);
```

`**` here is the power operator (i.e. `2 ** 3 = 2 * 2 * 2 = 8`, and `3 ** 2 = 3 * 3 = 9`)

if `**` was left-associative, then the order of evaluation would be:

```js
(2 ** 3) ** 2;
```

Evaluated as `8 ** 2 = 64`

if it was right-associative instead:

```js
2 ** (3 ** 2);
```

It would be evaluated as `2 ** 9 = 512`.

If you test out the evaluation of `2 ** 3 ** 2` you would notice that it results in `512`, suggesting that the operator `**` is right-associative.

### 1.2.X Summary

We started with the claim at the start that every programming language would provide:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

We have seen numbers as an example of primitive expression, and operators as a means of combination. In the next section, we will see how abstraction is achieved with means of providing names.

## 1.3 Naming

### 1.3.1 Constant Declaration

An important aspect of programming is the ability to name the result of a computation and to refer to it again by its name later. One such mechanism is the use of `variables`. Specifically, we will first limit ourselves to the means of a `constant` variable (one that doesn't change).

In JavaScript, we name a constant with a `constant declaration`

```js
const age = 17;
```

The const keyword above would indicate to the program to associate the value `17` with the name `age`. Once it has been associated, we can refer to the value by name.

```js
2025 - age;
```

The above would evaluate to `2025 - 17 = 2008`.

### 1.2.2 Reference Error

Note the sequence of events:

1. Naming a value
2. Referencing the value by name

If you try to reference value by name before it was associated with the name, you would encounter an error:

```js
2025 - age;
const age = 17;
```

```
> 2025 - age;
Uncaught ReferenceError: age is not defined
```

The above error `ReferenceError` indicate that there was an error when trying to reference a value by name. In this case `age is not defined` suggests that the name age is not yet defined (a.k.a. created) and associated with any value.

### 1.3.3 More examples

```js
const pi = 3.14159;
const radius = 10;
const surfaceArea = pi * radius * radius;
const radius = 2 * pi * radius;

const height = 4;
const volumeOfCylinder = surfaceArea * height;
```

### 1.3.4 Mutable variable declaration

Constant as the name suggests means that the variable can't be changed or re-assigned.

Another keyword apart from `const` would be `let`

```js
let age = 17;
age = 18;
```

> In practice, it is ideal for developers to be defensive, that is to start with `const`, the strictest level, and "down-grading" to `let` only if you are sure that your variables will be modified.

### 1.3.5 Error with modifying `const` variables

```
> const age = 13
> age = 14
Uncaught TypeError: Assignment to constant variable.
```

`TypeError` as the name suggests is thrown when an operation could not be performed, typically (but not exclusively) when a value is not of the expected type. In this case, a the assignment operator (`=`) cannot be performed on an constant variable.

## 1.3.X Summary

We started with the claim at the start that every programming language would provide:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

In 1.2, we saw how numbers as a primitive expression can be combined with operators. Then in 1.3, we saw how we can obtain a simple form of abstraction through constant declarations.

These basic mechanism, illustrates how we can combine simple ideas to build more complex ideas, like the example in 1.3.3, starting with simple ideas of `pi` and `radius`, we can combine them into `surfaceArea`. We then use the given name to form a more complex idea in the form of `volumeOfCylinder`.

> "In general, computational objects may have very complex structures, and it would be extremely inconvenient to have to remember and repeat their details each time we want to use them. Indeed, complex programs are constructed by building, step by step, computational objects of increasing complexity. (SICP, 2022)"

This suggest that writing a complex program requires first construction of basic building blocks, incrementally combining them together to eventually form the more complex parts.

One aspect that we will revisit later is that of `memory`. The possibility of associating value with a name and retrieving it later suggests that the program needs to keep track of the name-value pairs. This `memory` is called the environment which we will revisit at a later chapter.

## 1.4 Function as Abstraction

In every program, we deal with two kinds of elements: Data (as in values) and Functions (as in description of the rules for manipulating data). Take the `+` operator as an example, it is a `function` which describes the summation of the left and right-hand side (the data).

Just as how we can associate a value with a name and use it in combination with other values to create more complex values (e.g. radius --> area --> volume), we too can combine various operations and give it a name to create more complex operations from simpler operations.

### 1.4.1 Function Declaration

```js
function square(x) {
    return x * x;
}
```

The above example is an illustration of taking the `*` (multiply) operator and creating a `compound function` which has been given the name `square`. This function represents the operation of multiplying the number by itself. The thing to be multiplied is given a local name `x`.

This is called a `Function Declaration`. Evaluating this declaration **creates** this compound function and associates it with the name `square`. The structure of a function declaration is as follows:

```js
function1️⃣ name2️⃣ (parameter1, parameter2, ...)3️⃣ {
    ...
    statements4️⃣;
    ...

    return expression5️⃣;
}
```

1. The function declaration starts with the keyword `function`.
2. It is given a name to be referenced by.
3. It contains within the round bracket, parameters, separated by comma.
4. Followed by the body which is a series of other statements
5. The program will process each of the statements sequentially until:
    1. All statements are processed.
    2. A return statement is encountered.

### 1.4.2 Function Application Expression

Having declared the compound function `square`, we can now use it in a `function application expression`, which we turn it into a statement like:

```js
square(3);
```

Value: 9

The value that substitutes the function application expression is dependent on the returned value in the function declaration.

`Function application expression` are the second kind of mechanism for the combination of expression, the general form of a `function application` is:

$function-expression(argument-expressions)$

Where `function-expression` is the name of the function to be applied, followed by the `argument-expressions`, a series of comma-separated list of expressions. The number of expressions within the `argument-expressions` is dependent on the number of parameters expected in the function declaration. (See 3️⃣ in above example).

Like the nesting of operator combination described in 1.2.4, the program follows the following procedure to evaluate the expression part by part:

1. Evaluate the function-expression to obtain the function associated to the name.
2. Evaluate the expressions in the parenthesis from left-to-right.
3. Apply the function to the values of the argument-expressions.

Using the following as an example:

```js
const a = 3;
const b = 6;
square(a + b);
```

1. First we evaluate the function-expression, it retrieves the function associated with the name `square`.
2. Once the program confirms that `square` is a function, it will evaluate the only argument-expression `a + b`:
    1. `a + b`: first, it evaluates the left-hand-side of the operator, replacing `a` with its associated value of `3`
    2. `3 + b`: then, it evaluates the right-hand-side, replacing `b` with its associated value of `6`
    3. `3 + 6`: then, it applies the `+` operator's function on the 2 operand, producing a value of `9`.
3. Finally, we apply the function to the value of the argument expression (i.e. square of 9) producing the outcome of `81`

As each argument-expression is an expression, it can be another function-application-expression. E.g.:

```js
square(square(3));
```

$(3^2)^2 = 9^2 = 81$

### 1.4.3 Error

If you try to apply a function that does not exists, such as the example below, in the first step where the program tries to evaluate the function-expression, where it tries to retrieve the function associated with the name, it will fail and throw a `ReferenceError` (Recall that `ReferenceError` was also thrown when you try to reference an unknown variable):

```
> function foo (x) {
... return x + 1;
... }
> fooooooooo(2)
Uncaught ReferenceError: fooooooooo is not defined
```

Also, if you try to use function-application expressions on variables that are not functions, at the second step of the evaluation, the program will also fail and throw an `TypeError`

```
> const price = 123;
> price(123)
Uncaught TypeError: price is not a function
```

`TypeError` as the name suggests is thrown when an operation could not be performed, typically (but not exclusively) when a value is not of the expected type. In this case, a function-application expression can only be applied to functions and not number.

### 1.4.3 More examples

We can build more complex compound function with the `square` compound function we've created. For example we can create something to compute the following:

$$x^2 + y^2$$

```js
function square(x) {
    return x * x;
}

function sumOfSquares(x, y) {
    return square(x) + square(y);
}
```

and applying it:

```js
sumOfSquares(3, 4);
```

25

### 1.4.X Summary

We started with the claim at the start that every programming language would provide:

1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
2. **means of combination**: A way to combine multiple elements to form bigger elements.
3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.

That is, we started with understand what are primitive expression:

```js
123;
```

Then we found ways to **combine** through means of operator combination

```js
123 + 234;
```

We were then introduced to the mechanism of **names** to provide us with a means of abstractions

```js
const netPrice = 123 + 234;
```

This then allowed us to reference the value by using the name.

```js
const afterServiceCharge = netPrice * 1.1;
const afterGst = afterServiceCharge * 1.09;
```

Values are not the only elements in programming, there are also Functions. We can create abstraction of functions through our own compound-function:

```js
function calculateTotalPrice(netPrice) {
    const afterServiceCharge = netPrice * 1.1;
    const afterGst = afterServiceCharge * 1.09;
    return afterGst;
}
```

In which, we may **apply** it by means of `function-application` expressions

```js
const apple = 0.5;
const pear = 0.7;
calculateTotalPrice(apple * 3 + pear * 5);
```

We will wrap up this chapter, which focuses on primitive, combination, and abstraction by considering a more concrete illustration of how expressions are evaluated procedurally by an interpreter.

## 1.5 Substitution Model of evaluation

This section aims to provide a more concrete model to help us think about how an interpreter functions. Note that it provides merely a mental model and not necessarily how it _really_ works.

When an expression is evaluated, you can imagine that parts are gradually being _substituted_, hence the name of the model: The Substitution Model.

### 1.5.1 Evaluating Operator Combination

Take this expression as an example:

```js
(2 + 4 * 6) * (3 + 12);
```

Visually you should recognize that the bracket on the left and right hand side has to be substituted with their corresponding value before performing the final multiplication.

That is:

```js
(2 + 4 * 6) * (3 + 12);
> 26 * 15
```

But how did $26$ and $15$ came about?

$15$ is straight-forward, you sum $3$ and $12$ together producing $15$.

How about 26? It is again a process of substitution:

1. $2 + 4 * 6$: we first substitute the produced value of $4 * 6 = 24$
2. $2 + 24$: we then substitute this with the summed value of $26

Visualizing it as a tree:

```
                26
                |
        -------------------
        |       |         |
        26      *        15
        |                 |
    ---------          -------
    |   |   |          |  |  |
    2   +   24         3  +  12
            |
         -------
         |  |  |
         4  *  6
```

### 1.5.2 For Variables and Function Application

This way of substitution is similar with variables and function-application expressions

Take the following code as example:

```js
function areaOfCircle(radius) {
    return 3.1415 * radius * radius;
}

const diameter = 6;
const height = 5;
areaOfCircle(diameter / 2) * height;
```

In evaluating the last line `areaOfCircle(radius) * height`, which calculates the volume of a cylinder, it follows a series of substitution:

1. First, as functions-application expressions are the lowest in the order-of-precedence, we will first want to process the `*` (multiply) operator.
2. We will need to substitute the Left and right hand side with their corresponding values.
    1. Starting with the left: $areaOfCircle(diameter / 2)$ is a function-application expression, hence following the steps in 1.3.1:
        1. Evaluate $areaOfCircle$ and substitute it with the function the name is associated with.
        2. Evaluate the $argument-expressions$ one-by-one, in our case, we only have 1 such expression: $diameter / 2$
            1. $diameter / 2$ is a operator combination expression, so we will again evaluate the left and right hand side.
                1. Starting with the left: $diameter$ is a variable name, hence we will substitute it with the value associated with this name ($6$)
                2. Then the right: $2$ is just a primitive-expression, so no further substitution needed.
            2. We then evaluate the expression and substitute it with the produced value: $6 / 2 = 3$
        3. We then apply the function to the argument-expressions: $areaOfCircle(3) = 3.1415 * 3 * 3 = 28.2735$
            1. Note that $3.1415 * 3 * 3$ goes through its own series of substitution which we will omit and leave it as your own practice.
        4. So the left-hand-side is being substituted with $28.2735$
    2. Now the right: $height$ is a variable name, hence we will substitute it with the value associated with this name ($5$)
3. With the left and right evaluated, we then evaluate the expression and further substitute3 it with the produced valued: $28.2735 * 5 = 141.3675$

## 1.6 Summary

In this chapter, we have covered the following key ideas:

1. That every programming language would provide:
    1. **primitive expression**: The smallest unit in which the language defines and is concerned with.
    2. **means of combination**: A way to combine multiple elements to form bigger elements.
    3. **means of abstraction**: A way to which these combined elements may be named and manipulated as a single unit.
2. That every program handles 2 elements:
    1. Data - The values
    2. Function - The description of the rules for manipulating data
3. The Substitution Model of evaluation
    1. That we can think of evaluation as a gradual substitution of expressions with values.
