
# Lab Topic: Python Functions - Positional Arguments, Keyword Arguments, and Lambda Functions

Before implementation, first understand the concepts clearly.

## 1. What is a Function in Python?

A **function** is a block of code that performs a specific task.

Instead of writing the same code again and again, we put that code inside a function and call it whenever needed.

Example:

```python
def greet():
    print("Hello")

greet()
```

Output:

```text
Hello
```

A function can also receive values. These values are called **arguments**.

Example:

```python
def greet(name):
    print("Hello", name)

greet("Humais")
```

Output:

```text
Hello Humais
```

Here:

- `name` is called a **parameter**
- `"Humais"` is called an **argument**

---

# 2. Positional Arguments

A **positional argument** means that the arguments are passed to a function according to their **position or order**.

Consider this function:

```python
def student(name, age):
    print("Name:", name)
    print("Age:", age)
```

Now call it:

```python
student("Humais", 21)
```

Python understands:

```text
First argument  -> name
Second argument -> age
```

So:

```python
name = "Humais"
age = 21
```

Output:

```text
Name: Humais
Age: 21
```

## Order is Important

If we change the order:

```python
student(21, "Humais")
```

Python will assign:

```python
name = 21
age = "Humais"
```

Output:

```text
Name: 21
Age: Humais
```

This happens because Python follows the **position of arguments**.

### Simple Rule

```Python
Function:
student(name, age)

Call:
student("Humais", 21)

            ↓       ↓
           name    age
```

So in positional arguments:

> **Position matters.**

---

# 3. Keyword Arguments

In **keyword arguments**, we explicitly tell Python which value belongs to which parameter.

Example:

```python
def student(name, age):
    print("Name:", name)
    print("Age:", age)
```

We can call it like this:

```python
student(name="Humais", age=21)
```

Output:

```text
Name: Humais
Age: 21
```

The main advantage is that **order does not matter**.

For example:

```python
student(age=21, name="Humais")
```

This will still produce:

```text
Name: Humais
Age: 21
```

Because Python sees the parameter names:

```python
age=21
name="Humais"
```

### Simple Rule

```text
Positional Argument
student("Humais", 21)

Keyword Argument
student(name="Humais", age=21)
```

---

# Positional vs Keyword Arguments

| Feature       | Positional Arguments      | Keyword Arguments                  |
| ------------- | ------------------------- | ---------------------------------- |
| Based on      | Position                  | Parameter name                     |
| Order matters | Yes                       | No                                 |
| Easy to write | Yes                       | Yes                                |
| More readable | Less                      | More                               |
| Example       | `student("Humais", 21)` | `student(name="Humais", age=21)` |

---

# 4. Lambda Function

A **lambda function** is a small anonymous function in Python.

Anonymous means:

> It usually does not have a normal function name.

A normal function is created using:

```python
def
```

A lambda function is created using:

```python
lambda
```

---

## Normal Function Example

Suppose we want to add two numbers.

```python
def add(a, b):
    return a + b
```

Calling it:

```python
result = add(10, 5)

print(result)
```

Output:

```text
15
```

---

# Same Function Using Lambda

We can write the same thing using a lambda:

```python
add = lambda a, b: a + b
```

Then:

```python
result = add(10, 5)

print(result)
```

Output:

```text
15
```

So:

```python
def add(a, b):
    return a + b
```

and

```python
add = lambda a, b: a + b
```

perform the same task.

---

# Lambda Syntax

The basic syntax is:

```python
lambda arguments: expression
```

Example:

```python
lambda x: x * 2
```

Meaning:

```text
lambda
  ↓
Create a small function

x
↓
Argument

x * 2
  ↓
Expression / result
```

We can store it in a variable:

```python
double = lambda x: x * 2
```

Then:

```python
print(double(5))
```

Output:

```text
10
```

---

# Another Example

### Normal Function

```python
def square(x):
    return x * x
```

Usage:

```python
print(square(4))
```

Output:

```text
16
```

### Lambda Function

```python
square = lambda x: x * x

print(square(4))
```

Output:

```text
16
```

---

# Normal Function vs Lambda Function

| Normal Function                 | Lambda Function                      |
| ------------------------------- | ------------------------------------ |
| Uses`def`                     | Uses`lambda`                       |
| Can contain multiple statements | Usually contains one expression      |
| Can have a function name        | Often anonymous                      |
| Suitable for large logic        | Suitable for small logic             |
| Uses explicit`return`         | Automatically returns the expression |
| More readable for complex code  | Shorter for simple code              |

---

# Example Comparison

## Normal Function

```python
def multiply(a, b):
    result = a * b
    return result
```

## Lambda Function

```python
multiply = lambda a, b: a * b
```

Both can be called as:

```python
print(multiply(4, 5))
```

Output:

```text
20
```

---

# Why Lambda Functions Are Useful in Data Analytics

Lambda functions are very common in Data Analytics, especially with **Pandas**.

For example, suppose we have a column of salaries and want to increase every salary by 10%.

Later, you may see something like:

```python
df["Salary"] = df["Salary"].apply(lambda x: x * 1.10)
```

Here:

```python
lambda x: x * 1.10
```

means:

> Take each value `x` and multiply it by `1.10`.

So understanding lambda functions is particularly useful for your **Data Analytics course**.

---

# Complete Mental Model

Think of the three concepts like this:

### Positional Arguments

```python
def person(name, age):
    pass

person("Ali", 22)
```

Python says:

```text
1st value -> name
2nd value -> age
```

### Keyword Arguments

```python
person(age=22, name="Ali")
```

Python says:

```text
name="Ali"
age=22
```

Order doesn't matter.

### Lambda Function

Instead of:

```python
def square(x):
    return x ** 2
```

we can write:

```python
square = lambda x: x ** 2
```

---

## In One Line

- **Positional Argument:** value is assigned according to its **position**.
- **Keyword Argument:** value is assigned according to its **parameter name**.
- **Lambda Function:** a **short one-expression function** written using `lambda`.
