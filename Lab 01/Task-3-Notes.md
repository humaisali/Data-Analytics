
# Pandas Basics with `Titanic_Dataset.csv`

For this lab, we are going to use the **Pandas** library to read and inspect a CSV dataset.

Before implementation, first understand what each required operation means.

---

# 1. What is Pandas?

**Pandas** is a Python library mainly used for:

- Reading datasets
- Cleaning data
- Analyzing data
- Filtering rows and columns
- Handling missing values
- Working with CSV and Excel files

We usually import Pandas like this:

```python
import pandas as pd
```

Here:

```text
pandas  → actual library
pd      → short name / alias
```

---

# 2. What is a Dataset?

A dataset is simply a collection of data arranged in **rows and columns**.

For example:

```text
PassengerId   Name      Age   Sex
1             Ali       22    male
2             Sara      25    female
3             Ahmed     30    male
```

Here:

- Each **row** represents one record
- Each **column** represents one feature/property

In your case, the dataset is:

```text
Titanic_Dataset.csv
```

A Titanic dataset usually contains information related to passengers, such as age, gender, ticket class, survival status, fare, etc. The exact columns depend on your CSV file.

---

# 3. What is a CSV File?

CSV stands for:

**Comma-Separated Values**

It stores tabular data in a simple text format.

Example:

```text
Name,Age,Gender
Ali,22,Male
Sara,25,Female
```

Pandas can read this file using:

```python
pd.read_csv()
```

---

# 4. Reading the Titanic Dataset

Suppose your file is:

```text
Titanic_Dataset.csv
```

We can load it using:

```python
import pandas as pd

df = pd.read_csv("Titanic_Dataset.csv")
```

Here:

```text
pd.read_csv()
```

means:

> Read data from a CSV file.

And:

```python
df
```

is a variable containing the dataset.

`df` stands for:

> **DataFrame**

---

# 5. What is a DataFrame?

A **DataFrame** is the main data structure used in Pandas.

You can think of it like an Excel table:

```text
       Name       Age      Gender
0      Ali        22       Male
1      Sara       25       Female
2      Ahmed      30       Male
```

So after:

```python
df = pd.read_csv("Titanic_Dataset.csv")
```

the entire Titanic dataset is stored inside `df`.

---

# Task 1: Display 5 Random Rows

Your task says:

> Display random data, 5 rows.

For this, Pandas provides:

```python
.sample()
```

Example:

```python
df.sample(5)
```

This means:

> Randomly select 5 rows from the dataset.

For example, your output might look like:

```text
     PassengerId   Age    Sex
320  321           26     male
45   46            31     female
780  781           24     male
112  113           22     female
650  651           35     male
```

The important thing is:

### Every time you run:

```python
df.sample(5)
```

you may get **different rows**.

Because the rows are selected randomly.

---

# `.sample(5)` vs `.head(5)`

Do not confuse these two.

### `.sample(5)`

```python
df.sample(5)
```

Returns:

> Any 5 random rows.

### `.head(5)`

```python
df.head(5)
```

Returns:

> First 5 rows.

Example:

```text
Dataset:

Row 0
Row 1
Row 2
Row 3
Row 4
Row 5
Row 6
...
```

Then:

```python
df.head(5)
```

returns:

```text
Row 0
Row 1
Row 2
Row 3
Row 4
```

while:

```python
df.sample(5)
```

may return:

```text
Row 6
Row 100
Row 25
Row 450
Row 80
```

---

# Task 2: Display Basic Information of Dataset

Pandas provides:

```python
df.info()
```

This gives us basic information about the dataset.

Example:

```python
df.info()
```

Output may look similar to:

```text
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 891 entries, 0 to 890
Data columns (total 12 columns):

 #   Column       Non-Null Count   Dtype
 0   PassengerId  891 non-null     int64
 1   Survived     891 non-null     int64
 2   Pclass       891 non-null     int64
 3   Name         891 non-null     object
 4   Sex          891 non-null     object
 5   Age          714 non-null     float64
 ...
```

Don't worry if this looks complicated. Let's understand it.

---

## What Does `.info()` Tell Us?

It tells us things such as:

- Number of rows
- Number of columns
- Column names
- Number of non-null values
- Data type of each column
- Memory usage

For example:

```text
Age     714 non-null     float64
```

means:

- Column name = `Age`
- 714 values are available
- Data type = floating-point number

If the dataset has 891 rows but Age only contains 714 non-null values, that means some Age values are missing.

---

# Data Types in Pandas

You may see:

```text
int64
float64
object
```

### `int64`

Integer numbers:

```text
1
10
25
100
```

### `float64`

Decimal numbers:

```text
22.5
34.0
10.75
```

### `object`

Usually represents text/string values:

```text
"Ali"
"male"
"female"
```

---

# Task 3: Display Last Five Rows

Pandas provides:

```python
.tail()
```

By default:

```python
df.tail()
```

returns the last **5 rows**.

You can also write:

```python
df.tail(5)
```

Both mean the same thing.

---

## Example

Suppose we have:

```text
Row 0
Row 1
Row 2
...
Row 886
Row 887
Row 888
Row 889
Row 890
```

Then:

```python
df.tail(5)
```

returns:

```text
Row 886
Row 887
Row 888
Row 889
Row 890
```

