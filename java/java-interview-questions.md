# Java Interview Questions & Answers

## 1. What is Java and what are its main features?

**Answer:** Java is a high-level, class-based, object-oriented programming language developed by Sun Microsystems (now Oracle) in 1995.

**Main Features:**
- **Platform Independent:** "Write Once, Run Anywhere" (WORA)
- **Object-Oriented:** Everything is an object
- **Robust:** Strong memory management, exception handling
- **Secure:** No explicit pointers, bytecode verification
- **Multithreaded:** Built-in multithreading support
- **Architecture Neutral:** Works on any processor
- **High Performance:** JIT compiler improves performance

---

## 2. What is JVM, JRE, and JDK?

**Answer:**

**JVM (Java Virtual Machine):**
- Executes Java bytecode
- Platform-dependent
- Provides runtime environment

**JRE (Java Runtime Environment):**
- JVM + Library classes
- Required to run Java applications
- No development tools

**JDK (Java Development Kit):**
- JRE + Development tools (compiler, debugger)
- Required to develop Java applications
- Includes javac, java, javadoc

**Relationship:** JDK ⊃ JRE ⊃ JVM

---

## 3. What is the difference between JDK, JRE, and JVM?

**Answer:**

| Component | Purpose | Contains | Used By |
|-----------|---------|----------|---------|
| JDK | Development | JRE + Dev Tools | Developers |
| JRE | Execution | JVM + Libraries | End Users |
| JVM | Runtime | Execution Engine | Both |

---

## 4. Explain OOP concepts in Java.

**Answer:**

**1. Encapsulation:**
- Wrapping data and methods into single unit (class)
- Data hiding using access modifiers
- Getter/setter methods for data access

**2. Inheritance:**
- Acquiring properties from parent class
- Code reusability
- "IS-A" relationship
- Keywords: `extends`, `super`

**3. Polymorphism:**
- **Compile-time:** Method overloading
- **Runtime:** Method overriding
- Same method, different behavior

**4. Abstraction:**
- Hiding implementation details
- Showing only essential features
- Achieved through abstract classes and interfaces

---

## 5. What is the difference between abstract class and interface?

**Answer:**

| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Keyword | `abstract class` | `interface` |
| Methods | Can have abstract and concrete | All abstract (before Java 8) |
| Variables | Any type | Only public static final |
| Multiple Inheritance | No (single inheritance) | Yes (implements multiple) |
| Constructor | Can have | Cannot have |
| Access Modifiers | Any | Public by default |
| When to use | Partial implementation | Full abstraction/contract |

**Java 8+:** Interfaces can have default and static methods.

---

## 6. What is the difference between method overloading and method overriding?

**Answer:**

**Method Overloading (Compile-time Polymorphism):**
- Same method name, different parameters
- Within same class
- Different signature (parameters)
- Return type can be different

**Method Overriding (Runtime Polymorphism):**
- Same method name, same parameters
- In parent and child class
- Same signature
- Return type must be same or covariant

**Interview Tip:** Overloading = different parameters, Overriding = parent-child relationship.

---

## 7. What are access modifiers in Java?

**Answer:**

| Modifier | Class | Package | Subclass | World |
|----------|-------|----------|----------|-------|
| public | ✓ | ✓ | ✓ | ✓ |
| protected | ✓ | ✓ | ✓ | ✗ |
| default (no modifier) | ✓ | ✓ | ✗ | ✗ |
| private | ✓ | ✗ | ✗ | ✗ |

**Usage:**
- **private:** Encapsulation, hide data
- **default:** Package-level access
- **protected:** Inheritance scenarios
- **public:** Public API, accessible everywhere

---

## 8. What is the difference between String, StringBuilder, and StringBuffer?

**Answer:**

| Feature | String | StringBuilder | StringBuffer |
|---------|--------|--------------|--------------|
| Mutability | Immutable | Mutable | Mutable |
| Thread-Safe | Yes (immutable) | No | Yes (synchronized) |
| Performance | Slower (creates new object) | Fast | Slower (synchronization overhead) |
| When to use | Fixed strings | Single-threaded | Multi-threaded |

**Interview Tip:** Use StringBuilder for string concatenation in loops for better performance.

---

## 9. What is the difference between `==` and `.equals()`?

**Answer:**

