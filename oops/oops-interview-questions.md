# Object-Oriented Programming (OOP) - Interview Questions & Answers

## 1. What is Object-Oriented Programming?

**Answer:** OOP is a programming paradigm based on the concept of "objects" that contain data (attributes) and code (methods).

**Core Principles:**
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

**Benefits:**
- Code reusability
- Modularity
- Easier maintenance
- Real-world modeling
- Flexibility and scalability

---

## 2. What are the four pillars of OOP?

**Answer:**

**1. Encapsulation:**
- Bundling data and methods together
- Data hiding using access modifiers
- Controlled access through getters/setters

**2. Inheritance:**
- Child class inherits properties from parent
- Code reusability ("IS-A" relationship)
- Creates hierarchy

**3. Polymorphism:**
- Same interface, different implementations
- Method overloading (compile-time)
- Method overriding (runtime)

**4. Abstraction:**
- Hide complex implementation details
- Show only essential features
- Achieved through abstract classes/interfaces

---

## 3. What is a Class and Object?

**Answer:**

**Class:**
- Blueprint or template for objects
- Defines properties and behaviors
- Logical entity
- No memory allocated

**Object:**
- Instance of a class
- Has state and behavior
- Physical entity  
- Memory allocated

**Relationship:** Class is design, Object is implementation.

**Example Analogy:** Class = Car blueprint, Object = Actual car

---

## 4. What is Encapsulation?

**Answer:** Encapsulation is wrapping data (variables) and code (methods) together as a single unit and restricting direct access.

**Implementation:**
- Make variables private
- Provide public getter/setter methods
- Control data access and modification

**Benefits:**
- Data hiding
- Increased security
- Flexibility (change implementation without affecting outside code)
- Control over data

**Example:** Bank account - balance is private, accessed only through deposit/withdraw methods.

---

## 5. What is Inheritance?

**Answer:** Inheritance is a mechanism where one class acquires properties and behaviors of another class.

**Types:**

**Single Inheritance:** One parent, one child
**Multiple Inheritance:** Multiple parents (not supported in Java, supported in C++/Python)
**Multilevel Inheritance:** Chain of inheritance (A→B→C)
**Hierarchical Inheritance:** Multiple children from one parent
**Hybrid Inheritance:** Combination of above types

**Keywords:**
- `extends` (class inheritance)
- `implements` (interface inheritance)
- `super` (access parent members)

**Benefits:**
- Code reusability
- Method overriding
- Establish relationships

---

## 6. What is Polymorphism?

**Answer:** Polymorphism means "many forms" - ability of object to take many forms.

**Types:**

**Compile-Time (Static) Polymorphism:**
- Method Overloading
- Operator Overloading
- Resolved at compile time

**Runtime (Dynamic) Polymorphism:**
- Method Overriding
- Resolved at runtime
- Uses inheritance

**Real-world Example:** Person acts as employee at office, parent at home, customer at store.

---

## 7. What is the difference between Method Overloading and Method Overriding?

**Answer:**

| Feature | Overloading | Overriding |
|---------|------------|-----------|
| Definition | Same name, different parameters | Same name, same parameters |
| Inheritance | Not required | Required (parent-child) |
| Binding | Compile-time | Runtime |
| Return Type | Can differ | Must be same/covariant |
| Access Modifier | Any | Cannot be more restrictive |
| Purpose | Multiple behaviors in same class | Redefine parent behavior |

**Interview Tip:** Overloading = same class, Overriding = inheritance.

---

## 8. What is Abstraction?

**Answer:** Abstraction is hiding implementation complexity and showing only essential features.

**Implementation:**

**Abstract Classes:**
- Can have abstract and concrete methods
- Cannot instantiate
- 0 to 100% abstraction

**Interfaces:**
- All methods abstract (Java 7)
- 100% abstraction
- Multiple inheritance possible

**Benefits:**
- Reduces complexity
- Avoid code duplication
- Security (hide details)
- Loose coupling

