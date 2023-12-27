# Chapter 2: The Basics of Programming

In this section, we'll be going over some basics for programming. While examples are done in Python, these concepts are critical because they're "language-agnostic" - no matter what programming language you're using, you'll find these.

> Follow Along! Open a new file called `chapter2.py`.

We'll be covering the following:

* What "code" is
* Variables
* Operators
* Comments
* Conditionals
* Functions
* Iteration

> Throughout these lessons, we'll use the identifiers `foo`, `bar`, and `baz` as placeholders. They don't mean anything, they're just example names.

> Also note. There is a thing called `print()` that will "print out" whatever you want. We'll talk more about functions at the end of this, but if you want to see the value of a variable, just print it!
> ```py
> a = 1
> print(a)
> # 1
> ```

## What Code Really Is

If you remember nothing else, remember this:

> Programs are nothing more than things that:
> 1. Take data in
> 2. Do something interesting to it
> 3. Spit it back out

Every program boils down to this. Most of the work in programming is in step 2, but don't ignore step 1 - that's where most security vulnerabilities spring from!

Your job, as a programmer, is to create a sequence of precise instructions that tell the computer exactly what to do. We call this set of instructions your _program_. You then run your program on some data, and then use what it spits back out

> This becomes more unbelievable as things get more complicated, but remember: Computers _always do precisely what you ask them to_. Nothing more, nothing less.

## Variables

Variables are names for data in your program. As their name suggests, they can change value while your program runs.

In python, as in most languages, variables are easy to create:

```py
var_name = var_value
# Example: I have 73 apples
num_apples = 73
```
You use the `=` (called the "Assignment Operator") to __assign__ a value to a variable.

Variables always have a **type**, which represents what kind of data that variable holds. Python has a number of types built in; some examples:

* Number (1, 3.4, -5, etc.)
* String (text)
* Boolean (True or False)

```py
# Numbers are, well, numbers. You can't have separators -- no commas!
num1 = 1
num2 = -5
num3 = 1.2345

# Text is a string of characters (hence their name: String). You write them by enclosing them in single or double quotes:
str1 = "Hello!"
str2 = 'hi there!'
# You can have an empty string:
str3 = ''

# Booleans are only True or False:
b1 = True
b2 = False
```

It also has more advanced types; we'll look at these later on:
* Lists (a sequence of values)
* Dictionaries (A variable that allows you to associate a "key" with a "value")
* Tuples (a fixed-length list)
* Objects

> A note on types: Broadly speaking, there are two types of languages: **Statically-Typed** and **Interpreted**.
> 
> Statically typed languages have what's known as a **Compiler** that reads your code and makes sure that what you're doing is possible. For example, if you try to add a number to some text, that doesn't make sense, so the compiler will reject your code. Some examples are C/C++, Java, C#, and Rust. In these languages, you're not allowed to run _any_ code unless _all_ of it makes sense.
>
> On the other hand, **Interpreted** languages read your code, line by line. Any problems that arise will only be seen when you _run_ your code.
>
> Python is an interpreted language, which is good for starting out. But the best performance comes from statically-typed languages. These languages also help you avoid dumb errors like accidentally adding a number to text, or invoking functionality by the wrong name.

## Operators

Operators are fundamental "things" that, well, operate on variables. Sounds complicated, but you've been using them for decades! The addition operator `+` adds two variables (numbers) together; the Equals Operator `==` (That's TWO equal signs! `=` `=`. Remember, a single equal sign is _assignment_; it's how we assign a value to a variable) checks if two things are the same, which `>=` checks greater than, etc. All the friends from second grade math are here.

You mostly won't think of them, but you'll use them a lot.

## Comments

Sometimes your code just makes sense, but sometimes it could use context. For example, this doesn't make sense:

``` py
z = x + y
```
What's `x` or `y`, why are we adding them? This is where **comments** can be immensely helpful. They allow you to provide the necessary context so that, when you come back to this code later, it's easier to understand what's going on:

```py
# The z coordinate is calculated as the sum of the x and y coordinates
z = x + y
```

See? Now we know that this has to do with a coordinate system, and that we're calculating the third dimension.

Comments are critical to being able to come back later and fix your code, so don't be stingy!

## Conditionals

Variables are great and all, but sometimes we need to make choices. Suppose we are calculating the total bill from a subtotal. Tax will always be added, so that's simple enough...

```py
sub_total = 53.14
total = 1.0815 * sub_total
```
...but we only want to add a tip if we're in the United States! How do we do that? Up until now we've run every single line!

Luckily, all programming languages have what are known as **conditionals**. You can use these to make something happen _only_ if a condition is met. In python, we can use the `if` statement:

```py
if condition:
    # Stuff to do if the condition is met
    # The indentation isn't for show! Python requires that 
    # anything that should run if this condition is met be 
    # indented by four spaces.
    foo = bar
```

For example, we could say
```py
sub_total = 53.14
total = 1.0815 * sub_total
if is_united_states:
    total = total * 1.20
```

In this example, we only calculate a tip if the variable `is_united_states` is true. The first two lines will run regardless.

> Did you catch that? Look at this line:
>
> ```py
> total = total * 1.20
> ```
> You're allowed to use a variable's value in calculating its next value! Crazy! You're allowed to do this because what happens is _first_ we calculate the right-hand side (often abbreviated as **RHS**), then we assign to the left hand side.

### What if the condition isn't met?

Sometimes we want to do something if a condition is met, and something _different_ otherwise. For example, if I have turkey I'll make a sandwich; otherwise, I'll eat a bagel:
```py
if i_have_turkey:
    # make a sandwich
    print("Sandwich!")
else:
    # boo, bagel it is
    print("Bagel")
```

In this example, if `i_have_turkey` is `True`, we say "Sandwich!", but we do **not** say "Bagel"; if `i_have_turkey` is `False`, we do **not** say "Sandwich!", but we _do_ say "Bagel". Notice that both will never run; it's either one or the other

And sometimes I want to check multiple conditions! We can use the `elif` to check a secondary (or tertiary, etc.) condition:

```py
if grade >= 90:
    print("A")
elif grade >= 80:
    print("B")
elif grade >= 70:
    print("C")
else:
    print("LOL u suck")
```

Notice that only _one line of code will ever run_: If we have an A, we'll never print "B".

You might be wondering, "Alex, couldn't I just write it like this?"

```py
if grade >= 90:
    print("A")
if grade >= 80:
    print("B")
if grade >= 70:
    print("C")
else:
    print("LOL u suck")
```

But here we have a problem! Can you see it?

> Try to find the issue!
>
> Need a hint? Try setting `grade = 91` and see what happens

The problem is that each condition in this example is checked _independently_; that's not what we want.

## Functions

So you've been writing all your code, and it's going great! Suppose you've written the following:

```py
grade1 = 95
grade2 = 70
grade3 = 45
grade4 = 88

if grade1 >= 90:
    print("A")
elif grade1 >= 80:
    print("B")
elif grade1 >= 70:
    print("C")
else:
    print("LOL u suck")

if grade2 >= 90:
    print("A")
elif grade2 >= 80:
    print("B")
elif grade2 >= 70:
    print("C")
else:
    print("LOL u suck")

if grade3 >= 90:
    print("A")
elif grade3 >= 80:
    print("B")
elif grade3 >= 70:
    print("C")
else:
    print("LOL u suck")

if grade4 >= 90:
    print("A")
elif grade4 >= 80:
    print("B")
elif grade4 >= 70:
    print("C")
else:
    print("LOL u suck")
```

That's fine and all, but do you see all that duplicated code? It's almost identical! It would be awfully nice if we could make it where we only had to write that whole `if-elif-else` chain once.

That's what a _function_ does. A function is a way to name a sequence of steps, with inputs for those steps.

In python, functions are started with the `def` word, followed by the name of your function, followed by `():`