**`==` Operator:**
- Compares references (memory addresses)
- For primitives, compares values
- Checks if two references point to same object

**`.equals()` Method:**
- Compares content/values
- Can be overridden for custom comparison
- Default implementation in Object class uses `==`

**Example Logic:**
- String pool: Two "hello" literals → same reference (`==` true)
- New String: `new String("hello")` → different reference (`==` false, `.equals()` true)

---

## 10. What is String Pool in Java?

**Answer:** String Pool is a special memory area in heap where Java stores string literals to optimize memory usage.

**Key Points:**
- **Location:** Heap memory (Java 7+)
- **Purpose:** Avoid duplicate string objects
- **Mechanism:** Strings with same value share same reference
- **Creation:** String literals automatically added to pool

**Behavior:**
- `String s1 = "hello"` → goes to pool
- `String s2 = "hello"` → reuses from pool
- `String s3 = new String("hello")` → creates new object in heap

**Interview Tip:** Use `intern()` method to explicitly add string to pool.

---

## 11. What is the difference between ArrayList and LinkedList?

**Answer:**

| Feature | ArrayList | LinkedList |
|---------|-----------|------------|
| Data Structure | Dynamic array | Doubly linked list |
| Access Time | O(1) - Fast | O(n) - Slow |
| Insertion/Deletion | O(n) - Slow | O(1) - Fast |
| Memory | Less overhead | More (stores references) |
| Use Case | Frequent access | Frequent modifications |

**Interview Tip:** Choose ArrayList for search-heavy operations, LinkedList for insert/delete-heavy operations.

---

## 12. What is the difference between HashMap and HashTable?

**Answer:**

| Feature | HashMap | Hashtable |
|---------|---------|-----------|
| Synchronization | Not synchronized | Synchronized |
| Thread-Safe | No | Yes |
| Null Keys | One null key allowed | Not allowed |
| Null Values | Multiple null values | Not allowed |
| Performance | Faster | Slower |
| Legacy | Modern (Java 1.2) | Legacy (Java 1.0) |

**Alternative:** Use `ConcurrentHashMap` for thread-safe operations with better performance than Hashtable.

---

## 13. What is the difference between ArrayList and Vector?

**Answer:**

| Feature | ArrayList | Vector |
|---------|-----------|--------|
| Synchronization | Not synchronized | Synchronized |
| Performance | Faster | Slower |
| Growth | Increases 50% | Increases 100% |
| Legacy | Modern | Legacy |
| Thread-Safe | No | Yes |

**Interview Tip:** Vector is legacy class. Use ArrayList with Collections.synchronizedList() if needed.

---

## 14. What is the difference between Comparable and Comparator?

**Answer:**

| Feature | Comparable | Comparator |
|---------|------------|------------|
| Package | java.lang | java.util |
| Method | `compareTo()` | `compare()` |
| Sorting Logic | Natural ordering | Custom ordering |
| Modification | Modify class | Separate class |
| Usage | Single sorting sequence | Multiple sorting sequences |

**When to use:**
- **Comparable:** Default sorting (e.g., Employee by ID)
- **Comparator:** Custom sorting (e.g., Employee by name, salary, age)

---

## 15. What is exception handling in Java?

**Answer:** Exception handling manages runtime errors to maintain normal application flow.

**Hierarchy:**
- **Throwable**
  - **Error:** Serious problems (OutOfMemoryError) - not handled
  - **Exception:** Recoverable conditions
    - **Checked Exception:** Compile-time (IOException, SQLException)
    - **Unchecked Exception:** Runtime (NullPointerException, ArrayIndexOutOfBoundsException)

**Keywords:**
- **try:** Contains code that might throw exception
- **catch:** Handles exception
- **finally:** Always executes (cleanup code)
- **throw:** Manually throw exception
- **throws:** Declares exception

---

## 16. What is the difference between final, finally, and finalize?

**Answer:**

**final:**
- Keyword for constants, prevent inheritance/overriding
- Variable: Cannot change value
- Method: Cannot override
- Class: Cannot inherit

**finally:**
- Block that always executes after try-catch
- Used for cleanup (close resources)
- Executes even if exception occurs

**finalize:**
- Method called by garbage collector before destroying object
- Used for cleanup activities
- Deprecated in Java 9

---

## 17. What is multithreading in Java?

