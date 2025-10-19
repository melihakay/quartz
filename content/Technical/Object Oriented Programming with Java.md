# Java Basics

- **Java** (Compiled to bytecode, then interpreted by the JVM)
- **C#** (Compiled to Intermediate Language, then executed by the .NET
runtime)
- **Python** (JIT compilers like PyPy improve performance)

Properties:
- Java is a high-level, object-oriented language.
- "Write Once, Run Anywhere" makes it platform-
independent.
- Automatic garbage collection manages memory.
- Strong typing prevents runtime errors.
- Supports multi-threading for concurrent execution.
- Rich APIs enable diverse applications.
- Used in enterprise, Android, and large-scale
systems.

## Data Types

```java
byte smallNumber = 100;
// 1-byte integer (-128 to 127)
short shortNumber = 32000;
// 2-byte integer (-32,768 to 32,767)
int age = 25;
// 4-byte integer (-2^31 to 2^31-1)
long bigNumber = 123456789L;
// 8-byte integer (-2^63 to 2^63-1)
float pi = 3.14f; //real-number
// 4-byte floating-point Floating-point types
double precisePi = 3.1415926535; //real-
number
// 8-byte floating-point (higher precision)
char letter = 'A';
// 2-byte character (Unicode) Character type
boolean isStudent = true; //logical
// true or false Boolean type
```

- In Java, a complex type refers to any data type that is not a primitive type.
- These types are also known as reference types. (They store references (memory addresses) rather than the actual value. )
- They are object-based and typically contain multiple pieces of data or functions together.

```java
 // In Java, the runtime always starts with the
	 //main method.
 //The main method is the entry point where all
	 //code execution begins.
public static void main(String[] args)
// Here, static allows the JVM to call the main
	// method directly without creating an object
	//when the program starts.
```

- Static variables belong to the class, not to any object.
- Shared across all instances of the class

![[setter.png]]

- Except for some objects like String, Arrays, all objects are created using «new» keyword with a constructor.
- Constructors in Java do not have a return type.
- A class in Java cannot exist without a constructor.
- If you do not define any constructor, Java automatically creates a default constructor in
the background.

- this(): Calls another constructor within the same class.
- this: Passes the current object as a reference.

Example:

![[java_example_1.png]]

### Error Handling

![[java_error.png]]

Throws tells compiler that it doesn't raise but passes the exception.

![[java_error_throws.png]]
#### Checked

- IOException
- FileNotFoundException
* SQLException
* ParseException
- ClassNotFoundException

#### Unchecked

- NullPointerException
- ArrayIndexOutOfBoundsException
- ArithmeticException
- IllegalArgumentException
- NumberFormatException


# OOP

- Reusability - Code can be reused through inheritance, reducing redundancy.
- Encapsulation - Data is protected and only accessible through defined methods.
- Abstraction - Hides complex implementation, showing only necessary details.
- Modularity - Code is organized into separate objects, making it easier to maintain.
- Flexibility - Polymorphism allows objects to be used in different ways.
- Scalability - Easier to extend and modify programs without affecting existing code.
- Security - Restricts unauthorized access to data through encapsulation.

![[fout_pillars_of_oop.png]]

## Encapsulation

Encapsulation in object-oriented programming (OOP) is the process of hiding data (variables) and providing controlled access to them through methods within a class.

- Data Security: Prevents direct access to variables, reducing the risk of misuse.
- Controlled Access: Provides controlled access through getter and setter methods.
- Code Maintenance and Flexibility: If variable names change, external code remains
unaffected.
- Data Validation: setter methods allow validation checks before modifying values.

![[access_modifiers_oop.png]]

## Inheritance

- Inheritance allows a class to acquire the attributes and behaviors (methods) of another class.
- We can reuse properties (fields) and methodsof a parent class in a child class.
- «is-a » relation

### kw: extends 

- In Java, the extends keyword is used to create a subclass (child class) from a superclass (parent class).
- It allows the child class to inherit all the fields (variables) and methods of the parent class.

### kw: super
- It is used to access parent class members from the child class.
- You can use it to call the constructor, methods, or variables of the superclass

You can only extend one class at a time (Java supports single inheritance)

![[extends_super_java.png]]

## Polymorphism

- Polymorphism is the ability of objects of different classes to respond to the same method call in different ways. One interface, multiple implementations.

![[polymorphism_exaple_java.png]]

### Override

- The method must be defined in both superclass and subclass.
- The method signature (name + parameters) must be identical.
- The method in the subclass must have equal or more accessible access modifier.
- Only inherited methods can be overridden
- The return type must be the same or a subclass (covariant) of the method in the superclass.


### Overload 

Overloading is resolved at compile time, so it's also called compile-time polymorphism or static binding.

![[override_java.png]]

### Differences

Method Overloading:
• Occurs within the same class or in subclasses.
• The method name is the same, but the parameters must differ (either the number of parameters or their types).
• The return type can be the same or different.
• Overloading is resolved at compile time (static polymorphism).

Method Overriding:
• Occurs between a superclass and a subclass.
• The method name and the parameter list must be the same in both the superclass and subclass.
• The return type must also be the same or a subtype (covariant return type).
• Overriding is resolved at runtime (dynamic polymorphism

![[overload_vs_override.png]]

## Abstract Classes

An abstract class in Java is a class that cannot be instantiated, but can be extended by other classes.

- It is used as a base class to define a common interface and optionally some common
behavior for its subclasses.
- Declared using the abstract keyword.
- May contain abstract methods (methods without a body) and concrete methods (with
implementation).
- Can have constructors, fields, and static blocks.
- Cannot be instantiated directly.
- Used when you want to provide a common base and allow subclasses to implement specific behavior.

![[Pasted image 20250618131429.png]]

## Interfaces

An interface in Java is a reference type, similar to a class, that can contain only constants,
method signatures, default methods, static methods, and nested types.

- It cannot contain instance fields or constructors.
- Interfaces define abstract methods that must be implemented by any class that implements the interface.

![[Pasted image 20250618131544.png]]

![[Pasted image 20250618131554.png]]

Can a Class Implement Multiple Interfaces?

• Yes! In Java, a class can implement multiple interfaces.
• This is one of the key advantages of using interfaces, as Java does not support multiple
inheritance of classes but supports multiple inheritance of interfaces.

![[Pasted image 20250618131625.png]]

![[Pasted image 20250618131653.png]]



## UML

### Use Case

![[use_case.png]]

### Class Diagram

**Association**: A Driver is associated with a Car

**Generalization** (Inheritance): Car inherits from
Vehicle. "is-a" relationship

**Dependency**: A Car uses A FuelPump, One class temporarily depends on another.

- One-to-One (1..1): An employee has one ParkingSpot
- One-to-Many (1..*): A Library has many Books
- Many-to-Many (*..*): A Student can enroll in multiple Courses, and a
Course can have multiple Students
#### Aggregation & Composition

- "has-a" relationship
- **Aggregation** represents a relationship where the
component (Engine) can exist independently.
- **Composition** means that the component (Engine)
cannot exist independently.

![[java_oop_relationships.png]]

