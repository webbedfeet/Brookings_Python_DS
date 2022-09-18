# Introduction to Data Science using Python
```{r}

```


## Abhijit Dasgupta, PhD

## Plans for this workshop

We're meeting today and tomorrow 1:30 - 3:00 pm

| Day 1                        | Day 2                |
| ---------------------------- | -------------------- |
| Why Python for Data Science? | Data visualization   |
| A Python Primer              | Statistical modeling |
| Pandas for data munging      | Machine learning     |

## Scope

Obviously we are going to cover each topic at a high level, given time constraints. I intend to give you a taste for what is possible

There are much more detailed resources available as Jupyter notebooks.

[https://github.com/districtdatalabs/Brookings_Python_DS](https://github.com/districtdatalabs/Brookings_Python_DS)


| Topic                                          | Notebook           |
| ---------------------------------------------- | ------------------ |
| Python primer                                  | 00_python_primer   |
| Numpy and the data science stack (not covered) | 01_python_tools_ds |
| Pandas for data munging                        | 02_python_pandas   |
| Data visualization                             | 03_python_vis      |
| Statistical modeling                           | 04_python_stat     |
| Machine learning                               | 05_python_learning |



## Running notebooks on Binder

Binder is a free service that allows Python resources to be run on the web from Github repositories. 

[Binder demo](https://github.com/districtdatalabs/Brookings_Python_DS)

# Why Python for Data Science?

# Who is a data scientist?

## One definition


<img align="center" src="graphs/Data_Science_VD.png"/>

<aside class="notes">
1. It's the confluence of statistics, computer science, domain knowledge
2. You need all three to make this work
3. We'll be talking more about stat/CS than domain expertise here

</aside>

## Unclear definition

+ Statistician
+ Computer scientist
+ Database engineer
+ Software engineer
+ Data engineer
+ Mathematician

Some of the best ones I know are <br/>
neurobiologists and physicists

## A broad umbrella

Anyone who wants to work with data to solve problems within particular domains

# Data Science

## What it involves

![DSPipeline](graphs/DSPipeline.png)

## What it involves

![data-science-explore](graphs/data-science-explore.png)

## What it involves

1. Managing and cleaning data
1. Interest in exploring relationships between things, informed by domain knowledge

1. Statistical know-how
1. Computational skills

1. Tools

## We're here for the tools

The main two tools are

1. Python (https://www.python.org)
1. R (https://www.r-project.org)

There is a perpetual flame war between the two camps

That is not important

# Why Python?

## Pros

1. Very popular general purpose programming language
1. Strong ecosystem through packages (over 230K projects)
1. Succint syntax 
1. Reasonably fast while also relatively easy to program
  
    + Computational time vs Developer time
1. Self-documenting
1. Easier to integrate into production pipelines that already use Python
    + Web frameworks (Django, Flask, ...)
    + Workflow managers (Luigi, ...)
1. Increasingly strong Data Science Stack

## Cons

1. Not a rich-enough ecosystem for some purposes
1. More computer science-y, less statistical
1. Poorer frameworks for display and dissemination of information

These are areas where R tends to shine. 

## Python Data Science stack

Contributed packages over past 30 years

+ To emulate Matlab
    + Numpy
    + Scipy
    + Matplotlib
+ To emulate Maple
    + Sympy
+ To add statistics/data science
    + Pandas
    + Various data visualization packages
        - seaborn
        - plotly

+ Many more user-contributed packages
+ The basic philosophy has been to concentrate on a few monolithic comprehensive packages
    - statsmodels (Statistics)
    - scikit-learn (Machine Learning)
    - pillow (Image analysis)
    - nltk (Natural Language Processing)
    - tensorflow & PyTorch (Deep learning)
    - PyMC3 (Bayesian learning)
    

## Python as glue

![](graphs/r_py_glue.png)

* The `rpy2` Python package is not developed on Windows
* The `reticulate` R package actually works quite well

1. Data I/O
    + We can read data from a variety of formats into Python
        - Some proprietary
        - R, SAS, Stata, SQL, Parquet, JSON
1. There are ways of running R, SAS, others from within Python
1. The Jupyter sub-ecosystem allows the same interface for [many languages](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels)
    + R, SAS, Julia, Haskell, Javascript


# A Python Primer

Python is a popular, general purpose scripting language. The [TIOBE index](https://www.tiobe.com/tiobe-index/) ranks Python as the third most popular programming language after C and Java, while this recent article in IEEE Computer Society says

> "Python can be used for web and desktop applications, GUI-based desktop applications, machine learning, data science, and network servers. The programming language enjoys immense community support and offers several open-source libraries, frameworks, and modules that make application development a cakewalk." ([Belani, 2020](https://www.computer.org/publications/tech-news/trends/programming-languages-you-should-learn-in-2020))

### Python is a modular language

Python is not a monolithic language but is comprised of 

1. a base programming language
1. numerous modules or libraries that add functionality to the language. 


### Python is a scripting language

Using Python requires typing!! 

1. You write *code* in Python 
1. that is then interpreted by the Python interpreter 
1. to make the computer implement your instructions. 

**Your code is like a recipe that you write for the computer**. 

Python is a *high-level language* in that the code is English-like and human-readable and understandable, which reduces the time needed for a person to create the recipe. 

It is a language in that it has nouns (*variables* or *objects*), verbs (*functions*) and a structure or grammar that allows the programmer to write recipes for different functionalities.

Scripting can be frustrating in the beginning. You will find that the code you wrote doesn't work "for some reason", though it looks like you wrote it fine. The first things I look for, in order, are

One thing that is important to note in Python: **case is important!**. If we have two objects named `data` and `Data`, they will refer to different things. 

1. Did I spell all the variables and functions correctly
1. Did I close all the brackets I have opened
1. Did I finish all the quotes I started, and paired single- and double-quotes
1. Did I already import the right module for the function I'm trying to use. 
1. Do I have the right indentations in my code.

These may not make sense right now, but as we go into Python, I hope you will remember these to help debug your code. 

## An example

Let's consider the following piece of Python code:


```python
# set a splitting point
split_point = 3

# make two empty lists
lower = []; upper = []

# Split numbers from 0 to 9 into two groups, 
# one lower or equal to the split point and 
# one higher than the split point

for i in range(10):  # count from 0 to 9
    if i <= split_point:
        lower.append(i)
    else:
        upper.append(i)

print("lower:", lower)
print("upper:", upper)
```

    lower: [0, 1, 2, 3]
    upper: [4, 5, 6, 7, 8, 9]


First note that any line (or part of a line) starting with `#` is a **comment** in Python and is ignored by the interpreter. This makes it possible for us to write substantial text to remind us what each piece of our code does

The first piece of code that the Python interpreter actually reads is


```python
split_point = 3
```

This takes the number 3 and stores it in the **variable** `split_point`. Variables are just names where some Python object is stored. It really works as an address to some particular part of your computer's memory, telling the Python interpreter to look for the value stored at that particular part of memory. Variable names allow your code to be human-readable since it allows you to write expressive names to remind yourself what you are storing. The rules of variable names are:

1. Variable names must start with a letter or underscore
2. The rest of the name can have letters, numbers or underscores
3. Names are case-sensitive


The next piece of code initializes two **lists**, named `lower` and `upper`.


```python
lower = []; upper = []
```

The semi-colon tells Python that, even though written on the same line, a particular instruction ends at the semi-colon, then another piece of instruction is written.

Lists are a catch-all data structure that can store different kinds of things, In this case we'll use them to store numbers.



```python
for i in range(10):  # count from 0 to 9
    if i <= split_point 
        lower.append(i)
    else:
        upper.append(i)
```

This is a _for-loop_.

1. State with the numbers 0-9 (this is achieved in `range(10)`)
2. Loop through each number, naming it `i` each time
    1. Computer programs allow you to over-write a variable with a new value
3. If the number currently stored in `i` is less than or equal to the value of `split_point`, i.e., 3 then add it to the list `lower`. Otherwise add it to the list `upper`


```python
for i in range(10):  # count from 0 to 9
    if i <= split_point:
        lower.append(i)
    else:
        upper.append(i)
```

Note the indentation in the code. **This is not by accident**. Python understands the extent of a particular block of code within a for-loop (or within a `if` statement) using the indentations. 

In this segment there are 3 code blocks:

1. The for-loop as a whole (1st indentation)
2. The `if` statement testing if the number is less than or equal to the split point, telling Python what to do if the test is true
3. The `else` statement stating what to do if the test in the `if` statement is false


The last bit of code prints out the results


```python
print("lower:", lower)
print("upper:", upper)
```

The `print` statement adds some text, and then prints out a representation of the object stored in the variable being printed. In this example, this is a list, and is printed as

```
lower: [0, 1, 2, 3]
upper: [4, 5, 6, 7, 8, 9]
```

We will expand on these concepts in the next few sections.

### Some general rules on Python syntax

1. Comments are marked by `#`
2. A statement is terminated by the end of a line, or by a `;`.
3. Indentation specifies blocks of code within particular structures. Whitespace at the beginning of lines matters. Typically you want to have 2 or 4 spaces to specify indentation, not a tab (\t) character. This can be set up in your IDE.
4. Whitespace within lines does not matter, so you can use spaces liberally to make your code more readable
5. Parentheses (`()`) are for grouping pieces of code or for calling functions.

There are several conventions about code styling including the one in [PEP8](https://www.python.org/dev/peps/pep-0008/#function-and-variable-names) (PEP = Python Enhancement Proposal) and one proposed by [Google](https://google.github.io/styleguide/pyguide.html#316-naming). We will typically be using lower case names, with words separated by underscores, in this workshop, basically following PEP8. Other conventions are of course allowed as long as they are within the basic rules stated above.

# Data types

## Numbers

1. Floats (decimal numbers) : `float`
1. Integers : `int`

| Operation | Result                             |
| --------- | ---------------------------------- |
| x + y     | The sum of x and y                 |
| x - y     | The difference of x and y          |
| x * y     | The product of x and y             |
| x / y     | The quotient of x and y            |
| - x       | The negative of x                  |
| abs(x)    | The absolute value of x            |
| x ** y    | x raised to the power y            |
| int(x)    | Convert a number to integer        |
| float(x)  | Convert a number to floating point |


```python
x = 3; y = 5

(2*x) -  (5 * y**2)
```




    -119



## Strings


```python
first_name = 'Abhijit'
last_name = "Dasgupta"

'jit' in last_name
```




    False



## String operations


```python
first_name + last_name

first_name*3

"gup" in last_name
```

## Truthiness

Truthiness means evaluating the truth of a statement. This typically results in a Boolean object, which can take values `True` and `False`, but Python has several equivalent representations. The following values are considered the same as False:

> `None`, `False`, zero (`0`, `0L`, `0.0`), any empty sequence (`[]`, `''`, `()`), and a few others

All other values are considered True. Usually we'll denote truth by `True` and the number `1`.

| Operation | Result                            |
| --------- | --------------------------------- |
| x < y     | x is strictly less than y         |
| x <= y    | x is less than or equal to y      |
| x == y    | x equals y (note, it's 2 = signs) |
| x != y    | x is not equal to y               |
| x > y     | x is strictly greater than y      |
| x >= y    | x is greater or equal to y        |

We can chain these comparisons using Boolean operations

| Operation | Result                                   |
| --------- | ---------------------------------------- |
| x \| y    | Either x is true or y is true or both    |
| x & y     | Both x and y are true                    |
| not x     | if x is true, then false, and vice versa |


```python
x = 5

(x < 3) | (x <= 7)
```




    True



Variables are like individual ingredients in your recipe. It's *mis en place* or setting the table for any operations (*functions*) we want to do to them. 

+ Variables are like *nouns*, 
+ which will be acted on by verbs (*functions*). 

In the next section we'll look at collections of variables. These collections are important in that it allows us to organize our variables with some structure. 

# Data structures

1. Lists (`[]`)
2. Tuples (`()`)
3. Dictionaries or dicts (`{}`)

Lists are baskets that can contain different kinds of things. They  are ordered, so that there is a first element, and a second element, and a last element, in order. However, the *kinds* of things in a single list doesn't have to be the same type.

Tuples are basically like lists, except that they are *immutable*, i.e., once they are created, individual values can't be changed. They are also ordered, so there is a first element, a second element and so on.

Dictionaries are **unordered** key-value pairs, which  are very fast for looking up things. They work almost like hash tables.  Dictionaries will be very useful to us as we progress towards the PyData stack. Elements need to be referred to by *key*, not by position.


```python
test_list = ["apple", 3, True, "Harvey", 48205]
test_tuple = ("apple", 3, True, "Harvey", 48205)

test_list[0]

```




    'apple'



|                    |         |      |      |          |       |
| ------------------ | ------- | ---- | ---- | -------- | ----- |
| index              | 0       | 1    | 2    | 3        | 4     |
| element            | 'apple' | 3    | True | 'Harvey' | 48205 |
| counting backwards | -5      | -4   | -3   | -2       | -1    |



```python
contact = {
    "first_name": "Abhijit",
    "last_name": "Dasgupta",
    "Age": 48,
    "address": "124 Main St",
    "Employed": True,
}
```


```python
contact['first_name']
contact['address']
```


```python
contact.keys()
contact.values()
```

# Operations

# Loops

```pseudocode
Start with a list of datasets, one for each state
for each state
    compute and store fraction of votes that are Republican
    compute and store fraction of votes that are Democratic
```



```python
for i in range(len(test_list)):
    print(test_list[i])
```


```python
for u in test_list:
    print(u)
```


```python
test_list2 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
mysum = 0
for u in test_list2:
    mysum = mysum + u
print(mysum)
```

`enumerate` automatically creates both the index and the value for each element of a list.


```python
L = [0, 2, 4, 6, 8]
for i, val in enumerate(L):
    print(i, val)
```

    0 0
    1 2
    2 4
    3 6
    4 8


`zip` puts multiple lists together and creates a composite iterator. You can have any number of iterators in zip, and the length of the result is determined by the length of the shortest iterator. 


```python
first = ["Han", "Luke", "Leia", "Anakin"]
last = ["Solo", "Skywalker", "Skywaker", "Skywalker"]
types = ['light','light','light','light/dark/light']

for val1, val2, val3 in zip(first, last, types):
    print(val1, val2, ' : ', val3)
```

    Han Solo  :  light
    Luke Skywalker  :  light
    Leia Skywaker  :  light
    Anakin Skywalker  :  light/dark/light


## List comprehensions


```python
test_list2 = [1,2,3,4,5,6]

squares = [u**2 for u in test_list2]
squares
```

## Conditional evaluation

```pseudocode
if Condition 1 is true then
	do Recipe 1
else if (elif) Condition 2 is true then
  do Recipe 2
else
  do Recipe 3
```



```python

x = [-2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
y = []  # an empty list

for u in x:
    if u < 0:
        y.append("Negative")
    elif u % 2 == 1:  # what is remainder when dividing by 2
        y.append("Odd")
    else:
        y.append("Even")

print(y)
```

    ['Negative', 'Negative', 'Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even', 'Odd', 'Even']


## Functions


```python
def my_mean(x):
    y = 0
    for u in x:
        y += u 
    y = y / len(x)
    return y
```

A Python function must start with the keyword `def` followed by the name of the function, the arguments within parentheses, and then a colon. The actual code for the function is indented, just like in for-loops and if-elif-else structures. It ends with a `return` function which specifies the output of the function.



```python
def my_mean(x):
    """
  A function to compute the mean of a list of numbers.
  
  INPUTS:
  x : a list containing numbers
  
  OUTPUT:
  The arithmetic mean of the list of numbers
  """
    y = 0
    for u in x:
        y = y + u
    y = y / len(x)
    return y
```


```python
help(my_mean)
```

    Help on function my_mean in module __main__:
    
    my_mean(x)
        A function to compute the mean of a list of numbers.
        
        INPUTS:
        x : a list containing numbers
        
        OUTPUT:
        The arithmetic mean of the list of numbers
    


# Pandas (Python Data Analysis)

+ Data ingestion
+ Data cleaning and transformation
+ Data can be passed on to modeling and visualization packages

## Activating packages for use

+ Use the `import` command
+ Maybe provide an alias for the package


```python
import numpy as np
import pandas as pd
```

## Data import

| Format type | Description | reader       | writer     |
| ----------- | ----------- | ------------ | ---------- |
| text        | CSV         | read_csv     | to_csv     |
|             | Excel       | read_excel   | to_excel   |
| text        | JSON        | read_json    | to_json    |
| binary      | Feather     | read_feather | to_feather |
| binary      | SAS         | read_sas     |            |
| SQL         | SQL         | read_sql     | to_sql     |



```python
mtcars = pd.read_csv('data/mtcars.csv')
```

> One of the big differences between a spreadsheet program and a programming language from the data science perspective is that you have to load data into the programming language. It's not "just there" like Excel. This is a good thing, since it allows the common functionality of the programming language to work across multiple data sets, and also keeps the original data set pristine. Excel users can run into problems and [corrupt their data](https://nature.berkeley.edu/garbelottoat/?p=1488) if they are not careful.

## Exploring data

## Creating a DataFrame


```python
rng = np.random.RandomState(25)
d2 = pd.DataFrame(rng.normal(0,1, (4, 5)), 
                  columns = ['A','B','C','D','E'], 
                  index = ['a','b','c','d'])
d2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>0.228273</td>
      <td>1.026890</td>
      <td>-0.839585</td>
      <td>-0.591182</td>
      <td>-0.956888</td>
    </tr>
    <tr>
      <th>b</th>
      <td>-0.222326</td>
      <td>-0.619915</td>
      <td>1.837905</td>
      <td>-2.053231</td>
      <td>0.868583</td>
    </tr>
    <tr>
      <th>c</th>
      <td>-0.920734</td>
      <td>-0.232312</td>
      <td>2.152957</td>
      <td>-1.334661</td>
      <td>0.076380</td>
    </tr>
    <tr>
      <th>d</th>
      <td>-1.246089</td>
      <td>1.202272</td>
      <td>-1.049942</td>
      <td>1.056610</td>
      <td>-0.419678</td>
    </tr>
  </tbody>
</table>
</div>



A DataFrame has (mutable)

+ An `index` (row names)
+ A `column` (column names)‘


```python
d2.columns
d2.index
```




    Index(['a', 'b', 'c', 'd'], dtype='object')




```python
df = pd.DataFrame({
    'A':3.,
    'B':rng.random_sample(5),
    'C': pd.Timestamp('20200512'),
    'D': np.array([6] * 5),
    'E': pd.Categorical(['yes','no','no','yes','no']),
    'F': 'NIH'})
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3.0</td>
      <td>0.481343</td>
      <td>2020-05-12</td>
      <td>6</td>
      <td>yes</td>
      <td>NIH</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3.0</td>
      <td>0.516502</td>
      <td>2020-05-12</td>
      <td>6</td>
      <td>no</td>
      <td>NIH</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>0.383048</td>
      <td>2020-05-12</td>
      <td>6</td>
      <td>no</td>
      <td>NIH</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.0</td>
      <td>0.997541</td>
      <td>2020-05-12</td>
      <td>6</td>
      <td>yes</td>
      <td>NIH</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3.0</td>
      <td>0.514244</td>
      <td>2020-05-12</td>
      <td>6</td>
      <td>no</td>
      <td>NIH</td>
    </tr>
  </tbody>
</table>
</div>



You can also use a `dict` to create a `DataFrame`. If elements aren't of the same size, errors will be thrown, unless it is a single element. Then it will be repeated. 

## Slicing and dicing a DataFrame


```python
df['B']
df.B

```




    0    0.481343
    1    0.516502
    2    0.383048
    3    0.997541
    4    0.514244
    Name: B, dtype: float64



There are two extractor functions in `pandas`:

+ `loc` extracts by label (index label, column label, slice of labels, etc.
+ `iloc` extracts by index (integers, slice objects, etc.



```python
 df.loc[1:3, 'C']
```




    1   2020-05-12
    2   2020-05-12
    3   2020-05-12
    Name: C, dtype: datetime64[ns]



You can also extract rows by condition (filter)


```python
df = pd.DataFrame(np.random.randn(5, 3), index = ['a','c','e', 'f','g'], columns = ['one','two','three']) # pre-specify index and column names
df['four'] = 20 # add a column named "four", which will all be 20
df['five'] = df['one'] > 0
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
      <th>three</th>
      <th>four</th>
      <th>five</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>-0.847315</td>
      <td>0.663926</td>
      <td>0.182211</td>
      <td>20</td>
      <td>False</td>
    </tr>
    <tr>
      <th>c</th>
      <td>1.682927</td>
      <td>-0.056388</td>
      <td>0.244149</td>
      <td>20</td>
      <td>True</td>
    </tr>
    <tr>
      <th>e</th>
      <td>0.185502</td>
      <td>0.554072</td>
      <td>-0.739743</td>
      <td>20</td>
      <td>True</td>
    </tr>
    <tr>
      <th>f</th>
      <td>-0.151335</td>
      <td>-0.172999</td>
      <td>-0.656354</td>
      <td>20</td>
      <td>False</td>
    </tr>
    <tr>
      <th>g</th>
      <td>0.672965</td>
      <td>-0.680025</td>
      <td>-0.065153</td>
      <td>20</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[(df.one > 1) & (df.three < 0)]

df.query('(one > 1) & (three > 0)')
    
    
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
      <th>three</th>
      <th>four</th>
      <th>five</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>c</th>
      <td>1.682927</td>
      <td>-0.056388</td>
      <td>0.244149</td>
      <td>20</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## Replacing values


```python
#df2.replace(0, -9) # replace 0 with -9

df.replace({'one': {5: 500}, 'three':{0:-9, 8:800}})
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
      <th>three</th>
      <th>four</th>
      <th>five</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>-0.847315</td>
      <td>0.663926</td>
      <td>0.182211</td>
      <td>20</td>
      <td>False</td>
    </tr>
    <tr>
      <th>c</th>
      <td>1.682927</td>
      <td>-0.056388</td>
      <td>0.244149</td>
      <td>20</td>
      <td>True</td>
    </tr>
    <tr>
      <th>e</th>
      <td>0.185502</td>
      <td>0.554072</td>
      <td>-0.739743</td>
      <td>20</td>
      <td>True</td>
    </tr>
    <tr>
      <th>f</th>
      <td>-0.151335</td>
      <td>-0.172999</td>
      <td>-0.656354</td>
      <td>20</td>
      <td>False</td>
    </tr>
    <tr>
      <th>g</th>
      <td>0.672965</td>
      <td>-0.680025</td>
      <td>-0.065153</td>
      <td>20</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## Joins

There are basically four kinds of joins:

| pandas | R          | SQL         | Description                     |
| ------ | ---------- | ----------- | ------------------------------- |
| left   | left_join  | left outer  | keep all rows on left           |
| right  | right_join | right outer | keep all rows on right          |
| outer  | outer_join | full outer  | keep all rows from both         |
| inner  | inner_join | inner       | keep only rows with common keys |

## Joins

<img src="graphs/joins.png" align="center"/>


```python
survey = pd.read_csv('data/survey_survey.csv')
visited = pd.read_csv('data/survey_visited.csv')
```


```python
pd.merge(survey, visited, left_on = 'taken', right_on = 'ident', how = 'left')
# survey.merge(visited, left_on = 'taken', right_on = 'ident', how = 'left')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>taken</th>
      <th>person</th>
      <th>quant</th>
      <th>reading</th>
      <th>ident</th>
      <th>site</th>
      <th>dated</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>619</td>
      <td>dyer</td>
      <td>rad</td>
      <td>9.82</td>
      <td>619</td>
      <td>DR-1</td>
      <td>1927-02-08</td>
    </tr>
    <tr>
      <th>1</th>
      <td>619</td>
      <td>dyer</td>
      <td>sal</td>
      <td>0.13</td>
      <td>619</td>
      <td>DR-1</td>
      <td>1927-02-08</td>
    </tr>
    <tr>
      <th>2</th>
      <td>622</td>
      <td>dyer</td>
      <td>rad</td>
      <td>7.80</td>
      <td>622</td>
      <td>DR-1</td>
      <td>1927-02-10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>622</td>
      <td>dyer</td>
      <td>sal</td>
      <td>0.09</td>
      <td>622</td>
      <td>DR-1</td>
      <td>1927-02-10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>734</td>
      <td>pb</td>
      <td>rad</td>
      <td>8.41</td>
      <td>734</td>
      <td>DR-3</td>
      <td>1939-01-07</td>
    </tr>
    <tr>
      <th>5</th>
      <td>734</td>
      <td>lake</td>
      <td>sal</td>
      <td>0.05</td>
      <td>734</td>
      <td>DR-3</td>
      <td>1939-01-07</td>
    </tr>
    <tr>
      <th>6</th>
      <td>734</td>
      <td>pb</td>
      <td>temp</td>
      <td>-21.50</td>
      <td>734</td>
      <td>DR-3</td>
      <td>1939-01-07</td>
    </tr>
    <tr>
      <th>7</th>
      <td>735</td>
      <td>pb</td>
      <td>rad</td>
      <td>7.22</td>
      <td>735</td>
      <td>DR-3</td>
      <td>1930-01-12</td>
    </tr>
    <tr>
      <th>8</th>
      <td>735</td>
      <td>NaN</td>
      <td>sal</td>
      <td>0.06</td>
      <td>735</td>
      <td>DR-3</td>
      <td>1930-01-12</td>
    </tr>
    <tr>
      <th>9</th>
      <td>735</td>
      <td>NaN</td>
      <td>temp</td>
      <td>-26.00</td>
      <td>735</td>
      <td>DR-3</td>
      <td>1930-01-12</td>
    </tr>
    <tr>
      <th>10</th>
      <td>751</td>
      <td>pb</td>
      <td>rad</td>
      <td>4.35</td>
      <td>751</td>
      <td>DR-3</td>
      <td>1930-02-26</td>
    </tr>
    <tr>
      <th>11</th>
      <td>751</td>
      <td>pb</td>
      <td>temp</td>
      <td>-18.50</td>
      <td>751</td>
      <td>DR-3</td>
      <td>1930-02-26</td>
    </tr>
    <tr>
      <th>12</th>
      <td>751</td>
      <td>lake</td>
      <td>sal</td>
      <td>0.10</td>
      <td>751</td>
      <td>DR-3</td>
      <td>1930-02-26</td>
    </tr>
    <tr>
      <th>13</th>
      <td>752</td>
      <td>lake</td>
      <td>rad</td>
      <td>2.19</td>
      <td>752</td>
      <td>DR-3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>752</td>
      <td>lake</td>
      <td>sal</td>
      <td>0.09</td>
      <td>752</td>
      <td>DR-3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>752</td>
      <td>lake</td>
      <td>temp</td>
      <td>-16.00</td>
      <td>752</td>
      <td>DR-3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>752</td>
      <td>roe</td>
      <td>sal</td>
      <td>41.60</td>
      <td>752</td>
      <td>DR-3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>837</td>
      <td>lake</td>
      <td>rad</td>
      <td>1.46</td>
      <td>837</td>
      <td>MSK-4</td>
      <td>1932-01-14</td>
    </tr>
    <tr>
      <th>18</th>
      <td>837</td>
      <td>lake</td>
      <td>sal</td>
      <td>0.21</td>
      <td>837</td>
      <td>MSK-4</td>
      <td>1932-01-14</td>
    </tr>
    <tr>
      <th>19</th>
      <td>837</td>
      <td>roe</td>
      <td>sal</td>
      <td>22.50</td>
      <td>837</td>
      <td>MSK-4</td>
      <td>1932-01-14</td>
    </tr>
    <tr>
      <th>20</th>
      <td>844</td>
      <td>roe</td>
      <td>rad</td>
      <td>11.25</td>
      <td>844</td>
      <td>DR-1</td>
      <td>1932-03-22</td>
    </tr>
  </tbody>
</table>
</div>



Here, the left dataset is `survey` and the right one is `visited`. 

Since we're doing a left join, we keed all the rows from `survey` and add columns from `visited`, matching on the common key, called "taken" in one dataset and "ident" in the other. 

Note that the rows of `visited` are repeated as needed to line up with all the rows with common "taken" values. 

## Data aggregation and split-apply-combine

![](graphs/split-apply-combine.png)


```python
gapminder =  pd.read_csv('data/gapminder.tsv', sep = '\t') 
gapminder.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>continent</th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1952</td>
      <td>28.801</td>
      <td>8425333</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1957</td>
      <td>30.332</td>
      <td>9240934</td>
      <td>820.853030</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1962</td>
      <td>31.997</td>
      <td>10267083</td>
      <td>853.100710</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1967</td>
      <td>34.020</td>
      <td>11537966</td>
      <td>836.197138</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1972</td>
      <td>36.088</td>
      <td>13079460</td>
      <td>739.981106</td>
    </tr>
  </tbody>
</table>
</div>




```python
gapminder.groupby('country')['lifeExp'].mean()
```




    country
    Afghanistan           37.478833
    Albania               68.432917
    Algeria               59.030167
    Angola                37.883500
    Argentina             69.060417
                            ...    
    Vietnam               57.479500
    West Bank and Gaza    60.328667
    Yemen, Rep.           46.780417
    Zambia                45.996333
    Zimbabwe              52.663167
    Name: lifeExp, Length: 142, dtype: float64




```python
gapminder.groupby('country').get_group('United Kingdom')
```


```python
gapminder.groupby('continent').lifeExp.agg(np.median) # Medians
```




    continent
    Africa      47.7920
    Americas    67.0480
    Asia        61.7915
    Europe      72.2410
    Oceania     73.6650
    Name: lifeExp, dtype: float64




```python
gapminder.groupby('year').agg({'lifeExp': np.mean, 'pop': np.median, 'gdpPercap': np.median}).reset_index()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1952</td>
      <td>49.057620</td>
      <td>3943953.0</td>
      <td>1968.528344</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1957</td>
      <td>51.507401</td>
      <td>4282942.0</td>
      <td>2173.220291</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1962</td>
      <td>53.609249</td>
      <td>4686039.5</td>
      <td>2335.439533</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1967</td>
      <td>55.678290</td>
      <td>5170175.5</td>
      <td>2678.334741</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1972</td>
      <td>57.647386</td>
      <td>5877996.5</td>
      <td>3339.129407</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1977</td>
      <td>59.570157</td>
      <td>6404036.5</td>
      <td>3798.609244</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1982</td>
      <td>61.533197</td>
      <td>7007320.0</td>
      <td>4216.228428</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1987</td>
      <td>63.212613</td>
      <td>7774861.5</td>
      <td>4280.300366</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1992</td>
      <td>64.160338</td>
      <td>8688686.5</td>
      <td>4386.085502</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1997</td>
      <td>65.014676</td>
      <td>9735063.5</td>
      <td>4781.825478</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2002</td>
      <td>65.694923</td>
      <td>10372918.5</td>
      <td>5319.804524</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2007</td>
      <td>67.007423</td>
      <td>10517531.0</td>
      <td>6124.371109</td>
    </tr>
  </tbody>
</table>
</div>