**Example:** TV remote - hide complex circuitry, show simple buttons.

---

## 9. What is the difference between Abstract Class and Interface?

**Answer:**

| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Keyword | `abstract class` | `interface` |
| Methods | Abstract + Concrete | All abstract (before Java 8) |
| Variables | Any type | public static final only |
| Multiple Inheritance | No | Yes |
| Constructor | Can have | Cannot have |
| Access Modifiers | Any | Public by default |
| When to use | Partial implementation | Full abstraction/contract |

**Modern Java:** Interfaces can have default and static methods (Java 8+).

---

## 10. What is a Constructor?

**Answer:** Constructor is a special method that initializes objects when created.

**Characteristics:**
- Same name as class
- No return type (not even void)
- Called automatically when object created
- Can be overloaded

**Types:**

**Default Constructor:** No parameters
**Parameterized Constructor:** Accepts parameters
**Copy Constructor:** Creates object  from existing object

**Purpose:**
- Initialize instance variables
- Set up initial state
- Allocate resources

---

## 11. What is the difference between Constructor and Method?

**Answer:**

| Feature | Constructor | Method |
|---------|------------|--------|
| Name | Same as class | Any name |
| Return Type | No return type | Must have return type |
| Invocation | Automatically (object creation) | Explicitly called |
| Purpose | Initialize object | Perform operations |
| Inheritance | Not inherited | Inherited |
| Overriding | Not possible | Possible |

---

## 12. What is Constructor Overloading?

**Answer:** Constructor Overloading is having multiple constructors with different parameters in same class.

**Purpose:**
- Provide flexibility in object creation
- Initialize objects in different ways
- Default and custom initialization

**Rules:**
- Must differ in number or type of parameters
- Cannot differ only in return type (constructors have no return type)

**Interview Tip:** Allows creating objects with different initialization options.

---

## 13. What is the `this` keyword?

**Answer:** `this` is a reference to the current object instance.

**Uses:**

**1. Differentiate instance variable from parameter:**
- When names are same

**2. Call another constructor:**
- Constructor chaining (`this()`)

**3. Pass current object:**
- As argument to methods

**4. Return current object:**
- Method chaining

**Interview Tip:** `this` is implicit reference available in instance methods and constructors.

---

## 14. What is the `super` keyword?

**Answer:** `super` refers to the immediate parent class object.

**Uses:**

**1. Access parent class variables:**
- When child has same-named variable

**2. Call parent class method:**
- When overridden in child

**3. Call parent constructor:**
- `super()` - must be first statement

**Interview Tip:** Use when parent and child have same-named members or to explicitly call parent functionality.

---

## 15. What is the difference between `this` and `super`?

**Answer:**

| Feature | this | super |
|---------|------|-------|
| Refers to | Current class object | Parent class object |
| Use for | Current class members | Parent class members |
| Constructor | Call current class constructor | Call parent class constructor |
| Requirement | Not required for inheritance | Required for inheritance |

---

## 16. What is Method Overloading?

**Answer:** Method Overloading is defining multiple methods with same name but different parameters in same class.

**Can differ by:**
- Number of parameters
- Type of parameters
- Order of parameters

**Cannot differ by:**
- Return type only
- Access modifiers only

**Benefits:**
- Improved readability
- Flexibility
- Code reusability

**Example:** `add(int, int)`, `add(double, double)`, `add(int, int, int)`

---

## 17. What is Method Overriding?

**Answer:** Method Overriding is providing specific implementation of method that is already defined in parent class.

**Rules:**
- Same method name
- Same parameters
- Same or covariant return type
- Cannot have more restrictive access modifier
- Cannot override final/static methods

**Annotation:** `@Override` (recommended for compile-time checking)

**Purpose:**
- Provide specific implementation
- Runtime polymorphism
- Customize inherited behavior

---

## 18. What are Access Modifiers?

