# Module 4 — Functions, Tuples, Dictionaries, Data Processing and Exceptions

**Course:** Python Essentials 1 (edube.org) · **Certification:** PCEP · **Status:** In Progress

## Functions

A function is a named, reusable block of code that performs a specific task.

```python
def function_name(parameters):
    """optional docstring"""
    # body
    return value
```

```python
def greet(name):
    print("Hello,", name)

def add(a, b):
    return a + b

result = add(3, 5)   # 8
```

- Defined with `def` keyword
- `return` sends a value back to the caller and exits the function
- A function with no `return` statement returns `None`
- Functions must be defined before they are called

## Parameters and Arguments

```python
# Positional arguments — order matters
def subtract(a, b):
    return a - b

subtract(10, 3)       # a=10, b=3 → 7

# Keyword arguments — order does not matter
subtract(b=3, a=10)   # still 7

# Default parameter values
def greet(name, greeting="Hello"):
    print(greeting + ",", name)

greet("Wai")              # Hello, Wai
greet("Wai", "Hi")        # Hi, Wai

# Returning multiple values (as a tuple)
def min_max(lst):
    return min(lst), max(lst)

lo, hi = min_max([3, 1, 4, 1, 5])
```

- Default parameters must come after non-default parameters
- Keyword arguments can be passed in any order

## Scope — Local vs Global

```python
x = 10               # global variable

def my_func():
    x = 99           # local variable — does NOT change global x
    print(x)         # 99

my_func()
print(x)             # 10 — unchanged

# To modify global variable inside a function:
def change_global():
    global x
    x = 99
```

- Variables created inside a function are local — not visible outside
- Functions can READ global variables but cannot WRITE without `global`
- Avoid using `global` — pass values as arguments instead

## Tuples

```python
my_tuple = (1, 2, 3)
single   = (42,)          # one-element tuple — comma is required
empty    = ()
no_parens = 1, 2, 3       # parentheses are optional
```

- Ordered and indexed like lists — but **immutable** (cannot be changed)
- Faster than lists and safe from accidental modification

```python
t = (10, 20, 30)
t[0]              # 10
t[-1]             # 30
t[0:2]            # (10, 20)
len(t)            # 3
10 in t           # True

# Tuple unpacking
x, y, z = (1, 2, 3)
a, b = b, a       # swap using tuple packing/unpacking
```

| Feature  | List              | Tuple                        |
|----------|-------------------|------------------------------|
| Syntax   | `[1, 2, 3]`       | `(1, 2, 3)`                  |
| Mutable? | Yes               | No                           |
| Methods  | Many              | Only index() and count()     |
| Use case | Data that changes | Fixed data, function returns |

## Dictionaries

```python
my_dict = {"name": "Wai", "age": 23, "city": "Macon"}
empty   = {}
```

- Stores key-value pairs
- Keys must be unique and immutable (strings, numbers, tuples)
- Values can be anything
- Ordered by insertion in Python 3.7+

```python
# Access
my_dict["name"]               # "Wai"
my_dict.get("age")            # 23
my_dict.get("phone", "N/A")   # "N/A" (default if key missing)

# Add or update
my_dict["email"] = "wai@email.com"
my_dict["age"] = 24

# Delete
del my_dict["city"]
my_dict.pop("age")            # removes and returns the value

# Check key
"name" in my_dict             # True
```

## Dictionary Methods

| Method            | Description                                    |
|-------------------|------------------------------------------------|
| `keys()`          | Returns all keys                               |
| `values()`        | Returns all values                             |
| `items()`         | Returns all key-value pairs as tuples          |
| `get(k, default)` | Returns value for key k, or default if missing |
| `pop(k)`          | Remove and return value for key k              |
| `update(d)`       | Merge another dictionary into this one         |

```python
# Iterating
for key, value in my_dict.items():
    print(key, "→", value)
```

## Data Processing Patterns

```python
# List comprehension
squares = [x ** 2 for x in range(1, 6)]         # [1, 4, 9, 16, 25]
evens   = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]

# Useful built-in functions
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

sum(numbers)      # 31
min(numbers)      # 1
max(numbers)      # 9
len(numbers)      # 8
sorted(numbers)   # returns new sorted list — original unchanged
numbers.sort()    # sorts in place — modifies original
```

## Exceptions

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
except ValueError as e:
    print("Value error:", e)
except:
    print("Something went wrong")   # catches anything — use sparingly
else:
    print("Success:", result)       # runs only if no exception
finally:
    print("Done")                   # always runs
```

## Common Exception Types

| Exception           | Cause                                  |
|---------------------|----------------------------------------|
| `ZeroDivisionError` | Division by zero                       |
| `ValueError`        | Wrong value type e.g. int("hello")     |
| `TypeError`         | Wrong data type e.g. "5" + 5           |
| `IndexError`        | Index out of range e.g. lst[100]       |
| `KeyError`          | Key not found in dictionary            |
| `NameError`         | Variable not defined                   |
| `AttributeError`    | Object has no such attribute or method |
| `FileNotFoundError` | File does not exist                    |

## Raising Exceptions

```python
def divide(a, b):
    if b == 0:
        raise ValueError("Denominator cannot be zero")
    return a / b
```

## Key Takeaways

- Define functions with `def` — call them by name with arguments
- A function with no return statement returns None
- Default parameters must come after positional parameters
- Local variables only exist inside their function
- Use `global` sparingly — prefer passing arguments
- Tuples are immutable — use trailing comma for single-element tuples: `(42,)`
- Dictionaries store key-value pairs — keys must be unique and immutable
- Use .get() to safely access dictionary keys without risking KeyError
- try/except catches exceptions — finally always runs
- Catch specific exceptions — avoid bare `except:` clauses
- raise creates your own exceptions