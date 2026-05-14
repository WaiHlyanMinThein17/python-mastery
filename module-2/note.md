# Module 2 — Data Types, Variables, Basic I/O and Operators

**Course:** Python Essentials 1 (edube.org) · **Certification:** PCEP · **Status:** In Progress

## Data Types

Python has several built-in data types. The four core types for PCEP:

| Type    | Example               | Description                                    |
|---------|-----------------------|------------------------------------------------|
| `int`   | `42`, `-7`, `0`       | Whole numbers, positive or negative            |
| `float` | `3.14`, `-0.5`, `1.0` | Numbers with a decimal point                   |
| `str`   | `"hello"`, `'world'`  | Text wrapped in single or double quotes        |
| `bool`  | `True`, `False`       | Logical values — capital first letter required |

```python
type(42)        # int
type(3.14)      # float
type("hello")   # str
type(True)      # bool
```

- Python automatically detects the type — no need to declare it
- `True` and `False` are case sensitive — `true` is not valid
- Integer division of two ints can produce a float: `7 / 2 = 3.5`

## Type Conversion

```python
int("42")       # str to int → 42
float("3.14")   # str to float → 3.14
str(100)        # int to str → "100"
int(3.9)        # float to int → 3 (truncates, does NOT round)
bool(0)         # 0 → False
bool(1)         # any non-zero → True
bool("")        # empty string → False
bool("hello")   # non-empty string → True
```

## Variables

- A variable is a named container that stores a value
- Created with the assignment operator `=`
- No need to declare type — Python infers it
- Variable names are case sensitive: `name` and `Name` are different
- Names can contain letters, digits and underscores — cannot start with a digit
- Convention: use `snake_case` for variable names

```python
name = "Wai"           # str
age = 23               # int
gpa = 3.85             # float
is_student = True      # bool

# Multiple assignment
x = y = z = 0

# Swap values
a, b = 10, 20
a, b = b, a            # a=20, b=10
```

## Arithmetic Operators

| Operator | Name           | Example   | Result               |
|----------|----------------|-----------|----------------------|
| `+`      | Addition       | `5 + 3`   | `8`                  |
| `-`      | Subtraction    | `5 - 3`   | `2`                  |
| `*`      | Multiplication | `5 * 3`   | `15`                 |
| `/`      | Division       | `7 / 2`   | `3.5` (always float) |
| `//`     | Floor division | `7 // 2`  | `3` (rounds down)    |
| `%`      | Modulo         | `7 % 2`   | `1` (remainder)      |
| `**`     | Exponentiation | `2 ** 10` | `1024`               |
| `-`      | Unary negation | `-x`      | Negates value        |

- `/` always returns a float — even `4 / 2 = 2.0`
- `//` floors toward negative infinity: `-7 // 2 = -4` (not -3)
- `**` has higher precedence than unary `-`: `-2 ** 2 = -4` not `4`
- Any operation involving a float returns a float

## Operator Precedence (highest to lowest)

| Priority    | Operator            | Description                    |
|-------------|---------------------|--------------------------------|
| 1 (highest) | `**`                | Exponentiation (right-to-left) |
| 2           | `+x`, `-x`          | Unary plus and minus           |
| 3           | `*`, `/`, `//`, `%` | Multiplicative                 |
| 4 (lowest)  | `+`, `-`            | Additive                       |

- Use parentheses to override precedence: `(2 + 3) * 4 = 20`
- Left-to-right for same-level operators — except `**` which is right-to-left

## String Operators

```python
greeting = "Hello" + " " + "World"   # concatenation → "Hello World"
repeat   = "ha" * 3                  # repetition → "hahaha"
```

- `+` concatenates strings — both sides must be strings
- `*` repeats a string — one side must be int
- Cannot add a string and a number: `"age: " + 23` raises TypeError

## Basic Input — input()

```python
name = input("What is your name? ")   # shows prompt, waits for user
print("Hello,", name)

# input() always returns a string — convert before arithmetic
age = int(input("Enter your age: "))
```

- `input()` always returns a **string** — even if the user types a number
- Always convert input to the correct type before doing math

## Basic Output — print()

```python
print("Hello")                       # basic output
print("Hello", "World")              # multiple args — space separated
print("Hello", "World", sep=", ")    # custom separator → Hello, World
print("Hello", end="")               # suppress newline
print(f"My name is {name}")          # f-string
print("Value:", 42)                  # mix strings and numbers
```

- Default separator between arguments is a space
- Default end character is a newline `\n`
- f-strings: prefix with `f`, embed expressions in `{}`

## Shorthand Assignment Operators

| Shorthand | Equivalent   |
|-----------|--------------|
| `x += 5`  | `x = x + 5`  |
| `x -= 5`  | `x = x - 5`  |
| `x *= 5`  | `x = x * 5`  |
| `x /= 5`  | `x = x / 5`  |
| `x //= 5` | `x = x // 5` |
| `x %= 5`  | `x = x % 5`  |
| `x **= 2` | `x = x ** 2` |

## Key Takeaways

- Four core types: int, float, str, bool
- type() checks the type of any value
- int() truncates floats — it does NOT round
- / always returns float, // always returns int (floored)
- ** is right-associative: 2 ** 3 ** 2 = 2 ** 9 = 512
- input() always returns a string — convert before arithmetic
- print() sep and end parameters control formatting
- Cannot concatenate str and int directly — use str() or f-strings