---

# `.head()` vs `.tail()`

Very important:

| Function         | Meaning       |
| ---------------- | ------------- |
| `df.head()`    | First 5 rows  |
| `df.tail()`    | Last 5 rows   |
| `df.sample(5)` | Random 5 rows |

A simple way to remember:

```text
head → top
tail → bottom
sample → random
```

---

# Task 4: Display Whole Information of Dataset

This statement can mean two slightly different things depending on your teacher.

## Meaning 1: Display Entire Dataset

You can simply write:

```python
print(df)
```

or:

```python
df
```

However, Pandas usually does **not** display every row when a dataset is large.

Instead, it may show:

```text
     Name      Age
0    ...
1    ...
2    ...
..   ...
889  ...
890  ...

[891 rows x 12 columns]
```

The `...` means Pandas has hidden some rows for readability.

---

## If you truly want to display every row

One method is:

```python
print(df.to_string())
```

`to_string()` converts the complete DataFrame into printable text.

So:

```python
print(df.to_string())
```

can display the whole dataset.

For a large Titanic dataset, however, this will produce a **very large output**.

For most lab work, simply:

```python
print(df)
```

is enough unless your teacher specifically asks you to print every single row.

---

# Another Meaning of "Whole Information"

Sometimes teachers use:

> Display whole information of the dataset

to mean:

```python
df.info()
```

But since your lab already separately asks for **basic information**, I would interpret "whole information" as **displaying the dataset itself**.

So in the implementation we can use:

```python
print(df)
```

---

# Task 5: Display Shape of Dataset

This is a very important Pandas concept.

Use:

```python
df.shape
```

It tells us:

```text
(number of rows, number of columns)
```

Suppose the output is:

```text
(891, 12)
```

This means:

```text
891 rows
12 columns
```

---

# Understanding Shape

Suppose this dataset is:

```text
Name     Age    Gender
Ali      22     Male
Sara     25     Female
Ahmed    30     Male
```

There are:

```text
3 rows
3 columns
```

Therefore:

```python
df.shape
```

returns:

```text
(3, 3)
```

Always remember:

```text
shape = (rows, columns)
```

---

# Access Rows and Columns Separately

Suppose:

```python
df.shape
```

returns:

```text
(891, 12)
```

We can access them individually.

### Number of rows

```python
df.shape[0]
```

Result:

```text
891
```

### Number of columns

```python
df.shape[1]
```

Result:

```text
12
```

Why?

Because:

```text
df.shape
   ↓
(891, 12)
  ↑    ↑
 [0]  [1]
```

Therefore:

```python
df.shape[0]
```

means first value = rows.

And:

```python
df.shape[1]
```

means second value = columns.

---

# Important Pandas Functions From Your Lab

| Pandas Function    | Purpose                     |
| ------------------ | --------------------------- |
| `pd.read_csv()`  | Read CSV dataset            |
| `df.sample(5)`   | Display 5 random rows       |
| `df.head()`      | Display first 5 rows        |
| `df.tail()`      | Display last 5 rows         |
| `df.info()`      | Display dataset information |
| `df.shape`       | Display rows and columns    |
| `df.to_string()` | Display entire dataset      |

---

# Mental Model

Suppose your dataset contains:

```text
            Titanic Dataset

Row 0       Passenger A
Row 1       Passenger B
Row 2       Passenger C
...
Row 888     Passenger X
Row 889     Passenger Y
Row 890     Passenger Z
```

Then:

### Random five

```python
df.sample(5)
```

```text
Any 5 passengers
```

### First five

```python
df.head()
```

```text
Rows 0 → 4
```

### Last five

```python
df.tail()
```

```text
Rows 886 → 890
```

### Dataset information

```python
df.info()
```

```text
Columns
Data types
Missing values
Memory usage
etc.
```

### Shape

```python
df.shape
```

```text
(rows, columns)
```

---

# One More Important Concept: Function vs Property

You'll notice something interesting.

Some Pandas operations use parentheses:

```python
df.sample(5)
df.tail()
df.info()
```

These are **functions/methods**.

But:

```python
df.shape
```

doesn't use parentheses.

That is because `shape` is a **property/attribute**.

So:

```python
df.shape
```

Correct.

Not:

```python
df.shape()
```

Incorrect.

---

# Lab Requirements in Simple Words

Your assignment basically asks you to:

1. **Load Titanic CSV**

```python
pd.read_csv()
```

2. **Show 5 random records**

```python
df.sample(5)
```

3. **Show information about columns and data types**

```python
df.info()
```

4. **Show last 5 records**

```python
df.tail()
```

5. **Show dataset itself**

```python
print(df)
```

6. **Find number of rows and columns**

```python
df.shape
```

---

## Most Important Things for Viva

**Pandas** is a Python library used for data manipulation and analysis.

A **DataFrame** is a two-dimensional table containing rows and columns.

`pd.read_csv()` reads a CSV file into a DataFrame.

`df.sample(5)` returns five random rows.

`df.head()` returns the first five rows.

`df.tail()` returns the last five rows.

`df.info()` gives basic dataset information including columns, non-null values, data types, and memory usage.

`df.shape` returns:

```text
(rows, columns)
```

For example:

```text
(891, 12)
```

means **891 rows and 12 columns**.