**Answer:** Multithreading is concurrent execution of two or more threads for maximum CPU utilization.

**Benefits:**
- Better CPU utilization
- Reduced response time
- Simultaneous task execution
- Resource sharing

**Thread Creation:**
1. **Extending Thread class:** Override `run()` method
2. **Implementing Runnable interface:** Implement `run()` method (preferred)

**Thread Lifecycle:** New → Runnable → Running → Blocked/Waiting → Terminated

**Interview Tip:** Implementing Runnable is preferred as Java doesn't support multiple inheritance.

---

## 18. What is synchronization in Java?

**Answer:** Synchronization controls access of multiple threads to shared resources to prevent data inconsistency.

**Types:**

**Method Synchronization:**
- Entire method synchronized
- Only one thread can execute at a time

**Block Synchronization:**
- Specific code block synchronized
- Better performance (smaller critical section)

**Static Synchronization:**
- Class-level lock
- All instances share same lock

**Benefits:** Thread-safe, prevents race conditions
**Drawback:** Performance overhead, potential deadlock

---

## 19. What is the difference between Collection and Collections?

**Answer:**

**Collection:**
- Interface (java.util.Collection)
- Root interface of Collection Framework
- Represents group of objects
- Extended by List, Set, Queue

**Collections:**
- Utility class (java.util.Collections)
- Contains static methods
- Operations: sort, reverse, shuffle, search
- Helper methods for collections

**Example:** `Collections.sort(list)` sorts a Collection object.

---

## 20. What is the difference between Array and ArrayList?

**Answer:**

| Feature | Array | ArrayList |
|---------|-------|-----------|
| Size | Fixed | Dynamic |
| Type | Primitives + Objects | Only Objects |
| Performance | Faster | Slightly slower |
| Dimension | Multi-dimensional | Single dimension |
| Type Safety | Yes | Yes (generics) |
| Methods | Length property | Many utility methods |

**Interview Tip:** Use Array for fixed-size, ArrayList for dynamic size requirements.

---

## 21. What are constructors in Java?

**Answer:** Constructors are special methods that initialize objects when created.

**Characteristics:**
- Same name as class
- No return type
- Called automatically when object created
- Can be overloaded

**Types:**
1. **Default Constructor:** No parameters, provided by compiler if not defined
2. **Parameterized Constructor:** Accepts parameters
3. **Copy Constructor:** Creates object using another object

**Interview Tip:** If you define any constructor, compiler doesn't provide default constructor.

---

## 22. What is the difference between this and super?

**Answer:**

**this:**
- Refers to current class instance
- Access current class members
- Call current class constructor
- Pass current object as parameter

**super:**
- Refers to parent class instance
- Access parent class members
- Call parent class constructor
- Resolve name conflicts between parent and child

---

## 23. What is static keyword in Java?

**Answer:** Static belongs to class rather than instance.

**Usage:**

**Static Variable:**
- Shared among all instances
- Memory allocated once
- Example: counter, constants

**Static Method:**
- Can be called without object
- Cannot access instance variables/methods
- Example: `main()` method

**Static Block:**
- Executed when class loaded
- Initialize static variables

**Static Class:**
- Only nested classes can be static

**Interview Tip:** Common methods: `Math.sqrt()`, `Integer.parseInt()` are static.

---

## 24. What is garbage collection in Java?

**Answer:** Garbage collection automatically deallocates memory by removing unreachable objects.

**How it works:**
- JVM periodically checks for unused objects
- Objects with no references are eligible
- Automatic memory management

**Methods to request GC:**
- `System.gc()` - request (not guarantee)
- `Runtime.getRuntime().gc()`

**Generations:**
1. **Young Generation:** New objects (Minor GC)
2. **Old Generation:** Long-lived objects (Major GC)
3. **Permanent Generation:** Metadata (removed in Java 8)

**Interview Tip:** Cannot force GC, can only request. JVM decides when to run.

---

## 25. What is the difference between Heap and Stack memory?

**Answer:**

| Feature | Stack | Heap |
|---------|-------|------|
| Storage | Primitives, references, method calls | Objects, instance variables |
| Access | LIFO (Last In First Out) | Dynamic allocation |
| Speed | Faster | Slower |
| Size | Smaller | Larger |
| Lifetime | Method execution | Until garbage collected |
| Thread | Per thread | Shared across threads |
| Errors | StackOverflowError | OutOfMemoryError |

