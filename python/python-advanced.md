# Python Advanced - Interview Questions & Answers

## 1. What is the Global Interpreter Lock (GIL)?

**Answer:** The GIL (Global Interpreter Lock) is a mutex that allows only one thread to execute Python bytecode at a time, even on multi-core processors.

**Key Points:**
- **Purpose:** Protects Python object memory from race conditions
- **Impact on multi-threading:** Makes CPU-bound multi-threaded programs run on single core
- **I/O operations:** GIL released during I/O, so multi-threading works well for I/O-bound tasks
- **Workaround:** Use multiprocessing (separate processes) for CPU-bound tasks

**Interview Insight:** GIL is why Python threads don't provide true parallelism for CPU-intensive tasks, but they're still useful for I/O-bound operations like network requests or file operations.

---

## 2. What are metaclasses in Python?

**Answer:** Metaclasses are "classes of classes" that define how classes behave. A class is an instance of a metaclass. The default metaclass in Python is `type`.

```python
# Creating a class using type (metaclass)
MyClass = type('MyClass', (object,), {'x': 5, 'greet': lambda self: 'Hello'})
obj = MyClass()
print(obj.x)  # 5
print(obj.greet())  # Hello

# Custom metaclass
class Meta(type):
    def __new__(cls, name, bases, dct):
        # Add a new attribute to every class
        dct['custom_attr'] = 'Added by metaclass'
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    pass

print(MyClass.custom_attr)  # Added by metaclass
```

**Use Cases:**
- ORM frameworks (like Django)
- API validation
- Singleton pattern implementation
- Automatic registration of classes

---

## 3. What is the difference between `@staticmethod` and `@classmethod`?

**Answer:**

```python
class MyClass:
    class_variable = 'I am a class variable'
    
    def instance_method(self):
        return f'Instance method called by {self}'
    
    @classmethod
    def class_method(cls):
        return f'Class method called, can access {cls.class_variable}'
    
    @staticmethod
    def static_method():
        return 'Static method called, cannot access instance or class'

# Usage
obj = MyClass()

# Instance method needs an instance
obj.instance_method()

# Class method receives the class as first argument
MyClass.class_method()  # Can be called on class
obj.class_method()      # Can be called on instance

# Static method doesn't receive instance or class
MyClass.static_method()  # Can be called on class
obj.static_method()      # Can be called on instance
```

| Feature | Instance Method | Class Method | Static Method |
|---------|----------------|--------------|---------------|
| First Parameter | `self` (instance) | `cls` (class) | None |
| Access Instance Data | Yes | No | No |
| Access Class Data | Yes | Yes | No |
| Decorator | None | `@classmethod` | `@staticmethod` |

---

## 4. Explain Python's memory management and garbage collection.

**Answer:**

**Memory Management:**
- Python uses **private heap space** to store objects
- **Reference counting:** Each object keeps track of references to it
- **Garbage collector:** Cleans up circular references

```python
import sys
import gc

# Reference counting
a = []
print(sys.getrefcount(a))  # 2 (one from variable, one from getrefcount)

b = a
print(sys.getrefcount(a))  # 3 (variable a, b, and getrefcount)

# Circular reference
class Node:
    def __init__(self):
        self.ref = None

node1 = Node()
node2 = Node()
node1.ref = node2
node2.ref = node1  # Circular reference

# Manual garbage collection
gc.collect()  # Forces collection

# Check if garbage collection is enabled
print(gc.isenabled())  # True

# Get garbage collection thresholds
print(gc.get_threshold())  # (700, 10, 10)
```

**Three Generations:**
- **Generation 0:** Newly created objects
- **Generation 1:** Objects that survived one GC cycle
- **Generation 2:** Objects that survived multiple GC cycles

---

## 5. What are context managers and the `with` statement?

**Answer:** Context managers handle resource management automatically (setup and cleanup). The `with` statement ensures proper acquisition and release of resources.

