# Python Basics - Interview Questions & Answers

## 1. What is Python and what are its key features?

**Answer:** Python is a high-level, interpreted, object-oriented programming language created by Guido van Rossum in 1991. It emphasizes code readability and uses indentation to define code blocks.

**Key Features:**
- **Easy to learn:** Simple syntax similar to English
- **Interpreted:** No compilation needed
- **Dynamically typed:** No need to declare variable types
- **Cross-platform:** Runs on Windows, Linux, Mac
- **Extensive libraries:** Rich standard library and third-party packages
- **Multiple paradigms:** Supports OOP, functional, and procedural programming
- **Open source:** Free to use and distribute

---

## 2. What are the key differences between Python 2 and Python 3?

**Answer:**

| Feature | Python 2 | Python 3 |
|---------|----------|----------|
| Print | Statement: `print "Hello"` | Function: `print("Hello")` |
| Division | Integer division: `5/2 = 2` | Float division: `5/2 = 2.5` |
| Unicode | ASCII default | Unicode (UTF-8) default |
| Range | `range()` and `xrange()` | Only `range()` (like xrange) |
| Error Handling | `except Exception, e:` | `except Exception as e:` |
| Input | `raw_input()` and `input()` | Only `input()` |

**Note:** Python 2 reached end-of-life on January 1, 2020. Python 3 is the current and future version.

---

## 3. What are Python's built-in data types?

**Answer:**

**Numeric Types:**
- `int`: Integers (e.g., 5, -10, 1000)
- `float`: Floating-point numbers (e.g., 3.14, -2.5)
- `complex`: Complex numbers (e.g., 3+4j)

**Sequence Types:**
- `str`: Strings (e.g., "Hello", 'Python')
- `list`: Mutable ordered sequences (e.g., [1, 2, 3])
- `tuple`: Immutable ordered sequences (e.g., (1, 2, 3))

**Mapping Type:**
- `dict`: Key-value pairs (e.g., {"name": "John", "age": 30})

**Set Types:**
- `set`: Unordered unique elements (e.g., {1, 2, 3})
- `frozenset`: Immutable set

**Boolean Type:**
- `bool`: True or False

---

## 4. What is the difference between a list and a tuple?

**Answer:**

| Feature | List | Tuple |
|---------|------|-------|
| Mutability | Mutable (can modify) | Immutable (cannot modify) |
| Syntax | Square brackets `[1, 2, 3]` | Parentheses `(1, 2, 3)` |
| Performance | Slower | Faster (due to immutability) |
| Memory | Uses more memory | Uses less memory |
| Methods | Many methods (append, remove, etc.) | Limited methods (count, index) |
| Use Case | Dynamic collections | Fixed data, dictionary keys |

**Example:** Lists are used when data changes frequently, tuples for constant data like coordinates (x, y) or database records.

---

## 5. What are Python decorators?

**Answer:** Decorators are functions that modify the behavior of other functions or methods without changing their source code. They use the `@decorator_name` syntax above function definitions.

**Common Uses:**
- **Logging:** Track function calls
- **Authentication:** Check user permissions
- **Timing:** Measure execution time
- **Caching:** Store function results (memoization)
- **Validation:** Check input parameters

**Simple example:** `@login_required` decorator checks if user is logged in before executing a function.

---

## 6. What is the difference between `==` and `is`?

**Answer:**

- **`==`** compares **values** (checks if contents are equal)
- **`is`** compares **identity** (checks if same object in memory)

**Example:**
- `a == b` → "Do a and b have the same value?"
- `a is b` → "Are a and b the exact same object?"

**Interview Tip:** Use `==` for value comparison, use `is` only for singleton objects like `None`: `if x is None:`

---

## 7. What are *args and **kwargs?

**Answer:**

- **`*args`**: Passes variable number of positional arguments as a tuple
- **`**kwargs`**: Passes variable number of keyword arguments as a dictionary

**Use Cases:**
- When you don't know how many arguments will be passed
- Creating flexible functions that accept any number of parameters
- Wrapper functions and decorators

**Example usage:** `def log(level, *args, **kwargs)` - accepts any number of messages and configuration options.

---

## 8. What is list comprehension?

**Answer:** List comprehension is a concise way to create lists in a single line. It's more readable and faster than traditional loops.

**Syntax:** `[expression for item in iterable if condition]`

**Examples:**
- Create squares: `[x**2 for x in range(10)]`
- Filter even numbers: `[x for x in range(20) if x % 2 == 0]`
- Flatten matrix: `[item for row in matrix for item in row]`

