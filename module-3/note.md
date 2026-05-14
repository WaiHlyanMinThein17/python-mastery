# Module 3 — Boolean Values, Conditionals, Loops, Lists and Bitwise Operations

**Course:** Python Essentials 1 (edube.org) · **Certification:** PCEP · **Status:** In Progress

## Boolean Values

- Only two values: `True` and `False` — capital first letter required
- Internally, `True == 1` and `False == 0`
- Any value can be evaluated as a boolean (truthy/falsy)

| Falsy (evaluates to False) | Truthy (evaluates to True) |
|----------------------------|----------------------------|
| `0`, `0.0`                 | Any non-zero number        |
| `""` (empty string)        | Any non-empty string       |
| `[]` (empty list)          | Any non-empty list         |
| `None`                     | Any object                 |

## Comparison Operators

| Operator | Meaning               | Example         |
|----------|-----------------------|-----------------|
| `==`     | Equal to              | `5 == 5` → True |
| `!=`     | Not equal to          | `5 != 3` → True |
| `>`      | Greater than          | `5 > 3` → True  |
| `<`      | Less than             | `3 < 5` → True  |
| `>=`     | Greater than or equal | `5 >= 5` → True |
| `<=`     | Less than or equal    | `3 <= 5` → True |

- `=` is assignment, `==` is comparison — common mistake

## Logical Operators

| Operator | Meaning                      | Example                  |
|----------|------------------------------|--------------------------|
| `and`    | True if BOTH sides are true  | `True and False` → False |
| `or`     | True if AT LEAST ONE is true | `True or False` → True   |
| `not`    | Reverses the boolean value   | `not True` → False       |

```python
age = 20
if age >= 18 and age < 65:
    print("Working age")
```

- Short-circuit evaluation: `and` stops at first False, `or` stops at first True
- Precedence: `not` > `and` > `or`

## Conditional Execution — if / elif / else

```python
if condition:
    # runs if condition is True
elif another_condition:
    # runs if above is False and this is True
else:
    # runs if all above are False
```

```python
score = 85

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
else:
    print("F")
```

- Indentation defines the block — Python uses 4 spaces (no curly braces)
- `elif` = "else if" — can have as many as needed
- `else` is optional
- Only one branch executes — the first one whose condition is True

## Loops — while

```python
i = 0
while i < 5:
    print(i)
    i += 1          # don't forget to update — or infinite loop!
```

- Condition is checked before each iteration
- `break` — exit the loop immediately
- `continue` — skip the rest of this iteration, go to next
- `else` after while — runs when condition becomes False (not on break)

## Loops — for

```python
for i in range(5):          # 0 1 2 3 4
    print(i)

for i in range(1, 6):       # 1 2 3 4 5
    print(i)

for i in range(0, 10, 2):   # 0 2 4 6 8
    print(i)

for i in range(10, 0, -1):  # 10 9 8 ... 1
    print(i)
```

- `range(stop)` — 0 to stop-1
- `range(start, stop)` — start to stop-1
- `range(start, stop, step)` — with custom step
- `break` and `continue` work the same as in while

## Lists

```python
my_list = [1, 2, 3, 4, 5]
mixed   = [1, "hello", True, 3.14]   # lists can mix types
empty   = []
```

- Ordered, mutable (can be changed), allows duplicates
- Zero-indexed — first element is index 0
- Negative indexing: `-1` = last element, `-2` = second to last

## List Indexing and Slicing

```python
lst = [10, 20, 30, 40, 50]

lst[0]          # 10 (first)
lst[-1]         # 50 (last)
lst[1:3]        # [20, 30] (index 1 up to but not including 3)
lst[:3]         # [10, 20, 30] (from start)
lst[2:]         # [30, 40, 50] (to end)
lst[:]          # [10, 20, 30, 40, 50] (full copy)
lst[::2]        # [10, 30, 50] (every 2nd element)
```

## List Methods

| Method         | Description                           | Example             |
|----------------|---------------------------------------|---------------------|
| `append(x)`    | Add x to end                          | `lst.append(6)`     |
| `insert(i, x)` | Insert x at index i                   | `lst.insert(0, 99)` |
| `remove(x)`    | Remove first occurrence of x          | `lst.remove(3)`     |
| `pop(i)`       | Remove and return element at index i  | `lst.pop()`         |
| `sort()`       | Sort in place ascending               | `lst.sort()`        |
| `reverse()`    | Reverse in place                      | `lst.reverse()`     |
| `index(x)`     | Return index of first occurrence of x | `lst.index(3)`      |
| `count(x)`     | Count occurrences of x                | `lst.count(2)`      |

```python
len(lst)            # number of elements
x in lst            # True if x is in lst
x not in lst        # True if x is not in lst
lst1 + lst2         # concatenate two lists
lst * 3             # repeat list 3 times
```

## List Processing with Loops

```python
# Iterate over elements
for item in my_list:
    print(item)

# Iterate with index
for i in range(len(my_list)):
    print(i, my_list[i])

# Sum all elements
total = 0
for item in my_list:
    total += item

# Find maximum
max_val = my_list[0]
for item in my_list:
    if item > max_val:
        max_val = item
```

## Bitwise Operators

| Operator | Name             | Example  | Result |
|----------|------------------|----------|--------|
| `&`      | AND              | `5 & 3`  | `1`    |
| `\|`     | OR               | `5 \| 3` | `7`    |
| `^`      | XOR              | `5 ^ 3`  | `6`    |
| `~`      | NOT (complement) | `~5`     | `-6`   |
| `<<`     | Left shift       | `5 << 1` | `10`   |
| `>>`     | Right shift      | `5 >> 1` | `2`    |

```python
# How & works:
# 5 = 0101
# 3 = 0011
# &   0001 = 1

# How | works:
# 5 = 0101
# 3 = 0011
# |   0111 = 7
```

- Bitwise operators work on the binary representation of integers
- Left shift (`<<`) multiplies by 2 per shift: `5 << 1 = 10`
- Right shift (`>>`) divides by 2 per shift: `5 >> 1 = 2`
- `~x` = `-(x + 1)`

## Key Takeaways

- True == 1 and False == 0 in Python
- 0, empty string, empty list and None are all falsy
- = is assignment, == is comparison
- Logical operator precedence: not > and > or
- Indentation (4 spaces) defines code blocks — not curly braces
- range(start, stop, step) — stop is excluded
- Lists are zero-indexed, support negative indexing and slicing
- break exits a loop, continue skips to next iteration
- Bitwise & = AND, | = OR, ^ = XOR, ~ = NOT, << = left shift, >> = right shift