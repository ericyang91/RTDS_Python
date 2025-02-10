# Road to Data Science: Python

## Table of Contents
- [Introduction](#intro)
- [Essential Building Blocks of Computer Programs](#building)
- [Flow Control of Statements](#flow)
- [Handle Errors and Exceptions](#error)
- [Sequences, Sets, Dictionaries](#seq)
- [Algorithms](#algo)
- [Handling Text Files](#text)
- [Define and Use Functions](#functions)
- [Object-Oriented Programming (OOP)](#oop)
- [Modules and Packages](#module)

<h2 id ='intro'>Introduction</h2>

<details>
<summary><h2 id ='building'>Essential Building Blocks of Computer Programs</h2></summary>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Essential%20Building%20Blocks%20of%20Computer%20Programs%20Exercises.ipynb)

### Python Identifiers
- What are names or **identifiers** in Python? What characters can be used to make identifiers?
    - In Python, identifiers are names used to identify *variables*, *functions*, *classes*, *modules*, or any other entities in a program.
    - Identifiers can consist of **letters** (both small and large), **digits**, and **underscores**. Identifiers are *case-sensitive*, and cannot start with a digit. They can be of any length.
    - Different identifiers may be used to refer to the same memory location (a = 5, b = 5) and hold the same data or program code.
    - Changing one identifier to refer to something else will not change the value referred by the other identifier.
    - Python also uses the underscore as an identifier for a very special variable to hold the result of the last evaluation only when Python is running in an *interactive mode*.
    - Popular conventions: lowercase identifiers for variables and function names (x), capitalized class names (StatsClass), uppercase identifiers for constants (PI), underscores for separating the words.
    - How do we assign identifiers without causing confusion? 
        1. Follow L(local)E(enclosed)G(global)B(Built-in) rule.
        2. When a variable is defined both locally and globally, when it is used within the local function, its local definition is used. When a variable is defined only globally, and when it is used within the function, it is resolved to its global definition.
        3. A local name defined in a _function_ will not be seen anywhere outside the function.
        4. A local name defined in a _class_ can be seen outside the class or its objects if the name is not a private member of the class, with an explicit reference to the name with dot notation. For example, a name X defined in class C can be accessed using C.X, or O.X if O is an object of C.
        5. A name Nx globally defined in a Python script file named M1.py can be seen inside another Python script file by either importing the name explicitly from M or by importing M1 as a whole and using dot notation M1.Nx to access Nx.
     
| Identifier | Answer | Reason |
|------------|--------|--------|
| D3A | Can be used | It starts with a letter and is alphanumeric. |
| 5ty | Cannot be used | An identifier cannot start with a number. |
| x6 | Can be used | It starts with a letter and is alphanumeric. |
| if | Cannot be used | *if* is a reserved word in Python. |
| program | Can be used | *program* is not a reserved word in Python. |
| h$ | Cannot be used | An identifier cannot have the *$* symbol. |
| title | Can be used | *title* is not a reserved word in Python. |
| john | Can be used | *John* is not a reserved word in Python. |
| \_\_init\_\_ | Can be used | It is a dunder in Python, therefore, while technically usable, it's typically reserved for special methods |
| p_q | Can be used | An identifier can consist of underscores. |

### Python Reserved Keywords and Dunders
- What are reserved **keywords** in Python? What does each keyword mean in Python?
    - if, elif, else, and, as, class, del, except, True, False, for, in, is, lambda, None, return, with, while, await, break, continue, assert, yield, local, global, nonlocal, raise, finally etc.
    - They must not be used as identifiers.
- In Python, some identifiers are in the form of \_\_word\_\_ beginning and ending with two underscores. What special usage do such identifiers have in Python?
    - They are called **dunder methods** (double underscore). They have been given special meanings and hold special data/function and are called in specific situations. Technically, we can assign values to dunders, but it is not recommended.
 
### Primary Data Types
- What *primary types of data* can you use in Python?
    - Numbers (integers, floats, complex numbers), strings, booleans (True/ False)
- What are **Boolean values**? How are they represented in Python?
    - 0, '' (empty string), None are equivalent to False.
    - Empty string, empty tuple, empty set, empty dictionary are equivalent to False.
    - Everything else is equivalent to True. `(Bool('school'))` is equivalent to True.
    - bool([0,0,0,0]) is TRUE because it is not empty. It evaluates the list itself.
    - Lists are considered true unless they are empty.
    - any([0,0,0,0]) is FALSE because all elements inside the list are 0. The function evaluates elements in an iterable.
- What are **integers**? How big can they be?
    - Can be of arbitruary size, at least theoretically. In implementation, we can see the maximum integer by calling `sys.maxsize`
- How do you represent **binary** integers?
    - `bin(int)` converts an integer to its binary representation as a string.
- How do you represent **hexadecimal** integers?
    - `hex(int)` converts an integer to its hexadecimal representation as a string.
- What operators can you use on integers?
    - +, -(subtraction), *, /, **, -(negation), %(modulo), //(floor division)
- What is the difference between the / and //
    - Classic division vs. integer division operators
    - Integer division returns an integer rounded down.
- What is the modular operator in Python?
    - %
    - Returns the remainder of a division
- What are **float** numbers in Python?
    - Float numbers are numbers represented by decimals, in the form 12.5 in decimal notation or 1.25e1 in scientific notation.
- What operators can you use on float numbers?
    - +, -, *, /, **, //, %
    - You can use underscore to separate large numbers, similar to commas; 123_456_789.32
- How big can a float number be in Python?
    - `sys.float_info.max`
- How do you convert a float number to an integer?
    - `int(float)` simply removes decimals.
    - `round()`
- What are complex numbers?
    - A complex number is a representation of a point on a plane with X and Y axes that take the form of x + yj, in which x and y are float number that represent and define the location of a point on the plane. Examples of complex numbers are 1 + 1j, 3 − 6j, 2.5 − 8.9j, and so on (Notice the j's!).
- How do you represent complex numbers in Python?
    - x = 3.5 + 6.7j, etc.
- What operators can you use on complex numbers?
    - Same as float
- What built-in methods can be used on complex numbers?
    - `real`, `imag`, `conjugate()`, etc.

### Compound Data Types
- What are **compound data types** in Python?
    - **Sequential**
        - Strings: indexed and ordered but immutable
        - Lists: indexed and ordered and mutable
        - Tuples: indexed and ordered but immutable
    - **Non-sequential**
        - Sets: not ordered but mutable (However, it can only hold immutable elements whereas lists and tuples can hold any element!)
        - Dictionaries: not ordered; immutable keys, mutable/immutable values
- What are **strings** in Python?
    - It is a type of sequential compound data type that can be indexed and is ordered. It is a sequence of characters, numbers, and symbols enclosed in a pair of double quotation marks or single quotation marks.
    - It is immutable.
- How do you represent strings?
    - '' or "" or """ """ for long strings that needs to span more than one line.
    - You can also use the backslash \ to cancel the invisible newline ASCII character.
    - \n starts a new line
    - \t creates a tab
- How do you include special characters such as ‘, “, and \ in a string?
    - Add a backslash \
- How do you form a string using the f operator?
    - f is a prefix (the other common prefix being r) that is used before the opening quote.
    - It causes the evaluation of expressions enclosed within {}.
    - With r, nothing in the string is evaluated, not even the backslash.
- How do you form a string across multiple lines?
    - """
- What operators, built-in functions and methods can be used on strings?
    - Operators: +, *, ==, !=, and other comparison operators
    - Built-in functions: len(), str(), format()
    - Methods: .lower(), .capitalize(), .upper(), etc.
- What constants are built into Python?
    - True, False, None, \_\_debug_\_, quit, exit, copyright, credits, license, \_\_name_\_, etc.
- What are **lists**?
    - Lists are compound, sequential data type that encloses in square brackets different data types.
    - Multiple lists can be joined together with operator +.
- How do you construct a list?
    - Square brackets
    - `list()`
- How do you access an element in a list?
    - You acces an element by calling the corresponding index.
- How do you get a sublist from a list?
    - You use list slicing. `L[start:stop:step]`
- How do you use the range() function in Python?
    - `range(start, stop, step)`
    - Start is inclusve while Stop is exclusive.
- How do you represent a multi-dimensional array with a list?
    - list = [[list_1], [list_2], [list_3]]
- What are **sets** in Python?
    - Compound, non-sequential data type that encloses in curly brackets immutable data.
    - Sets themselves are mutable.
    - Sets are unordered and unindexed.
    - You can use membership operator *in* to test if an object is a member of a set.
    - All members are unique in a set.
- What are **tuples** in Python?
    - Compound, sequential data type that encloses in parantheses different data types.
    - Tuples themselves are immutable, but it can contain both mutable and immutable data types.
    - You can create a tuple using parantheses.
    - `list(tuple)` converts a tuple into a list.
- How do tuples differ from lists?
    - Tuple is immutable.
- How do you slice a string, a list, and a tuple in Python? What is slicing?
    - Slicing in Python refers to extracting a portion (subsequence) of a sequence (such as a string, list, or tuple) by specifying a range of indices.
- What are **dictionaries** in Python?
    - It is a collection of comma-separated key-value pairs enclosed in curly brackets and separated by a colon :.
    - It is a compound, non-sequential data type.
    - The members are unindexed and unordered.
    - Keys are used to retrieve the values. Keys must be unique.
What built-in functions are available in Python?
    - Built-in functions include set(), list(), tuple(), float(), int(), str(), which are also called constructors or converters because they are used to construct or convert to one respective type of data from another type.
- How do you use print and input statements in your programs?
    - `print()`
        - sep argument decides how multiple values in a print statement should be separated. Default is an empty space.
        - end argument decides how the print statement should end. Default is \n.
    - `input()`
        - Everything taken from the user input is treated as a string.
        - To provide more detailed instructions in the prompt to the user, use triple quotation marks to include multiple lines of instruction as prompt.

### Other Python Basics

- In your program, how do you use a standard library/module that comes with Python distribution?
    - import
- What are **docstrings** in Python programs?
    - It is a special type of string used to document a specific segment of code. Docstrings are used to describe the purpose, functionality, and usage of code elements like modules, classes, methods, and functions. They help developers understand the code and its intended use, making the codebase easier to maintain and extend.
    - It is a formal documentation of the program or module and is accessible through the built-in help() function, with the _doc_ variable automatically attached to each module, function, class and method, whereas end-of-line comments are not.
    - A docstring should also be written for every function, class, and public method right after the header of the definition. Docstrings must be indented the same amount as the suite of function or class definition.
    - Limit the maximum line length to 79 or 72 characters if the line is part of a docstring.
    - Use inline comments whenever necessary.
    - Some code may need more than one line of comments, which makes it a block comment. A block comment should be written right before the code and indented to the same level as the code below.

- What is an end-of-line comment in a Python program?
    - An end-of-line comment is usually used to explain what the code on the line does. Everything behind the # mark on that line is ignored by Python Virtual Machine (PVM) and intended for only humans to read. An end-of-line comment can also be started at the beginning of a line.
- How do you write a code block in Python? Why is proper indentation important in Python programs?
    - In programs, some statements are grouped and run in sequence as a unit or a suite. We call such a group of statements a code block. Unlike C, C++, Java, and some other languages that use curly brackets to make code blocks, *Python uses indentation to form code blocks*. In Python, a program can have multiple code blocks, and code blocks can be nested with proper indentation. Statements intended to be in the same code block must use the same indentation.
    - Rule of thumb: statements in the same code block share the same indentation. For statements inside the compound statements such as *if* or *while*, statements are indented to form a code block as a suite for the compound statements.
- A quick overview of the types of results you can expect when using various arithmetic operators with different types of numbers (integers and floats):
    - Addition, Subtraction, Multiplication: When both operands are integers, the result is an integer. When one of the operands is a float, the result is a float.
    - Division: *The result is always a float*, regardless of the operand types.
    - Floor Division, Modulus: When both operands are integers, the result is an integer. When one of the operands is a float, the result is a float.
    - Exponentiation: When both operands are integers, the result is an integer. When one of the operands is a float, the result is a float.
    - Except for modulus and floor division where the result is 'TypeError', any operations involving one or more complex numbers will result in complex numbers.
- Operations precedence rules:
    1. Exponent operation (**) has the highest precedence.
    2. Unary negation (−) is the next.
    3. Multiplication (*), division (/), floor division (//), and modulus operation(%) have the same precedence and will be evaluated next unary negation.
    4. Addition (+) and subtraction (−) are next, with the same precedence.
    5. Comparison operators are next, with the same precedence.
    6. The three logical operators (not, and, or) are next, with not having the highest precedence among the three, followed by and, then or.
    7. When operators with equal precedence are present, the expression will be evaluated from left to right, hence left association.
    8. Parentheses can be used to change the order of evaluation.
- When a comparison is applied to lists or tuples, the comparison will be applied to pairs of items, one from each list or tuple, and the final result is True if there are more Trues; otherwise it will be False.
- *Logical operators* are used to form logical expressions. Any expression whose value is a Boolean True or False is a logical expression.
- **Assignment operators**:
    - x += y is x = x + y
    - x -= y is x = x - y
    - x *= y is x = x * y
    - x *= y + z is x = x * (y + z)
    - x /= y is x = x / y
    - x %= y is x = x % y
    - x //= y is x = x // y
    - x **= y is x = x ** y

- **Identity operators** (is/ is not):
    1. x = 3; y = 1 + 2
        - x is y
            - This returns True.  
    2. x = [1,2,3]; y = [1,2,3]
        - x is y
            - This returns False.
            - The expression x is y evaluates to False because x and y are two different objects in memory, even though they contain the same values.
            - If x = y, then x is y returns True
- **Sequence operators** (Strings, Lists, Tuples):
    - *: repeats a sequence
    - +: adds sequences
    - [n]: slice out a member of the sequence based on its index
    - [n:m]: slice a sequence start from n inclusive to m exclusive
- **Membership operators** are used to test whether an element is a member of a sequence.
    - v in s
    - v not in s
    - . operator is used to access members of objects, modules, or packages.
        - `pd.DataFrame()`
        - `math.sqrt(35)`
- The precedencies of operators:
    1. Within arithmetic operators, other operators take precedence over addition and subtraction.
    2. Arithmetic operators take precedence over comparison operators.
    3. Membership operators, identity operators, and comparison operators take precedence over logic operators.
    4. Among logic operators, the order of precedence, from high to low, is not > and > or.
- For a more complex application, several or even hundreds of Python files may be needed. Of these files, there will be only one Python file defining the starting point of the program that implements the application, while all other files are used as modules to be imported into the main Python file, either directly or indirectly. So essentially, the relationships of all the Python files used for an application can be depicted as a tree in which the root is the main Python file.
- [How a Python Code Should be Written](https://pep8.org/)
    1. A Python program/script file should begin with a docstring as the main documentation of the program file, stating the application and functionality of the program, as well as the author and revision history.
    2. In a script file, use **double blank lines** to separate the actual program code from the documentation section at the beginning of the file.
    3. Also use double blank lines to separate top-level function and class definitions.
    4. Use a single blank line to surround the definition of a method in a class definition.
    5. Pay attention to indentation, especially when an expression, a simple statement, or the header of a compound statement is too long and needs to cross multiple lines.
        1. When an expression or a statement needs a closing brace, bracket, or parenthesis mark to complete it, there is no need to escape (\) newline at the end of an unfinished line.
        2. When a string needs to cross multiple lines, newline must be escaped by putting a backslash at the end of each unfinished line.
        3. The four-space rule is optional. The next line can be started wherever it makes more sense, such as in the column next to the opening delimiter.
- Annotated assignment statement

- **Compound Statements**:
    - A compound statement consists of at least one clause, and each clause is made of a header and a suite, or code block. A header starts with a keyword such as if-elif-else, for, while, class, def, try-except, finally, and so on and ends with a colon ":".
  
- Rules of Indentation:
    1. The first line of code of a program must start at the very first column of line, though there can be some blank lines before the first line of code, for better readability, if you like.
    2. All lines of code in the same code block must be indented the same.
    3. The suite of a compound statement must be indented further than the header of the compound statement.
    4. All code blocks that are at the same level must use the same indentation.
    5. All lines of code in the same suite must use the same indentation.
- Rules of Spacing:
    1. There must be at least one space between two words.
    2. As a convention, there should be only one space between two words.
    3. Also as a convention, there should be one space before each operator and one space behind each operator in an expression. So x>y should be written as x > y.
    4. For better readability, there should be no space between a unary negation operator (−) and the term it negates. So -x should be written as -x.
    5. Also for readability, in a function call, there should be no space between a function name and the list of parameters. So abs (y) should be written as abs(y).
    6. The same goes for definitions of functions. There should be no space between the function name and the list of arguments.
    7. There should be no blank lines between lines of simple statements if they are intended to be in the same code block.
    8. For better readability, there should be a blank line between simple statement(s) and compound statements if they are in the same code block.


### Character Standards and Encoding
- **ASCII**:
    - ASCII is a character encoding standard used to represent text in computers and other devices.
    - It uses 7 bits to represent 128 (2^7) different characters, including control characters, uppercase and lowercase English letters, digits, and punctuation marks.
    - Originally developed for telecommunication equipment, ASCII is widely used for representing English text in computers and communication protocols.
- **Unicode**:
    - Unicode is a character set or standard that assigns unique code points (numeric values) to every character in the world’s writing systems, symbols, and special characters. It’s a universal character set that defines a unique identifier for each character. Unicode values, also known as code points, are unique numbers assigned to each character in the Unicode standard. The Unicode standard provides a consistent way to represent text from various languages, symbols, and special characters across different platforms and systems. 
    - Here are the key points about Unicode values:
        - Each character is assigned a unique number: Every character in Unicode is mapped to a unique integer value called a "code point". For example, the letter 'A' has a code point of 65, 'B' has a code point of 66, and so on.
        - Unicode is a standard: It includes characters from almost every writing system, including Latin, Cyrillic, Arabic, Greek, Chinese, and more. It also includes special characters like emojis, mathematical symbols, and control characters.
        - Unicode values are represented in hexadecimal: Unicode code points are often represented in hexadecimal (base 16), and in Unicode notation, a code point is usually written as U+<hexadecimal \value>. For example, the code point for 'A' is U+0041 (hexadecimal 41).
        - `ord('A')` Converts a character into its Unicode code point (a numeric representation of the character).
            - Output: 65
        - `chr(65)`Converts a Unicode code point (an integer) back into its corresponding character.
            - Output: A
        - ```python
          asc = {chr(character) for character in range(ord('A'), ord('Z')+1)}
          print(asc) # Output: {'X', 'E', 'R', 'W', 'L', 'H', 'U', 'D', 'K', 'J', 'Y', 'P', 'G', 'B', 'M', 'C', 'I', 'O', 'F', 'Z', 'Q', 'T', 'A', 'V', 'N', 'S'}
          ```
     
- **Encoding**:
    - Encoding defines how Unicode code points (numbers) are represented in binary format, i.e., how they are stored in memory or written to a file.
    - Common Unicode encodings include UTF-8, UTF-16, UTF-32
    - What is **UTF-8**?
        - Variable-width encoding where each character is represented by 1 to 4 bytes.
        - ASCII characters (code points 0-127) are represented by a single byte (7 bits), maintaining compatibility with ASCII.
        - Non-ASCII characters are represented by multiple bytes, with the number of bytes depending on the character's code point.
        - https://www.youtube.com/watch?v=DntKZ9xJ1sM
        - The *default encoding of Python programs is UTF-8*, which includes Unicode, so you can simply include any Unicode character in a string and PVM will recognize and handle it correctly (including emojis, Korean characters, etc.)

</details>

<details>
<summary><h2 id='flow'>Flow Control of Statements</h2></summary>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Flow%20Control%20of%20Statements.ipynb)

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

</details>

<details>
<summary><h2 id='error'>Handle Errors and Exceptions</h2></summary>

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

</details>

<details>
<summary><h2 id='seq'>Sequences, Sets, Dictionaries</h2></summary>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Use%20of%20Sequences%2C%20Sets%2C%20Dictionaries%2C%20and%20Text%20Files.ipynb)

### Basics of Sequences, Sets, Dictionaries

- What data types are categorized as sequences?
   - **Sequences** are types that can be **ordered** and **indexed**. In Python, these include **strings**, **lists**, and **tuples**.

- What are strings, lists, and tuples?
   - These are Python data types that allow ordering, slicing, and indexing.

- How do you access individual characters of a string, a list, and a tuple?
   - For strings: `string[index]`
   - For lists: `list[index]`
   - For tuples: `tuple[index]`

- How do you slice a sequence?
   - For strings: `string[start:end]`
   - For lists: `list[start:end]`
   - For tuples: `tuple[start:end]`

- What are **mutable** and **immutable** data types?
   - Mutable types can be modified after creation, like lists and sets..
   - Immutable types cannot be changed after creation, like tuples.

- How do you access the items, keys, and values of a dictionary?
   - Items: `d.items()`
   - Keys: `d.keys()`
   - Values: `d.values()`

- What is an **iterator**?
    - An iterator lets you loop through elements in an iterable like **lists**, **strings**, **tuples**, **sets**, or dictionaries. Use `iter(iterable)` to create an iterator and `next(iterator)` to get items. Python handles this automatically in loops.

- What is a **generator** of iterables?
    - A generator is a type of iterable created using a function with `yield`. Generators are efficient because they produce items one at a time.
  
- How do you use `range()` to make a list?
    - Use: `list(range(10))` to create a list of numbers from 0 to 9.

- How do you use `range()` to create a tuple?
    - Use: `tuple(range(10))` to create a tuple of numbers from 0 to 9.
 
### Strings

- **Strings** are sequences of characters that are *ordered* and *indexed*.
- **Strings** are immutable, meaning that any *slicing*, *concatenating*, or *replacing* operations will create a new string and not modify the existing.
- To convert other data types to a string, use the built-in `str()` function.

- **Methods of the String Class**
  - Note that string methods do not modify the original string; they return a new string with the changes.
  - `s.capitalize()`: Capitalizes the first letter of the string and makes the rest lowercase.
  - `s.casefold()`: Converts all characters to lowercase.
  - `s.center(10)`: Centers the string within a space of 10 characters.
  - `s.count('i')`: Counts the occurrences of 'i' in the string.
  - `s.startswith('i')`: Returns `True` if the string starts with 'i'.
  - `s.endswith('i')`: Returns `True` if the string ends with 'i'.
  - `s.expandtabs(10)`: Sets tab size to 10 spaces.
  - `s.find('i')`: Finds the first occurrence of 'i' and returns its index, or `-1` if not found.
  - `s.index('i')`: Finds the first occurrence of 'i' and returns its index, or raises `ValueError` if not found.
  - `s.isalnum()`: Returns `True` if all characters are alphanumeric. Space is not alphanumeric.
  - `s.isalpha()`: Returns `True` if all characters are alphabetic. Space is not aphabetic.
  - `s.isdecimal()`: Returns `True` if all characters are decimal digits (no decimals or hyphens allowed).
  - `s.isdigit()`: Returns `True` if all characters are digits (includes Unicode digits not limited to the commonly used ASCII digits (0 to 9), but also include digits from various writing systems and cultures around the world).
  - `s.isnumeric()`: Returns `True` if all characters are numeric (same as .isdigit() but broader and includes fractions and Roman numerals. Does not include decimals or hyphens.).
  - `s.islower()`: Returns `True` if all characters are lowercase.
  - `s.isupper()`: Returns `True` if all characters are uppercase.
  - `s.isprintable()`: Returns `True` if all characters are printable.
  - `s.isspace()`: Returns `True` if all characters are whitespace.
  - `s.istitle()`: Returns `True` if the string is title-cased (first letter of each word is uppercase).
  - `SEP.join(ITERABLE)`: Joins elements of an iterable with a separator. Each element must be a string.
  - `s.lower()`: Converts the string to lowercase.
  - `s.upper()`: Converts the string to uppercase.
  - `s.lstrip()`, `s.rstrip()`, `s.strip()`: Remove whitespace from the left/right/both ends of the string. When called without any arguments, removes all leading and trailing whitespace characters, no matter how many there are. This includes spaces, tabs (\t), and newlines (\n).
  - `s.split(SEP)`, `s.rsplit(SEP)`: Splits the string at the separator and returns a list of substrings excluding the separator. Unlike `s.partition(separator)`, it divides at every separator unless maxsplit=n. If the delimiter is at the start of end of a string, the function will return '' along with the other splitted parts.
      - ```python
        my_str = 'hello world'
        my_str.split('h') # Output: ['', 'ello world']
        ```
      - ```python
        my_str = 'hello world'
        my_str.split('l') # Output: ['he', '', 'o wor' 'd']
        ```
  - `s.partition(separator)`, `s.rpartition(separator)`: Splits the string into a tuple with three parts around the FIRST (or last in the case of `s.rpartition(separator)` separator while preserving the separator. If the delimiter is at the start of end of a string, the function will return '' along with the other splitted parts.
      - ```python
        my_str = 'hello world'
        my_str.partition(' ') # Output ('hello', ' ', 'world')
        ```
  - `s.replace(s1, s2)`: Replaces occurrences of `s1` with `s2` in the string.
  - `s.splitlines()`: Splits the string at line breaks and returns a list of lines. Blank lines are treated as ''.
  - `s.title()`: Converts the first letter of each word to uppercase and the rest to lowercase.

- **Built-in Functions and Operators**
  - +: Concatenates strings.
  - *: Repeats strings.
  - `len(STRING)`: Returns the length of the string.
  - `STRING[i:j]`: Slices the string from index `i` to `j`.

- **Format Method**
  - `s = "{0} is my wife and {1} is my daughter.".format('Lack Young', 'Dahee')`
  - `{}` are placeholders or replacement fields.
  - Example:
    - `'X: {}; Y: {}'.format(3, 5)` results in `'X: 3; Y: 5'`.
  - You can include conversion types with `!`, such as:
    - `!r`: Converts value to a raw string.
    - `!s`: Converts value to a regular string.
    - `!a`: Converts value to an ASCII string.
  - **Examples:**
    - ```python
      c = 23 - 35j
      print('The complex number {0} has a real part {0.real} and an imaginary part {0.imag}.'.format(c))
      ```
      - Output: `'The complex number (23 -35j) has a real part 23.0 and an imaginary part -35.0.'`
        
    - ```python
      print('{!r} is displayed as a raw string'.format('\t is not tab, \n is not newline'))
      ```
      - Output: `'\t is not tab, \n is not newline' is displayed as a raw string.`
        
    - ```python
      print('{!s} is not displayed as a raw string'.format('\t is a tab'))
      ```
      - Output: `'	 is a tab is not displayed as a raw string'`
        
    - ```python
      print('{!a} is displayed as an ASCII string'.format('Python is not 大蟒蛇.'))
      ```
      - Output: `'Python is not \u5927\u87d2\u86c7.' is displayed as an ASCII string.`

  - **Note:** The `print()` function works with escape characters like \t and \n. These characters are interpreted as special characters within the string.
 
### Lists

- **Lists** are *ordered* and *mutable* collections of elements.
- **Creating a List:**
  - `list(iterable)` - Converts an iterable into a list. Note, `list('a','b','c') is invalid as it is not an iterable.
  - `[a, b, c, d]` - Initializes a list with elements `a`, `b`, `c`, and `d`.
  - `list(range(1, 4))` - Generates a list from a range object, resulting in `[1, 2, 3]`.

- **Slicing Lists:**
  - `l[start:end:step]` - Extracts a slice from the list starting at index `start`, ending at `end`, and stepping by `step`.

- **Replacing Elements:**
  - `l[N] = E` - Replaces the element at index `N` with `E`.

- **Concatenating Lists:**
  - `l1 + l2` - Combines `l1` and `l2` into a new list.
  - Note: *This operation does not modify `l1`. To store the result, assign it to a new variable.*

- **Duplicating Lists:**
  - `l1 * 3` - Creates a new list with `l1` repeated three times, leaving the original list unchanged.

- **Checking Membership:**
  - `N in l1` - Returns `True` if `N` is present in `l1`.

- **List Length:**
  - `len(l1)` - Gives the number of elements in `l1`.

- **List Methods:**
  - `l.append(x)` - Appends `x` to the end of the list.
  - `l.clear()` - Clears all elements from the list.
  - `l.copy()` - Returns a shallow copy of the list. A shallow copy creates a new list containing references to the same elements as the original list. This means: Changes to elements in the original list will not affect the shallow copy if the elements are *immutable* (like numbers or strings). However, for nested *mutable* objects (like other lists or dictionaries inside the list), changes to these objects will be reflected in both the original and the shallow copy because the nested objects themselves are not copied.
      - ```python
        original = [[1, 2], 3, 4]
        copied = original.copy()

        copied[0][0] = 10
        copied[1] = 22

        print(original) # Output: [10, 2], 3, 4
        print(copied) # Output: [10, 2], 22, 4
        ```
  - `l.index('dahee')` - Finds the index of the first occurrence of 'dahee'. Raises *ValueError* if not found.
  - `l.pop()` - Removes and returns the last element of the list.
  - `l.pop(2)` - Removes and returns the element at index '2'.
  - `l.reverse()` - Reverses the order of elements in the list in place. Returns *None* if assigned to a variable.
      - In order to create a new reversed list without modifying the original, use `l2 = l[::-1]`
  - `l.sort()` - Sorts the *original* list in ascending order without creating a new list. Returns *None* if assigned to a variable. Use `l.sort(reverse=True)` for descending order. This method only works on lists.
  - `sorted(l)` - Creates a new list that is sorted in ascending order. This method works on other iterables such as tuples and sets. Always returns a new *list* even if applied on other iterables.
  - `l1.extend(l2)` - Appends elements from 'l2' to 'l1'. Modifies the original list whereas concatenating two lists create a new list.
  - `l.insert(5, 14)` - Inserts '14' at index '5'. Does not replace the value at the existing index. Modifies the existing list.
  - `l.remove(5)` - Removes the first occurrence of '5' from the list. Modifies the original list.
  - `l.count('a')` - Counts how many times 'a' appears in the list.

- **Nested or Embedded Lists:**
  - Can represent structured or two-dimensional data.

### Tuples

- **Tuples** are *ordered* collections that cannot be modified (*immutable*).

- **Counting Occurrences:**
  - `t.count('e')` - Counts how many times 'e' appears in the tuple.

- **Finding the Index of an Element:**
  - `t.index('dahee')` - Finds the index of the first occurrence of `'dahee'`. Raises a `ValueError` if `'dahee'` is not present.
  - Note, unlike lists, tuples *do not* have method `.find()`

- **Creating a Tuple:**
  - `tuple(iterable)` - Converts an iterable into a tuple. tuple('a','b') does not work as 'a' and 'b' are not iterables.
  - `(a, b, c, d)` - Initializes a tuple with elements 'a', 'b', 'c', and 'd'.
  - `tuple(range(1, 4))` - Generates a tuple from a range object, resulting in `(1, 2, 3)`.

- **Accessing Elements:**
  - `t[n]` - Retrieves the element at index `n` in the tuple `t`.

- **Slicing a Tuple:**
  - `t[start:end:step]` - Extracts a slice from the tuple starting at index `start`, ending at `end`, and stepping by `step`.

- **Concatenating Tuples:**
  - `T1 + T2` - Combines `T1` and `T2` into a new tuple.
  - **Note:** This operation does not modify `T1`. To keep the result, assign it to a new variable.

- **Duplicating Tuples:**
  - `T1 * 3` - Creates a new tuple with `T1` repeated three times, leaving the original tuple unchanged.

- **Checking Membership:**
  - `N in T1` - Returns `True` if `N` is in `T1`.

- **Tuple Length:**
  - `len(T1)` - Provides the number of elements in the tuple `T1`.

- **Single-value Tuple**
    - Tuples can have single value. Must include trailing comma. For instance, `t = (1,)`. This tuple has one element, 1.

- Note that tuples, unlike lists, do not have methods that modify the original tuple because tuples are **immutable** in nature.


### Sets

- **Sets** are *unordered* collections that are *mutable* and *do not allow duplicate elements*.

- **Creating a Set:**
  - `set(iterable)` - Converts an iterable into a set. `set('a', 'b')` raises AttributeError as 'a' and 'b' are not iterables.
  - `{a, b, c, d}` - Initializes a set with elements 'a', 'b', 'c', and 'd'.
  - `set(range(1, 4))` - Creates a set from a range object, resulting in '{1, 2, 3}'.
  - `set()` creates an empty set. Note, {} is reserved for dictionaries.

- **Checking Membership:**
  - `N in s1` - Verifies if `N` is a member of the set `s1`.

- **Set Length:**
  - `len(s1)` - Provides the number of elements in the set `s1`.

- **Adding an Element:**
  - `s1.add(element)` - Adds `element` to the set `s1`. Modifies the original set.
  - Note: `list.insert(INDEX, VALUE)`, `list.append(VALUE)`

- **Clearing a Set:**
  - `s1.clear()` - Removes all elements from the set `s1`.

- **Copying a Set:**
  - `s1.copy()` - Creates and returns a copy of the set `s1`.

- **Finding Differences and Returning a New Set:**
  - `s0.difference(s1, s2)` - Returns a new set containing elements in 's0' but not in 's1' or 's2'. *Returns a new set.*

- **Updating Differences and Modifying the Original Set:**
  - `s0.difference_update(s1, s2)` - Updates 's0' by removing elements that are also present in 's1' or 's2'. *Modifies the original set.*

- **Removing an Element:**
  - `s1.discard('e')` - Removes the element 'e' from the set 's1' if it exists. Does nothing if the element does not exist.
  - `s1.remove('e') - Same, but raises KeyError if the element does not exist.
  - Note: `list.remove('e')`

- **Finding Intersections:**
  - `s0.intersection(s1)` - Returns a new set containing elements that are common to both `s0` and `s1`.

- **Finding Unions:**
    - `s0.union(s1)` - Return a new set containing the union of sets, meaning all the unique elements in both s0 and s1.

- **Updating a Set:**
    - `s0.update(s1)`: Modifies s0 by adding members of s1.

### Dictionaries

- A **dictionary** is an *ordered*, *mutable* collection of **key-value pairs** enclosed in curly brackets.
- A **dictionary** *cannot have duplicate keys*.

- **Creating a Dictionary:**
  - `dict(**kwarg)` - Constructs a dictionary from *keyword arguments*.
    - Example: `dict(a=1, b=2)`
    - Note, in the case of keyword arguments, the keys must be valid identifiers, which means they do not need quotation marks. Valid identifiers are typically simple names like a, b, etc.
    - Example: `dict(zip(['a', 'b'], [1, 2]), c=3, d=4)`
  - `{'a':1, 'b':2, 'c':3}`

- **Accessing and Modifying Elements:**
  - `list(dict)` - Returns a list of keys in the dictionary.
  - `dict[key]` - Retrieves the value associated with 'key' in the dictionary. If the 'key' does not exist, it raises KeyError.
      - Note, `dict.get(key, 'Second Argument') also retrieves the value associated with 'key', but does not raise KeyError if 'key' does not exist. Instead, it returns *None*, or the 'Second Argument' (For instance, 'Not Found').
  - `dict[key] = value` - Assigns 'value' to the specified 'key'. Overwrites if the key already exists.
  - `del dict[key]` - Removes the key-value pair associated with `key` from the dictionary.

- **Checking for Existence and Length:**
  - `k in dict` - Checks if 'dict' contains the key 'k'.
  - `len(dict)` - Returns the number of key-value pairs in the dictionary.

- **Dictionary Methods:**
  - `dict.clear()` - Removes all elements from the dictionary.
  - `dict.copy()` - Creates and returns a shallow copy of the dictionary.
  - `dict.get(k, 'Second Argument')` - Returns the value for the specified key `k`. Returns 'Second Argument' if the key is not found.
  - `dict.items()` - Returns an iterable view object of key-value pairs.
  - `dict.keys()` - Returns an iterable view object of keys.
  - `dict.values()` - Returns an iterable view object of values.
  - `dict.pop(k)` - Removes and returns the value for the key 'k'.
  - `dict.popitem()` - Removes and returns the key-value pair from the end of the dictionary.
  - `dict.update(dict2)` - Update the dict with the key-value pairs in dict2. Modifies dict.
 

### Comprehensions

- List, set, and dictionary comprehensions are compact and efficient ways to create these data structures in Python.
- **List Comprehensions**
    - `[expression for item in iterable if condition]`
    - ```python
      [a * 2 for a in range(1, 11) if a % 2 == 0]
      ```
    - **Outer and inner loops**:
        - In a list comprehension, the first for loop corresponds to the outer loop, and any subsequent for loops or conditions (if present) correspond to inner loops or filtering logic.
        - **[expression for outer in iterable1 for inner in iterable2]**
            - This translates to:
            - ```python
                result = []
                for outer in iterable1:  # Outer loop
                    for inner in iterable2:  # Inner loop
                        result.append(expression)
              ```
            - ```python
              combo = [year + str(month+1) for year in ['2025', '2026'] for month is range(6)] # year corresponds to the outer loop while month corresponds to the inner loop
              ```
- **Set Comprehension**
    - `{expression for item in iterable if condition}`
    - ```python
      {x ** x for x in range(1, 11) if x > 5}
      ```
- **Dictionary Comprehension**
    - `{key_expression: value_expression for item in iterable if condition}`
    - ```python
      original_dic = {'apple':1, 'banana':2, 'cherry':3}

      new_dic = {key.upper():value**2 for key, value in original_dic.items() if value >= 2}
      ```
</details>

<h2 id='algo'>Algorithms</h2>

- **Insertion sort**
    - ```python
      def insertion_sort(number_lst):
        """
        Perform insertion sort on the input list.
    
        This algorithm builds the sorted portion of the list incrementally by taking one element 
        from the unsorted portion and inserting it into its correct position within the sorted portion.
    
        Parameters:
            number_lst (list): The list of numbers to be sorted.
    
        Returns:
            list: The sorted list in ascending order.
        """
        n = len(number_lst)  # Get the length of the list.

        # Loop through the list starting from the second element (index 1).
        for i in range(1, n):
            holder = number_lst[i]  # Store the current element to be inserted.
            j = i - 1  # Start comparing from the last element of the sorted portion.
    
            # Shift elements of the sorted portion that are greater than 'holder' to the right.
            while j >= 0 and number_lst[j] > holder:
                number_lst[j + 1] = number_lst[j]  # Move the larger element one position to the right.
                j -= 1  # Move to the previous element in the sorted portion.
    
            # Insert 'holder' into its correct position in the sorted portion.
            number_lst[j + 1] = holder
    
        return number_lst  # Return the fully sorted list.
      ```

  - **Tower of Hanoi**
  - ```python
      def tower_of_hanoi(n, source, target, temp):
        """
        Solves the Tower of Hanoi puzzle using recursion.
    
        Parameters:
        n (int): Number of discs to move.
        source (str): The starting pole where the discs are initially placed.
        target (str): The destination pole where the discs need to be moved.
        temp (str): The temporary pole used as an intermediary.
    
        Moves 'n' discs from the source pole to the target pole using the temporary pole as a placeholder.
        """
        # Base Case:
        if n == 1:
            # Move a single disc directly from the source pole to the target pole
            print(f'Move disc {n} from {source} to {target}.')
            return
    
        # Recursive Case:
        # 1. Move n-1 discs from the source pole to the temporary pole using the target pole as intermediary
        tower_of_hanoi(n-1, source, temp, target)
    
        # 2. Move the nth (largest) disc directly from the source pole to the target pole
        print(f'Move disc {n} from {source} to {target}.')
    
        # 3. Move the n-1 discs from the temporary pole to the target pole using the source pole as intermediary
        tower_of_hanoi(n-1, temp, target, source)
    ```

<details>
<summary><h2 id='text'>Handling Text Files</h2></summary>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Use%20of%20Sequences%2C%20Sets%2C%20Dictionaries%2C%20and%20Text%20Files.ipynb)

- **The `open()` function**: Used to open a file for reading or writing. It returns a file object, commonly referred to as a file handle, that allows interaction with the file's content.
    - Syntax: `open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)`
    - The file to be opened can be a text file ('t') or a binary file ('b'). For example, for writing to a binary file, use `f = open("file_directory", "wb")`.

- **File Modes:**
  | Mode Function | Description |
  | --- | --- |
  | `r` | Open for reading only; file must exist. Otherwise, raises FileNotFoundError |
  | `w` | Open for writing only; creates a new file or overwrites an existing one. |
  | `r+` | Open for reading and writing; file must exist, does not automatically overwrite. The cursor pointer is set to the beginning of the file. Might need to shift the pointer to avoid overwriting. |
  | `w+` | Open for writing and reading; creates or overwrites the file. |
  | `a` | Open for appending; adds to the end without overwriting. File does not have to exist. |
  | `a+` | Open for appending and reading; adds to the end without overwriting. If you try to read after opening the file, the file handle will not return anything as the cursor is set to the end of the file. |
  | `x` | Create a new file for writing; raises FileExistsError if the file exists. |


- **Optional Arguments:**
  - **Buffering**: Controls the buffering policy. The default value is `-1`, meaning the default buffering policy.
  - **Encoding**: Specifies the encoding for text files. Default is typically UTF-8.
    ```python
    with open('example_ignore.txt', 'w', encoding='ascii', errors='ignore') as file:
        file.write('Some text with special characters: ñ, é, ü')
    ```
    - In this example, the special characters cannot be encoded using ASCII. However, errors are ignored. Therefore, these characters will be ignored and not written to the file.
    ```python
    with open('example_ignore.txt', 'w', encoding='ascii', errors='strict') as file:
        file.write('Some text with special characters: ñ, é, ü')
    ```
    - This code will raise UnicodeEncodeError because the special characters cannot be encoded in ASCII.
  - **Errors**: Specifies how encoding errors are handled. Options include 'ignore' or 'strict'.
  - **Newline**: Controls how newlines are handled in text files. Options include `None`, `''`, `'\n'`, `'\r'`, and `'\r\n'`.


- **File Operations:**
  - After opening a file, operations like read, write, and close are performed on the file handle.
 
- **File Path**:
    - `os.path.join(path, paths)`
        - `The os.path.join()` function in Python is part of the os.path module, which provides utilities for dealing with file and directory paths in a way that is portable across different operating systems. It helps you create file paths by joining one or more path components. The key benefit is that it automatically handles the different path separators (/ on Unix-like systems like Linux and macOS, \ on Windows), so you don’t need to worry about platform-specific issues.
        - path: The first component of the path
        - paths: Additional components to join. Can be multiple
        - ```python
          import os

          path = os.path.join("home", "user", "documents", "file.txt")
          print(path)
          ```

- **Closing the File**:
    - Use `f.close()` to close the file manually.
    - This is needed to prevent data loss. Some data might be temporarily stored in a buffer to improve performance. `f.close()` flushes, or writes the buffered data to disk.
        - When writing to a file, Python may temporarily hold the data in memory (the buffer) to improve performance. This means that changes may not be immediately reflected in the file until the buffer is flushed (e.g., via f.close() or using the with statement.
    - Using a `with` statement *automatically closes* the file when done.
    - Example with `with`:
      ```python
      with open("file_directory.txt", "w") as f:
          f.write('Hello World!')
      ```
    - Example without `with`:
      ```python
      f = open("file_directory.txt", "w")
      f.write('Hello World!')
      f.close()
      ```
      
- **Writing to Files**:
  - `f.write()` writes a single string to the file. Buffering means changes may not appear immediately.
    ```python
    f.write(f'hello\nworld')
    ```
  - `f.writelines(SEQUENCE)` writes multiple strings. Strings must include newline characters if desired.
      - Argument passed into the function must be an iterable like a list or tuple that contains strings.
      - ```python
        with open('file_directory.txt', 'w', encoding='UTF-8') as w:
            w.writelines(['hello\n', 'world'])
        ```
  - If you are writing a file without using the `with open()` statement, you must always use `f.flush()` to flush the new data. Otherwise, the new data will be kept in an internal buffer.
    - In practice, `f.flush()` is unnecessary if you are closing the file immediately after writing, as f.close() will automatically flush the buffer and ensure all data is written to disk. This means that if you use `with open()` statement that automatically closes the file at the end of the code block, `f.flush()` is unnecessary.
  - Both `f.write()` and `f.writelines()` do not automatically write on new lines! Include the \n newline character if you want to write on a new line.
    - For instance, if you want to write `f.writelines(['TEDA INTERNATIONAL SCHOOL', 'CHOIR TEAM', JOY GIVES US WINGS'])` on separate lines, you would write `f.writelines(['TEDA INTERNATIONAL SCHOOL\n', 'CHOIR TEAM\n', 'JOY GIVES US WINGS\n'])`. The f.writelines() will interpret `\n` to mean newlines.
  - Example: Practice creating a multiplication table.

- **Reading from Files**:
  - `f.read(SIZE)` reads the entire file or a specified number of character in a string.
  - `f.readline(SIZE)` reads one line, optionally with a size limit. It stops when it encounters a newline character (\n) or when the specified size is reached, whichever comes first. Returns string.
    ```python
    with open('directory', 'r') as f:
        for line in f:
            print(line, end='') # Default for end is end = '\n'. This may give an additional unnecessary blank line between the two lines. end = '' prevents that.
    ```
    ```python
    f = open('directory', 'r')
    try:
        while True:
            line = next(f)
            print(line, end='')
    except StopIteration:
        f.close()
    ```
  - `f.readlines(SIZEHINT)` reads multiple lines into a list, with a size hint. Returns a list of strings. Each string represents one line from the text.
  - `f.tell()` returns the current position of the file pointer, representing the number of bytes from the beginning. In simple English text, it is safe to assume that 1 byte = 1 character. However, do not use `f.tell()` with `f.readlines(SIZEHINT)` as it will raise OSError. Instead, use it without the SIZEHINT argument.
      - ```python
        with open('Texts/Attack on Titans.txt', 'r+, encoding='UTF-8') as r:
            r.readlines()
            print(r.tell()) # Output 70,900
        ```
  - `f.seek(OFFSET, START)` moves the file pointer by 'OFFSET' from 'START'. If 'OFFSET' is positive, it moves the pointer forward. If 'OFFSET' is negative, it moves the pointer backward.
    - START values:
      - 0: Absolute file start. OFFSET is applied from the beginning of the file.
      - 1: Current file position. OFFSET is applied relative to the current file pointer position.
      - 2: End of file. OFFSET is applied relative to the end of the file.
    - In binary mode such as 'rb' and 'wb', all  three operations are allowed. However, in text mode such as 'r' and 'w', only absolute moves (START=0) are allowed. Relative moves (START=1) is somewhat supported, but OFFSET must be 0. Moves from the end (START=2) is not allowed.
        - Allowed: `seek(OFFSET,0)`, `seek(0,1)` `seek(0,2)`
        - Not Allowed: `seek(OFFSET, 1)`, `seek(OFFSET, 2)` when OFFSET != 0

- **Updating Existing Content**:
  - You can open the file in 'a' mode to amend. The cursor will begin at the end of the existing file to ensure no data is overwritten.
  - OR:
    1. Open the file in 'r+' mode.
    2. Determine the position with `f.tell()`.
    3. Move the pointer with `f.seek(offset, start)`.
    4. Write new content, which will replace old content. Be cautious of overwriting if new content is longer or shorter.

- **Deleting a Portion of a Text File**:
  - Deleting text or a portion of text from a file in Python requires you to read the file's content, modify it as needed (e.g., by removing the portion you want to delete), and then rewrite the file with the updated content. Python doesn't have a built-in method to directly delete text from a file without rewriting it.
  - Here's a general approach to deleting a portion of the text:
    1. Open the file in read mode and read its content.
    2. Modify the content by removing the desired portion.
    3. Open the file in write mode (this will clear the file) and write the updated content back to it.
  - ```python
      # Define the portion of the text you want to delete
      text_to_delete = "Joy"

      # Read the content of the file
      with open("Joy Gives Us Wings.txt", 'r') as file:
          content = file.read()

      # Remove the portion of the text
      updated_content = content.replace(text_to_delete, "")

      # Write the updated content back to the file
      with open("Joy Gives Us Wings.txt", 'w') as file:
          file.write(updated_content)
    ```

  - Refer to the specific handling procedures on page 286.
 
</details>

<details>
<summary><h2 id='functions'>Define and Use Functions</h2></summary>

- [Exercise](https://github.com/ericyang91/RTDS_Python/blob/main/Functions%20Exercises.ipynb)

### Basics of Functions

1. What are **functions**?
    - A **function** is a *block of code* that can be *reused* to perform specific *tasks*.
    - It is composed of the function name and the parameters, into which arguments are passed.
2. Why are functions important in programming and software development?
    - Functions are reusable! It can help programmers solve problems by breaking them down into manageable pieces. It also makes the code easier to read and maintain. It also makes debugging easier because it can be tested individually.
3. What role does the **return** statement play in functions?
    - The **return** statement is used to send a result back from a function to the caller. It also helps control flow by exiting the function as soon as the `return` statement is executed.
4. How do you return **multiple values** from a function?
    - Put the values after the `return` statement in a compound data-type such as lists, tuples, sets, etc. or you can put all the values separated by comma after the return statement.
    - `return a, b, c`. The values are automatically packed in a **tuple**.
5. What are **positional arguments** in a function definition?
    - Positional arguments are the arguments passed to their respective parameters in accordance with their positions. That is, the first parameter in a function call is passed to the first argument in the definition of the function, etc.
    - Definition: `function(a,b,c)`
    - Call: `function(1,2,3)`
6. What are **keyword arguments** in a function definition? What advantages do they offer?
    - A parameter name, such as x, can be used as a keyword to explicitly indicate that a specific value, such as v, will be passed to x. This is done using x = v.
    - Definition: `function(a, b, c)`
    - Call: `function(b = 2, a = 1, c = 3)`
        - Advantage: not restrained to the order of arguments
    - *You cannot pass positional arguments AFTER keyword arguments!*
        SyntaxError:
            - Definition: `function(a,b,c)`
            - Call: `function(b = 2, 1, 3)` NOT ALLOWED and will result in SYNTAXERROR
    - *Also, in a function definition, parameters expected to be used as keywords must be placed behind those expecting positional arguments. An error will occur otherwise.*
    - **Default Value**:
        - When a parameter in a function definition has a default value, the argument for the parameter can be omitted if the default value is to be used.
        - Note, all default parameters are treated as keyword arguments. This means when defining a function, default parameters must be placed AFTER positional arguments.
        - ```python
            def powerof(x, y=2):
                return '{x} power of {y} is {x ** y}'
            ```
        - In the example above, if we omit passing the y value, the function defaults to y = 2, and calculates the square of x.
        
7. What are **variable-length lists of arguments**? What advantages do they offer?
   
    - **Variable-length non-keyword argument**:
        - ```python
            def productof(*args): # Creates a tuple of arguments
                product = 1
                for i in args: # Iterates over the tuple
                    product *= i
                return product
           ```
        - An example of the call of the function above: `productof(5, 2, 10)`
          
    - **Variable-length keyword argument**:
        - ```python
            def staffreport(**kwargs): # The keyword parameter and argument pairs are stored in a dictionary!
                for k, v in kwargs.items():
                    print(f'{k} = {v}')
            ```
        - An example of the call of the function above: `staffreport(Name='Eric', 'Age'= 32)
          
    - Advantages:
        - You can pass a tuple straight into the variable-length non-keyword argument!
        - You can pass a dictionary straight into the variable-length keyword argument!
        - *args and **kwargs: These provide flexibility because they allow for variable-length arguments. You can call the function with zero, some, or many arguments without changing the function definition.
        - Tuples/Dictionaries: When using these, you must ensure they match the function’s parameters. Missing or extra values will cause errors unless defaults are provided.
             

9. How do we call a function with positional arguments only?
    - ```python
        def function(a,b,c):
            return f'a = {a}, b = {b}, c = {c}'
        ```
    - `function(2, 5, 10)`
      
10. How do we correctly call functions with keyword arguments?
    - ```python
        def function(a, b, c=3):
            return a, b, c
        ```
    - `function(b=2, a=1)`


11. How do we correctly call functions with a variable-length list of arguments?
    - ```python
        def function(*args): # Creates a tuple of arguments
            return sum(args)
        ```
    - `function(1,2,3,4,5)`


12. How do we call functions with both positional arguments and keyword arguments?
    - No matter when defining or calling, always place keyword arguments AFTER positional arguments.
    - ```python
        def function(a, b, c, d = 4):
            return a, b, c, d
        ```
    - `function(3, 10, 5, d=3)` OR
    - `funciton(3, 10, 5, 3)`

13. How do we call functions with both positional arguments and a variable-length list of arguments?
    - Always specify the positional arguments FIRST before the variable-length list of arguments.
    - ```python
        def function(a, b, c, *args):
            return a, b, c, args
        ```
    - `function('Eric', 32, 'Toronto', 'Business Analyst', 'Data Scientist')`
      
14. How do we call functions with both a variable-length list of arguments and keyword arguments?
    - Make sure *args is specified before **kwargs.
    - ```python
        def function(*args, **kwargs):
            return args, kwargs
        ```
    - `function('Eric', 'Data Scientist', age=32, city='Toronto')
      
15. How do we call functions with all three types of arguments?
    - This is the correct order:
        - 1. Positional arguments
        - 2. *args
        - 3. Keyword arguments (with default values)
        - 4. **kwargs

16. What are **recursive functions**?
    - A function is recursive if it *calls itself* either directly or indirectly. Recursion is a powerful concept in computing and computational theory. In computational theory, it has been proven that any problem computable by modern computers can be represented as a recursive function. In programming, recursive functions do not make your programs run fast. However, they do provide a powerful means of algorithm design to solve a problem and make neater program code.

17. How do you define recursive functions?
    -   ```python
        def recursive(n):
            base case
            recursive case
        ```
### Defining a Function

- How to define function:
    - ```python
        def func(positional arguments, *args, keyword arguments, **kwargs):
            pass
      ```
- What makes a code block in a function definition different from code blocks in other compound statements such as for, while, and if is that *it will always
return a value with the return statement*. Even if you do not have anything to return from a function definition and do not have a return statement, special
value *None* will still be automatically returned from the function.
    - For instance, if you have a function without a return statement but has a print statement instead, printing the function will print the print statement as well as 'None'.
    - ```python
        def greet(name):
            print(f"Hello, {name}!")

        result = greet("Alice")
        print(result)  # Output: Hello, Alice! \n None
       ```

- Sometimes you need to return more than one value from a function. To do that, you can either put the values in a compound data type such as a
list, tuple, set, or dictionary, or just put the value all behind return. In the latter case, the values will be automatically packed in a tuple by the return statement.
- When you define a function, you can use variables within the parentheses right next to the function name to specify what values can be taken when the function is called. These variables within the parentheses are called parameters, and the values to be passed to the parameters in a function call are called arguments.
- In Python, a function call may take *positional arguments*, *keyword arguments*, *variable-length lists of nonkeyword arguments*, *variable-length lists of keyword arguments*, and *default arguments*.

### Lambda

- **lambda:**
  - Sometimes, especially when the operations of the function are simple and used only once, it is more convenient to simply use a small code block as a function without defining a function with a name.
  - `lambda <formal argument list> : <expression whose value is to be returned>`
  - A formal argument list is a list of variables separated by commas but without surrounding parentheses, and everything behind the colon takes the role of the code block in the regular function definition. But it must be a single expression whose value is to be returned by the lambda function without a keyword return.

- **Sample Usage:**
  - ```python
      lambda n: 2 * n + 1
    ```
  - This function takes n and returns an odd number.
  - The common use of lambda functions is to call it directly when it is defined, as below:
    - ```python
        (lambda n: 2 * n + 1)(4)
      ```
        - The function returns 9.
        - Note the pair of parentheses, which signify the end of the lambda function.
  - ```python
      (lambda x, y: x + y)(3, 4)
    ```
    - A lamda function can have multiple arguments.
      - ```python
          (lambda *x: sum(*x) * 5)(1,2,3)
        ```
        - Note *x takes in multiple args just like *args.

- **Naming:**
  - lambda_name = lambda x: x + 5
  - `lambda_name(5)`
  - ```python
      is_multiple = lambda x, y: x % y == 0
    ```
    - Checks if x is a multiple of y.


### Mapping, Filtering, Reducing

- Python treats everything as objects, including functions!
    - `f_objects = [len, abs, sum]`
    - `f_objects[0]`
    - `f_objects[0](f_objects)`
        - This returns 3!

- In Python, **mapping**, **filtering**, and **reducing** are functional programming concepts used for transforming or processing collections of data like lists or tuples. These concepts are typically implemented using the built-in functions map(), filter(), and reduce() (from functools).
  
- **Mapping:**
    - Apply a function to each item in an iterable (e.g., list, tuple) and return a new iterable with the transformed values.
    - `map(function, iterable)` returns a mapped object
    - ```python
        integers = [-1, -2, -3]
        tuple(map(abs, integers)) # Output: (1, 2, 3)
      ```
    - ```python
        list(map(lambda x: x + 2, range(10))) # Output: [2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
        ```
    - ```python
        lst = [[1,2,3], [1,2], [1,2,3,4,5,6]]
        a = tuple(map(lambda x: sum(x), lst))
        print(a) # Output: (6, 3, 21)

- **Filtering:**
    - The filtering function selects only the items from an iterable that satisfy a condition (i.e., the function returns True).
    - `filter(function, iterable)` returns a filtered Python object
    - ```python
        def even(n):
            return n % 2 == 0 # Returns True or False boolean value.
        ```
    - `list(filter(even, range(10)))`
        - This returns [0, 2, 4, 6, 8]
        - This can be rewritten as:
            - `list(filter(lambda n: n % 2 == 0, range(10)))`
    - ```python
            st = "The filter function may play an important role in selecting words from a given text. In the following example, only words that contain the letter o are selected"
            contain_o = list(filter(lambda s: 'o' in s, st.split()))
            print(contain_o)
        ```
        - Note that only the words that include the letter 'o' are selected.

- **Reducing:**
    - The reduce function from the functools module in Python is used to apply a function to a sequence of elements cumulatively, from left to right, so that the sequence is reduced to a single value. The reduce function applies the provided function to the first two elements of the iterable, and then applies the result to the next value in the iterable.
    - Unlike map and filter, you do not need to wrap iterables such as lists and tuples around the reduce() function because the reduce() function does not return an iterable. It simply returns a single value.
    - ```python
        from functools import reduce
        reduce(lambda n, m: n**m, range(2, 6)) # Output 14
        ```
    - ```python
      from functools import reduce
      lst = [5, 50, 3, 6, 70, 81, 9]
      reduce(lambda x,y: x if x>y else y, lst) # Output 81
      ```

### Functions as Closures

- In Python and some other programming languages such as JavaScript, **closures** are the result of a nested function — that is, one function that is defined inside another.
- A **closure** occurs when a nested function (inner function) captures and remembers the values from its enclosing (outer) function, even after the outer function has finished executing.
- They are useful for *encapsulation*, *function factories*, and *stateful functions*.
- If a function returns another function, and that inner function uses outer variables, you have a closure!
  
    - ```python
      def outer():
        greeting = 'Good day!'  # This is a local variable within the outer function.
        def inner(who):          # This is the inner function, which is defined inside the outer function.
          print(greeting, who)  # The inner function uses the 'greeting' variable from the outer function. The key here is that the inner function has access to variables that are defined in the outer function's scope. Even though the variable greeting is defined inside outer(), the inner function can access it because of closure.
      return inner
      
      say_hello = outer()  # This calls outer() and returns the inner() function
      say_hello('Alice')  # This calls inner('Alice'), which prints 'Good day! Alice'
      ```
  

      


</details>        

<details>

<summary><h2 id='oop'>Object-Oriented Programming</h2></summary>

- [Exercises](https://github.com/ericyang91/RTDS_Python/blob/main/Object%20Oriented%20Programming%20Exercises.ipynb)

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
      - `isinstance(o, c)`: Return `True` if o is an instance of c.
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

      p = Pet('crested gecko', 'rainforest', 'insects', 6, 'Queen')
      p.__age # AttributeError
      p._name # Queen
  ```

- If you want to access the protected members of a class from outside, the built-in functions `hasattr` and `getattr` can be used to access *protected members* of a class or its instance. It cannot, however, access *private members*.
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
      - **Operator overloading** allows you to define custom behavior for operators when they are used with objects of your class. Examples of the dunder/magic methods that can be used for overloading operators are \_\_add\_\_ for addition, \_\_sub\_\_ for subtraction, \_\_mul\_\_ for multiplication, and \_\_div\_\_ for division.
      - `__call__`
         - The \_\_call\_\_ method in Python allows an instance of a class to be called as if it were a function. This means you can use parentheses (()) *after an object of the class*, just like calling a function, and Python will execute the \_\_call\_\_ method of that object.
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



| **Operator** | **Dunder Method**            | **Description**                                    |
|--------------|------------------------------|----------------------------------------------------|
| `+=`         | `__iadd__(self, other)`       | Performs in-place addition.                        |
| `-=`         | `__isub__(self, other)`       | Performs in-place subtraction.                     |
| `*=`         | `__imul__(self, other)`       | Performs in-place multiplication.                  |
| `/=`         | `__idiv__(self, other)`       | Performs in-place division.                        |
| `//=`        | `__ifloordiv__(self, other)`  | Performs in-place floor division.                  |
| `%=`         | `__imod__(self, other)`       | Performs in-place modulo operation.                |
| `**=`        | `__ipow__(self, other[, modulo])` | Performs in-place exponentiation (with optional modulo). |



| **Operator** | **Dunder Method**            | **Description**                                    |
|--------------|------------------------------|----------------------------------------------------|
| `<`          | `__lt__(self, other)`         | Less than comparison.                              |
| `<=`         | `__le__(self, other)`         | Less than or equal to comparison.                  |
| `==`         | `__eq__(self, other)`         | Equal to comparison.                               |
| `!=`         | `__ne__(self, other)`         | Not equal to comparison.                           |
| `>=`         | `__ge__(self, other)`         | Greater than or equal to comparison.               |
| `>`          | `__gt__(self, other)`         | Greater than comparison.                           |


### Class as a Decorator
- A class can be used as a **decorator** by implementing the \_\_call_\_ method, which allows instances of the classes to behave like functions. Here's how it works:
    - Define a class with an \_\_init_\_ method to store the function.
    - Impleent the \_\_call_\_ method to execute the function when the instance is called.

    - ```python
      class Logger:
        def __init__(self, func): # Initialize with the function to be decorated
            self.func = func
    
        def __call__(self, *args, **kwargs): # Execute the function and log its execution
            print(f"Calling function: {self.func.__name__} with arguments: {args}, {kwargs}")
            result = self.func(*args, **kwargs)
            return result
      
      # Using the class as a decorator  
      @Logger
      def add(x,y):
          return x + y

      # Calling the decorated function
      add(5, 6) # Output: Calling function: add with arguments: (5, 6), {}
                        # 11
        ```
- This is often used to calculate the execution time of a function.
    - ```python
        from time import time
        
        class Timer:
            def __init__(self, func):
                self.func = func
            
            def __call__(self, *args, **kwargs):
                print(f'Executing {self.func.__name__}.')
                start = time()
                result = self.func(*args, **kwargs)
                end = time()
                print(f'It took {end - start} seconds.')
                return result
        
        @Timer
        def fed_tax(net_taxable_income):
            if not isinstance(net_taxable_income, (float,int)):
                raise ValueError('You must enter a number without the dollar sign and commas.')
            else:
                if net_taxable_income <= 57375:
                    net_tax = net_taxable_income * 0.15
                elif net_taxable_income <= 114750:
                    net_tax = (net_taxable_income - 57375) * 0.205 + (57375 * 0.15)
                elif net_taxable_income <= 177882:
                    net_tax = (net_taxable_income - 114750) * 0.26 + (114750 - 57375) * 0.205 + (57375 * 0.15)
                elif net_taxable_income <= 253414:
                    net_tax = (net_taxable_income - 177882) * 0.29 + (177882 - 114750) * 0.26 + (114750 - 57375) * 0.205 + (57375 * 0.15)
                else:
                    net_tax = (net_taxable_income - 253414) * 0.33 + (253414 - 177882) * 0.29 + (177882 - 114750) * 0.26 + (114750 - 57375) * 0.205 + (57375 * 0.15)
        
            return net_tax
        
        fed_tax(81500) # Output: Executing fed_tax.
                               # It took 0.0 seconds.
                               # 13551.875
      ```

### Built-in Property() Function and Property Decorator
- The `property()` function in Python is a built-in way to create managed attributes in a class. It allows you to define *custom behavior* when getting, setting, or deleting an attribute. The main benefit of **@property** (or using `property()`) is that it allows you to control and customize how attributes are accessed, modified, or deleted. Without it, attributes would be accessed directly, and you'd have less control (setattr(), getattr(), delattr()).
- Basic `property()` usage:
    - Syntax: `property(fget=None, fset=None, fdel=None, doc=None)`
        - `fget`: A function to get the attribute's value
        - `fset`: A function to set the attribute's value
        - `fdel`: A function to delete the attribute
        - `doc`: A string representing the attribute's documentation
- Example 1: Using `property()` directly
    - ```python
        class Person:
            def __init__(self, firstname):
                self._firstname = firstname # Note the underscore. This is done because the property() function is being assigned to 'firstname',
                                            # which overrides the instance attribute self.firstname. '_firstname' will store the actual value
            def get_firstname(self):
                return self._firstname
            def set_firstname(self, new_firstname):
                self._firstname = new_firstname
            def del_firstname(self):
                del self._firstname
            firstname = property(get_firstname, set_firstname, del_firstname, "First name of the person.")
        
        p = Person('Dahee')
        print(p.firstname) # Calls get_firstname
        p.firstname = 'Eric' # Calls set_firstname
        del p.firstname  # Calls del_firstname
      ```
- Example 2: Using `property()` without arguments and adding methods later
    - ```python
        class Person:
            def __init__(self, firstname):
                self._firstname = firstname
        
            @property # Defines the getter method. firstname() is no longer a regular method. It's a property
            def firstname(self):
                return self._firstname
        
            @firstname.setter
            def firstname(self, newname):
                self._firstname = newname
        
            @firstname.deleter
            def firstname(self):
                del self._firstname
        
        p = Person('Dahee)
        print(p.firstname) # Calls the getter
        p.firstname = 'Eric' # Calls the setter
        del p.firstname # Calls the deleter
      ```
    - ```python
        class Person:
            def __init__(self, age):
                self._age = age  # Using a protected attribute
        
            @property
            def age(self):
                print("Getting age...")
                return self._age
        
            @age.setter
            def age(self, value):
                if value < 0:
                    raise ValueError("Age cannot be negative!")
                print("Setting age...")
                self._age = value
        
        p = Person(30)
        print(p.age)  # Calls the getter and prints "Getting age..."
        p.age = 25    # Calls the setter and prints "Setting age..."
        p.age = -5    # Raises an error: "Age cannot be negative!"
      ```

</details>

<details>
    
<summary><h2 id='module'>Modules and Packages</h2></summary>

- [Datetime](https://github.com/ericyang91/RTDS_Python/blob/main/Datetime.ipynb)

</details>