**Benefits:** More Pythonic, faster execution, less code.

---

## 9. What is the difference between `append()` and `extend()`?

**Answer:**

- **`append(item)`**: Adds single element to end of list (item added as-is)
- **`extend(iterable)`**: Adds each element from iterable to list

**Example:**
- `[1,2].append([3,4])` → `[1, 2, [3, 4]]` (nested list)
- `[1,2].extend([3,4])` → `[1, 2, 3, 4]` (flattened)

**Interview Tip:** Use `append()` to add one item, `extend()` to add multiple items.

---

## 10. What is a lambda function?

**Answer:** Lambda functions are small anonymous functions defined with the `lambda` keyword. They can have multiple arguments but only one expression.

**Syntax:** `lambda arguments: expression`

**Use Cases:**
- With `map()`, `filter()`, `reduce()`
- As key functions in `sorted()`
- Simple operations without defining full function
- Short-lived functions passed as arguments

**Example:** `sorted(students, key=lambda x: x['grade'])` - sort students by grade.

---

## 11. What is the difference between `remove()`, `del`, and `pop()`?

**Answer:**

| Method | Purpose | Returns Value | Usage |
|--------|---------|---------------|-------|
| `remove(value)` | Removes first occurrence of value | No | `list.remove(3)` |
| `del` | Removes item at index | No | `del list[2]` |
| `pop(index)` | Removes and returns item | Yes | `item = list.pop(0)` |

**Interview Tip:** Use `pop()` when you need the removed value, `remove()` when you know the value but not position, `del` when you know the position.

---

## 12. What are Python generators and why use them?

**Answer:** Generators are functions that use `yield` instead of `return` to produce values one at a time. They create iterators in a memory-efficient way.

**Benefits:**
- **Memory efficient:** Generate values on-demand, don't store all in memory
- **Better for large datasets:** Can handle infinite sequences
- **Lazy evaluation:** Values computed only when needed

**Use Cases:**
- Reading large files line by line
- Generating infinite sequences (Fibonacci)
- Data pipelines
- Processing streams

**Syntax:** Replace `return` with `yield` in function.

---

## 13. What is the difference between shallow copy and deep copy?

**Answer:**

- **Shallow Copy:** Creates new object but references same nested objects
- **Deep Copy:** Creates completely independent copy with new nested objects

**When it matters:** For nested structures (lists of lists, objects containing objects).

**Example scenario:** If you shallow copy a list of lists and modify inner list, original is affected. Deep copy prevents this.

**Import:** `import copy` then use `copy.copy()` (shallow) or `copy.deepcopy()` (deep).

---

## 14. What are Python's naming conventions (PEP 8)?

**Answer:**

| Type | Convention | Example |
|------|-----------|---------|
| Variables | lowercase_with_underscores | `user_name`, `total_count` |
| Functions | lowercase_with_underscores | `calculate_total()` |
| Classes | CapitalizedWords (PascalCase) | `UserProfile`, `DataManager` |
| Constants | UPPERCASE_WITH_UNDERSCORES | `MAX_SIZE`, `API_KEY` |
| Private | _single_leading_underscore | `_internal_method` |
| Modules | lowercase (no underscores preferred) | `utils.py`, `database.py` |

**Interview Tip:** Following PEP 8 shows you write professional, maintainable code.

---

## 15. What is the `self` keyword in Python?

**Answer:** `self` represents the instance of the class. It's used to access instance variables and methods within class methods.

