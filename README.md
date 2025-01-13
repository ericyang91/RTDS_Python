# Road to Data Science: Python

## Table of Contents
- [Flow Control of Statements](#flow)
- [Handle Errors and Exceptions](#error)
- [Sequences, Sets, Dictionaries](#seq)
- [Handling Text Files](#text)
- [Object-Oriented Programming (OOP)](#oop)

<h2 id='flow'>Flow Control of Statements</h2>

### Selective Statements

- What are **selective statements**?
    - **Selective statements** in Python are programming constructs that enable a program to make decisions based on specific conditions. The primary mechanism for implementing selective statements in Python is the *if statement*. These statements evaluate a condition or set of conditions and execute specific blocks of code based on whether the conditions are true or false.
- Why do I need selective statements in programming?
    - Selective statements empower programmers to create decision-making logic, manage diverse scenarios, and direct program behavior according to changing conditions, thereby improving application functionality and user experience.
- What can I use in Python to make selective statements?
    - **if-elif-else** statement

### If, Elif, Else

- How do I use an **if statement** to run a code block only under a certain condition? How do I specify conditions for my selective statements?
    - ```python
      name = input("Guess my name")
      
      if name == "Eric":
          print("That's me!")
      ```
- How do I use **if-else statements** to make double selections?
    - ```python
      name = input("Guess my name")
      
      if name == "Eric":
          print("That's me!")
      else:
          print("That's not me!")
      ```
- How do I use **if-elif statements** to make multiple selections?
    - ```python
      name = input("Guess my name")
      
      if name == "Eric":
          print("That's me!")
      elif name == "Leah":
          print("That's my wife!")
      ```
- How do I use **if-elif-else statements** to make multiple selections?
    - ```python
      name = input("Guess my name")
      
      if name == "Eric":
          print("That's me!")
      elif name == "Leah":
          print("That's my wife!")
      else:
          print("That's neither me nor my wife!")
      ```
### For

- How do I use **for statements** to make loops in Python?
    - ```python
      lst1 = [1, 2, 3, 4, 5]
      lst2 = []
      for i in lst1:
          lst2.append(i**2)
    
      print(lst2)
      ```
- What is the built-in `range(start, stop, step)` function?
    - Allows users to iterate through the start number up to but excluding the end number.
    - ```python
      lst = []
      for i in range(10):
          lst.append(i**2)
    
      print(lst)
      ```
- How do I use the list, tuple, set, string, and dictionary compound data types with **for statements**?
    - `for element in list:`
    - `for element in tuple:`
    - `for element in set:`
    - `for character in string:`
    - `for key in dictionary:` or `for key in dictionary.keys()`
    - `for value in dictionary.values():`
    - `for key, value in dictionary.items():`

### While

- How do I use **while statements** to make loops in Python?

    - ```python
        import random
    
        def guessing_game():
            correct_number = random.randint(1,10)
            print("Welcome to the number guessing game!")
            while True:
                try:
                    number = int(input("Guess your number between 1 and 10: "))
                    if number != correct_number:
                        print("Incorrect guess. Try again.")
                    else:
                        print("Correct!")
                        break
                except ValueError:
                    print("Invalid entry. Enter an integer.")
    
       guessing_game()
      ```
- What is the difference between **for** and **while** statements?
    - **for** is used when we know the number of iterations.
    - **while** is used when we do not know the number of iterations.
    - for loops can always be replaced by while loops. while loops cannot be replaced with for loops in cases when the number of iterations is unknown.

- Can I use the range() function and the list, tuple, set, string, and dictionary compound data types with while statements?
    - Yes.
  
- In Python, is there another statement I can use to make a loop?
    - No. **for** and **while** are the only loop statements in Python.
 
### Common Mistakes with the For and While Loops

- Common mistakes with the **for** loop:
    - Remember to not change the value of any iteration variable within the code block of a **for loop** because it needs to be changed automatically by Python interpreter to the next item in the sequence. The iteration might be unexpected if the value of the iteration variable is changed in the code block.
- Common mistakes with the **while** loop:
    - There should be at least one iteration variable within the code block of the while loop.
    - The value(s) of iteration variable(s) must change within the code block.
    - The logical expression of the looping condition is not correctly written. This mistake may occur when inequal operators are involved in the logical expression of the looping condition. For example, using > in place of >=, or using < in place <=, will cause the program to miss one iteration of the loop.
 
### Break and Continue
- **break** is used to get out of the loop immediately by ignoring all the code before it without going back to test the looping condition. This is a way to get out of a loop in the middle of an iteration and is applicable to both the while loop and for loop.
    - ```python
        for i in range(1,11):
            if i <= 5:
                print(i)
            else:
                break
      ```
- **continue** statement is used within a loop to go back directly to the beginning of the iteration. Skips the rest of the current iteration and moves to the next iteration.
    - ```python
        i = 1
        while i <= 10:
            if i % 2 != 0:
                print(i)
                i += 1
            else:
                i += 1
                continue
      ```
 
### Zip Function

- What is the `zip()` function?
  - The `zip()` function in Python is used to combine two or more iterables (e.g., lists, tuples, strings, etc.) element-wise, creating an iterator of tuples. Each tuple contains one element from each iterable. It's especially useful when you want to iterate over multiple iterables simultaneously. `zip()` stops when the shortest iterable is exhausted.

- ```python
    name = ['eric', 'leah', 'dahee']
    age = [33, 36, 2]
    height = [175, 153, 87]
    
    zipped_list = list(zip(name, age, height))
    
    for name, age, height in zipped_list:
        print(f"{name} is {age} years old and {height}cm in height.")
  ```



<h2 id='error'>Handle Errors and Exceptions</h2>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Exception%20Handling.ipynb)

### Basics of Errors

- What types of errors can occur in a program?
   - **Syntax errors:** These include misspelled keywords, improper identifiers, use of undefined functions or variables. They are typically caught by Python IDEs during development or at runtime due to Python's interpreted nature.
   - **Runtime errors:** Occur during program execution and can include issues like division by zero or accessing out-of-bounds indices.
   - **Logic errors:** Involve incorrect use of operators (e.g., '<' instead of '>'), misinterpretation of sequence boundaries, and often result in incorrect program output. These errors are costly as they require careful debugging and logic correction.

### Types of Errors

1. **TypeError:** Raised when a function or operation is applied to an object of an incorrect type.
    - `result = 'Hello' + 5`
2. **ArithmeticError:** The base class for arithmetic errors, including:
   - **OverflowError:** Raised when the result of an arithmetic operation is too large to be represented.
   - **ZeroDivisionError:** Raised when the divisor of a division or modulo operation is 0.
   - **FloatingPointError:** Related to floating-point operations but less common in Python.
3. **NameError:** Raised when a variable that is not defined is used.
    - `print(undefined_variable)`
4. **AssertionError:** Raised when an assertion statement (`assert`) fails.
    - `assert 1 + 1 == 3`
5. **AttributeError:** Raised when an attribute assignment or reference fails because the attribute does not exist.
    - ```python
        class myClass:
            def __init__(self, name):
                self.name = name
        
        class_instance = myClass('class1')
        class_instance.functionalities # Output: AttributeError: 'myClass' object has no attribute 'functionalities'
      ```
    - ```python
        lst = [1,2,3,4]
        lst.sum() # Output: AttributeError: 'list' object has no attribute 'sum'
      ```
6. **ImportError:** Raised when an imported module is not found.
    - `import non_existent_module`
7. **ModuleNotFoundError:** Raised by `import` when a module could not be located in `sys.modules`.
8. **IndexError:** Raised when the index of a sequence is out of range.
    - ```python
        my_list = [1,2,3]
        item = my_list[5]
      ```
9. **KeyError:** Raised when a key is not found in a dictionary.
    - `dict['non_existent_key']` where `dict = {'key': 'value'}`
10. **OSError:** The base class for system-related errors, including:
    - **FileExistsError:** Raised when trying to create a file or directory that already exists.
    - **FileNotFoundError:** Raised when a file or directory is requested but does not exist.
        - ```python
            with open('non_existent_file.txt') as file:
                content = file.read()
          ```
    - **PermissionError:** Raised when attempting an operation without adequate access rights.
11. **RuntimeError:** Raised when an error does not fit into any other predefined category.  
12. **StopIteration:** Raised by the `next()` function to indicate that no further items are available in an iterator.
13. **SyntaxError:** Raised by the parser when a syntax error is encountered.
    - ```python
        if True   # Missing colon
            print("Hello")
        # Raises: SyntaxError: expected ':'
      ```
    - ```python
        def greet():
        print("Hello")  # IndentationError (a subtype of SyntaxError)
      ```
    - ```python
        def = 5  # Invalid
        # Raises: SyntaxError: invalid syntax
      ```
    - ```python
        x = (1 + 2   # Missing closing parenthesis
        # Raises: SyntaxError: unexpected EOF while parsing
      ```

14. **IndentationError:** Raised when there is incorrect indentation.
15. **TabError:** Raised when the indentation mixes tabs and spaces inconsistently.
16. **ValueError:** Raised when a function receives an argument of the correct type but with an inappropriate value.
    - `int(input('Four'))`: It received an argument of the correct type (string), but with an inappropriate value (Four). 
17. **ZeroDivisionError**: Raised when divided by zero
    - `5 / 0`

### Try-Except-Else-Finally

- When programming, runtime errors or **exceptions** are inevitable. Therefore, it's crucial for a programmer to handle exceptions properly when they occur.
- Python exceptions are managed using a *try* statement.
    - A *try* statement begins with a try clause, enclosing code that may potentially cause errors and raise exceptions.
- Following the *try* clause, one or more *exception* clauses start with the keyword "except," followed by a system-defined error/exception name. Each exception clause specifies how to handle a specific error if it occurs.
- The *else* clause contains code that executes if no exceptions are raised during the execution of the try clause.
- The *finally* clause includes code that executes regardless of whether an exception was raised within the try clause.
- In Python, a try statement can take several forms: try-except, try-except-else, try-except-finally, try-except-else-finally, and try-finally.
- ```python
    try:
        # Code that might raise an exception
        result = 10 / 2
    except ZeroDivisionError:
        # Handle division by zero exception
        print("Error: Division by zero!")
    else:
        # This block executes if no exceptions are raised
        print("Division successful!")
    finally:
        # This block always executes, regardless of exceptions
        print("Execution complete.")
    
    # Output if no exceptions are raised:
    # Division successful!
    # Execution complete.
    
    # Output if a ZeroDivisionError is raised:
    # Error: Division by zero!
    # Execution complete.
  ```
- ```python
      def manual_division(x, y):
         try:
            result = x / y
         except ZeroDivisionError:
            print('Cannot divide by zero!')
         else:
            print(f'Result is {result}')
         finally:
            print('End')
        
      print(manual_division(4, 0))
    ```

### Raise and Assert

- How do you intentionally raise an exception using the **raise statement**?
   - The **raise statement** is used to deliberately raise an exception in Python. This is useful for signaling specific error conditions in your code or when certain criteria are met that warrant an exception to be thrown.
   - ```python
      try:
         age = int(input("What's your age?"))
         if age < 0:
            raise ValueError('Invalid age!')
         
      except ValueError as e:
         print(e)
         print('Invalid input')
      ```
    - ```python
        def withdraw(balance, amount):
            if amount > balance:
                raise ValueError("Insufficient balance!")
            return balance - amount
        
        try:
            print(withdraw(100, 150))
        except ValueError as e:
            print(f"Transaction failed: {e}")
        # Output: Transaction failed: Insufficient balance!
      ```
    - ```python
        def custom_division(a,b):
            if not isinstance(a, (int, float)) or not isinstance(b, (int, float)):
                raise TypeError("Wrong type! Use integer or float!")
            if b == 0:
                raise ZeroDivisionError("You cannot divide by zero!")
            
            else:
                return a/b
                
        try:
            custom_division(1,'hello')
        except ZeroDivisionError as e:
            print(e)
        except TypeError as e:
            print(e) # Output: Wrong type! Use integer or float!
      ```
- What is **Assert** statement in Python?
    - The **assert** statement is used to validate assumptions in code, such as checking if a variable holds an expected value or if a condition is met. If the assumption proves to be false during runtime, Python raises an **AssertionError**. This helps in identifying and handling unexpected conditions in programs. The **assert** statement in Python is a debugging aid that helps you catch and handle unexpected conditions during development. It allows you to assert that a certain condition is true at a specific point in your code. If the condition evaluates to False, Python raises an **AssertionError**, which can be useful for identifying bugs or logical errors in your code.
 
    - For example, consider the following code snippet:

    - ```python
        my_list = range(10)
        assert 12 in my_list, '12 should be in the list'
        ```

        - Since 12 is not in the list, it raises an AssertionError with the message '12 should be in the list'.

    - ```python
        def calculate_square_root(x):
            assert x >= 0, "Input should be a non-negative number"
            return math.sqrt(x)
    
        print(calculate_square_root(9))  # Works fine
        print(calculate_square_root(-1)) # Raises AssertionError
        ```

- The **assert** statement is a simple yet powerful tool for debugging and enforcing assumptions in your code. While it should not replace robust error handling in production, it is invaluable during development for catching errors early and verifying program logic.

<h2 id='seq'>Sequences, Sets, Dictionaries</h2>

<h2 id='text'>Handling Text Files</h2>


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
                return f"{self.species} are reptiles that live in {self.habitat} and eat {self.diet} for food."
        
        
        class Pet(Reptile):
            def __init__(self, species, habitat, diet, age, name):
                # Call the superclass's __init__ method to initialize species, habitat, and diet
                super().__init__(species, habitat, diet)
                # Initialize additional attributes specific to Pet
                self.age = age
                self.name = name
        
            def introduce_pet(self):
                return f"The name of the pet is {self.name}. It is {self.age} years old."
        
        
        # Create an instance of Pet
        pet = Pet("Crested Gecko", "terrariums", "insects", 10, "KG")
        
        # Access inherited attributes
        print(pet.species)  # Output: Crested Gecko
        print(pet.describe())  # Output: Crested Gecko are reptiles that live in terrariums and eat insects for food.
        
        # Access Pet-specific methods and attributes
        print(pet.introduce_pet())  # Output: The name of the pet is KG. It is 10 years old.
    ```
        - What Are We Inheriting?
            - **Attributes**: *species*, *habitat*, *diet*: These attributes are initialized in the Reptile class and describe general characteristics of reptiles. By inheriting them, the Pet class can also represent these characteristics for pet reptiles.
            - **Methods**: *describe*: The describe method provides a reusable way to describe any reptile, including those represented by the Pet class.
        - How Is It Useful?
            - Reusability of Code: We don't need to redefine common attributes (species, habitat, diet) or methods (describe) in the Pet class. This avoids redundancy and follows the DRY (Don't Repeat Yourself) principle.
            - Consistency: Any changes to shared logic (e.g., modifying how reptiles are described) only need to be made in the Reptile class. This ensures all subclasses (like Pet) automatically inherit the updated behavior.
            - Extensibility: We can extend or override the behavior inherited from the Reptile class. For example, the Pet class could override the describe method to provide a more specific description for pet reptiles.
            - Hierarchical Representation: Inheritance lets us represent relationships logically. A Pet is a type of Reptile, so it makes sense to inherit from the Reptile class rather than creating a completely independent Pet class.
     
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

- If you want to access the protected members of a class from outside, the built-in functions `hasattr` and `getattr` can be used to access protected members of a class or its instance. It cannot, however, access private members.
   - `hasattr(my_pet, '_name')`
   - `getattr(my_pet, '_name')`
   - ```python
     class Student:
       def __init__(self, firstname, lastname):
           self._firstname = firstname
           self._lastname = lastname
   
      s0 = Student('Eric', 'Yang')
      setattr(s0, '_firstname', 'Lack Young')
      setattr(s0, '_lastname', 'Son')
      print(getattr(s0, '_firstname'), getattr(s0, '_lastname')) # Output 'Lack Young Son'
      print(hasattr(s0, '_lastname')) # Output 'True'
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

### Class Attributes
- What are the **class attributes**?
   - In Python, you can define a class without explicitly declaring attributes of the class. However, Python does allow the explicit declaration of attributes within a class definition. These attributes are called class attributes.
      - This means that the attribute is declared _outside_ of the `__init__` method.
   - In Python, class attributes are shared among all the objects of the class and can also be accessed directly from the class, without an instance of the class.
      - For example, `Class.class_attr` accesses the class attribute, class_attr, directly from the class, Class.
- ```python
      class Graduate:
          student_id = 260374177 # student_id is a class attribute, defined outside of the __init__ method. Class attributes are shared across all instances of the class.
          def __init__(self, fullname): # self refers to the instance in normal method
              firstname, lastname = fullname.split(' ')
              self.firstname = firstname
              self.lastname = lastname
              self.student_id = self.__class__.student_id
              self.__class__.student_id += 1 # It allows you to access class-level attributes and methods from within an instance. When you modified student_id, you're modifying the value for all instances of that class
                                             # This can be read as "Access the class associated with this instance (self.__class__) and then access the student_id attribute of that class, and increment it by 1"
                                             # __class__ refers to the class of an object, in this case, class of self. It is referring to Graduate. If it is simply self.student_id = self.__class__.student_id + 1, student_id would become
                                             # an attribute of each instance of the class. This means we will get 260374178 for all instances.
          
          @classmethod # Decorator
          def newGraduate(cls, firstname, lastname):
          #cls refers to the class itself, not the instance
              return cls(f'{firstname} {lastname}') # Creates an instance of Graduate(fullname)
          
          def __str__(self):
              return f'{self.firstname} {self.lastname}, {self.student_id}' # Returns a string representation of the object
          
      g0 = Graduate('Jiyeol Yang')
      print(g0) # Output "Jiyeol Yang, 260374177"
      
      g1 = Graduate.newGraduate('Jiyeol', 'Yang')
      print(g1) # Output "Jiyeol Yang, 260374178"
      
      g2 = Graduate('Lackyoung Son')
      print(g2) # Output "Lackyoung Son, 260374179"
   ```

### Dunder Methods
- How may dunder methods be used in a new class?
   - **Dunder methods**, also known as "magic methods" or "special methods," are predefined methods in Python that start and end with double underscores (hence "dunder"). These methods are integral to Python’s object model and allow you to define how objects of your class interact with built-in operations such as addition, subtraction, or string representation.
   - Operator overloading with dunder methods:
      - Operator overloading allows you to define custom behavior for operators when they are used with objects of your class. Examples of the dunder/magic methods that can be used for overloading operators are \_\_add\_\_ for addition, \_\_sub\_\_ for subtraction, \_\_mul\_\_ for multiplication, and \_\_div\_\_ for division.
      - `__call__`
         - The \_\_call\_\_ method in Python allows an instance of a class to be called as if it were a function. This means you can use parentheses (()) after an object of the class, just like calling a function, and Python will execute the \_\_call\_\_ method of that object.
         - ```python
           class Home:
             def __init__(self, size, value):
                 self.size = size
                 self.value = value
         
             def __call__(self, check='average'):
                 """
                 Return the size, value, or average value per unit size based on the 'check' argument.
                 """
                 if check == 'size':
                     return self.size
                 elif check == 'value':
                     return self.value
                 else:
                     return self.value / self.size
            
            
            # Create an instance of Home
            h1 = Home(3270, 986500)
            
            # Example usage
            print(h1())  # Using the default value for the keyword argument ('average')
            print(h1(check='size'))  # Check the size of the home
            print(h1('value'))  # Check the value of the home
      - `__new__`
         - The \_\_new\_\_ method is a special dunder method in Python that is responsible for creating a new instance of a class. It is called before \_\_init\_\_ and is used in cases where control over the creation of a new instance is necessary. This method is especially useful when dealing with immutable types (like tuples or strings) or when implementing design patterns such as singletons.
         - ```python
           class TravelPlan:
             _places = {} # A class-level dictionary to store travel destinations 
             _step = 0 # A class-level counter to keep track of the number of stops
         
             def __new__(cls, newPlace): # The __new__ method is called before __init__ and is used to control object creation
                                         # It checks if the newPlace is already in the _places dictionary
                 if newPlace in TravelPlan._places.values():
                     print(f'{newPlace} is already in the plan!')
                     return newPlace # Instead of creating a new instance, return the newPlace string directly
                 else:
                     return super(TravelPlan, cls).__new__(cls)
                     # We are calling the super function, which takes two arguments: the first argument specifies the class from which you want to start looking
                     # for the __new__ method. In this case, it is the superclass of TravelPlan, 'object'. The second argument is the class whose __new__ method
                     # you want to call. The __new__(cls) creates a new instance of TravelPlan, initializing the __init__.
                     # In other words, the super() function is calling the super class of TravelPlan, which is the generic 'object', 
                     # to call the method '__new__', to create an instance of TravelPlan, which then intializes the __init__ method
             
             def __init__(self, newPlace):
                 # This method is only called if a new TravelPlan instance was created
                 TravelPlan._places[TravelPlan._step] = newPlace # You can access class attributes directly using the class name, if inside the __init__ method.
                 print(f'{TravelPlan._places[TravelPlan._step]} is added.')
                 TravelPlan._step += 1
         
             @staticmethod
             def printPlan():
                 for pl in TravelPlan._places:
                     print(f'Stop {pl + 1}: {TravelPlan._places[pl]}') # Loop through the dictionary
            
            TravelPlan('Vancouver')
            TravelPlan('Seoul')
            TravelPlan('Vancouver')
            TravelPlan.printPlan()
      - `__str__`, `__len__`, `__repr__`
         - `__str__`: Defines a user-friendly, human-readable string representation of an object. It is invoked by the built-in `str()` function and by `print()`. Used when you want a description of the object that is easy to understand for end-users.
         - `__len__`: Defines the behavior of the len() function for objects. Used to return a size, count, or length property of the object.
         - `__repr__`: Provides a detailed string representation for debugging. Used by `repr()` and in interactive sessions to display objects. It can be used to return the object representation of a class instance so that, for example, the object can be saved to and retrieved from a file or database. An object representation can be in the form of a list, tuple, or dictionary, but it has to be returned as a string in order to be written to and read from a file or database.
         - ```python
           class Graduate:
                student_id = 260374177
            
                def __init__(self, fullname):
                    firstname, lastname = fullname.split(' ')
                    self.firstname = firstname
                    self.lastname = lastname
                    self.student_id = self.__class__.student_id
                    self.__class__.student_id += 1
            
                @classmethod
                def newGraduate(cls, firstname, lastname):
                    return cls(f'{firstname} {lastname}')
                
                def __str__(self): # Provides a human-readable string representation of the object. 
                                   # It's used by the print() function and str() to convert the object to a string.
                    return f'{self.firstname} {self.lastname}' # Returns a string combining the firstname and lastname attributes of the Graduate instance. 
                                                               # When you call print(g0), it will output Jiyeol Yang for g0
            
                def __len__(self): # Returns the length of the object. This is used by the len() function to determine the size of the object.
                    return len(self.firstname) + len(self.lastname) + len(str(self.__class__.student_id)) # This method calculates and returns the total length 
                                                                                                        # of the firstname, lastname, and student_id 
                                                                                                        # (converted to a string). For g0, if firstname is 
                                                                                                        # Jiyeol and lastname is Yang and student_id is 260374178, 
                                                                                                        # len(g0) would be 6 + 4 + 9 = 19.
                def __repr__(self): # Provides a string representation that is useful for debugging and development. 
                                    # It should ideally return a string that, when passed to eval(), would recreate the object.
                    return f"firstname:{self.firstname}, lastname:{self.lastname}, student_id:{self.student_id}"
                """
                This method returns a string with a detailed representation of the Graduate object. 
                It's meant to be unambiguous and could be used for debugging. The output might be something like 
                {'firstname':Jiyeol, 'lastname':Yang, 'student_id':260374178} for g0."""
         
            g0 = Graduate('Jiyeol Yang')
            print(g0) # Uses __str__ to print a string representation of the object; Output "Jiyeol Yang"
            print(g0.student_id) # Output "260374177"
           
            g1 = Graduate.newGraduate('Lackyoung', 'Son')
            print(len(g1)) # Output 21
            print(repr(g1)) # Output firstname:Lackyoung, lastname:Son, student_id:260374178
        ```

### Dunder Methods and Binary Operators
| **operator** | **Dunder Method** | **Description**|
|---|---|---|
| `+`           | `__add__(self, other)`       | Adds `self` and `other`.                          |
| `-`           | `__sub__(self, other)`       | Subtracts `other` from `self`.                    |
| `*`           | `__mul__(self, other)`       | Multiplies `self` and `other`.                    |
| `//`          | `__floordiv__(self, other)`  | Performs floor division (integer division).       |
| `/`           | `__truediv__(self, other)`   | Divides `self` by `other`.                        |
| `%`           | `__mod__(self, other)`       | Computes the remainder of division.               |
| `**`          | `__pow__(self, other[, mod])`| Raises `self` to the power of `other`. Optionally takes a modulus value. |

- ```python
  class Number:
       def __init__(self, number):
           self.number = number
   
       def __add__(self, other):
           return self.number + other.number
   
       def __sub__(self, other):
           return self.number - other.number
   
       def __mul__(self, other):
           return self.number * other.number
   
       def __floordiv__(self, other):
           return self.number // other.number
   
       def __truediv__(self, other):
           return self.number / other.number
   
       def __mod__(self, other):
           return self.number % other.number
   
       def __pow__(self, other):
        return self.number ** other.number

   first_num = Number(10)
   second_num = Number(4)

   print(first_num.__add__(second_num)) # Output "14"
  ```
| **Operator** | **Dunder Method**            | **Description**                                    |
|---------------|-------------------------------|----------------------------------------------------|
| `<<`          | `__lshift__(self, other)`    | Performs bitwise left shift.                      |
| `>>`          | `__rshift__(self, other)`    | Performs bitwise right shift.                     |
| `&`           | `__and__(self, other)`       | Performs bitwise AND.                             |
| `^`           | `__xor__(self, other)`       | Performs bitwise XOR.                             |
| `|`           | `__or__(self, other)`        | Performs bitwise OR.                              |