---

## 26. What are Java 8 features?

**Answer:**

**Lambda Expressions:**
- Anonymous functions
- Functional programming support
- Syntax: `(parameters) -> expression`

**Functional Interfaces:**
- Interface with single abstract method
- `@FunctionalInterface` annotation

**Stream API:**
- Process collections declaratively
- Operations: filter, map, reduce

**Default Methods:**
- Methods with implementation in interfaces
- Backward compatibility

**Optional:**
- Container object for null values
- Avoid NullPointerException

**Method References:**
- Shorthand for lambda expressions
- Syntax: `ClassName::methodName`

---

## 27. What is the difference between Object clone() and copy constructor?

**Answer:**

**clone():**
- Creates exact copy at runtime
- Requires implementing `Cloneable` interface
- Returns `Object` type (needs casting)
- Can throw `CloneNotSupportedException`

**Copy Constructor:**
- Constructor accepting same class object
- Type-safe
- More flexible and clear
- No exception handling needed

**Interview Tip:** Copy constructor is preferred over clone() for clarity and type safety.

---

## 28. What is marker interface in Java?

**Answer:** Marker interface is an empty interface with no methods or fields, used to mark or tag classes.

**Examples:**
- `Serializable` - marks class as serializable
- `Cloneable` - marks class as cloneable
- `Remote` - marks class for remote access

**Purpose:**
- Provide runtime information to JVM/compiler
- Enable special behavior
- Type checking

**Modern Alternative:** Annotations are preferred over marker interfaces in modern Java.

---

## 29. What is the difference between ClassNotFoundException and NoClassDefFoundError?

**Answer:**

**ClassNotFoundException:**
- **Type:** Checked exception
- **Cause:** Class not found at runtime (dynamic loading)
- **Scenario:** `Class.forName()`, `ClassLoader.loadClass()`
- **Reason:** Wrong classpath or misnamed class

**NoClassDefFoundError:**
- **Type:** Error
- **Cause:** Class present at compile-time, missing at runtime
- **Scenario:** Class successfully compiled but not available during execution
- **Reason:** Class file deleted or not deployed

---

## 30. What is serialization in Java?

**Answer:** Serialization is converting object state into byte stream for storage or transmission.

**Purpose:**
- Save object state to file
- Send objects over network
- Cache objects
- Deep cloning

**Requirements:**
- Implement `Serializable` interface
- All fields must be serializable
- Use `transient` keyword for non-serializable fields

**Keywords:**
- `transient`: Skip field during serialization
- `serialVersionUID`: Version control for serialized objects

**Related:** Deserialization converts byte stream back to object.

---
## 31. What is the difference between `Comparable` and `Comparator`?

**Answer:**

| Comparable | Comparator |
|------------|------------|
| In `java.lang` package | In `java.util` package |
| Uses `compareTo()` method | Uses `compare()` method |
| Single sorting sequence | Multiple sorting sequences |
| Modifies actual class | Separate class |
| Natural ordering | Custom ordering |

**Use Comparable:** When class has natural ordering (e.g., numbers, strings)
**Use Comparator:** When multiple sorting options needed.

---

## 32. What are Java's access modifiers?

**Answer:**

**Four Access Levels:**

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| default (no modifier) | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

**Default:** Package-private, visible within same package only.

---

## 33. What is the `finalize()` method?

**Answer:** `finalize()` is called by garbage collector before object destruction.

**Characteristics:**
- Called once per object
- Not guaranteed to be called
- Slows garbage collection
- Deprecated since Java 9

**Better Alternatives:**
- Try-with-resources
- `AutoCloseable` interface
- Manual cleanup methods

---

## 34. What is the difference between `throw` and `throws`?

**Answer:**

**throw:**
- Keyword used to explicitly throw exception
- Used inside method body
- Followed by exception object
- Can throw only one exception at a time

**throws:**
- Keyword used in method signature
- Declares exceptions method might throw
- Followed by exception class names
- Can declare multiple exceptions

---

## 35. What are Java Streams?

**Answer:** Streams are sequence of elements supporting sequential and parallel aggregate operations (Java 8+).

**Characteristics:**
- Not a data structure
- Doesn't store elements
- Functional in nature
- Lazy evaluation
- Can be infinite