```python
# Without context manager
file = open('data.txt', 'r')
try:
    data = file.read()
finally:
    file.close()

# With context manager
with open('data.txt', 'r') as file:
    data = file.read()
# File is automatically closed

# Creating custom context manager
class DatabaseConnection:
    def __enter__(self):
        print('Opening database connection')
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print('Closing database connection')
        if exc_type:
            print(f'Exception occurred: {exc_val}')
        return False  # False = propagate exception, True = suppress

with DatabaseConnection() as db:
    print('Working with database')

# Using contextlib
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    file = open(filename, mode)
    try:
        yield file
    finally:
        file.close()

with file_manager('data.txt', 'r') as f:
    content = f.read()
```

---

## 6. What are descriptors in Python?

**Answer:** Descriptors are objects that define how attributes are accessed using `__get__`, `__set__`, and `__delete__` methods.

```python
class Descriptor:
    def __init__(self, name=None):
        self.name = name
    
    def __get__(self, instance, owner):
        if instance is None:
            return self
        return instance.__dict__.get(self.name)
    
    def __set__(self, instance, value):
        if not isinstance(value, int):
            raise TypeError('Value must be an integer')
        instance.__dict__[self.name] = value
    
    def __delete__(self, instance):
        del instance.__dict__[self.name]

class MyClass:
    age = Descriptor('age')
    
    def __init__(self, age):
        self.age = age

obj = MyClass(25)
print(obj.age)  # 25
obj.age = 30    # Works
# obj.age = "thirty"  # Raises TypeError
```

**Examples of Built-in Descriptors:**
- `@property`
- `@staticmethod`
- `@classmethod`

---

## 7. What is monkey patching?

**Answer:** Monkey patching is dynamically modifying or extending a class or module at runtime.

```python
# Original class
class Calculator:
    def add(self, a, b):
        return a + b

calc = Calculator()
print(calc.add(2, 3))  # 5

# Monkey patching
def new_add(self, a, b):
    print(f"Adding {a} and {b}")
    return a + b

Calculator.add = new_add
print(calc.add(2, 3))  # Prints message and returns 5

# Patching built-in modules
import math
math.pi = 3.14  # Not recommended!
```

**Use Cases:**
- Testing (mocking)
- Quick fixes in third-party libraries
- Adding functionality temporarily

**Cautions:**
- Can make code hard to maintain
- May cause unexpected behavior
- Use with caution in production

---

## 8. Explain Python's method resolution order (MRO).

**Answer:** MRO determines the order in which base classes are searched when looking for a method. Python uses C3 linearization algorithm.

```python
class A:
    def process(self):
        print('A process')

class B(A):
    def process(self):
        print('B process')

class C(A):
    def process(self):
        print('C process')

class D(B, C):
    pass

# Check MRO
print(D.__mro__)
# (<class 'D'>, <class 'B'>, <class 'C'>, <class 'A'>, <class 'object'>)

print(D.mro())
# Same as above

# Method resolution follows MRO
d = D()
d.process()  # B process (B comes before C in MRO)

# Using super() respects MRO
class B(A):
    def process(self):
        print('B process')
        super().process()

class C(A):
    def process(self):
        print('C process')
        super().process()

class D(B, C):
    def process(self):
        print('D process')
        super().process()

d = D()
d.process()
# Output:
# D process
# B process
# C process
# A process
```

---

## 9. What are Python's magic/dunder methods?

**Answer:** Magic methods (double underscore methods) allow you to define behavior for built-in operations.

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    # String representation
    def __repr__(self):
        return f'Vector({self.x}, {self.y})'
    
    def __str__(self):
        return f'({self.x}, {self.y})'
    
    # Arithmetic operations
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)
    
    # Comparison operations
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    def __lt__(self, other):
        return (self.x**2 + self.y**2) < (other.x**2 + other.y**2)
    
    # Container operations
    def __len__(self):
        return 2
    
    def __getitem__(self, index):
        if index == 0:
            return self.x
        elif index == 1:
            return self.y
        raise IndexError('Index out of range')
    
    # Boolean conversion
    def __bool__(self):
        return self.x != 0 or self.y != 0
    
    # Context manager
    def __enter__(self):
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        return False

# Usage
v1 = Vector(1, 2)
v2 = Vector(3, 4)