**Answer:** Access Modifiers control visibility and accessibility of classes, methods, and variables.

**Types:**

**Public:**
- Accessible from anywhere
- Most open

**Protected:**
- Accessible within package and subclasses
- Used for inheritance

**Default (Package-Private):**
- Accessible only within same package
- No keyword needed

**Private:**
- Accessible only within same class
- Most restricted
- Used for encapsulation

---

## 19. What is the difference between Public, Private, Protected, and Default?

**Answer:**

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| public | ✓ | ✓ | ✓ | ✓ |
| protected | ✓ | ✓ | ✓ | ✗ |
| default | ✓ | ✓ | ✗ | ✗ |
| private | ✓ | ✗ | ✗ | ✗ |

**Interview Tip:** More restrictive = better encapsulation.

---

## 20. What is the `static` keyword?

**Answer:** `static` belongs to class rather than instance.

**Used with:**

**Variables:**
- Shared among all instances
- Single copy per class
- Memory allocated once

**Methods:**
- Called without creating object
- Cannot access instance variables directly
- Example: `Math.sqrt()`, utility methods

**Blocks:**
- Execute when class loaded
- Initialize static variables

**Nested Classes:**
- Static inner classes

**Interview Tip:** Static members accessed using class name, not object.

---

## 21. What is the `final` keyword?

**Answer:** `final` makes entity unchangeable/unmodifiable.

**Used with:**

**Variables:**
- Value cannot be changed (constant)
- Must initialize when declared or in constructor

**Methods:**
- Cannot be overridden
- Prevent modification in subclasses

**Classes:**
- Cannot be inherited
- Prevent subclassing
- Example: String class

**Benefits:**
- Immutability
- Security
- Performance optimization

---

## 22. What is the difference between static and final?

**Answer:**

| Feature | static | final |
|---------|--------|-------|
| Purpose | Class-level member | Constant/unchangeable |
| Variable | Shared across instances | Cannot reassign |
| Method | Class method | Cannot override |
| Class | N/A (nested classes only) | Cannot inherit |
| Initialization | Can change value | Cannot change after initialization |

**Can combine:** `static final` for constants (e.g., `static final double PI = 3.14`)

---

## 23. What is Composition?

**Answer:** Composition is a design principle where class contains reference to other class objects (HAS-A relationship).

**Characteristics:**
- Stronger relationship than inheritance
- "Has-a" relationship
- Part cannot exist independently
- Better flexibility

**Example:** Car has Engine - Engine is part of Car, cannot exist without Car.

**vs Inheritance:**
- Composition: "HAS-A"
- Inheritance: "IS-A"

**Interview Tip:** Favor composition over inheritance for better flexibility and loose coupling.

---

## 24. What is Aggregation?

**Answer:** Aggregation is a specialized form of association representing "HAS-A" relationship where objects have independent lifecycle.

**Difference from Composition:**
- **Aggregation:** Part can exist independently (weak relationship)
- **Composition:** Part cannot exist independently (strong relationship)

**Example:**
- Aggregation: Teacher and Department - Teacher can exist without Department
- Composition: Car and Engine - Engine is part of Car

---

## 25. What is Association?

**Answer:** Association is a relationship where objects are independent and have their own lifecycle.

**Types:**

**One-to-One:** One object associated with one other
**One-to-Many:** One object associated with many
**Many-to-One:** Many objects associated with one
**Many-to-Many:** Many objects associated with many

**Example:** Teacher and Student - both can exist independently, can have multiple students per teacher.

---

## 26. What is Multiple Inheritance and Diamond Problem?

**Answer:**

**Multiple Inheritance:** Class inherits from multiple parent classes.

**Diamond Problem:**
- Class D inherits from B and C
- Both B and C inherit from A
- If B and C override method from A
- Which version does D inherit?

