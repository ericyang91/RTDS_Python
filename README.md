# Road to Data Science: Python

## Table of Contents
- [Object-Oriented Programming (OOP)](#oop)

<h2 id='oop'>Object-Oriented Programming</h2>

### Basics of Object-Oriented Programming

- What is __object-oriented programming (OOP)__?
   - Object-Oriented Programming (OOP) is a programming paradigm centered around the concept of "objects," which are instances of classes. In OOP, the primary focus is on designing software by modeling real-world entities as objects that have attributes (data) and methods (functions or procedures) that define their behavior. The three fundamental principles of OOP are abstraction, data encapsulation, and inheritance.

- What are __classes__ and __objects__? How are they related?
   - A __class__ is a blueprint or template for creating objects. It defines a set of attributes (variables) and methods (functions) that the objects created from the class will have.
      - __Attributes__: These are the data members (variables) that store information about the object.
      - __Methods__: These are functions defined inside a class that describe the behaviors or actions an object can perform.
   - An __object__ is an instance of a class. When you create an object from a class, you are creating an entity that follows the structure and behavior defined by the class.

- What is __abstraction__ in OOP? Why is it needed?
   - Abstraction involves hiding the complex implementation details of an object and exposing only the necessary parts. It helps in reducing complexity and allows the programmer to focus on interactions at a high level rather than the inner workings.

- What is information hiding (__data encapsulation__) in OOP? What advantages does it offer?
   - This concept refers to bundling the data (attributes) and methods that operate on the data into a single unit or class, and restricting direct access to some of the object's components, which helps to protect the integrity of the data.
   - Offers information protection and ease of use.
      - An example of information hiding that you have already seen is defining and using functions. The code block of a function can be very lengthy and hard to understand. After a function is defined, however, a programmer only needs to know what the function does and how to use it, without considering the lengthy code block of how the function works.
   - The built-in `property()` function, which manages access to/modifications to instance-level attributes (private or protected) of a class, provides data encapsulation.

- What does __inheritance__ mean in OOP?
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
   - How do you define the __constructor__ of a class?
      - The constructor (`__init__` method) is used to initialize the attributes of a class when a new object is created.
      - A class cannot have more than one `__init__` effectively defined. If you define two or more `__init__` within a class definition, _only the last_ one will take effect.
   - We can use `help(Class)` statement to see that the class has been created.
   - The builtins.object is a built-in class of Python from which all classes automatically inherit by default.

- What are __subclasses__ and __superclasses__? How are they related?
   - superclasses and subclasses are terms that describe the relationship between classes in an inheritance hierarchy.
      - A superclass (also known as a parent class or base class) is the class from which other classes inherit. It provides common attributes and methods that are shared by its subclasses.
      - A subclass (also known as a child class or derived class) is a class that inherits from a superclass. It can use the attributes and methods of the superclass and can also extend or override them to provide more specific behavior.
      - A subclass in Object-Oriented Programming (OOP) inherits all attributes and methods from its superclass.
      - All classes inherit from the built-in Python object.
  - ```python
       class Reptile:
          def __init__(self, species, habitat, diet):
              self.species = species
              self.habitat = habitat
              self.diet = diet
          def describe(self):
              return f"{self.species} are reptile that live in {self.habitat} and eat {self.diet} for food."

      class Pet(Reptile):
          def __init__(self, species, habitat, diet, age, name):
              self.species = species
              self.habitat = habitat
              self.diet = diet
              self.age = age
              self.name = name
          def introduce_pet(self):
              return f"The name of the pet is {self.name}. It is {self.age} years old."
    ```
     
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
### Public, Private, Protected Attributes
- What are __public__, __private__, and __protected__ members of a class?
   - In Python, the concepts of public, private, and protected members are used to control access to the attributes and methods of a class. These concepts help in implementing _data encapsulation_, which is one of the fundamental principles of object-oriented programming (OOP).
   - Python doesn’t differentiate attributes between public, private, and protected members. Instead, Python treats all attributes of a class as public.
   - It is up to the programmers to decide whether a member should be public, private, or protected.
   - __Public__: Public members are attributes and methods that can be accessed from anywhere, both inside and outside the class.
   - __Protected__: Protected members are intended to be accessed within the class and its subclasses. They can still be accessed outside the class, but it is generally discouraged. Python does not strictly enforce access.
   - __Private__: Private members are meant to be accessed only within the class in which they are defined. They are not accessible directly from outside the class or its subclasses. Private members are used to encapsulate (or hide) the inner workings of a class, so that these details are not accessible or modifiable from outside the class. This ensures that the class maintains control over its data and behavior. Python somewhat enforces acccess, however it is not entirely impossible to access private attributes from outside.

- In a Python program, how do you define public, private, and protected members of a class?
   - __Public__: name
   - __Protected__: _name
   - __Private__: __name
- ```python
     class Pet:
       def __init__(self, species, habitat, diet, age, name):
           self.species = species
           self.habitat = habitat
           self.diet = diet
           self.__age = age # Private attribute. Accessing it from outside by using pet_instance.__age will raise error.
           self._name = name # Protected attribute. Accessing it from outside will not raise error. However, it is not intended to be accessed directly outside the class.
  ```

- If you want to access the private members of a class from outside, the built-in functions `setattr` and `getattr` can be used to access both private and protected members of a class or its instance.
   - `setattr(my_pet, '_name', 'Gamlae')`
   - `getattr(my_pet, '_name')`
   - ```python
     class Student:
       def __init__(self, firstname, lastname):
           self.__firstname = firstname
           self.__lastname = lastname
   
      s0 = Student('Eric', 'Yang')
      setattr(s0, '__firstname', 'Lack Young')
      setattr(s0, '__lastname', 'Son')
      print(getattr(s0, '__firstname'), getattr(s0, '__lastname')) # Output 'Lack Young Son'
      print(hasattr(s0, '__lastname')) # Output 'True'
     ```

### Class Methods and Static Methods

- What are class methods and static methods? How do they differ?
   - __Class method__:
        - A class method in Python is a method that is bound to the class rather than the instance of the class. This means that the method can be called on the class itself, without creating an instance, and it has access to the class itself, rather than instance attributes. It is defined using the `@classmethod` decorator.
      - A class cannot have more than one `__init__` effectively defined.
      - ```python
           class Animal:
              species = 'unknown'
              def __init__(self, name):
                 self.name = name
              @classmethod
              def change_species(cls, new_species):
                 cls.species = new_species
                 print(f"Species changed to {cls.species}")
        
            # Calling the class method on the class itself
            Animal.change_species("Dog")

            # Creating an instance of Animal
            a = Animal("Buddy")
            print(a.species)  # Output: Dog
        
            # You can also call the class method through an instance
            a.change_species("Cat")
            print(a.species)  # Output: Cat
        ```

      - Class methods are often used as __factory methods__ to create instances of the class in different ways. So how can you create an instance of a class differently in Python if there can be only one constructor, the special `__init__` method, in a class definition?
         - This is where __class methods__ come in. A __class method__ can be used to provide an alternative way to create instances of a class. Unlike the `__init__` method, which is designed for a single initialization process, a class method can encapsulate different logic for creating and returning instances.
      - ```python
        class Graduate:
          def __init__(self, fullname): # Standard constructor that initializes and instance by taking a full name
              firstname, lastname = fullname.split(' ')
              self.firstname = firstname
              self.lastname = lastname
      
              # The limitation of the above method is that you cannot create a class object by taking separate first and last names. It only allows for a full name.
              # You also can't add a second __init__ method. This is where a class method can help.
      
          @classmethod # This decorator declares a class method (first parameter refers to the class instead of an instance of the class)
          def newGraduate(cls, firstname, lastname): # This is a class method. Constructs the full name internally and calls the __init__ method via the class.
              return cls(f'{firstname} {lastname}') # Return an object, or an instance of the class
          
          def __str__(self): # The __str__ method is another special method used to define the string representation of an object.
              return f'{self.firstname} {self.lastname}' # When print() is called on an instance of Graduate, this method is invoked, 
                                                         # returning a string in the format '{self.firstname} {self.lastname}'.
         
         # Creating instances of the class using the standard constructor __init__ and the class method    
         g0 = Graduate('Jiyeol Yang')
         g1 = Graduate.newGraduate('Jiyeol', 'Yang')
         
         print(g0) # Output is 'Jiyeol Yang'
         print(g1) # Output is 'Jiyeol Yang'
        ```
  
   - __Static method__:
      - Similar to the class method of a class, a __static method__ can be called directly through the class. The difference is that in the definition of a static method, no parameter refers to the class nor to the instance itself.
      - Static methods are methods that belong to a class but do not access or modify the class or instance itself. Instead, they perform a specific task that is relevant to the class but doesn't require any knowledge of the instance or class state.
      - The static methods can be called directly through the class, without an instance. Defining a static method within a class is a way to add utility functions to the class so that it can be used without instantiating an object.
      - ```python
        class Converter:
             @staticmethod
             def kg2lb(w):
                 return w * 2.20462
             
             @staticmethod
             def lb2kg(w):
                 return w / 2.20462
          
         """
         The static methods can be called directly on the class without creating an instance of the class. 
         This is useful for utility functions like these conversions, which don't need to access any instance-specific data.
         """
         
         print(Converter.kg2lb(65)) # Output "131.33003000000002
        ```
        