print(v1 + v2)    # Vector(4, 6)
print(v1 * 3)     # Vector(3, 6)
print(v1 == v2)   # False
print(len(v1))    # 2
print(v1[0])      # 1
```

**Common Magic Methods:**
- `__init__`, `__del__`: Constructor and destructor
- `__str__`, `__repr__`: String representation
- `__add__`, `__sub__`, `__mul__`: Arithmetic operations
- `__eq__`, `__lt__`, `__gt__`: Comparison operations
- `__len__`, `__getitem__`, `__setitem__`: Container operations
- `__call__`: Make object callable
- `__enter__`, `__exit__`: Context manager

---

## 10. What is the difference between `__new__` and `__init__`?

**Answer:**

- `__new__`: Creates and returns a new instance (called first)
- `__init__`: Initializes the instance (called after `__new__`)

```python
class MyClass:
    def __new__(cls, *args, **kwargs):
        print('__new__ called')
        instance = super().__new__(cls)
        return instance
    
    def __init__(self, value):
        print('__init__ called')
        self.value = value

obj = MyClass(42)
# Output:
# __new__ called
# __init__ called

# Singleton pattern using __new__
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

s1 = Singleton()
s2 = Singleton()
print(s1 is s2)  # True (same instance)
```

---

## 11. Explain coroutines and async/await in Python.

**Answer:** Coroutines enable asynchronous programming, allowing you to write concurrent code using `async` and `await` keywords.

```python
import asyncio

# Basic coroutine
async def fetch_data(id):
    print(f'Fetching data {id}...')
    await asyncio.sleep(2)  # Simulate I/O operation
    return f'Data {id}'

# Running coroutine
async def main():
    result = await fetch_data(1)
    print(result)

# asyncio.run(main())

# Concurrent execution
async def main_concurrent():
    # Run multiple coroutines concurrently
    results = await asyncio.gather(
        fetch_data(1),
        fetch_data(2),
        fetch_data(3)
    )
    print(results)

# asyncio.run(main_concurrent())

# Async context manager
class AsyncDatabase:
    async def __aenter__(self):
        print('Connecting to database')
        await asyncio.sleep(1)
        return self
    
    async def __aexit__(self, exc_type, exc_val, exc_tb):
        print('Closing database connection')
        await asyncio.sleep(1)

async def use_database():
    async with AsyncDatabase() as db:
        print('Using database')

# Async iterator
class AsyncRange:
    def __init__(self, n):
        self.n = n
        self.i = 0
    
    def __aiter__(self):
        return self
    
    async def __anext__(self):
        if self.i >= self.n:
            raise StopAsyncIteration
        await asyncio.sleep(0.5)
        self.i += 1
        return self.i

async def iterate():
    async for num in AsyncRange(5):
        print(num)
```

---

## 12. What are slots in Python classes?

**Answer:** `__slots__` is a class attribute that explicitly declares instance attributes, saving memory by preventing the creation of `__dict__` for each instance.

```python
# Without __slots__ (uses more memory)
class WithoutSlots:
    def __init__(self, x, y):
        self.x = x
        self.y = y

# With __slots__ (uses less memory)
class WithSlots:
    __slots__ = ['x', 'y']
    
    def __init__(self, x, y):
        self.x = x
        self.y = y

obj1 = WithoutSlots(1, 2)
obj2 = WithSlots(1, 2)

# With __slots__, you cannot add new attributes dynamically
# obj2.z = 3  # Raises AttributeError

# Check memory usage
import sys
print(sys.getsizeof(obj1.__dict__))  # Larger
# print(sys.getsizeof(obj2.__dict__))  # AttributeError: no __dict__
```

**Advantages:**
- Reduces memory usage
- Faster attribute access
- Prevents accidental attribute creation

**Disadvantages:**
- Cannot add attributes dynamically
- Cannot use weak references
- Slightly less flexible

---

## 13. What is the difference between `iter()` and `next()`?

**Answer:**

- `iter()`: Returns an iterator object
- `next()`: Retrieves the next item from an iterator

```python
# Creating an iterator
my_list = [1, 2, 3]
iterator = iter(my_list)

# Getting items using next()
print(next(iterator))  # 1
print(next(iterator))  # 2
print(next(iterator))  # 3
# print(next(iterator))  # Raises StopIteration

# Custom iterator
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

counter = Counter(1, 5)
for num in counter:
    print(num)  # 1, 2, 3, 4, 5
