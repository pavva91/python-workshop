# Python

- Python is interpreted.
- Python is strongly typed (values won't change in unexpected ways)
- Python is dynamically typed.
- Python does not need ';' (is not pythonic to use ';')
- Python is a very dynamic language
- In Python everything is an object
- Python is OOP
- Name variables as explicit as possible
- Python scoping happens through indentation (4 spaces) and not through brackets ({})
- Package manager: pip
- Python has 33 keywords
- Index of a list starts at zero

# Project Virtual Environment Setup

```bash
python3 -m venv env
source env/bin/activate
```

# Python REPL

```python
name = "hello"
type(name)
dir(name)
dir(str)
name.upper()
help(str)
```

If you have doubts on something type:

- dir()
- help()

# Variables

1. Cannot start with a number

**_NOTE_:** read the traceback from the bottom to the top

**_NOTE_:** Python let's you do a lot of stuff that will shoot you in the foot
**_NOTE_:** I can name a variable 'list' and override the built-in type

# Python Features

1. Python is open source
2. Rich fully featured standard library (batteries included language)
3. PyPi package index for 3rd party packages
4. Big and supportive community

# Types

## Immutable Types

1. String
2. Numbers
   - int
   - float

Built-in types:

1. None
2. True
3. False

These are singletons, they are only declared once

## Difference between == and is

'==' equality
'is' do they point to the same thing in memory

### Verify type:

- type(x)

## Special Type in Python (NoneType)

'None' in Python signifies 'null' in other languages

## Numbers

- Integers (e.g. 2)
- Float (e.g. 0.0)
- complex (e.g. 42j)

Integers and other simple data types are just objects under the hood, so you can just create new ones by calling the method that is associated with that type
The result of Integers division is a float

```python
type(4/2)
```

## String

One can use either single quotes ('') or double quotes (""). The best practice is to use double quotes.

### Long String

Triple double quotes (""") to open and triple double quotes to end the long string

### String Formatting

#### F-String

One of the biggest advantages of Python 3 is something called f-strings. It's the new fancy way of string formatting
f-string starts with a f"
curly braces to reference a variable

```python
name = "Nina"
print(f"Hello, {name}")
```

is the same as:

```python
name = "Nina"
print("Hello %s" % name)
```

```python
name = "Nina"
print("Hello", name)
```

#### Percent Formatting

You may see on legacy python.

### Common Mistakes

- Mixed single and double quotes
- String concatenation of integer and string

## Functions

Goal: make our code reusable
Python does not use brackets
Python does use indentation instead
indentation: use spaces instead of tabs
The return statement is optional

```python
def function_name(x, y):
    sum = x + y
    print(sum)
    return(sum)
```

### Default arguments

The default arguments comes last in the function signature.
The default arguments get instantiated once, when the function is defined.

```python
def say_greeting(name, greeting="Hello"):
    print(f"{greeting} {name}!")
```

#### Never use a list as default argument

You never want to use mutable types as list as a default argument

DON'T DO THIS:

```python
def foo(a, b=[]):
    b.append(a)
    print(b)

foo(5) # [5]
foo(6) # [5, 6]
```

DO THIS INSTEAD:

```python
def foo(a, b=None):
    if b is None:
        b = []
    b.append(a)
    print(b)

foo(5) # [5]
foo(6) # [6]
```

b gets instantiated once, when the function is defined

# Lists

Lists can contain any type
Mutability means: "can the content of this item be changed after it is declared?"
A list is mutable
**_NOTE_**: items in a list don't have to be the same type.

This is a legit list:

```python
names = [1, 5.0, "Nina", True, None]
len(names)
print(names[0])
```

Index of a list starts at zero
[] -> Create an empty list
list() -> Create an empty list
Lists retain the order of the elements inside it.

```python
names = ['a','b','c']
len(names)
print(names[0])
```

**_NOTE_**: get help with: dir(list) and then use help for have info on the function (e.g. help(list.reverse))

## Sorting a list

1. Just return sorted version without changing the original list.

```python
names = ['z','b','c']
print(sorted(names))
print(names)
```

2. Change the original list

```python
names = ['z','b','c']
names.sort()
print(names)
```

3. Change the original list (reverse the order)

```python
names = ['z','b','c']
names.reverse()
print(names)
```

## Add Items into a list

1. Use append() to add in the tail of the list

```python
names = ['z','b','c']
names.append('d')
print(names)
```

2. Use insert() to add in a specific position of the list.

```python
names = ['z','b','c']
names.insert(0,'d')
print(names)
```

will insert 'd' at the beginning of 'names' list

3. Combine 2 lists together (extend)

```python
names = ['z','b','c']
colors = ["Blue", "Red"]
names.extend(colors)
print(names)
```

## Lookup (search an item in a list)

The search speed is slow

1. use 'in'

```python
colors = ["Blue", "Red"]
isBluePresent = "Blue" in names
print(isBluePresent)
```

2. use 'index' to find the index of the potential first match

```python
colors = ["Blue", "Red"]
print(colors.index("Blue"))
```

3. use 'count' to count how many times the item matches

```python
colors = ["Blue", "Red", "Blue"]
print(colors.count("Blue"))
```

## Removing items from a list

1. use 'remove' to remove the first instance of the item

```python
colors = ["Blue", "Red", "Blue"]
colors.remove("Blue")
print(colors)
```

2. use 'pop' to remove the last element of the list

```python
colors = ["Blue", "Red", "Blue"]
removed_item = colors.pop()
print(colors)
```

3. use 'pop' to remove the indexed element on the list

```python
colors = ["Blue", "Red", "Blue"]
removed_item = colors.pop(1)
print(colors)
```

# Tuples

Tuples are a lightweight collection that are generally used to keep track of related but different items
Tuples are immutable.
It means that once a tuple has been created the items in it can't change
Tuples are very useful to return multiple values from a function and then use tuple unpacking to get the single values as named variables

## Empty tuple

```python
a = ()
type(a)
```

## One Item tuple

### Correct way

```python
a = (1,)
type(a)
```

### Wrong way

```python
a = (1)
type(a) # will be 'int'
```

## Unpacking Tuples

```python
student = ("Marco", 8, "History", 3.5)
name, age, subject, gpa = student
print(name)
print(gpa)
```

If we don't care about one of the values of the tuple we can use underscore (\_)

```python
student = ("Marco", 8, "History", 3.5)
name, _, subject, _ = student
print(name)
print(subject)
```

# Sets

Sets are used to store immutable data-types uniquely.
Sets are mutable (you can add and remove items from the set)
Sets are a data type that allows you to store other immutable types in an unsorted way.
An item can only be store into a set once, there are no duplicates allowed. (The duplicate values are ignored)
A set doesn't have an order.
A set doesn't have positions.
The advantages of a set are:

- very fast testing of a membership (if an item is in the set) (it is using hashing)

Curly braces are used by sets and dictionaries

```python
type({}) # is a 'dict'
```

```python
type({1}) # is a 'set'
```

## Create empty set

```python
empty_set = set()
```

## Create set with duplicates

1. By using 'set'

```python
names = ["Nina", "Max", "Rose", "Max", "Nina"]
set_names = set(names)
len(set_names) # 3
```

2. Directly by using brackets {}

```python
names = { "Nina", "Max", "Rose", "Max", "Nina" }
len(names) # 3
```

## Adding, Removing & Updating a Set

### Remove

1. Use 'discard'

```python
colors = { "Red", "Blue", "Green"}
colors.discard("Blue")
len(colors) # 2
```

'discard' will get rid of the item in the set, whether or not it is present (no returning error).

2. Use 'remove'

```python
colors = { "Red", "Blue", "Green"}
colors.remove("Blue")
len(colors) # 2
```

'remove' will get rid of the item in the set, if present, if the item is not present it will return an error.

### Update

```python
colors = { "Red", "Blue", "Green"}
numbers = {1, 4, 5}
colors.update(numbers)
len(colors) # 6
```

'update' expects a sequence.
**_NOTE_**: If you pass a string into update it will get each single char as a sequence:

```python
colors = { "Red", "Blue", "Green"}
colors.update("Purple")
len(colors) # 9
print(colors)
```

If you want to add "Purple" to colors set do this:

```python
colors = { "Red", "Blue", "Green"}
colors.update({"Purple"})
len(colors) # 4
print(colors)
```

### Check if item is in the set

1. in

```python
colors = { "Red", "Blue", "Green"}
print("Blue" in colors) # True
```

```python
colors = { "Red", "Blue", "Green"}
print("Purple" in colors) # False
```

### Union

All the items that are in set 'A' or in set 'B'

1. Use pipe (|)

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors | favorite_colors)
```

2. Use 'union'

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors.union(favorite_colors))
```

### Intersection

All the items that are in set 'A' and in set 'B'

1. Use ampersand (&)

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors & favorite_colors) # {'Violet', 'Black'}
```

2. Use 'intersection'

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors.intersection(favorite_colors)) # {'Violet', 'Black'}
```

### Difference

All the items that are in set 'A' but not in set 'B'

1. Use 'difference'

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors.difference(favorite_colors)) # {'Red', 'Green', 'Blue'}
```

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(favorite_colors.difference(colors)) # {'White'}
```

### Symmetric Difference

All the items that are in set 'A' but not in set 'B' and viceversa
Is the union minus the intersection

1. Use hat (^)

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors ^ favorite_colors) # {'Red', 'Green', 'Blue', 'White'}
```

2. Use 'symmetric_difference'

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
favorite_colors = { "Violet", "Black", "White"}
print(colors.symmetric_difference(favorite_colors)) # {'Red', 'Green', 'Blue', 'White'}
```

## Convert set into a list

```python
colors = { "Red", "Blue", "Green", "Violet", "Black"}
col_list = list(colors)
print(col_list) # ['Red', 'Green', 'Blue', 'White']
```

# Dictionaries

Allow us to store our data in key, value pairs.
Dictionaries themselves are mutable, but, dictionary keys can only be immutable types
JSON is key, value pairs data-structure, so dictionaries is the perfect data structure to work with JSON.
Dictionaries uses hash functions under the hood
I can have mutable types as values
I cannot have mutable types as keys
Only immutable types can be used as dictionary keys
Like in sets, the keys of the dictionary are not ordered
We can have duplicate values
We cannot have duplicate keys

## Empty Dictionary

1. Using brackets

```python
empty_dictionary = {}
type(empty_dictionary)
```

2. Using 'dict'

```python
empty_dictionary = dict()
type(empty_dictionary)
```

## Normal Dictionary

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums)
print(nums['one'])
```

## Accessing Items

1. Directly (will return error if key is not present)

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums['one'])
```

2. With 'get' (will not return error if the key is not present)

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums.get("one"))
print(nums.get("four", "default value"))
```

## Add Items

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums)
nums["four"] = 4
print(nums)
```

## Check if item is in the dictionary

```python
nums = {"one": 1, "two": 2, "three":3}
print("one" in nums)
```

## Combine dictionaries together

```python
colors = {"r": "Red", "g": "Green"}
nums = {"one": 1, "two": 2, "three":3}
colors.update(nums)
print(colors)
```

In case that both dictionaries contains the same key, the key will be updated with incoming dictionary's value

```python
colors = {"r": "Red", "g": "Green", "one": "uno"}
nums = {"one": 1, "two": 2, "three":3}
colors.update(nums)
print(colors)
print(colors["one"]) # will print 1
```

## Get values

1. Get all the values of dictionary

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums.values())
```

2. Get all the keys of dictionary

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums.keys())
```

3. Get all the key-value pairs (items) of a dictionary

```python
nums = {"one": 1, "two": 2, "three":3}
print(nums.items())
```

# Boolean Logic

## Truthiness

'True' is true, 'False' is false.
0 is 'False'.
All other numbers are 'True' (including negative).

**_NOTE_**: Don't name your variables True, False, None

```python
print(bool(0)) # will print False
```

```python
print(bool(1)) # will print True
```

```python
print(bool(-1)) # will print True
```

```python
print(bool(0 == False)) # will print True
```

```python
print(bool(1 == True)) # will print True
```

- Empty list is falsy:

```python
print(bool([])) # will print False
```

- Empty dictionary is falsy:

```python
print(bool({})) # will print False
```

- Empty tuple is falsy:

```python
print(bool(())) # will print False
```

- Empty set is falsy:

```python
print(bool(set())) # will print False
```

- Non empty list is truthy:

```python
print(bool([1])) # will print True
```

- Non empty dictionary is truthy:

```python
print(bool({1 is truthy:1})) # will print True
```

- Non empty tuple is truthy:

```python
print(bool((1,))) # will print True
```

- Non empty set is truthy:

```python
print(bool({1})) # will print True
```

- None is falsy:

```python
print(bool(None)) # will print False
```

- Empty String is falsy:

```python
print(bool("")) # will print False
```

- Non-empty String is truthy:

```python
print(bool("hello")) # will print True
```

- None is falsy:

```python
print(bool(None)) # will print False
```

# Comparisons

In Python you can compare items of the same type.
For the built-in types it doesn't make sense to compare items of different types.
You can't compare different types in python3
Strings are compared by the underlying ascii value of the character (capital letters comes before lower case letters)

## Operators

- >
- <
- > =
- <=
- ==
- !=

```python
print("T" < "t") # will print True
```

```python
print("T" > "t") # will print False
```

```python
print("a" < "b") # will print True
```

```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b) # will print True
```

```python
print([1, 2, 3] == [1, 2, 3]) # will print True
```

```python
print([1, 2, 3] == [0, 2, 3]) # will print False
```

## Equality vs Identity

Equality is ==
Identity is the 'is' keyword
Identity := if the 2 objects are stored at the same memory location. (if they point to the same thing)

```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b) # will print True
print(a is b) # will print False
print(a != b) # will print False
print(a is not b) # will print True
```

# Looping & Control Flow

## For Loop

```python
colors = ["Red", "Green", "Blue"]
for color in colors:
   print(f"The color is: {color}")

print(color) # Blue
```

### For with range

1. Will print 0 to 4:

```python
for number in range(5):
   print(f"The number is: {number}")

print(number) # 4
```

2. Will print 1 to 4:

```python
for number in range(1, 5):
   print(f"The number is: {number}")

```

3. Will print 1 to 7 with step of 2 (1, 3, 5, 7):

```python
for number in range(1, 8, 2):
   print(f"The number is: {number}")

```

**_NOTE_:** color is accessible from outside the for loop

## Control Flow

1. If statement

```python
if 3 < 5:
   print("hello")

```

```python
a = []
if a:
   print("truthy")
else:
   print("falsy")


```

```python
a = False
if a:
   print("Hello")
else:
   print("Goodbye")

```

```python
a = False
b = True
if a:
   print("1")
elif b:
   print("2")
else:
   print("3")

```

## While Loop

```python
counter = 0
max = 4
while counter < max:
   print(f"The count is: {counter}")
   counter = counter + 1

```

### Break, Continue and Return

Break := Stops the loop execution

```python
names = ["Max", "Rose", "Nina", "Jimmy"]
for name in names:
   print(f"Hello, {name}")
   if name == "Nina":
      break

```

Will print:
Hello, Max
Hello, Rose
Hello, Nina

Continue := Goes back to the start of the loop, skipping every statement after the continue

```python
names = ["Max", "Rose", "Nina", "Jimmy"]
for name in names:
   if name == "Nina":
      continue
   print(f"Hello, {name}")

```

Will print:
Hello, Max
Hello, Rose
Hello, Jimmy

# Conventions

Name collections (lists) in plural

## PEP8

PEP8 is a Python coding standard, that sets guidelines for how our Python code should look like. ([](https:#pep8.org))