**Key Points:**
- First parameter of instance methods
- Not a keyword, just a strong convention (could use any name, but don't)
- Automatically passed when calling methods on objects
- Required to differentiate instance variables from local variables

**Why needed:** Python doesn't implicitly know which object's data to access, so we explicitly pass `self`.

---

## 16. What is the difference between `break`, `continue`, and `pass`?

**Answer:**

- **`break`**: Exits the loop completely
- **`continue`**: Skips current iteration, continues with next
- **`pass`**: Does nothing, placeholder for future code

**Use Cases:**
- `break`: Stop searching when item found
- `continue`: Skip invalid items in processing
- `pass`: Define empty classes/functions to implement later

---

## 17. What are mutable and immutable objects in Python?

**Answer:**

**Mutable (can be changed):**
- list, dict, set, bytearray
- Can modify content without creating new object

**Immutable (cannot be changed):**
- int, float, string, tuple, frozenset, bool
- Any modification creates new object

**Why it matters:**
- Affects function parameters (mutable objects can be modified inside functions)
- Dictionary keys must be immutable
- Performance implications

---

## 18. What is the difference between `range()` and `xrange()`?

**Answer:**

**Python 3:** Only `range()` exists (behaves like old `xrange()`)
- Returns iterator object
- Memory efficient
- Generates values on demand

**Python 2:**
- `range()` returns list (all values in memory)
- `xrange()` returns iterator (one value at a time)

**Interview Tip:** In Python 3, `range()` is lazy and memory-efficient by default.

---

## 19. What is the purpose of `__init__` method?

**Answer:** `__init__` is the constructor method automatically called when creating a new object. It initializes object's attributes.

**Key Points:**
- Not the first method called (that's `__new__`)
- Used to set up initial state
- Can accept parameters beyond `self`
- Optional (Python provides default if not defined)

**Purpose:** Set up instance variables and perform any setup needed for the object.

---

## 20. What are Python modules and packages?

**Answer:**

**Module:** Single Python file (.py) containing functions, classes, variables
- Example: `math.py`, `datetime.py`
- Import: `import math`

**Package:** Directory containing multiple modules and an `__init__.py` file
- Organizes related modules
- Example: Django, NumPy packages

**Benefits:**
- Code reusability
- Better organization
- Namespace management
- Easier maintenance

---

## 21. What is the difference between `import module` and `from module import`?

**Answer:**

**`import module`:**
- Imports entire module
- Access: `module.function()`
- Keeps namespace clean

**`from module import function`:**
- Import specific items
- Access: `function()` directly
- Cleaner syntax but can cause name conflicts

**Best Practice:** Use `import module` to avoid namespace pollution, use `from` for frequently used items.

---

## 22. Explain Python's exception handling.

**Answer:**

**Structure:**
```
try: # Code that might raise exception
except ExceptionType: # Handle specific exception
else: # Runs if no exception
finally: # Always runs (cleanup)
```

**Best Practices:**
- Catch specific exceptions, not bare `except:`
- Use `finally` for cleanup (close files, connections)
- Don't silence exceptions without good reason
- Custom exceptions inherit from `Exception` class

---

## 23. What is the difference between `strip()`, `lstrip()`, and `rstrip()`?

**Answer:**

- **`strip()`**: Removes whitespace from both ends
- **`lstrip()`**: Removes whitespace from left (start)
- **`rstrip()`**: Removes whitespace from right (end)

**Default:** Removes spaces, tabs, newlines
**Custom:** Can specify characters to remove: `'###Hello###'.strip('#')` → `'Hello'`

---

## 24. What are Python's logical operators?

**Answer:**

- **`and`**: Returns True if both conditions true
- **`or`**: Returns True if at least one condition true
- **`not`**: Reverses boolean value

**Short-circuit evaluation:** Python stops evaluating as soon as result is determined.

---

## 25. What is slicing in Python?

**Answer:** Slicing extracts portions of sequences (strings, lists, tuples) using `[start:stop:step]` syntax.

**Examples:**
- `list[2:5]`: Items from index 2 to 4
- `list[:3]`: First 3 items
- `list[3:]`: From index 3 to end
- `list[-1]`: Last item
- `list[::-1]`: Reverse sequence
- `list[::2]`: Every second item

**Interview Tip:** Remember slicing creates a new object (copy).

---

## 26. What is the difference between local and global variables?

**Answer:**

**Local Variables:**
- Declared inside function
- Accessible only within function
- Created when function called, destroyed when function ends
- Cannot be accessed outside function

**Global Variables:**
- Declared outside all functions
- Accessible throughout program
- Exist for entire program lifetime
- Can be accessed by any function

**Modifying global variable in function:** Use `global` keyword

---

## 27. What is PEP 8?

**Answer:** PEP 8 is Python Enhancement Proposal that provides coding conventions for Python code.

**Key Guidelines:**
- Use 4 spaces for indentation
- Maximum line length of 79 characters
- Blank lines to separate functions and classes
- Imports at top of file
- Naming conventions (lowercase for functions, CamelCase for classes)
- Comments should be complete sentences
- Use docstrings for functions and classes

**Why follow PEP 8:** Makes code readable and consistent across projects.

---

## 28. What are Python's membership operators?

**Answer:**

**`in` operator:**
- Returns True if value exists in sequence
- Example: `'a' in 'apple'` → True

**`not in` operator:**
- Returns True if value doesn't exist in sequence
- Example: `'z' not in 'apple'` → True

**Works with:** strings, lists, tuples, sets, dictionaries (checks keys)

---

## 29. What are Python's identity operators?

**Answer:**

**`is` operator:**
- Returns True if variables point to same object
- Checks memory location

**`is not` operator:**
- Returns True if variables point to different objects

**Difference from `==`:** `==` compares values, `is` compares identities

---

## 30. What is the difference between `type()` and `isinstance()`?

**Answer:**

**type():**
- Returns exact type of object
- Doesn't consider inheritance
- Returns type object

**isinstance():**
- Checks if object is instance of class or subclass
- Considers inheritance
- Returns Boolean
- Recommended for type checking

**Example:** If B inherits from A, `isinstance(b, A)` returns True, but `type(b) == A` returns False.

---

## 31. What is the `pass` statement?

**Answer:** `pass` is a null statement that does nothing. It's a placeholder.

**Use Cases:**
- Empty functions or classes (to be implemented later)
- Empty control flow statements
- Syntactically required but no action needed

**Difference from `continue`:** `continue` skips current iteration, `pass` does nothing and continues execution.

---

## 32. What are docstrings?

**Answer:** Docstrings are documentation strings that describe what function, class, or module does.

**Syntax:** Triple quotes `""" """` or `''' '''`

**Purpose:**
- Document code
- Auto-generate documentation
- Accessible via `__doc__` attribute
- Used by help() function

**Best Practice:** First line should be summary, followed by blank line, then detailed description.

---

## 33. What is the difference between `is` and `==`?

**Answer:**

**`is` operator:**
- Compares object identity (memory location)
- Checks if two variables refer to same object
- Uses `id()` function internally

**`==` operator:**
- Compares object values
- Checks if contents are equal
- Calls `__eq__()` method

**When to use `is`:** Only with `None`, `True`, `False` (singletons)

---

## 34. What are Python's bitwise operators?

**Answer:**

**Operators:**
- `&` (AND): Sets bit to 1 if both bits are 1
- `|` (OR): Sets bit to 1 if one of bits is 1
- `^` (XOR): Sets bit to 1 if bits are different
- `~` (NOT): Inverts all bits
- `<<` (Left shift): Shifts bits left
- `>>` (Right shift): Shifts bits right

**Use Cases:** Low-level programming, optimization, flags/permissions.

---

## 35. What is the `with` statement?

**Answer:** `with` statement simplifies exception handling by encapsulating common preparation and cleanup tasks.

**Purpose:**
- Ensures proper resource acquisition and release
- Automatically handles exceptions
- No need for explicit try-finally

**Common Use:** File operations, database connections, locks

**Advantage:** Resources automatically closed even if error occurs.

---

## 36. What is the `global` keyword?

**Answer:** `global` keyword allows modifying global variable inside a function.

**Without global:** Assignment creates new local variable
**With global:** Modification affects global variable

**Best Practice:** Avoid global variables when possible; use function parameters and return values instead.

---

## 37. What is the `nonlocal` keyword?

**Answer:** `nonlocal` keyword refers to variable in nearest enclosing scope (not global).

**Use Case:** Nested functions where inner function needs to modify outer function's variable

**Difference from global:** Refers to enclosing function scope, not module-level scope.

---

## 38. What are Python packages?

**Answer:** Package is a directory containing Python modules and an `__init__.py` file.

**Structure:**
- Organize related modules
- Hierarchical structure
- Can contain sub-packages

**`__init__.py`:**
- Makes directory a package
- Can be empty or contain initialization code
- Executed when package imported

**Import syntax:** `from package import module` or `import package.module`

---

## 39. What is `__name__` == `"__main__"`?

**Answer:** This condition checks if Python file is being run directly or being imported.

**Behavior:**
- If run directly: `__name__` is `"__main__"`
- If imported: `__name__` is module name

**Use Case:** Write code that executes only when file run directly, not when imported.

**Best Practice:** Put test code or main execution inside this condition.

---

## 40. What are Python's string formatting methods?

**Answer:**

**Old style (%):**
- `"Hello %s" % name`
- Similar to C printf

**str.format():**
- `"Hello {}".format(name)`
- More powerful and flexible

**f-strings (Python 3.6+):**
- `f"Hello {name}"`
- Fastest and most readable
- Recommended modern approach

**Interview Tip:** f-strings are the preferred method for string formatting in modern Python.

---