```

---

## 14. What are Python's built-in higher-order functions?

**Answer:** Higher-order functions are functions that take other functions as arguments or return functions.

```python
# map() - applies function to all items
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# filter() - filters items based on condition
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4]

# reduce() - applies function cumulatively
from functools import reduce
sum_all = reduce(lambda x, y: x + y, numbers)
print(sum_all)  # 15

# sorted() with key function
students = [
    {'name': 'John', 'grade': 88},
    {'name': 'Jane', 'grade': 95},
    {'name': 'Dave', 'grade': 82}
]
sorted_students = sorted(students, key=lambda x: x['grade'], reverse=True)
print(sorted_students)

# any() and all()
print(any([False, True, False]))   # True
print(all([True, True, True]))     # True

# zip() - combines multiple iterables
names = ['John', 'Jane', 'Dave']
ages = [30, 25, 35]
combined = list(zip(names, ages))
print(combined)  # [('John', 30), ('Jane', 25), ('Dave', 35)]
```

---

## 15. Explain Python's import system and circular imports.

**Answer:**

```python
# Different import methods
import module_name
from module_name import function_name
from module_name import *
import module_name as alias

# Circular import problem
# file1.py
from file2 import function_b
def function_a():
    function_b()

# file2.py
from file1 import function_a  # Circular import!
def function_b():
    function_a()

# Solutions to circular imports:

# 1. Restructure code to remove circular dependency
# 2. Import inside function
def function_a():
    from file2 import function_b
    function_b()

# 3. Import module instead of specific function
import file2
def function_a():
    file2.function_b()