```py
def func():
    # Cool function stuff
```

Functions can take inputs; you name them within the parentheses:

```py
def take_one(input1):
    print(input1)
```

This takes a single input and prints it. In programming, inputs are called **Arguments**; so one would say "this function takes one argument".

You can give multiple inputs; their names are separated with commas:

```py
def take_three(i1, i2, i3):
    print(i1)
    print(i2)
    print(i3)
```

OK great! Run the following file and see what you get:

```py
def letter(grade):
    if grade >= 90:
        print("A")
    elif grade >= 80:
        print("B")
    elif grade >= 70:
        print("C")
    else:
        print("LOL u suck")
```

What happened? Nothing! Functions are basically recipes; by themselves they don't do anything. The interesting things happen when you ask the computer to _follow_ that recipe.

In programming, this is called **Calling a function**. You call a function by writing its name, and then the arguments you'd like to give it enclosed in parentheses:

```py
# Here I define the recipe (function)...
def letter(grade):
    if grade >= 90:
        print("A")
    elif grade >= 80:
        print("B")
    elif grade >= 70:
        print("C")
    else:
        print("LOL u suck")
# ... and here I call it, with 91 as the "grade" input
letter(91)
```

> Hey! That looks like `print(stuff)`! What's going on here?
>
> Good catch. `print` is actually just a function! It's purpose in life is to take a variable as input (its argument), and write it out so you can see it in your terminal.

Programmers make liberal use of functions, because they serve as what's known as _abstraction_. This is the idea that I don't want to have to think about how to do something every time; I'll write the function once, and then trust that it handles all the nitty gritty details.

I can take the 

## Iteration

Programming is all about reducing repetitive stuff. Imagine I want to sum the first 50 numbers:

```py
total = 1 + 2 + 3 + 4 + ...
```

That's boring. Instead we can use iteration! In Python, there are two flavors of iteration: `while` loops and `for` loops.

`while` loops do something until a condition is no longer met. For example, this will add 1 to a variable until the variable gets too big:
```py
counter = 1
while counter < 500:
    counter = counter + 1
print(counter)
# 500
```

> While loops can be dangerous because if you're not careful, you'll end up in what's called an **infinite loop**. For example:
> ```py
> counter = 1
> while counter > 0:
>    counter = counter + 1 # Going the wrong way! counter 
>    # will NEVER be less than 0
> ```
> 
> If you ever get caught in one, you'll notice the terminal will seem to "hang"; if this happens, press `Ctrl + C` to exit

We can rewrite the sum of the first 50 numbers:

```py
total = 0
num = 1
while num <= 50:
    total = total + num
    num = num + 1
print(num)
# 1275
```

`for` loops iterate _through_ something. The syntax:
```py
for var in thing_to_iterate:
    # var is each thing, one at a time
```

Later on when we talk about lists, this will become a lot more useful; for now, let me tell you about the "range" function. It takes in one input: An endpoint, and lets you iterate over the numbers from 0 to that endpoint, **excluding** the endpoint!

```py
total = 0
# Remeber range excludes the endpoint!
for n in range(51):
    total = total + n
print(total)
```

That's a pretty bad explanation of `for` loops, but we'll get more practice with that later.

Each run of a loop is called an **Iteration**; in the above examples, each loop ran 50 times, or for 50 iterations.

## Bonus: Nesting

The cool (and horrible) thing about these things is they can pretty much all be inside each other. For example, take the following program:

``` py
foo = 55
while foo < 100:
    if foo > 65:
        for i in range(100):
            print("stuff!")
    elif foo > 85:
        if foo != 86:
            print("Woah!")
    else:
        for j in range(10):
            print(j)
    foo = foo + 1
```

# Practice

Time to put your skills to the test!

## Problem 1

Write a program that calculates the _product_ of the first 20 numbers. You must use iteration.

## Problem 2

Write a function that takes in the width and height of a rectangle, and prints its area.