**Solutions:**
- **Java:** Doesn't allow multiple inheritance of classes
- **Java Interfaces:** Default methods with override
- **C++:** Virtual inheritance
- **Python:** Method Resolution Order (MRO)

---

## 27. What is Coupling?

**Answer:** Coupling is degree of interdependence between classes/modules.

**Types:**

**Tight Coupling:**
- High dependency
- Changes affect other classes
- Harder to maintain

**Loose Coupling:**
- Low dependency
- Independent modules
- Easier to maintain

**How to achieve loose coupling:**
- Use interfaces
- Dependency injection
- Avoid hardcoding dependencies

**Interview Tip:** Aim for loose coupling for better maintainability.

---

## 28. What is Cohesion?

**Answer:** Cohesion is degree to which elements of module belong together.

**Types:**

**High Cohesion:**
- Related functionality grouped together
- Single, well-defined purpose
- Desirable

**Low Cohesion:**
- Unrelated functionality
- Multiple purposes
- Hard to maintain

**Example:**
- High: Calculator class with only math operations
- Low: Calculator class with math operations and file I/O

**Interview Tip:** Aim for high cohesion (Single Responsibility Principle).

---

## 29. What is SOLID Principles?

**Answer:** SOLID is a set of five design principles for maintainable and scalable OOP code.

**S - Single Responsibility Principle:**
- Class should have one reason to change
- One responsibility per class

**O - Open/Closed Principle:**
- Open for extension, closed for modification
- Add new features without changing existing code

**L - Liskov Substitution Principle:**
- Objects should be replaceable with subtypes
- Subclass should behave like parent

**I - Interface Segregation Principle:**
- Many specific interfaces better than one general
- Don't force classes to implement unused methods

**D - Dependency Inversion Principle:**
- Depend on abstractions, not concretions
- High-level modules shouldn't depend on low-level

---

## 30. What is the difference between Procedural and Object-Oriented Programming?

**Answer:**

| Feature | Procedural | OOP |
|---------|-----------|-----|
| Approach | Function-based | Object-based |
| Data Security | Less secure (global data) | More secure (encapsulation) |
| Reusability | Limited | High (inheritance) |
| Modular | Less | Highly modular |
| Maintenance | Difficult | Easier |
| Examples | C, Pascal | Java, C++, Python |
| Focus | What to do | What data to operate on |

**Interview Tip:** OOP provides better organization, reusability, and maintainability for large applications.

---
## 31. What is a constructor?

**Answer:** Constructor is special method called automatically when object is created.

**Characteristics:**
- Same name as class (in most languages)
- No return type
- Called automatically
- Initializes object state

**Types:**
- **Default:** No parameters
- **Parameterized:** Takes parameters
- **Copy:** Creates copy of object

**Use:** Initialize variables, allocate resources

---

## 32. What is a destructor?

**Answer:** Destructor is special method called when object is destroyed.

**Characteristics:**
- Opposite of constructor
- Cleanup operations
- No return type, no parameters
- Cannot be overloaded
- Automatic invocation

**Use Cases:**
- Release resources
- Close file handles
- Free memory
- Close database connections

---

## 33. What is method overriding?

**Answer:** Method overriding is providing specific implementation of method in subclass that's already defined in parent class.

**Requirements:**
- Inheritance required
- Same method signature
- Same or covariant return type
- Access level cannot be more restrictive

**Purpose:**
- Runtime polymorphism
- Specific behavior for subclass

**Annotation:** @Override (in Java)

---

## 34. What is method overloading?

**Answer:** Method overloading is defining multiple methods with same name but different parameters.

**Differences:**
- Number of parameters
- Type of parameters
- Order of parameters

**Characteristics:**
- Compile-time polymorphism
- Same class
- Return type can differ
- Cannot overload by return type alone

**Example:** print(int), print(String), print(int, String)

---

## 35. What is the `this` keyword?

**Answer:** `this` refers to current instance of class.

**Use Cases:**
- Distinguish instance variables from parameters
- Call other constructors (constructor chaining)
- Pass current object as parameter
- Return current object