**Operations:**
- **Intermediate:** filter, map, sorted (return stream)
- **Terminal:** forEach, collect, reduce (return result)

**Benefits:** Cleaner code, parallel processing, functional programming style.

---

## 36. What is method overloading and overriding?

**Answer:**

**Method Overloading:**
- Same method name, different parameters
- Compile-time polymorphism
- Within same class
- Can change return type
- Can change access modifier

**Method Overriding:**
- Same method signature in subclass
- Runtime polymorphism
- Requires inheritance
- Same or covariant return type
- Cannot reduce visibility

---

## 37. What is the `synchronized` keyword?

**Answer:** `synchronized` provides thread synchronization to prevent data corruption.

**Usage:**
- Synchronized methods
- Synchronized blocks
- Static synchronization

**Benefits:**
- Thread safety
- Prevents race conditions
- Ensures visibility

**Drawbacks:**
- Performance overhead
- Can cause deadlocks
- Reduces concurrency

---

## 38. What is the difference between `Stack` and `Heap` memory?

**Answer:**

**Stack Memory:**
- Stores method calls and local variables
- LIFO structure
- Fast access
- Limited size
- Thread-specific
- Automatically deallocated

**Heap Memory:**
- Stores objects and class variables
- Slower than stack
- Larger size
- Shared among threads
- Requires garbage collection

**StackOverflowError:** Stack memory exhausted (deep recursion)
**OutOfMemoryError:** Heap memory exhausted.

---

## 39. What are Java annotations?

**Answer:** Annotations provide metadata about program elements.

**Built-in Annotations:**
- `@Override`: Indicates method overriding
- `@Deprecated`: Marks outdated element
- `@SuppressWarnings`: Suppresses compiler warnings
- `@FunctionalInterface`: Marks functional interface

**Use Cases:**
- Compiler instructions
- Runtime processing
- Code generation
- Framework configuration (Spring, Hibernate)

---

## 40. What is Java Reflection?

**Answer:** Reflection allows inspecting and manipulating classes, methods, fields at runtime.

**Capabilities:**
- Get class information
- Create objects dynamically
- Invoke methods
- Access/modify fields
- Bypass access restrictions

**Use Cases:**
- Frameworks (Spring, Hibernate)
- Testing tools
- Serialization
- Debugging tools

**Drawbacks:** Performance overhead, security concerns, breaks encapsulation.

---

## 41. What is the difference between `StringBuffer` and `StringBuilder`?

**Answer:**

| StringBuffer | StringBuilder |
|--------------|---------------|
| Synchronized | Not synchronized |
| Thread-safe | Not thread-safe |
| Slower | Faster |
| Since Java 1.0 | Since Java 5 |
| Use in multi-threaded | Use in single-threaded |

**Both:** Mutable, more efficient than String for concatenation.

---

## 42. What is Java's garbage collection?

**Answer:** Garbage collection automatically frees memory by removing unreferenced objects.

**Types of GC:**
- Serial GC: Single thread
- Parallel GC: Multiple threads
- CMS (Concurrent Mark Sweep): Low pause time
- G1 GC: Large heaps, predictable pause times

**GC Generations:**
- Young Generation: New objects
- Old Generation: Long-lived objects
- Permanent Generation: Metadata (removed in Java 8)

---

## 43. What is autoboxing and unboxing?

**Answer:**

**Autoboxing:** Automatic conversion from primitive to wrapper class (int → Integer)
**Unboxing:** Automatic conversion from wrapper to primitive (Integer → int)

**Benefits:** Convenience, cleaner code
**Drawback:** Performance overhead, potential NullPointerException

---

## 44. What is the `volatile` keyword?

**Answer:** `volatile` ensures visibility of variable changes across threads.

**Characteristics:**
- No caching of variable
- Reads/writes directly from main memory
- Prevents instruction reordering
- Lighter than synchronized
- Cannot guarantee atomicity

**Use Case:** Flags, status variables in multi-threading.

---

## 45. What is dependency injection?

**Answer:** Dependency injection is design pattern where objects receive dependencies from external source.

**Types:**
- Constructor injection
- Setter injection
- Field injection

**Benefits:**
- Loose coupling
- Easy testing
- Flexibility
- Maintainability

**Frameworks:** Spring, Google Guice, CDI

---