```

**Import Search Path:**
1. Current directory
2. PYTHONPATH environment variable
3. Installation-dependent default paths

---

## 26. What are Python's built-in data structures?

**Answer:**

**Mutable:**
- List: Ordered, allows duplicates
- Dictionary: Key-value pairs, unordered (before 3.7)
- Set: Unordered, unique elements

**Immutable:**
- Tuple: Ordered, allows duplicates
- Frozenset: Immutable version of set
- String: Sequence of characters

**Interview Tip:** Choose based on mutability needs and performance requirements.

---

## 27. What is the difference between shallow copy and deep copy?

**Answer:**

**Shallow Copy:**
- Creates new object
- Copies references to nested objects
- Changes to nested objects affect both copies
- Use `copy()` or `copy.copy()`

**Deep Copy:**
- Creates new object
- Recursively copies all nested objects
- Completely independent copies
- Use `copy.deepcopy()`

**When to use:** Use shallow copy for simple structures, deep copy for nested structures.

---

## 28. What are Python's memory management techniques?

**Answer:**

**Reference Counting:**
- Objects have reference count
- Count increases when reference created
- Count decreases when reference deleted
- Object deleted when count reaches zero

**Garbage Collection:**
- Detects and removes circular references
- Generational garbage collection (3 generations)
- Can be controlled using `gc` module

**Memory Pools:**
- Small objects use dedicated pools
- Reduces memory fragmentation
- Improves allocation speed

---

## 29. What is the `collections` module?

**Answer:** `collections` module provides specialized container datatypes.

**Key Types:**
- **namedtuple:** Tuple with named fields
- **deque:** Double-ended queue, efficient append/pop from both ends
- **Counter:** Count hashable objects
- **OrderedDict:** Dictionary that remembers insertion order (redundant in Python 3.7+)
- **defaultdict:** Dictionary with default value for missing keys
- **ChainMap:** Combine multiple dictionaries

**Use Case:** When built-in types don't meet specific requirements.

---

## 30. What is the difference between `@staticmethod` and `@classmethod`?

**Answer:**

**@staticmethod:**
- Doesn't receive automatic first argument
- Cannot access class or instance data
- Behaves like regular function
- Use for utility functions related to class

**@classmethod:**
- Receives class as first argument (`cls`)
- Can access and modify class state
- Used for alternative constructors
- Inherited by subclasses

**Key Difference:** classmethod knows about class, staticmethod doesn't.

---

## 31. What are Python's context managers?

**Answer:** Context managers manage resources using `with` statement.

**Protocol:**
- `__enter__()`: Setup, returns resource
- `__exit__()`: Cleanup, handles exceptions

**Benefits:**
- Automatic resource management
- Exception safe
- Clean and readable code

**Common Examples:** File operations, locks, database connections

**contextlib module:** Provides utilities to create context managers easily.

---

## 32. What is method resolution order (MRO)?

**Answer:** MRO determines order in which base classes are searched when calling methods in inheritance hierarchy.

**Algorithm:** C3 Linearization (Python 3)

**Rules:**
- Children before parents
- Left to right order
- Parent appears once

**View MRO:** Use `ClassName.__mro__` or `ClassName.mro()`

**Diamond Problem:** MRO solves ambiguity in multiple inheritance diamond pattern.

---

## 33. What are Python descriptors?

**Answer:** Descriptors are objects that define how attribute access is handled.

**Protocol Methods:**
- `__get__()`: Get attribute value
- `__set__()`: Set attribute value
- `__delete__()`: Delete attribute

**Types:**
- **Data descriptor:** Has `__get__` and `__set__`
- **Non-data descriptor:** Has only `__get__`

**Examples:** `property`, `staticmethod`, `classmethod` are all descriptors

**Use Case:** Custom attribute access control, validation, lazy loading.

---

## 34. What is the difference between `__repr__` and `__str__`?

**Answer:**

**`__repr__`:**
- For developers
- Should be unambiguous
- Goal: recreate object
- Used by repr() and interactive shell
- Fallback for `__str__`

**`__str__`:**
- For end users
- Should be readable
- Goal: display information
- Used by str() and print()

**Best Practice:** Always implement `__repr__`, implement `__str__` only if needed.

---

## 35. What are Python's iterator protocols?

**Answer:**

**Iterator Protocol:**
- `__iter__()`: Returns iterator object
- `__next__()`: Returns next item

**Iterable vs Iterator:**
- **Iterable:** Object that can return iterator (has `__iter__`)
- **Iterator:** Object that implements iterator protocol (has `__iter__` and `__next__`)

**All iterators are iterables, but not all iterables are iterators.**

**Built-in Functions:** `iter()` gets iterator, `next()` gets next item.

---

## 36. What is pickling and unpickling?

**Answer:** Pickling is serializing Python objects to byte stream. Unpickling is reverse process.

**pickle Module:**
- Serializes objects
- Can handle complex Python objects
- Platform-independent
- Not secure against malicious data

**Use Cases:**
- Save/load machine learning models
- Cache complex computations
- Send objects over network
- Save program state

**Security Warning:** Only unpickle trusted data.

---

## 37. What are Python's abstract base classes?

**Answer:** Abstract base classes (ABCs) define common interface for subclasses.

**abc Module:**
- Provides infrastructure for defining ABCs
- `@abstractmethod` decorator for abstract methods
- Cannot instantiate abstract class directly

**Purpose:**
- Enforce interface implementation
- Document expected interface
- Type checking

**Common ABCs:** `Iterable`, `Iterator`, `Sequence`, `Mapping`

---

## 38. What is the `__slots__` attribute?

**Answer:** `__slots__` restricts attributes that instances can have.

**Benefits:**
- Reduces memory usage (no `__dict__`)
- Faster attribute access
- Prevents dynamic attribute creation

**Drawbacks:**
- Cannot add attributes dynamically
- Slightly more complex inheritance
- Cannot use weak references (unless `__weakref__` in slots)

**Use Case:** Classes with many instances and fixed attributes.

---

## 39. What are metaclasses?

**Answer:** Metaclasses are classes of classes. They define how classes behave.

**Default Metaclass:** `type`

**Use Cases:**
- API design
- Class validation
- Automatic registration
- ORM implementations

**Creation:** Inherit from `type` and override `__new__` or `__init__`

**Philosophy:** If you're not sure whether you need metaclasses, you probably don't.

---

## 40. What is the difference between `enumerate()` and `zip()`?

**Answer:**

**enumerate():**
- Adds counter to iterable
- Returns tuple of (index, value)
- Single iterable input
- Useful for tracking position

**zip():**
- Combines multiple iterables
- Returns tuple of corresponding elements
- Multiple iterables input
- Stops at shortest iterable

**Both:** Return iterators, often used in for loops.