**Benefits:** Clarity, avoiding naming conflicts

---

## 36. What is the `super` keyword?

**Answer:** `super` refers to parent class object.

**Use Cases:**
- Call parent class constructor
- Access parent class methods
- Access parent class variables (if hidden)

**Constructor Chaining:** `super()` must be first statement in constructor

**Purpose:** Access parent functionality in inheritance

---

## 37. What is an inner class?

**Answer:** Inner class is class defined within another class.

**Types:**
- **Member Inner Class:** Inside another class
- **Static Nested Class:** Static member of outer class
- **Local Inner Class:** Inside method
- **Anonymous Inner Class:** Without name

**Benefits:**
- Logical grouping
- Encapsulation
- Access to outer class members
- Code organization

---

## 38. What is an interface?

**Answer:** Interface is contract that specifies what methods class must implement.

**Characteristics:**
- All methods abstract (before Java 8)
- Cannot have instance variables
- Cannot be instantiated
- Supports multiple inheritance
- 100% abstraction

**Modern Features (Java 8+):**
- Default methods
- Static methods

**Use:** Define common behavior, achieve multiple inheritance

---

## 39. What is multiple inheritance and why is it problematic?

**Answer:** Multiple inheritance allows class to inherit from multiple parent classes.

**Diamond Problem:**
- Two parents have same method
- Which method should child inherit?
- Ambiguity resolution needed

**Solutions:**
- Interfaces (Java, C#)
- Method resolution order (Python)
- Virtual inheritance (C++)

**Java Approach:** Multiple interface implementation, single class inheritance

---

## 40. What is coupling?

**Answer:** Coupling is degree of interdependence between modules.

**Types:**
- **Tight Coupling:** High dependency, changes affect others
- **Loose Coupling:** Low dependency, independent modules

**Loose Coupling Benefits:**
- Easy maintenance
- Better testability
- Reusability
- Flexibility

**Achieve via:** Interfaces, dependency injection, event-driven design

---

## 41. What is cohesion?

**Answer:** Cohesion is degree to which elements within module belong together.

**Types (Low to High):**
- **Coincidental:** Random grouping
- **Logical:** Logically related
- **Temporal:** Executed at same time
- **Procedural:** Sequential execution
- **Communicational:** Operate on same data
- **Sequential:** Output of one is input to next
- **Functional:** Single well-defined task (BEST)

**Goal:** High cohesion (single, well-focused purpose)

---

## 42. What is association?

**Answer:** Association is relationship between two classes where objects have their own lifecycle.

**Types:**
- **One-to-One:** Student has one ID card
- **One-to-Many:** Teacher has many students
- **Many-to-Many:** Students enroll in many courses

**Characteristics:**
- Bi-directional or uni-directional
- Independent lifecycle
- "HAS-A" relationship

**Implementation:** References between classes

---

## 43. What is aggregation?

**Answer:** Aggregation is special form of association representing "whole-part" relationship.

**Characteristics:**
- Weak relationship
- Parts can exist independently
- Lifecycle independent
- "HAS-A" relationship

**Example:** Department has employees (employees can exist without department)

**Symbol (UML):** Hollow diamond

---

## 44. What is composition?

**Answer:** Composition is strong form of aggregation where parts cannot exist without whole.

**Characteristics:**
- Strong relationship
- Parts lifecycle dependent on whole
- Parts destroyed when whole destroyed
- Strong ownership

**Example:** House has rooms (rooms can't exist without house)

**Symbol (UML):** Filled diamond

---

## 45. What is the difference between `==` and `equals()`?

**Answer:**

**== operator:**
- Compares references (memory addresses)
- For primitives, compares values
- Cannot be overridden

**equals() method:**
- Compares object content/state
- Can be overridden
- Default implementation same as ==

**Best Practice:** Override equals() to compare meaningful content, not just references

---