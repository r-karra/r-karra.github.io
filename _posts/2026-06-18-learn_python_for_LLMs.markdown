---
layout: post
comments: true
title: "Learn Python with the Feynman Technique"
excerpt: "An intuitive guide to Python concepts including Lists, Dictionaries, Comprehensions, Lambda functions, Decorators, Generators, Type Hinting, and Constructors."
date: 2026-06-18 22:00:00
---

# Learn Python with me using the Feynman technique


```

Choose a concept to learn.
Teach it to yourself or someone else.
Return to the source material if you get stuck.
Simplify your explanations and create analogies.
```

# Python Intuition Guide: Think Like a Python Programmer 🐍
Instead of memorizing syntax, build mental models.

# 1. Lists → Your Backpack 🎒
A list is an ordered collection.

Imagine a backpack where you can put items in order.

```python
bag = ["apple", "banana", "mango"]
bag
```

### Access items

```python
print(bag[0])
print(bag[-1])
```

### Common operations

```python
# append()
#bag.append("orange")
print(bag)
print()
# remove()
#bag.remove("mango")
print(bag)
print()
print(f" length of a bag =", len(bag))

# Iterate
for fruit in bag:
  print(fruit)
```

# 2. Dictionaries → A Phone Contact Book 📖
Lists answer: "What's at position 2?"

Dictionaries answer: "What's associated with this key?"

```python
person = {
    "name": "John",
    "Age": 22,
    "City": "Nordic"
}

for key, value in person.items():
  print(key, value)
```

### Access

```python
print(person["name"])
print(person["Age"])
```

### Add/Update

```python
person["Age"] = 24
person["Professsion"] = "Researcher"

for key, value in person.items():
  print(key, value)
```

# 3. List Comprehensions → Tiny Factories 🏭

```python
# squares = []

# for x in range(5):
#   squares.append(x*x)
# print(squares)

squares = [x*x for x in range(5) ];print("squares", squares)
```

```python
cubes = [x ** x for x in range(5)]; print(cubes)
```

Read it as:

Build a list using x*x for every x.

Pattern:

```[new_item for item in iterable]```

### Add condtions

```python
evens = [x for x in range(25) if x % 2 == 0]; evens
```

```python
primes = [x for x in range(99) if x > 1 and all(x % i !=0 for i in range(2, int(x ** 0.5) + 1))]; print(primes)
```

'if-else' ternary operator inside a list comprehension to replace even numbers with 'Even' and odd numbers with 'Odd'?

```python
evenOdd = ['Even' if x % 2 == 0 else 'Odd' for x in range(20)]; print(evenOdd)
```

```python
# Flatern the matrix:
# The loops read left-to-right, meaning it extracts each row first, and then
# sequentially loops through each number inside that row.
matrix = [[1, 2], [3, 4]]; print(matrix)
flat = [num for row in matrix for num in row]; print(flat)
```

```python
# It performs redundant evaluations by converting strings into integers twice per valid element.
# The int(x) constructor runs inside both the output mapping assignment block and the filtering clause
vals = [int(x) for x in ['10', '20', '15', '30'] if int(x) < 25]; print(vals)
```

```python
# This creates an assignment reference during the filtering stage, allowing the
# mapped output variable to reuse the computed integer
vals1 = [v for x in ['10', '20', '18','30'] if (v:=int(x))<25]; print(vals1)
```

```python
# The outer loop creates a two-element container grid,
# where each sequence independently biilds a linear sequence running from 0 to 2
nested = [[x for x in range(3)] for _ in range(3)]; print(nested)
```

```python
# Python cleanly handles implicit tuple unpacking within the iteration asignment parameters of list comprehensions
pairs = [(1, 'a'), (2, 'b')]
res = [num * 2 for num, char in pairs]; print(res)
```

# Data Structures

```python
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
print("total apples: ", fruits.count('apple'))

print("Total Tangerine", fruits.count('tangerine'))

print("index of banana", fruits.index('banana'))

fruits.reverse()
fruits
```

