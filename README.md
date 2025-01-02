# Road to Data Science: Python

## Table of Contents
- [Object-Oriented Programming (OOP)](#oop)

<h2 id='oop'>Object-Oriented Programming</h2>

### Basics of Object-Oriented Programming

- What is object-oriented programming (OOP)?
   - Object-Oriented Programming (OOP) is a programming paradigm centered around the concept of "objects," which are instances of classes. In OOP, the primary focus is on designing software by modeling real-world entities as objects that have attributes (data) and methods (functions or procedures) that define their behavior. The three main features of OOP are abstraction, data encapsulation, and inheritance.

- What are classes and objects? How are they related?
   - A class is a blueprint or template for creating objects. It defines a set of attributes (variables) and methods (functions) that the objects created from the class will have.
      - Attributes: These are the data members (variables) that store information about the object.
      - Methods: These are functions defined inside a class that describe the behaviors or actions an object can perform.
   - An object is an instance of a class. When you create an object from a class, you are creating an entity that follows the structure and behavior defined by the class.

- What is abstraction in OOP? Why is it needed?
   - Abstraction involves hiding the complex implementation details of an object and exposing only the necessary parts. It helps in reducing complexity and allows the programmer to focus on interactions at a high level rather than the inner workings.

- What is information hiding (data encapsulation) in OOP? What advantages does it offer?
   - This concept refers to bundling the data (attributes) and methods that operate on the data into a single unit or class, and restricting direct access to some of the object's components, which helps to protect the integrity of the data.
   - Offers information protection and ease of use.
      - An example of information hiding that you have already seen is defining and using functions. The code block of a function can be very lengthy and hard to understand. After a function is defined, however, a programmer only needs to know what the function does and how to use it, without considering the lengthy code block of how the function works.
   - The built-in `property()` function, which manages access to/modifications to instance-level attributes (private or protected) of a class, provides data encapsulation.

- What does inheritance mean in OOP?
   - Most often, things are categorized and put in a tree-like hierarchy with the root on the top. In such a tree-like hierarchy, the root of the tree is the most generic class or concept, and the leaves are the most specific and often refer to specific objects. From the root down to the leaves, nodes on a lower level will inherit the properties of all the connected nodes at higher levels.
   - If you want to inherit from multiple base classes,
      ```python
         class myClass(base_1, base_2, base_3):
            pass
      ```
   - The new class will inherit all the attributes and methods from base_1, base_2, and base_3 and override the methods defined in the base classes.
   - In Python, all classes are a subclass of the built-in base object class and inherit all the properties and methods of object, even if object is not explicitly included in the inheritance list.

### Class
- How do you define a new class?
   - A class would include some attributes and methods, as well as a constructor or initiator for creating instances of the class.
   - ```python
       class Reptile:
         def __init__(self, species):
           self.species = species
     ```
   - We can use `help(Class)` statement to see that the class has been created.
   - The builtins.object is a built-in class of Python from which all classes automatically inherit by default.

- What are subclasses and superclasses? How are they related?
   - superclasses and subclasses are terms that describe the relationship between classes in an inheritance hierarchy.
      - A superclass (also known as a parent class or base class) is the class from which other classes inherit. It provides common attributes and methods that are shared by its subclasses.
      - A subclass (also known as a child class or derived class) is a class that inherits from a superclass. It can use the attributes and methods of the superclass and can also extend or override them to provide more specific behavior.
      - A subclass in Object-Oriented Programming (OOP) inherits all attributes and methods from its superclass.
      - All classes inherit from the built-in Python object.
     
  - Formally in Python, if you are defining a class that needs to inherit from another class, you can put the superclass(es) in a pair of parentheses
    - For example, `class PC(Computer)`
      - Here, Computer is the superclass and PC is the subclass.

### Attributes
  - When defining a class, how do you define attributes or properties of that class?
     - Two methods:
        1. Using `__init__` method: In this example, the `__init__` method initializes the CPU attribute when the instance c is created. It is called when creating new objects of the class.
           ```python
           class Computer:
              def __init__(self, CPU):
                 self.CPU = CPU # self is used to refer to the instance of the class.
  
           c = Computer('Intel i6800')
           print(c.CPU)  # Output: Intel i6800
           ```
        2. Using `setattr` function: Here, the `setattr` function is used to add the CPU attribute to the instance c after it has been created.
           ```python
           class Computer:
              pass  # No initialization in this case
  
           c = Computer()  # Creating an instance of Computer
           setattr(c, 'CPU', 'Intel i6800')  # Dynamically setting the attribute
           print(c.CPU)  # Output: Intel i6800
           ```
        - Both are valid, but `__init__` is more commonly used for initial setup, while `setattr` is handy for adding or modifying attributes later.
        - In Python, X() will be automatically the constructor of class X, but it calls a special method named `__init__`, which can be defined within the class to instantiate instances of the class.
        - Now we can use special attribute `__dict__` of instance c of class Computer to check the attribute and value of object c.
           - `print(c.__dict__)`
         
   - Other built-in functions for class and object manipulation:
      - `getattr(o, attr)`: Return the value of object o's attribute attr, same as `o.attr`
      - `hasattr(o, attr)`: Test if object o has attribute attr; return `True` if it does
      - `setattr(o, a, v)`: Set/add attribute a to object o, and assign value v to the attribute. Overwrites if exist.
      - `delattr(o, a)`: Delete attribute a from object o
      - `isinstance(o, c)`: Return `True` if o is an instance of c, or if o is a subclass of c.
      - `issubclass(c, C)`: Return `True` if c is a subclass of C.
      - `repr(o)`: Return string representation of object o.

### Methods
   - When defining a class, how do you define methods of that class?
      ```python
         class Gecko:
            def __init__(self, diet, length): # Method!
               self.diet = diet
               self.length = length
            def species(self): # Method!
               if self.length > 20:
                  return 'Tokay'
               else:
                  return 'Crested'
            def describe(self): # Method!
               return f"The gecko's diet is {self.diet} and is {self.length} in length."
      ```
### Public, Private, Protected

     