```python
stack = [3, 4, 5]
print(stack)
stack.append(6)
print(stack)
stack.append(7)
print(stack)
stack.pop()
print(stack)
stack.pop()
print(stack)
stack.pop()
print(stack)
```

```python
from collections import deque
queue = deque(["Eric", "John", "Michael"]); queue
queue.append("Terry")
print(queue)
queue.popleft()
print(queue)
```

```python
squares = list(map(lambda x: x**2, range(10))); print(squares)
```

```python
squares = [x**2 for x in range(10)]; print(squares)
```

```python
# listcomp combines the elements of two lists if they are not equal:
[(x,y) for x in [1,2,3] for y in [3,1,4] if x !=y]
```

```python
vec = [-4, -2, 0, 2, 4]
# create a new list with the values doubled
doubled = [x*2 for x in vec];print(vec);print(doubled)
```

```python
# Filter the list to exclude negative numbers
nonNeg = [x for x in vec if x >= 0];print(nonNeg)
```

```python
# Apply a function to all the elements
abs = [abs(x) for x in vec]; print(abs)
```

```python
# Call a method on each element
freshFruit = [' banana ', ' loganberry ', ' passion fruit ']
[x.strip() for x in freshFruit]
```

```python
# Create a list of 2-tuples like (number, square)
# the tuple must be parenthesized, otherwise an error is raised
two_tuples = [(x, x**2) for x in range(10)]; print(two_tuples)
```

```python
# flatten a list using a listcomp with two 'for'
vec = [[1,2,3],[3, 4,5], [6,7,8]]
flattern = [num for row in vec for num in row ]; flattern
```

```python
# List comprehensions can contain complex expressions and nested functions:
from math import pi
[str(round(pi, i)) for i in range(1, 6)]
```

```python
# Consider the following example of a 3x4 matrix implemented as a list of 3 lists of length 4:

matrix = [
    [1,2,3,4],
    [5,6,7,8],
    [9,10,11,12]
]
```

```python
# The following list comprehension will transpose rows and columns:
[[row[i] for row in matrix] for i in range(4)]
```

```python
# In the real world, you should prefer built-in functions to complex flow statements. The zip() function would do a great job for this use case:

list(zip(*matrix))
```

### Unpacking in Lists and List Comprehensions

```python
x = [1,2,3,4]
[0, *x, 5,6,7]
```

This only works if the expression following the * evaluates to an iterable object; trying to unpack a non-iterable object will raise an exception:
```
x = 1
[0, *x, 2, 3, 4]
Traceback (most recent call last):
  File "<python-input-1>", line 1, in <module>
    [0, *x, 2, 3, 4]
TypeError: Value after * must be an iterable, not int
```

```python
# Unpacking can also be used in list comprehensions, as a way to build a new list representing the concatenation of an arbitrary number of iterables:
x = [
    [1,2,3],
    [4,5,6],
    [],
    [7],
    [8,9]
]

# To flatten the list using a list comprehension, you need nested for loops
# flat_x = [item for sublist in x for item in sublist]
flat_x = [num for row in x for num in row]
print(flat_x)
```

```python
x = [[1, 2, 3], [4, 5, 6], [], [7], [8, 9]]
[*element for element in x]
```

```python
x = [
    [1,2,3],
    'cat',
    {'spam': 'eggs'}
]
# [*elements for elements in x] -> python 3.16 0a0
[num for row in x for num in row]
```

## 4. Dict Comprehensions → Automatic Label Makers 🏷️

```python
numbers = [1,2,3,4]; print(numbers)

squares = {x:x*x for x in numbers}; print(squares)
```

# 5. Lambda → Mini Functions ⚡

```python
# Normal function
def square(x):
  return x*x
print(square(25))
```

```python
# Using lamda function

cubes = lambda x: x*x; cubes(3)
```

```python
add = lambda x, y: x * y; add(3, 8)
```
