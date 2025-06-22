# Python

> Created by Salman Al Qureshi
Linkedin: Salman Qureshi
> 
> 
> http://www.linkedin.com/in/salman-qureshi-4aa41a247
> 

# Python Automation

## **Concepts**

- **Syntax:**
Syntax refers to the set of rules that define how Python code is structured. It dictates how you write statements, expressions, and instructions for the computer to understand. Proper indentation (using spaces) is essential in Python, unlike some other programming languages.
- **Strings:**
Strings are sequences of characters enclosed in single (`'`) or double (`"`) quotes. They represent text data that your program can use. Examples:
- **Numericals:**
Numericals represent numeric data in Python. There are two main kinds:
Integers (whole numbers): Represented by whole numbers without decimals. Example: `age = 30`
Floats (decimal numbers): Numbers with a decimal point. Example: `pi = 3.14159`
- **Variables:**
Variables are named containers that store data in your program. You can think of them as boxes with labels where you can place and retrieve information.
Naming: Choose descriptive names that reflect the data they hold (e.g., `message`, `temperature`).
Assigning values: The equal sign (`=`) is used to assign a value to a variable. Example: `temperature = 25`.
Reassignment: Variables are flexible; you can change the value stored in them later in your code.
- **Constants:**
Constants represent fixed values that shouldn't change during your program's execution. Unlike variables, they are usually written in ALL_CAPS with underscores for clarity. They help improve code readability and maintainability. Example: `MAX_SPEED = 100` (speed limit).

### Python Operators Precedence

![Operator  Precedence ( like BODMAS in maths).png](Python%202193e043159d81e3bf48ce20e7aebc8c/Operator__Precedence_(_like_BODMAS_in_maths).png)

### **Data Structures:**

- **Lists:** Ordered collections of items enclosed in square brackets `[]`. They can hold elements of different data types. Useful for storing sequences of data. Example: `fruits = ["apple", "banana", "cherry"]`
- **Tuples:** Similar to lists but immutable (cannot be changed after creation). Useful for representing data that shouldn't be modified. Example: `coordinates = (10, 20)`
- **Dictionaries:** Unordered collections of key-value pairs enclosed in curly braces `{}`. Used to store data associated with unique keys. Example: `person = {"name": "Bob", "age": 35}`

### **Control Flow:**

- **Conditional statements (if/else):** Allow you to execute code based on certain conditions
- **Loops (for/while):**
Enable you to repeat a block of code multiple times.
`for` loops: Iterate over a sequence of elements. Example:
[ `for fruit in fruits:
print(fruit)` ]
- while loops: Execute code as long as a condition is true. Example:
[`count = 0
while count < 5:
    print(count)
    count += 1`]
- **User defined Functions:**
Reusable blocks of code that perform specific tasks. They promote code modularity and maintainability.
Defining functions: Use the `def` keyword followed by the function name and parameters (inputs). Example:
`def greet(name):
    print("Hello,", name)
greet("Alice")`
- Conditional statments:
Allows program to make decision based on True or False (boolean) statments 
`if condition1:`
                     `Code to execute if condition1 is True
elif condition2:`
                       `Code to execute if condition1 is False and condition2 is True
elif condition3:`
                        `Code to execute if condition1 and condition2 are False and condition3 is True`
#You can have as many elif statements as needed
`else:`
      `Code to execute if all conditions (if and elif) are False`
- **Object-Oriented Programming (OOP):**
A programming paradigm based on objects that encapsulate data (attributes) and behavior (methods).
- **Modules and Packages:**
Reusable code organized in files called modules (`.py` files) and packages (directories containing modules). They allow you to import and use functionalities from other codebases.
- Comments:
This is data that is ignored by the proggraming language 
you can use `#` to start commenting or use triple double or single quotes `“”” This is commented “””` like this for multiple line comment
    
    

### **Global Interpreter Lock (GIL) in Python**

The **Global Interpreter Lock (GIL)** is a mutex (mutual exclusion lock) used in **CPython**, the most widely used Python interpreter. It ensures that only **one thread** executes Python bytecode at a time, even on multi-core processors.

---

### **Why Does Python Have a GIL?**

The GIL exists mainly because **CPython's memory management is not thread-safe**. Python uses **reference counting** for garbage collection, meaning that every object in memory has a reference count that increases or decreases when assigned or deleted. If multiple threads modify an object's reference count simultaneously, it can lead to **race conditions** and memory corruption.

To prevent this, CPython enforces the **GIL**, ensuring that only one thread modifies memory at any given time.

---

### **Effects of GIL**

1. **Threading in Python does not provide true parallelism**
    - Even if you create multiple threads, they will not run simultaneously on multiple cores. Instead, Python switches between threads using **context switching**.
2. **Multi-threading is not efficient for CPU-bound tasks**
    - Since only one thread executes Python code at a time, multi-threading does not improve performance for **CPU-intensive tasks** (e.g., numerical computations, image processing).
3. **Multi-threading works well for I/O-bound tasks**
    - The GIL is released when performing **I/O operations** (e.g., network requests, file I/O), making multi-threading beneficial in these cases.

---

### **How to Overcome GIL Limitations?**

1. **Use Multiprocessing Instead of Threading**
    - The **multiprocessing** module creates separate processes, each with its own Python interpreter and memory space, bypassing the GIL.
    
    ```python
    from multiprocessing import Process
    
    def task():
        print("Running in a separate process")
    
    if __name__ == "__main__":
        p = Process(target=task)
        p.start()
        p.join()
    ```
    
    - This takes full advantage of multiple CPU cores.
2. **Use C Extensions**
    - Libraries like **NumPy**, **TensorFlow**, and **Numba** execute code in **C/C++**, which can bypass the GIL.
3. **Use Alternative Python Interpreters**
    - **Jython** (Java-based) and **IronPython** (C#-based) do not have a GIL and allow true multi-threading.

---

### **Summary**

- The **GIL** prevents multiple threads from running Python bytecode simultaneously.
- It exists to manage Python’s memory safely.
- **CPU-bound** tasks do not benefit from multi-threading due to the GIL.
- **I/O-bound** tasks (e.g., web scraping, file handling) can still benefit from multi-threading.
- To leverage multiple CPU cores, use **multiprocessing** or optimized C extensions.

## Syntax:

- Printing something:
you can Print anything using `“ ”`,`’ ’` or `“”” ”””` 
# triple quotes are used for multiple lines

### **Combining Strings and Variables:**

- **Combining Strings and Variables:**
You can combine strings and variables using the `+` operator. This is a common approach.
OR
Alternatively, you can use a comma (`,`) to separate the string and variable. Both methods achieve the same result of creating a single string with the variable's value inserted.
OR
**f-strings (formatted string literals):**
Introduced in Python 3.6, f-strings offer a concise and readable way to embed variables directly within strings.
Enclose the string in curly braces `{}` and place the variable name inside.
F-strings can also perform basic formatting expressions within the curly braces.
Examples:
    
    **Example:**
    `name = "Bob"
    age = 30
    greeting = f"Hello, {name}! You are {age} years old."
    print(greeting)  # Output: Hello, Bob! You are 30 years old.`
    OR
    **The `.format()` method:**
    This method (available in all Python versions) provides more control over complex formatting scenarios.
    Define a template string with placeholders (`{}`) where you want to insert variables.
    Use the `.format()` method on the template string, passing the variables as arguments (by position or name).
    **Example (positional formatting):**
    `name = "Charlie"
    age = 25
    greeting = "Hello, {}! You are {} years old.".format(name, age)
    print(greeting)  # Output: Hello, Charlie! You are 25 years old.`
    OR
    **String formatting with `%s` (older method)**
    The `%s` operator is an older method for combining strings and variables.
    Define a template string with placeholders `%s`.
    Use the `%` operator after the template string, followed by a tuple containing the values.
    **Example:**
    `name = "Alice"
    age = 30
    greeting = "Hello, %s! You are %s years old." % (name, age)
    print(greeting)  # Output: Hello, Alice! You are 30 years old.`
    # use %s for string, %d for integers %f for floats
    

### **Escape sequences**

- **Escape sequences** are a way to represent special characters within strings in Python. They use a backslash (`\`) followed by another character. Here are some common ones
    
    **\n:** Newline character (prints text on a new line)
    Example: `print("Hello,\nworld!")` (prints "Hello," on a new line and then "world!")
    
    **\t:** Horizontal tab character (creates spaces)
    Example: `print("Item1\tItem2\tItem3")` (creates spaces between items)
    
    **\:** Backslash character (prints the actual backslash)
    Example: `print("This is a backslash \\ character")` (prints the actual backslash)
    
    **'** (single quote): Single quote character
    Example: `print('He said, "Hello!"')` (prints the double quote within the single-quoted string)
    
    **"** (double quote): Double quote character
    Example: `print("She said, 'Hi there!'")` (prints the single quote within the double-quoted string)
    

### Conditional operators

- Conditional operators are used to compare values. 
Common comparison operators include:
    
    `==`: Equal to
    `!=`: Not equal to
    `<`: Less than
    `>`: Greater than
    `<=`: Less than or equal to
    `>=`: Greater than or equal to
    `!` : not operator
    `&&` : and operator 
    `||` : OR operator
    

### range()

- range() # IMP
    
    
    The `range` function in Python generates a sequence of numbers, which is commonly used in loops.
    When you use `range(5)`, it creates a range object, but it does not automatically produce any output. To see the numbers generated by `range(5)`, you need to iterate over it or convert it to
    a list.
    Here’s an overview of its usage and different forms.
    **Basic Syntax
    range(stop)**: Generates numbers from 0 to `stop`-1.
    Example: `range(5)` → `[0, 1, 2, 3, 4]`
    Usage: `for i in range(5):`
                  `print(i)`
    **range(start, stop)**: Generates numbers from `start` to `stop`-1.
    Example: `range(2, 7)` → `[2, 3, 4, 5, 6]`
    Usage: `for i in range(2, 7):` 
                `print(i)`
    **range(start, stop, step)**: Generates numbers from `start` to `stop`-1 with a step increment.
    Example: `range(1, 10, 2)` → `[1, 3, 5, 7, 9]`
    Usage: `for i in range(1, 10, 2):`
                `print(i)`
    example:
    `print(list(range(0,21,2)))` → [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
    to-print, to-list, range-of-0-to-20-adding-2-after-each .
    

### **Functions**

- **Functions**:
A function is a reusable block of code that performs a specific task and can be executed whenever called in a program.
    
    There are two types of functions:
    
    **Built-in Functions**:
    These are functions that come with Python, such as `print()`, `len()`, `sorted()`, `dir()`, `type()`, etc.
    
    **User-Defined Functions**:
    These are functions that you create to perform specific tasks in your program.
    
    **Defining a Function**:
    To define a function, use the `def` keyword, followed by the function name and parentheses. Inside the parentheses, you can specify parameters (optional), and the function body is indented below.
    
    **Syntax**:
    
    ```python
    def function_name(parameters):
        # statements
    ```
    
    **Example**:
    
    ```python
    def greet():
        print("Hello, World!")
    ```
    
    **Parameters and Arguments**:
    
    - **Parameters**: These are variables listed inside the parentheses in the function definition. They act as placeholders for the values that the function will use.
    - **Arguments**: These are the actual values you pass to the function when calling it.
    
    **Example**:
    
    ```python
    def greet(name):
        print(f"Hello, {name}!")
    
    greet("Alice")  # This will print "Hello, Alice!"
    ```
    
    **Return Values**: Functions can return a value using the `return` keyword.
    
    ```python
    def add(a, b):
        return a + b
    
    result = add(3, 5)  # result will be 8
    ```
    
    **Default Parameters**: You can provide default values for parameters.
    
    ```python
    def greet(name="World"):
        print(f"Hello, {name}!")
    
    greet()       # Prints "Hello, World!"
    greet("Alice")  # Prints "Hello, Alice!"
    ```
    
    **Keyword and Positional Arguments**: Functions can accept arguments in different ways.
    
    ```python
    def greet(name, greeting="Hello"):
        print(f"{greeting}, {name}!")
    
    greet("Alice")            # Prints "Hello, Alice!"
    greet("Alice", "Hi")      # Prints "Hi, Alice!"
    ```
    

### loops

- loops:
repeat/iterate through a block of code until the requirement is met 
like a bolean True,False or a Range etc
Two imp loops are for loop, while loop
    
    
    For loop syntax:
    `for <variable> in <range or list> :`
                `statments`  
    example:
    `for i in range(0,21,2):`
           `print(i)`
    This will print from 0 to 20 while adding 2 so the output will be: even numbers from 0 to 20
    you can also use other thing instead of `print(i)` like `print("this will be printed 11 times")` 
    **For Loop with Lists**
    For loops can also be used to iterate over elements in a list.
    **Example**:
    `my_list = [1, 2, 3, 4, 5]
    for item in my_list:
    print(item)`
    This will print each item in `my_list` one by one.
    
    For Loop with Dictionaries
    For loops can also be used to iterate over keys, values, or key-value pairs in a dictionary.
    **Example - Iterating Over Key-Value Pairs**:
    `for key, value in my_dict.items():
    print(f"{key}: {value}")`
    This will print each key-value pair in `my_dict`.
    
    While loop:
    syntax:
    `while <condition true>:`
             `statments`
    Example:
    `i=0
    while i <= 10:`
        `print(i)`
        `i +=1` 
    

### **Break, Continue, and Pass in Python**

These are control flow statements that allow you to influence the execution of loops and conditional statements.

---

### **1. `break`**

- **Purpose**: Immediately stops the loop and exits it.
- **Use Case**: When you want to terminate a loop based on a condition.

### Example:

```python
for num in range(1, 10):
    if num == 5:
        break  # Loop stops as soon as num equals 5
    print(num)
# Output: 1, 2, 3, 4
```

---

### **2. `continue`**

- **Purpose**: Skips the current iteration and moves to the next iteration of the loop.
- **Use Case**: When you want to bypass certain conditions within the loop but still continue iterating.

### Example:

```python
for num in range(1, 10):
    if num == 5:
        continue  # Skip printing 5, but continue the loop
    print(num)
# Output: 1, 2, 3, 4, 6, 7, 8, 9
```

---

### **3. `pass`**

- **Purpose**: Acts as a placeholder, doing nothing.
- **Use Case**: When you need to have a syntactically valid block but don't want it to execute anything.

### Example:

```python
for num in range(1, 10):
    if num == 5:
        pass  # Does nothing; used as a placeholder
    print(num)
# Output: 1, 2, 3, 4, 5, 6, 7, 8, 9
```

---

### **Key Differences**

| Statement | Effect | Use Case |
| --- | --- | --- |
| **`break`** | Exits the loop entirely. | Stop the loop on a condition. |
| **`continue`** | Skips the current iteration. | Skip processing for some values but keep looping. |
| **`pass`** | Does nothing (a placeholder). | Write code later or to avoid errors in an empty block. |

- You can use “`in`” to check if a value is equal to an of the given value 
syntax:
`if op in ['+', '-', '*', '/']:`  
      `print("correct")`

### **Python Exception Handling**

- **Python Exception Handling**
Exception handling in Python is a way to handle runtime errors gracefully, allowing the program to continue running or provide useful error messages to the user. This is done using the `try`, `except`, `else`, and `finally` blocks.
    
    
    Basic Syntax
    **`try`**:
    Attempt to execute code that might cause an exception.
    **`except`**:
    Handle the exception if one occurs.
    **`else`**:
    Execute code if no exceptions are raised.
    **`finally`**:
    Execute code regardless of whether an exception occurred.**Handling Multiple Exceptions**:
    `try`:
    # Code that might raise an exception
    result = 10 / 0
    `except ZeroDivisionError:`
    # Code to handle ZeroDivisionError
    `print("Cannot divide by zero")
    except TypeError:`
    # Code to handle TypeError
    `print("Invalid type")`
    Output: `"Cannot divide by zero"except Exception as variable`  is used to catch exceptions and access their details. Here's a detailed explanation:
    
    **Explanation**
    
    When an exception occurs, it generates an instance of an exception class (e.g., `ZeroDivisionError`, `FileNotFoundError`). By using `except Exception as variable`, you can capture this instance and access its attributes or methods.Example:
    
    `try:`
        `num1=eval(input("Enter a number: "))`
        `num2=eval(input("Enter a number: "))`
        `divi= num1/num2`
        `print(divi)
    except Exception as e:`
        `print("There was an error: ",e)strftime` stands for "string format time" and is a method in Python's `datetime` module used to format `datetime` objects into readable strings. This method allows you to specify the format in which you want the date and/or time to be represented.
    Example:
    `import datetime
    now = datetime.datetime.now()`
    
    `formatted_datetime = now.strftime("%Y-%m-%d %H:%M:%S")
    print("Formatted datetime:", formatted_datetime)`  # Output: Formatted datetime: 2024-07-11 14:45:30`strptime` this stands for "string parse time" and is a method in Python's `datetime` module used to parse a string representing a date and/or time into a `datetime` object. This method allows you to specify the format of the input string so that it can be correctly interpreted and converted into a `datetime` object.
    Example:
    `import datetime
    date_string = "2024-07-11 14:45:30"
    parsed_datetime = datetime.datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
    print("Parsed datetime:", parsed_datetime)`  # Output: Parsed datetime: 2024-07-11 14:45:30
    

### **File Handeling:**

- **File Handeling:**
File handling in Python involves reading from and writing to files. Here are the basics, including how to open, read, write, and close files.
    
    
    **Opening a File
    open(file, mode)**: Opens a file and returns a file object. If the file does not exist, it will be created.
    **file**: Name of the file to be opened.
    **mode**: Specifies the mode in which the file is opened. Common modes include:
    **`'r'`**: Read (default mode). Opens the file for reading.
    **`'w'`**: Write. Opens the file for writing (creates a new file or truncates an existing file).
    **`'a'`**: Append. Opens the file for appending.
    **`'b'`**: Binary mode.
    **`'+'`**: Read and write.
    Examples:
    **Opening a File**
    `open("example.txt", "r")`: Opens a file named "example.txt" in read mode.
    `open("example.txt", "w")`: Opens a file named "example.txt" in write mode. # if file is not in same directory then provide the full path
    **Reading a File
    read(size=-1)**: Reads from the file. If the size argument is omitted or negative, the entire content is read.
    **readline(size=-1)**: Reads one line from the file. If the size argument is omitted or negative, the entire line is read.
    **readlines(hint=-1)**: Reads all lines from the file and returns them as a list.
    Example:
    **Reading from a File**:
    `file = open("example.txt", "r")
    content = file.read() # Reads the entire file content
    line = file.readline() # Reads the first line
    lines = file.readlines() # Reads all lines into a list
    file.close()`
    # Use print to print the read file **Writing to a File
    write(string)**: Writes the string to the file.
    **writelines(lines)**: Writes a list of lines to the file.
    Examples:
    **Writing to a File**:
    `file = open("example.txt", "w")`
    `file.write("Hello, world!")` # Writes "Hello, world!" to the file
    `file.writelines(["Hello, world!\n", "Another line.\n"])` # Writes multiple lines to the file
    `file.close()` # This will close the file**Closing a File
    `filename.close()`**: Closes the file. It's good practice to close the file after its operations are done.**Using with Statement**:
    `with open("example.txt") as file:` # This will open the file and while it’s open it will perform the instructions given in the indentation and then close it 
    `content = file.read()` # No need to explicitly close the file
    `print(content)`
    **Creating a New File and Writing to It**:
    `file = open("newfile.txt", "w")`
    `file.write("Hello, this is a new file!")` # Writes to the file
    `file.close()` # Closes the file**Appending to a File**:
    `file = open("newfile.txt", "a")
    file.write("\nAppending a new line.")` # Appends a new line to the file
    `file.close()` # Closes the file**Open a JSON File and Convert It to a Dictionary**
    Import the `json` module.
    Open the JSON file using the `open` function.
    Use `json.load` to parse the JSON file and convert it into a dictionary.
    Close the file (if not using the `with` statement).
    Example:
    `import json
    with open("example.json", "r") as file:
    data = json.load(file) # Converts the JSON file into a dictionary called data
    print(data)`**Converting a dictionary into a JSON file:**
    Import the `json` module.
    
    Open (or create) a JSON file in write mode.
    
    Use `json.dump` to write the dictionary to the JSON file.
    
    Close the file (if not using the `with` statement).
    example:
    `import json
    data = {
    "name": "John Doe",
    "age": 30,
    "city": "New York",
    "isStudent": False
    }
    with open("output.json", "w") as file:
    json.dump(data, file, indent=4)` # Converts the dictionary into JSON and writes to the file, Here the `data` is the dictionary `file` is the opened file(output.json) in write mode and `indent=4` specifies the indentation level for the JSON file, making it more readable by adding indentation. The value `4` means that each level in the JSON structure will be indented by 4 spaces
    **Reading from and writing to CSV files** in Python can be done easily using the `csv` module**Reading CSV Files**
    To read a CSV file, you need to:
    Import the `csv` module.
    Open the CSV file in read mode.
    Use `csv.reader` to read the file.
    Iterate over the rows in the CSV file.
    Example:
    
    `import csv
    with open("example.csv", "r") as file:`
        `reader = csv.reader(file)` # Create a CSV reader object, You can also add a delimeter after the file name and specify the delimeter you want to use e.g  `reader = csv.reader(file,delimeter='-')` this will use - as a delimeter instead of the default , 
        `for row in reader:`
        `print(row)` # Print each row in the CSV file
    
    **Writing CSV Files**
    
    To write to a CSV file, you need to:
    Import the `csv` module.
    Open the CSV file in write mode.
    Use `csv.writer` to write data to the file.
    Use `writerow` or `writerows` to write rows to the file.
    Example:
    `import csv
    with open("output.csv", "w", newline='') as file:` # `newline=''` is used to prevent adding extra newlines on some platforms.
        `writer = csv.writer(file)` # Create a CSV writer object
        `writer.writerows(data)` # Write multiple rows to the CSV file, here data is the variable containing the content that needs to be added to the csv file
    

## String & Some Important Functions Section

### Combining strings-Slicing-functions-methods-function parameters

- **Python Strings: Modifying and Editing**
    
    
    ****1. **Concatenation**: Joining two or more strings together.
    **Syntax**: `+` operator
    E**xample**: `str1 = "Hello"`, `str2 = "World"`, `result = str1 + " " + str2`, `print(result)` (Output: Hello World)
    
    2. **Slicing**
    **Slicing**: Extracting a portion of a string using a range of indices.
    **Syntax**: `string[start:end]`
    **Example**:
    `str = "Hello, World!"
    print(str[0:5])` (Output: Hello)
    `print(str[7:])` (Output: World!)
    `print(str[:5])` (Output: Hello)
    `print(str[::2]` (Output: Hlo ol!) # This will leave on character and then take the 2nd one 
    IMP `print(str[::-1]` (Output !dlroW ,olleH) # To reverse a variable just use [::-1]
    # You can also use double brackets for lists like [2][1] this will print the 1st index of 2nd value 
    # for example `list_str=[9,7,[4,1],6,2]` —> `print(list_str[2][1]` {output: 1} 
    # ALSO you have to use string value when calling dictonary and not [0][1] etc use —> [’server1][’IBM’] etc 
    
    3. **String Methods and Function**
    **Methods**: Called on the string object itself, usually come after the variable with a dot (`.`).
    **Functions**: Passed the string object as an argument, not called on the string object.
    **Examples**:
    Methods:
    `str = "hello"
    print(str.upper())` (Output: HELLO)
    `print(str.lower())` (Output: hello)
    Functions:
    `str = "hello"
    print(len(str))` (Output: 5) # here print and len are both default python Functions
    

### **Function Parameters**

In Python, function parameters are inputs that you pass to a function to control its behavior. Here are a few common examples of function parameters:

1. **`sep` and `end` in `print()`**:
    - `sep`: Specifies the separator between multiple values. By default, it is a space. You can change it to any string.
    - `end`: Specifies what to print at the end of the output. By default, it is a newline character (`\n`). You can change it to any string.
    
    Example:
    `print("Hello", "World", sep="-", end="!")`
    This will output: `Hello-World!`
    
2. **`file` in `print()`**:
    - The `file` parameter in `print()` specifies where the output should go. By default, it goes to the console (`sys.stdout`), but you can redirect it to a file.
    
    Example:
    
    ```python
    with open("output.txt", "w") as f:
        print("Hello, World!", file=f)
    ```
    
    This will write "Hello, World!" to `output.txt`.
    
3. **`key` in `sorted()`**:
    - The `key` parameter allows you to specify a function to be called on each list element before making comparisons during sorting. 
    # The `key` parameter in the `sorted()` function (or other functions that take a `key` argument) specifies a function to be applied to each element before making comparisons for sorting.
    
    Example:
    `sorted([("a", 2), ("b", 1)], key=lambda x: x[1])`
    This will sort the list based on the second item in each tuple.
    
4. **`reverse` in `sorted()`**:
    - The `reverse` parameter, when set to `True`, sorts the list in descending order.
    
    Example:
    `sorted([1, 2, 3], reverse=True)`
    This will output: `[3, 2, 1]`
    
5. **`mode` in `open()`**:
    - The `mode` parameter in `open()` specifies the mode in which the file is opened (e.g., `r` for read, `w` for write, `a` for append).
    
    Example:
    `open("file.txt", mode="r")`
    

These are just a few examples of common function parameters in Python. Many functions have their own parameters that let you control their behavior.

### Enumerate() Function

- The `enumerate()` function in Python is used to iterate over a sequence (like a list or tuple) while keeping track of the index of the current item. It adds a counter to an iterable and returns it as an `enumerate` object. This is useful when you need both the index and the value from the iterable during a loop.
    
    ### Syntax
    
    `enumerate(iterable, start=0)`
    
    - **`iterable`**: The collection you want to iterate over.
    - **`start`** (optional): The starting index of the counter (default is 0).
    
    ### Example: Basic Usage
    
    ```python
    fruits = ["apple", "banana", "cherry"]
    for index, fruit in enumerate(fruits):
        print(index, fruit)
    
    **Output:**
    0 apple
    1 banana
    2 cherry
    ```
    
    Here, `enumerate(fruits)` produces pairs of index and value. In each iteration of the loop, `index` and `fruit` are assigned to the index and value of the current item in the `fruits` list, respectively.
    
    ```python
    with open("text.txt","r") as f1, open("output.txt","w") as f2:
        for f1_index, f1_lines in enumerate(f1, start=1):
            if f1_index != 5:
                f2.write(f1_lines)
    ```
    
    This Code will copy all the lines except line 5 and paste it into another file
    
    ### Exampl: Starting from a Different Index
    
    ```python
    pythonCopy code
    fruits = ["apple", "banana", "cherry"]for index, fruit in enumerate(fruits, start=1):
        print(index, fruit)
        
        
    **Output:**
    1 apple
    2 banana
    3 cherry
    ```
    
    In this example, the `start` parameter is set to 1, so the index starts from 1 instead of the default 0.
    
    ### Use Cases
    
    - **Tracking the Index**: Useful when you need both the index and value during iteration.
    - **Creating Dictionaries**: When you want to create a dictionary with list elements as values and indices as keys.

### **`iter`**, and **`next`**

---

### **What Are Iterators?**

- An **iterator** in Python is an object that allows you to **traverse through a collection** (e.g., a list, tuple, or string) **one element at a time**.
- It’s like a bookmark: it keeps track of where you are as you go through the collection.

---

### **Key Concepts**

1. **Iterable**:
    - Any object you can loop through, like a list or a string.
    - Examples: Lists (`[1, 2, 3]`), Strings (`"hello"`), Tuples (`(1, 2, 3)`).
2. **Iterator**:
    - A special object created from an iterable.
    - It **remembers** where you are as you iterate through the elements.
3. **`iter`**:
    - The function used to create an iterator from an iterable.
    - Example: `iter([1, 2, 3])` creates an iterator for the list `[1, 2, 3]`.
4. **`next`**:
    - Fetches the **next element** from the iterator.
    - Once you’ve reached the end of the collection, calling `next` will raise a `StopIteration` error.

---

### **Example 1: Iterating Through a List**

```python
# Step 1: Create a list (iterable)
numbers = [10, 20, 30, 40]

# Step 2: Create an iterator from the list
iterator = iter(numbers)

# Step 3: Use next() to fetch elements one by one
print(next(iterator))  # Output: 10
print(next(iterator))  # Output: 20
print(next(iterator))  # Output: 30
print(next(iterator))  # Output: 40

# Step 4: Try fetching beyond the end (raises an error)
# print(next(iterator))  # Raises StopIteration
```

---

### **How It Works**

1. **`iter(numbers)`**:
    - Converts the list `numbers` into an **iterator**.
    - The iterator knows the list and where it starts.
2. **`next(iterator)`**:
    - Fetches the first element (`10`) and moves the pointer forward.
    - Fetches the second element (`20`) when called again, and so on.
3. **End of Iteration**:
    - Once all elements are accessed, calling `next` again raises a `StopIteration` error.

---

### **Example 2: Iterating Through a String**

```python
# Step 1: Create a string (iterable)
word = "hello"

# Step 2: Create an iterator for the string
iterator = iter(word)

# Step 3: Fetch characters one by one
print(next(iterator))  # Output: h
print(next(iterator))  # Output: e
print(next(iterator))  # Output: l
print(next(iterator))  # Output: l
print(next(iterator))  # Output: o

# Step 4: StopIteration occurs after the last character
# print(next(iterator))  # Raises StopIteration
```

---

### **Example 3: Using a Loop Instead of `next`**

Instead of manually calling `next`, you can use a `for` loop, which handles the iterator automatically.

```python
# Step 1: Create a list
fruits = ["apple", "banana", "cherry"]

# Step 2: Iterate with a for loop
for fruit in fruits:
    print(fruit)

# Output:
# apple
# banana
# cherry
```

**Why?**

- A `for` loop implicitly creates an iterator and uses `next` behind the scenes to fetch elements.

---

### **Why Are Iterators Useful?**

1. **Memory Efficient**:
    - Instead of loading all data at once, iterators fetch elements **one at a time**, saving memory.
    - Great for handling large datasets or streams of data.
2. **Custom Traversals**:
    - You can customize how you access data, such as skipping elements or processing in chunks.

---

### **Custom Example: Simulating a Playlist**

Imagine you’re creating a playlist system where you play one song at a time:

```python
# Step 1: Create a playlist (iterable)
playlist = ["Song 1", "Song 2", "Song 3"]

# Step 2: Create an iterator
song_iterator = iter(playlist)

# Step 3: Play songs one by one
print("Now playing:", next(song_iterator))  # Output: Now playing: Song 1
print("Now playing:", next(song_iterator))  # Output: Now playing: Song 2
print("Now playing:", next(song_iterator))  # Output: Now playing: Song 3

# Step 4: Handle the end
try:
    print("Now playing:", next(song_iterator))  # Raises StopIteration
except StopIteration:
    print("End of playlist!")
```

---

### **Summary**

1. **`iter`**: Converts an iterable (like a list or string) into an iterator.
2. **`next`**: Fetches the next item from the iterator.
3. **Why Useful**: Efficient for large data and allows for custom traversal.

### Python String Methods

- Python String Methods
    
    
    var = " The variable "
    
    You can also use some functions on them like 
    `print(func-name(var))` where func-name can be: min,max,sum,len etc. 
    
    **.strip**: Removes leading and trailing whitespace from the string
    `print(var.strip())` → `The variable` 
    
    **.lstrip**: Removes leading whitespace from the string
    `print(var.lstrip())` → `The variable`
    
    **.rstrip**: Removes trailing whitespace from the string
    `print(var.rstrip())` → `The variable`
    
    **.lower**: Converts all characters in the string to lowercase
    `print(var.lower())` → `the variable`
    
    **.upper**: Converts all characters in the string to uppercase
    `print(var.upper())` → `THE VARIABLE`
    
    **.title**: Converts the first character of each word to uppercase
    `print(var.title())` → `The Variable`
    
    **.split**: Splits the string into a list where each word is a list item
    `print(var.split())` → `['The', 'variable']`
    
    **.join**: Joins the elements of a list into a single string
    `print(' '.join(['The', 'variable']))` → `The variable`# You can also use the variable name e.g ' '.join(var)
    `` 
    **.find**: Returns the index of the first occurrence of the specified substring
    `print(var.find('variable'))` → `5`
    
    **.replace**: Replaces a specified phrase with another specified phrase
    `print(var.replace('The', 'A'))` → `A variable`
    
    **.startswith**: Returns `True` if the string starts with the specified value
    `print(var.startswith(' The'))` → `True`
    
    **.endswith**: Returns `True` if the string ends with the specified value
    `print(var.endswith('variable '))` → `True`
    

- Understanding the "before" and "after"
**Function before:** Functions that take the variable as an argument (e.g., `print(len(var))`).
**Method after:** Methods that are called on the variable itself using dot notation (e.g., `print(var.upper())`).
- Understanding `dir()
**dir()**`: Returns a list of the attributes and methods of any object (functions, modules, strings, lists, dictionaries, etc.).
**Example**: `str = "hello"`, `print(dir(str))` (Outputs a list of methods available for the string object `str`)
- `del var_name` # This is used to delete a variable you can also use this on list tuples etc but not inside tupel if you use on tupel it will delete the whole tupel

## Python Data Structures and Types

### List [ ]

- List [ ]
**Description**: An ordered, mutable collection of elements.
**Example**: `my_list = [1, 2, 3, 4]`
use print(dir(my_list)) # To get the methods that you can use this variable 
you can convert a variable to list using `list(var)` ,to print use print function
To make a list `**list(range(start, stop, step))`**
: Converts the range object to a list.
Examples:
    
    Example:
    `list(range(1, 10, 2))` → `[1, 3, 5, 7, 9]`
    
    **.append**: Adds an element to the end of the list 
    `my_list.append(5)` → `[1, 2, 3, 4, 5]`
    **.remove**: Removes the first occurrence of the specified value
     `my_list.remove(2)` → `[1, 3, 4, 5]` 
    **.pop**: Removes and returns the element at the specified position
     `my_list.pop(1)` → `[1, 4, 5]` (returns `3`)
    **.sort**: Sorts the list in ascending order
     `my_list.sort()` → `[1, 4, 5]`
    To Join a list:
    `input=["Abdeali","Dodia","Bangalore"]
    print(" ".join(input))` 
    Make list From Strings:
    
    - **`word.split()`**: Splits a string into a list of words (substrings) based on a delimiter (default is whitespace). For example, `"hello world".split()` returns `['hello', 'world']`.
    - **`list(word)`**: Converts a string into a list of individual characters. For example, `list("hello")` returns `['h', 'e', 'l', 'l', 'o']`.

### Tuple ( )

- Tuple ( )
**Description**: An ordered, immutable collection of elements.
Elements in a tuple maintain the order in which they were added. You can access elements by their position (index) starting from 0.
**Example**: `my_tuple = (1, 2, 3, 4)`
**.count**: Returns the number of times a specified value occurs in a tuple
`my_tuple.count(2)` → `1`
**.index**: Returns the index of the first occurrence of the specified value
`my_tuple.index(3)` → `2`

### Dictionary { }

- Dictionary { }
**Description**: A collection of key-value pairs.
Dictionaries in Python use string keys for accessing values.
for example `print(my_dict[’a’])` and not `print(my_dict[0])` this is wrong 
Examples:
    
    **Example**: `my_dict = {"a": 1, "b": 2, "c": 3}` 
    **.keys**: Returns a view object containing the dictionary's keys
    `my_dict.keys()` → `dict_keys(['a', 'b', 'c'])`
    
    .**values**: Returns a view object containing the dictionary's values
    `my_dict.values()` → `dict_values([1, 2, 3])` 
    
    **.items**: Returns a view object containing the dictionary's key-value pairs
    `my_dict.items()` → `dict_items([('a', 1), ('b', 2), ('c', 3)])` 
    
    **.get**: Returns the value for the specified key if the key is in the dictionary
    `my_dict.get('a')` → `1` 
    
    **.update**: Updates the dictionary with elements from another dictionary or an iterable of key-value pairs
    `my_dict.update({"d": 4})` → `{"a": 1, "b": 2, "c": 3, "d": 4}`  
    

### Set { }

- Set { }
**Description**: An unordered collection of unique elements, That’s Mutable, The order in which elements appear within the set might not be the same when you iterate over them. Elements are unique and accessed directly
    
    
    **Example**: `my_set = {1, 2, 3, 4}` 
    
    .**add**: Adds an element to the set
    `my_set.add(5)` → `{1, 2, 3, 4, 5}` 
    
    **.remove**: Removes the specified element from the set
    `my_set.remove(3)` → `{1, 2, 4, 5}` 
    
    **.union**: Returns a set containing all elements from both sets
    `my_set.union({6, 7})` → `{1, 2, 4, 5, 6, 7}` 
    
    .**intersection**: Returns a set containing only elements found in both sets
    `my_set.intersection({4, 5, 6})` → `{4, 5}` 
    
    **.difference**: Returns a set containing elements in the first set but not in the second
    `my_set.difference({2, 4})` → `{1, 5}`
    

## Modules :-

**Module**: A file containing Python code (functions, classes, variables, etc.) that can be imported and used in other Python files

- Using Code/module from Another File
1. create a file `mymodule.py` and add some code to it e.g 
`lname=”Qureshi”` 
2. create a new file in same directory and import the first file 
`import mymodule` # This line imports the first file , you can also use `as` to give it an alias e.g `import mymodule as mod` and then use `mod.lname`
`print(mymodule.lname)` # This will print lname variable from the module  
# You can also use `from mymodule import *` this will import everything from the specified module and you won’t even have to use `mymodule.lname`  you can then call the variable directly like `print(lname)`
- help(<module-name>) 
# you can use help() to get help/manual page but you have to import the module first e.g
`import os
help(os)` ( Output: help page for os module)
#You can also use `dir(os)` to get the function and methods for the os module
- PIP
you can also install modules using pip
pip install module-name
pip uninstall module-name
pip install pandas==1.3.4 # This is used to install a specific version of the module

### OS Module

- OS Module in python
The `os` module is a powerful tool for interacting with the underlying operating system from your Python programs. By understanding its functionalities, you can automate tasks, manage files and directories, and leverage system resources effectively.
    
    
    `dir(os)` # To get the function and methods of os module 
    `os.system(”ipconfig”)` # This is used to run commands, But it only runs the command and dosen’t save the output , To save output use popen.
    `cmd1=os.popen("dir").read()` # This will run the command but also output if .read() is used 
    
    `import os
    print(os.getcwd())
    os.chdir("C:\\users\\salman\\")
    print(os.getcwd())` 
    `os.getcwd()` # is used to print the current working directory 
    `os.chdir()` # this is used to change the working directory 
    `os.mkdir("dir_name")`
    `os.listdir()`
    `os.walk(top)` This function is used to generate the file names in a directory tree by walking either top-down or bottom-up. It is useful for processing all files and subdirectories within a directory.
    When you call `os.walk`, it starts at the directory specified by `top` and walks through each directory and its subdirectories. For each directory it visits, it yields a 3-tuple (`dirpath`, `dirnames`, `filenames`).
    For each directory it visits, `os.walk` yields a 3-tuple:
    
    - `dirpath`: The path to the current directory being traversed.
    - `dirnames`: A list of the names of subdirectories in the current directory.
    - `filenames`: A list of the names of non-directory files in the current directory.
    
    `os.remove()
    os.rename('my_dir','new_dir')`
    `print(os.path.exists("c:"))`# This is used to check if the path exists , this can also be usefull to check if its a windows ( c: ) or a linux ( / ) OS 
    
    `os.path.getctime(mypath)`: This part uses the `os.path.getctime` function to retrieve the creation time of the file specified by `mypath`. It returns the creation time in seconds since the epoch (a reference point in time).
    `datetime.datetime.fromtimestamp(os.path.getctime(mypath))`: This part (if uncommented) would convert the timestamp retrieved by `os.path.getctime` into a human-readable datetime object using the `datetime` module. The result would be stored in the variable `mycutomdte`.
    
    # there  are many other things that we can use in os module best to use dir(os)
    

### Platform Module

- Platform Module 
The `platform` module in Python provides information about the system platform your program is running on. It offers various functions to retrieve details like operating system name, version, architecture, Python version, and more.
**Common Functions:**
    
    `platform.system()`: Returns the operating system name (e.g., "Windows", "Linux", "Darwin" for macOS).
    `platform.release()`: Returns the operating system release version (e.g., "10.0.0" for Windows 10).
    `platform.version()`: Returns the operating system kernel version (more specific than release version).
    `platform.machine()`: Returns the computer architecture (e.g., "x86_64", "arm").
    `platform.processor()`: Returns the processor name or identification.
    `platform.python_version()`: Returns the Python version string (e.g., "3.10.7").
    

### Sys Module ( getting Args-Parameters)

- Sys Module # IMP
The `sys` module in Python provides various functions and variables that allow you to interact with the Python interpreter. These tools help you control and inspect the execution environment of your Python programs.
**Commonly Used Functions and Variables**
    
    **sys.argv**: A list of command-line arguments passed to a Python script. # its like positional parameters in bash e.g`./script argu1 arg2` 
     Example: When you run `python3 script.py arg1 arg2`, `sys.argv` will be `['script.py', 'arg1', 'arg2']`. 
    Usage: Helps in reading input parameters passed during script execution.
    
    `sys.argv`: A list containing command-line arguments passed to the Python script when it's executed. The first element (`sys.argv[0]`) is always the script name itself, and subsequent elements are the arguments provided by the user.
    

### Date and Time Module

- Date and Time Module:
The `datetime` module in Python provides classes for manipulating dates and times. It allows you to work with dates, times, and intervals in an easy and intuitive way.
    
    `import datetime`
    **Classes in datetime Module
    `date`**: Represents a date (year, month, day).
    **`time`**: Represents a time (hour, minute, second, microsecond).
    **`datetime`**: Combines a date and a time.
    **`timedelta`**: Represents the difference between two dates or times.
    **`tzinfo`**: Provides time zone information.
    
    **datetime Module Functions and Methods
    `datetime.date`**: Represents a date (year, month, day)
    `today()`: Returns the current local date
    `fromtimestamp(timestamp)`: Returns the local date corresponding to the given POSIX timestamp
    **`datetime.time`**: Represents a time (hour, minute, second, microsecond)
    `replace()`: Returns a new `time` object with specified attributes replaced
    `isoformat()`: Returns the time formatted as a string in ISO 8601 format
    **`datetime.datetime`**: Combines a date and a time
    `now()`: Returns the current local date and time
    `utcnow()`: Returns the current UTC date and time
    `fromtimestamp(timestamp)`: Returns the local date and time corresponding to the given POSIX timestamp
    `strptime(date_string, format)`: Parses a string into a `datetime` object using the given format
    `strftime(format)`: Returns a string representing the `datetime` object formatted according to the given format
    **`datetime.timedelta`**: Represents the difference between two dates or times
    `total_seconds()`: Returns the total number of seconds contained in the duration
    **`datetime.tzinfo`**: Provides time zone information
    `utcoffset(dt)`: Returns the offset of the local time from UTC
    `dst(dt)`: Returns the daylight saving time (DST) adjustment
    
    Examples:
    `import datetime
    today = datetime.date.today()
    print("Today's date:", today)`  # Output: Today's date: 2024-07-11
    
    time.time(): Gets the current time in seconds since the epoch (January 1, 1970) #
    `sec = time.time() 
    print(sec)` -> 1657812345.678901 (example output)
    
    **Convertion:**
    datetime.datetime.fromtimestamp(seconds):
     Converts the time in seconds to a datetime object # 
    `readable_time = datetime.datetime.fromtimestamp(sec) 
    print(readable_time)` -> 2023-07-11 14:45:30.123456 (example output)
    Example:
    `os.path.getctime(mypath)`: This part uses the `os.path.getctime` function to retrieve the creation time of the file specified by `mypath`. It returns the creation time in seconds since the epoch (a reference point in time).
    `datetime.datetime.fromtimestamp(os.path.getctime(mypath))`: This part would convert the timestamp retrieved by `os.path.getctime` into a human-readable datetime object using the `datetime` module. The result would be stored in the variable `mycutomdte`.
    
    **To get today’s year date:**
    
    `date = datetime.datetime.now().year
    print(date)`
    
    ### **Common Errors with `datetime`**
    
    1. **Class vs. Instance**
        - `datetime.date` and `datetime.datetime` are classes.
        - Use `today()` or `now()` to create an instance:
            
            ```python
            today = datetime.date.today()  # Instance of today's date
            
            ```
            
    2. **`strftime` Usage**
        - Formats a date/time object into a string.
        - Must be called on an instance:
            
            ```python
            today = datetime.date.today()
            print(today.strftime("%Y"))  # Outputs year
            ```
            
    3. **Method Calls**
        - Add parentheses `()` to call methods:
            
            ```python
            datetime.date.today()  # Correct
            datetime.date.today    # Returns method reference, not the date
            ```
            
    4. **Undefined Variables**
        - Ensure variables like `date` are defined and initialized.
    
    ---
    
    ### **Best Practices**
    
    1. Always create an instance before formatting or using methods.
    2. Verify method names and arguments.
    3. Test small parts of your code for clarity.
    
    More info: [Python `datetime` docs](https://docs.python.org/3/library/datetime.html)
    

### **smtplib Module (sending emails)**

- **smtplib Module:**
`smtplib` module is used for sending emails using the Simple Mail Transfer Protocol (SMTP). Below is a detailed guide on how to use `smtplib` to send emails.
    
    Example:
    `import smtplib
    my_mail="email@gmail.com"
    password="password123"
    SUBJECT="Alnafi"
    TEXT="HI team, This testing email via smtp server"
    abd='Subject: {}\n\n{}'.format(SUBJECT,TEXT)
    connection=smtplib.SMTP('smtp.gmail.com')
    connection.starttls()`       #TLS transport layer security
    `connection.login(user=my_mail,password=password)
    connection.sendmail(from_addr=my_mail,to_addrs="sender's.email@gmail.com",msg=abd)
    connection.close()
    print("Mail has been sent")`
    
    **Using EmailMessage**:
    
    `import smtplib
    from email.message import EmailMessage`
    
    #Set up the SMTP server and port
    
    `smtp_server = '[smtp.example.com](http://smtp.example.com/)'
    smtp_port = 587` 
    
    #Log in to the SMTP server
    
    `smtp_user = 'your_email@example.com'
    smtp_password = 'your_password'`
    
    #Create the email content
    
    `from_email = 'your_email@example.com'
    to_email = 'recipient@example.com'
    subject = 'Test Email'
    body = 'This is a test email sent from Python using EmailMessage.'`
    
    #Create the EmailMessage object
    
    `msg = EmailMessage()
    msg['From'] = from_email
    msg['To'] = to_email
    msg['Subject'] = subject
    msg.set_content(body)` 
    #Attach a file
    `file_path = 'path/to/your/file.txt'
    with open(file_path, 'rb') as file:
    file_data = file.read()
    file_name = 'file.txt'
    msg.add_attachment(file_data, maintype='application', subtype='octet-stream', filename=file_name)`
    
    #Send the email
    
    `try:
    server = smtplib.SMTP(smtp_server, smtp_port)`  # Connect to the SMTP server
    `server.starttls()`  # Secure the connection
    `server.login(smtp_user, smtp_password)`  # Log in to the server
    `server.send_message(msg)`  # Send the email
    `print('Email sent successfully!')
    except Exception as e:
    print(f'Failed to send email: {e}')
    finally:
    server.quit()`  # Close the connection to the SMTP server
    
    **Sending email using MIME (Multipurpose Internet Mail Extensions):**
    MIME (Multipurpose Internet Mail Extensions) is an extension of the original Simple Mail Transport Protocol (SMTP) email protocol. It lets users exchange different kinds of data files, including audio, video, images and application programs, over email.
    
    ```
    import smtplib
    from email.mime.multipart import MIMEMultipart
    from email.mime.text import MIMEText
    from email.mime.base import MIMEBase
    from email.mime.image import MIMEImage
    from email import  encoders
    
    filename=r"C:\Users\AbdealiDodiya\Desktop\DevOps\Python\Lecture 40\test.txt"
    mylogo=r"C:\Users\AbdealiDodiya\Desktop\DevOps\Python\Lecture 40\alnafi.jpg"
    msg=MIMEMultipart()
    
    my_mail="automation52786@gmail.com"
    password="nrjxoxmahyxzybvm"
    msg['Subject']= "my subject"
    msg['From']= my_mail
    msg['To'] = my_mail
    msg['Cc'] = 'abdealipython@gmail.com'
    
    body="""
    <html><p> <b> <i>Hi Team,<br> This is testing email server via python script. <b> <i> <br> <img src="cid:alogo" width="100" height="50"></p> </html>
    """
    msg.attach(MIMEText(body,'html'))
    
    ###LOGO section
    filelogo=open(mylogo,'rb')
    msgIMAGE=MIMEImage(filelogo.read())
    filelogo.close()
    msgIMAGE.add_header('Content-ID','<alogo>')
    msg.attach(msgIMAGE)
    
    #ATTACHMENT section
    attachment=open(filename,'rb')
    part = MIMEBase('application','octet-stream')
    part.set_payload((attachment).read())
    encoders.encode_base64(part)
    part.add_header('Content-Disposition',"attachment; filename=%s" % filename)
    msg.attach(part)
    
    connection=smtplib.SMTP('smtp.gmail.com')
    connection.starttls()       #TLS transport layer security
    connection.login(user=my_mail,password=password)
    connection.send_message(msg)
    connection.close()
    print("Mail has been sent")
    
    ```
    

### Schedule module

- schedule Module:
The `schedule` module in Python is used for scheduling tasks to run at specific intervals. This module is handy for automating repetitive tasks, such as sending emails, running backups, or checking the status of a system.
Common Methods:
    
    
    **`every`**: Schedules a new periodic job.
    **`.second(s)`**: Schedule a job to run every few seconds.
    **`.minute(s)`**: Schedule a job to run every few minutes.
    **`.hour(s)`**: Schedule a job to run every few hours.
    **`.day(s)`**: Schedule a job to run every few days.
    **`.week(s)`**: Schedule a job to run every few weeks.
    **`at`**: Schedule a job at a specific time of the day.
    **`.at('HH')`**: Schedule a job at a specific time (e.g., '10:30').
    **`do`**: Specifies the job function to be run.
    **`cancel`**: Cancels a scheduled job.
    **`run_pending`**: Runs all jobs that are scheduled to run.
    **`clear`**: Removes all jobs.
    Example:
    `import schedule
    import time`
    
    `def job():
    print("Job is running...")`
    
    `schedule.every(10).seconds.do(job)` #Schedule a job to run every 10 seconds
    
    `schedule.every().day.at("10:30").do(job)` #Schedule a job to run every day at 10:30 AM
    
    `while True:` #Run pending jobs
    `schedule.run_pending()
    time.sleep(1)`
    

### RE Module

- **Regular expressions (regex)** are a powerful tool in Python for matching patterns in text. The `re` module in Python provides functions to work with regular expressions.
**Key Functions in the `re` Module:**
    
    
    **`compile`**: Compile a regular expression pattern into a regex object. This can be used to search for patterns.
    **`re.compile(pattern)`**: Compile the pattern into a regex object.
    
    **`search`**: Search for the first location where the regex pattern matches in the string.
    **`re.search(pattern, string)**:` Returns a match object if a match is found, otherwise returns `None`.
    
    **`match`**: Check if the regex pattern matches the beginning of the string.
    **`re.match(pattern, string)`**: Returns a match object if a match is found at the beginning, otherwise returns `None`.
    
    **`findall`**: Find all substrings where the regex pattern matches in the string and return them as a list.
    **`re.findall(pattern, string)`**: Returns a list of all matches.
    
    **`finditer`**: Find all substrings where the regex pattern matches in the string and return them as an iterator of match objects.
    **`re.finditer(pattern, string)**:` Returns an iterator yielding match objects for all matches.
    
    **`sub**:` Substitute all occurrences of the regex pattern in the string with a replacement string.
    **`re.sub(pattern, repl, string)`**: Returns the string obtained by replacing the leftmost non-overlapping occurrences of the pattern in string by the replacement `repl`.
    
    **`split`**: Split the string by the occurrences of the regex pattern.
    **`re.split(pattern, string)`**: Returns a list of strings split by the pattern.
    
    Example:
    
    `import re`
    
    #Sample text
    
    `text = "The rain in Spain stays mainly in the plain."`
    
    #Search for the first occurrence of 'rain'
    
    `search_result = re.search("rain", text)
    print(search_result.group())`  # Output: rain
    
    #Find all occurrences of 'in'
    
    `findall_result = re.findall("in", text)
    print(findall_result)`  # Output: ['in', 'in', 'in', 'in']
    
    #Replace 'rain' with 'sun'
    
    `sub_result = re.sub("rain", "sun", text)
    print(sub_result)`  # Output: The sun in Spain stays mainly in the plain.
    
    #Split the text at each 'in'
    
    `split_result = re.split("in", text)
    print(split_result)`  # Output: ['The ra', ' ', ' Spa', ' stays ma', 'ly ', ' the pla', '.']
    
    The **"preceding pattern"** in regular expressions refers to the pattern or character that comes immediately before a special character like `*`, `+`, `?`, or `{}`. These special characters modify how many times the preceding pattern should appear.
    
    To clarify:
    
    - **Preceding pattern**: The specific character(s) or sub-pattern that comes directly before a special character.
    
    ### Examples:
    
    - In the pattern `a*`, the preceding pattern is `a`, meaning "0 or more occurrences of the character 'a'."
    - In the pattern `\d+`, the preceding pattern is `\d` (which represents any digit), meaning "1 or more digits."
    - In the pattern `ab{2}`, the preceding pattern is `b`, meaning "exactly two occurrences of 'b' after an 'a'."
    
    So, when we say a special character like `*` matches "0 or more repetitions of the preceding pattern," we mean it applies to the character or group of characters directly before it.
    
    Regular expressions (regex) provide a variety of special characters and sequences to help match patterns in text.
    
    ### Use the following code for sample data and practicing with re module
    
    ```python
    import re
    import nltk
    nltk.download('words')
    
    nltk.corpus.words.words('en')
    wordlist = [w for w in nltk.corpus.words.words('en') if w.islower()]
    
    [w for w in wordlist if re.search(r'^.j..t..$',w)] 
    
    output: ['ejector']
    ```
    
    ### Special Characters and Sequences
    
    **`.`**: Matches any character except a newline.
    
    **`^`**: Matches the start of the string.
    
    **`$`**: Matches the end of the string.
    
    **`*`**: Matches 0 or more repetitions of the preceding pattern.
    
    **`+`**: Matches 1 or more repetitions of the preceding pattern.
    
    **`?`**: Matches 0 or 1 repetition of the preceding pattern.
    
    **`{n}`**: Matches exactly n repetitions of the preceding pattern.
    
    **`{n,}`**: Matches n or more repetitions of the preceding pattern.
    
    **`{n,m}`**: Matches between n and m repetitions of the preceding pattern.
    
    **`\`**: Escapes special characters or signals a special sequence.
    
    `[]`: Represents a character class 
    
    ### With Examples:
    
    **`.`**: Matches any character except a newline.
    Example:
    `import re`
    
    `text = "cat bat hat"
    result = re.findall("c.t", text)`
    Output: `['cat']`
    
    Explanation: The pattern `c.t` matches any three-character word that starts with "c" and ends with "t". It found "cat".
    
    ---
    
    **`^`**: Matches the start of the string.
    Example:
    `import re`
    
    `text = "Start here"`
    
    `result = re.search("^Start", text)`
    Output: `'Start'`
    
    Explanation: The pattern `^Start` matches if the string begins with "Start".
    
    ---
    
    **`$`**: Matches the end of the string.
    Example:
    `import re`
    
    `text = "Finish here"`
    
    `result = re.search("here$", text)`
    Output: `'here'`
    
    Explanation: The pattern `here$` matches if the string ends with "here".
    
    ---
    
    **`*`**: Matches 0 or more repetitions of the preceding character.
    Example:
    `import re`
    
    `text = "aaaab"`
    
    `result = re.search("a*b", text)`
    Output: `'aaaab'`
    
    Explanation: The pattern `a*b` matches any string of "a" followed by "b", even if there are no "a"s. It found "aaaab".
    
    ---
    
    **`+`**: Matches 1 or more repetitions of the preceding character.
    Example:
    `import re`
    
    `text = "aaaab"`
    
    `result = re.search("a+b", text)`
    Output: `'aaaab'`
    
    Explanation: The pattern `a+b` matches "a" repeated one or more times followed by "b". It found "aaaab".
    
    ---
    
    **`?`**: Matches 0 or 1 repetition of the preceding character.
    Example:
    `import re`
    
    `text = "ab ac"`
    
    `result = re.findall("a?b", text)`
    Output: `['ab', 'b']`
    
    Explanation: The pattern `a?b` matches "b" optionally preceded by "a". It found "ab" and "b".
    
    ---
    
    **`{n}`**: Matches exactly n repetitions of the preceding character.
    Example:
    `import re`
    
    `text = "aaaab"`
    
    `result = re.search("a{4}b", text)`
    Output: `'aaaab'`
    
    Explanation: The pattern `a{4}b` matches exactly four "a"s followed by "b". It found "aaaab".
    
    ---
    
    **`{n,}`**: Matches n or more repetitions of the preceding character.
    Example:
    `import re`
    
    `text = "aaaaab"`
    
    `result = re.search("a{3,}b", text)`
    Output: `'aaaaab'`
    
    Explanation: The pattern `a{3,}b` matches three or more "a"s followed by "b". It found "aaaaab".
    
    ---
    
    **`{n,m}`**: Matches between n and m repetitions of the preceding character.
    Example:
    `import re`
    
    `text = "aaaaab"`
    
    `result = re.search("a{2,4}b", text)`
    Output: `'aaaab'`
    
    Explanation: The pattern `a{2,4}b` matches between two and four "a"s followed by "b". It found "aaaab".
    
    ---
    
    **`\`**: Escapes special characters or signals a special sequence.
    Example:
    `import re`
    
    `text = "2 + 2 = 4"`
    
    `result = re.search("\+", text)`
    Output: `'+'`
    
    Explanation: The pattern `\+` matches the "+" character (normally "+" is a special character in regex).
    
    ### Special Sequences
    
    **`\d`**: Matches any digit (equivalent to `[0-9]`).
    
    **`\D`**: Matches any non-digit character (equivalent to `[^0-9]`).
    
    **`\w`**: Matches any word character (equivalent to `[a-zA-Z0-9_]`).
    
    **`\W`**: Matches any non-word character (equivalent to `[^a-zA-Z0-9_]`).
    
    **`\s`**: Matches any whitespace character (spaces, tabs, newlines).
    
    **`\S`**: Matches any non-whitespace character.
    
    **`\b`**: Matches a word boundary (the position between a word and a non-word character).
    
    **`\B`**: Matches a non-word boundary.
    
    ### Example Patterns and Their Usage
    
    **`\w\w\w`**: Matches any sequence of exactly three word characters.
    
    **`\d{1,3}-\d{1,2}-\d{4}`**: Matches a pattern like a social security number (e.g., `123-45-6789`).
    
    **`[A-Za-z]+`**: Matches one or more letters, both uppercase and lowercase.
    
    **`[^0-9]+`**: Matches one or more characters that are not digits.
    
    **`a.*b`**: Matches any string that starts with `a` and ends with `b` with any characters in between.
    
    Example:
    
    `import re`
    
    Sample text
    
    `text = "My phone number is 123-456-7890. Call me at 555-1234."`
    
    Find all three-letter words
    
    `three_letter_words = re.findall(r'\b\w\w\w\b', text)
    print(three_letter_words)`  # Output: ['My', '123', 'Call']
    
    Find all phone numbers in the format xxx-xxx-xxxx
    
    `phone_numbers = re.findall(r'\d{3}-\d{3}-\d{1,4}', text)
    print(phone_numbers)`  # Output: ['123-456-7890']
    
    Find all sequences of non-digit characters
    
    `non_digit_sequences = re.findall(r'\D+', text)
    print(non_digit_sequences)`  # Output: ['My phone number is ', '-', '-', '. Call me at ', '-']
    
    Find all word boundaries
    
    `word_boundaries = re.findall(r'\b\w+\b', text)
    print(word_boundaries`)  # Output: ['My', 'phone', 'number', 'is', '123', '456', '7890', 'Call', 'me', 'at', '555', '1234']
    
    **"Either/Or", "And/In-between", and special handling for characters like `.`** in regular expressions.
    
    ---
    
    ### Logical Operators and Special Handling in Regex
    
    ### 1. **Either/Or (`|`)**
    
    - The pipe (`|`) acts like an OR operator, matching either the pattern on the left or the pattern on the right.
    
    **Example**:
    
    ```python
    import re
    
    text = "cat bat hat"
    result = re.findall("cat|bat", text)
    print(result)  # Output: ['cat', 'bat'
    
    ```
    
    Explanation: The pattern `cat|bat` matches either "cat" or "bat".
    
    ---
    
    ### 2. **And/In-Between (`.*` or explicit sequences)**
    
    - Regex does not have a direct AND operator but can match patterns in sequence.
    - To match text containing both patterns in any order, use `.*` to allow any characters in between.
    
    **Example**:
    
    ```python
    import re
    
    text = "I have a cat and a bat."
    result = re.search("cat.*bat|bat.*cat", text)
    print(result.group())  # Output: 'cat and a bat'
    ```
    
    Explanation: The pattern `cat.*bat|bat.*cat` matches "cat" followed by "bat" or "bat" followed by "cat", with any characters in between.
    
    ---
    
    ### 3. **Matching a Literal `.` (or Other Special Characters)**
    
    - Use a backslash (`\`) to escape special characters like `.` if you want to match them literally.
    
    **Example**:
    
    ```python
    import re
    
    text = "file1.txt file2.doc"
    result = re.findall(r"\.txt", text)
    print(result)  # Output: ['.txt']
    ```
    
    Explanation: The pattern `\.txt` matches the literal string ".txt".
    
    ---
    
    ### 4. **Using `()` for Grouping**
    
    Suppose you have a string, and you want to find patterns like "abc123" or "abc456", where the numbers can vary, but the prefix "abc" is consistent.
    
    ```python
    import re
    
    text = "abc123 def456 abc789 ghi101 abc456"
    
    # Pattern to match 'abc' followed by exactly three digits
    pattern = r"(abc)\d{3}"
    
    matches = re.findall(pattern, text)
    
    print(matches)  # Output: ['abc', 'abc', 'abc']
    ```
    
    ### Explanation:
    
    - `(abc)` is the grouped part. It matches the string "abc" as a separate group.
    - `\d{3}` matches exactly three digits after "abc."
    - Using `findall`, only the part of the pattern inside the parentheses (`abc`) is returned for each match.
    
    ### Why Use Grouping?
    
    If you didn't group `abc` (i.e., removed the parentheses), the `findall` result would include the entire match (e.g., `['abc123', 'abc789', 'abc456']`). Grouping isolates specific portions of the match for further processing.
    
    ---
    
    ### 5. Using `not` in Regular Expressions
    
    Regular expressions don’t have a direct `not` operator like in logical expressions. Instead, you use the `^` symbol (caret) **inside square brackets** `[^...]` to negate a character class. It matches any character **not listed** inside the brackets.
    
    ### Syntax:
    
    ```
    [^abc]
    ```
    
    This matches any character **except** `a`, `b`, or `c`.
    
    ---
    
    ### Examples:
    
    ### 1. Match Everything Except Specific Characters
    
    ```python
    import re
    
    text = "apple banana cherry"
    
    # Match words that do NOT contain the letters 'a', 'b', or 'c'
    pattern = r"\b[^abc\s]+\b"
    
    matches = re.findall(pattern, text)
    
    print(matches)  # Output: ['apple']
    ```
    
    - `[^abc\s]`: Matches any character that is NOT `a`, `b`, `c`, or whitespace (`\s`).
    - `\b`: Ensures word boundaries are considered.
    
    ---
    
    ### 2. Match Lines That Don’t Contain a Word
    
    If you want to match lines that do NOT contain a specific word, you can use the negative lookahead assertion `(?!...)`.
    
    ```python
    text = """This line has apples
    This line has bananas
    No fruits here"""
    
    # Match lines that do NOT contain the word 'bananas'
    pattern = r"^(?!.*bananas).*"
    
    matches = re.findall(pattern, text, re.MULTILINE)
    
    print(matches)
    # Output: ['This line has apples', 'No fruits here']
    ```
    
    - `^(?!.*bananas)`: Ensures the line does NOT contain `bananas`.
    - `.*`: Matches the rest of the line after confirming the condition
    
    ---
    
    ### Summary Table for Key Concepts
    
    | **Symbol** | **Meaning** | **Example** | **Matches** |
    | --- | --- | --- | --- |
    | ` | ` | Either/Or | `cat |
    | `.*` | Any characters (0 or more) | `cat.*bat` | "cat...bat" |
    | `\.` | Literal `.` | `file\.txt` | "file.txt" |
    | `()` | Grouping for precedence or capturing | `(cat | bat)fish` |
    | `(?:...)` | Non-capturing group | `(?:cat | bat)fish` |

### Paramiko Module (ssh)

- `Paramiko` is a Python library used to interact with SSH (Secure Shell) and SCP (Secure Copy Protocol) servers. It provides the capability to programmatically perform operations like executing remote commands, transferring files, and managing SSH keys.
**Key Features of Paramiko:**
    
    
    **SSH Client**: Connect to an SSH server and execute commands.
    **SFTP Client**: Transfer files to and from an SSH server.
    **SSH Server**: Implement your own SSH server.
    
    **SSHClient**: Represents an SSH client.
    **`connect(hostname, port, username, password)**:` Connect to an SSH server.
    **`exec_command(command)`**: Execute a command on the SSH server.
    **`close()**:` Close the SSH connection.
    
    **SFTPClient**: Represents an SFTP client.
    **`from_transport(transport)**:` Create an SFTP client from an existing SSH transport.
    **`get(remote_path, local_path)**:` Download a file from the remote server.
    **`put(local_path, remote_path)**:` Upload a file to the remote server.
    **`close()**:` Close the SFTP connection.
    
    **Connecting to an SSH Server and Executing a Command**
    
    ```python
    pythonCopy code
    import paramiko
    
    # Create an SSH client
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    # Connect to the server
    ssh.connect(hostname='your_server_ip', port=22, username='your_username', password='your_password')
    
    # Execute a command
    stdin, stdout, stderr = ssh.exec_command('ls -l')
    print(stdout.read().decode())
    
    # Close the connection
    ssh.close()
    
    ```
    
    **Transferring Files with SFTP**
    
    ```python
    pythonCopy code
    import paramiko
    
    # Create an SSH client
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    # Connect to the server
    ssh.connect(hostname='your_server_ip', port=22, username='your_username', password='your_password')
    
    # Create an SFTP client
    sftp = ssh.open_sftp()
    
    # Upload a file
    sftp.put('local_file.txt', 'remote_file.txt')
    
    # Download a file
    sftp.get('remote_file.txt', 'local_file.txt')
    
    # Close the SFTP and SSH connections
    sftp.close()
    ssh.close()
    
    ```
    

### Subprocess Module

The `subprocess` module in Python is used to run external commands or programs from within a Python script. It allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes. It's often used for executing shell commands or interacting with other command-line tools.

Here's an overview of the `subprocess` module:

### **Commonly Used Functions:**

1. **`subprocess.run()`**:
    - This is the most common way to execute a command. It runs the command described by its arguments, waits for it to complete, and then returns a `CompletedProcess` object.
    - **Example**:
        
        ```python
        import subprocess
        
        result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
        print(result.stdout)
        ```
        
2. **`subprocess.Popen()`**:
    - This is a more advanced function for running commands. It gives you more control over how the command is executed and allows interaction with the process while it's running.
    - **Example**:
        
        ```python
        import subprocess
        
        process = subprocess.Popen(["ls", "-l"], stdout=subprocess.PIPE, stderr=subprocess.PIPE)
        stdout, stderr = process.communicate()
        print(stdout.decode())
        ```
        

### **Parameters and Options:**

1. **`args`**:
    - The command and its arguments as a list. If `shell=True`, you can also provide the command as a string.
2. **`capture_output`**:
    - If `True`, captures both `stdout` and `stderr`. This is available in `subprocess.run()`.
3. **`text` (or `universal_newlines`)**:
    - If `True`, treats the input/output as text (strings) rather than bytes.
4. **`shell`**:
    - If `True`, the command will be executed through the shell. This allows you to run shell-specific commands like piping, but it can be a security risk if you're using user input in the command.
5. **`stdout`, `stderr`, `stdin`**:
    - These parameters allow redirection of the standard streams. For example, you can redirect `stdout` to a file or `PIPE` to capture the output programmatically.
6. **`check`**:
    - If `True`, raises a `CalledProcessError` if the command exits with a non-zero status.
7. **`cwd`**:
    - Specifies the working directory in which to run the command.
8. **`env`**:
    - A dictionary to set environment variables for the command.

### **Examples:**

- **Running a simple command**:
    
    ```python
    import subprocess
    
    subprocess.run(["echo", "Hello, World!"])
    ```
    
- **Capturing output**:
    
    ```python
    import subprocess
    
    result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
    print(result.stdout)
    ```
    
- **Running a command in a different directory**:
    
    ```python
    import subprocess
    
    subprocess.run(["ls", "-l"], cwd="/path/to/directory")
    ```
    
- **Handling errors**:
    
    ```python
    import subprocess
    
    try:
        subprocess.run(["false"], check=True)
    except subprocess.CalledProcessError as e:
        print(f"Command failed with return code {e.returncode}")
    ```
    

### **Use Cases:**

- Automating command-line tasks from Python.
- Interacting with other command-line tools (e.g., Git, Docker, system utilities).
- Running scripts or commands as part of automation pipelines.

### **Best Practices:**

- **Use `subprocess.run()` for simpler needs**: It’s easier to use and is sufficient for most cases.
- **Avoid using `shell=True` when possible**: This can introduce security vulnerabilities, especially when passing user input. Instead, pass commands as lists.
- **Handle errors properly**: Always check the return code or use the `check` parameter to handle errors effectively.

Here's a detailed example of how to use the `subprocess` module with many of the common parameters and options. The scenario will be a script that automates the backup of files to a remote server using `rsync`, captures the output, and logs it into a file. We'll also handle errors and specify the environment for the process.

### **Use Case: Automated File Backup with Error Handling**

```python
import subprocess
import os

# Define the source directory and the destination (remote server)
source_dir = "/path/to/backup/"
destination = "user@remote-server:/path/to/remote/backup/"

# Create a log file to store the output and errors
log_file = "backup_log.txt"

# Define the rsync command as a list of arguments
command = ["rsync", "-avz", source_dir, destination]

# Define custom environment variables (if needed)
env_vars = os.environ.copy()
env_vars["RSYNC_RSH"] = "ssh"

# Open the log file in append mode
with open(log_file, "a") as log:
    try:
        # Run the rsync command using subprocess.run()
        result = subprocess.run(
            command,
            capture_output=True,     # Capture both stdout and stderr
            text=True,               # Treat output as text (string), not bytes
            check=True,              # Raise an error if rsync fails
            env=env_vars,            # Pass custom environment variables
            cwd="/home/user",        # Change the working directory to /home/user
        )

        # Write the stdout and stderr to the log file
        log.write("Backup successful!\n")
        log.write(result.stdout)  # Write the output (stdout) to the log
        log.write(result.stderr)  # Write any error messages (stderr) to the log

    except subprocess.CalledProcessError as e:
        # Handle the error if rsync fails
        log.write(f"Backup failed with return code {e.returncode}\n")
        log.write(e.stdout)  # Write any output before the failure
        log.write(e.stderr)  # Write the error message to the log
        print(f"Backup failed! Check {log_file} for details.")
    except Exception as e:
        # Catch any other exceptions that might occur
        log.write(f"An unexpected error occurred: {e}\n")
        print(f"An unexpected error occurred. Check {log_file} for details.")
    else:
        # If everything was successful, print a confirmation message
        print("Backup completed successfully!")
```

### **Explanation:**

1. **Define the command:**
    - The `command` variable contains the `rsync` command and its arguments as a list of strings. `rsync` is a tool for copying and synchronizing files.
2. **Environment Variables (`env` parameter):**
    - We create a copy of the current environment variables using `os.environ.copy()` and modify it to add a custom variable `RSYNC_RSH`. This specifies that `rsync` should use SSH for the transfer.
3. **Running the command (`subprocess.run()`):**
    - We use `subprocess.run()` to execute the command. Key options:
        - `capture_output=True`: Captures the output and error messages.
        - `text=True`: Treats the output as text instead of raw bytes.
        - `check=True`: Raises a `CalledProcessError` if `rsync` fails.
        - `env=env_vars`: Passes the modified environment variables to the subprocess.
        - `cwd="/home/user"`: Changes the working directory to `/home/user` before running the command.
4. **Logging:**
    - We open a log file in append mode (`"a"`) so that we can continuously log the results of each backup run.
    - After the command is executed, we write both the `stdout` (standard output) and `stderr` (error output) to the log file.
5. **Error Handling:**
    - We handle errors using a `try-except` block.
    - If `rsync` fails, the `subprocess.CalledProcessError` is caught, and the error message, along with any output, is written to the log.
    - A generic `except` block catches any other unexpected errors and logs them as well.
6. **Success Message:**
    - If the backup completes successfully, a message is printed to the console, and the success message is logged.

- Running `pip freeze > requirements.txt` will save all the installed Python packages and their versions in a file named `requirements.txt`. This file can later be used to recreate the same environment by running `pip install -r requirements.txt`.

### **Boto3 Overview**

Boto3 is the official Python SDK for Amazon Web Services (AWS). It allows developers to interact with AWS services programmatically. Using Boto3, you can automate AWS tasks like creating and managing resources (EC2 instances, S3 buckets, etc.).

### **Key Features of Boto3**

- **Resource and Client APIs**: Simplified and low-level APIs to interact with AWS services.
- **Session Management**: Handles authentication and authorization using AWS credentials.
- **Support for AWS Services**: Covers a wide range of AWS services with pre-built methods.
- **Asynchronous Operations**: Supports long-running operations using pagination and waiters.

### **Use Cases for Boto3**

- Automating the provisioning of AWS resources like EC2, RDS, and S3.
- Managing AWS infrastructure as part of DevOps workflows.
- Fetching data from AWS services for analytics or monitoring.
- Uploading and downloading files to/from S3 buckets.

---

### **Key Components of Boto3**

### **1. Sessions**

A session stores configuration information (e.g., credentials and regions).

```python
import boto3

# Create a session
session = boto3.Session(
    aws_access_key_id='YOUR_ACCESS_KEY',
    aws_secret_access_key='YOUR_SECRET_KEY',
    region_name='us-west-2'
)

```

### **2. Clients**

Clients provide a low-level interface to AWS services.

```python
# Create an S3 client
s3_client = boto3.client('s3')

# List all S3 buckets
buckets = s3_client.list_buckets()
print(buckets['Buckets'])

```

### **3. Resources**

Resources offer a higher-level, object-oriented interface.

```python
# Create an S3 resource
s3_resource = boto3.resource('s3')

# Access a bucket and upload a file
bucket = s3_resource.Bucket('my-bucket')
bucket.upload_file('local_file.txt', 'remote_file.txt')

```

---

### **Commonly Used Boto3 Methods**

| **Method** | **Description** |
| --- | --- |
| `client('service')` | Creates a low-level client for a service (e.g., S3, EC2). |
| `resource('service')` | Creates a high-level resource for a service. |
| `list_buckets()` | Lists all S3 buckets in the account. |
| `upload_file()` | Uploads a file to an S3 bucket. |
| `create_instances()` | Launches EC2 instances. |
| `terminate_instances()` | Terminates EC2 instances. |

---

### **Example: Automating S3 File Upload**

```python
import boto3

# Initialize the S3 resource
s3 = boto3.resource('s3')

# Specify the bucket name and file
bucket_name = 'my-s3-bucket'
local_file = 'example.txt'
s3_file = 'uploaded_example.txt'

# Upload the file
s3.Bucket(bucket_name).upload_file(local_file, s3_file)
print(f"Uploaded {local_file} to {bucket_name}/{s3_file}")

```

---

### **Best Practices**

- Use **IAM roles** instead of hardcoding credentials.
- Enable **logging** for debugging and tracking API calls.
- Use **pagination** for large datasets to avoid overwhelming responses.
- Secure sensitive data (e.g., access keys) using environment variables or AWS Secrets Manager.

---

### **Links**

- Official Boto3 Documentation
- [AWS SDKs and Tools](https://aws.amazon.com/tools/)

# Python Selenium

**Selenium** 
is a popular open-source tool used for automating web browsers. It allows you to write scripts that can interact with web pages, just like a human would, by performing tasks such as clicking buttons, filling out forms, navigating through pages, and more.

### Overview of Selenium

**Purpose**: Selenium is primarily used for testing web applications, but it can also be used for web scraping and automating repetitive tasks on web pages.

### Key Components of Selenium

1. **Selenium WebDriver**:
    - **WebDriver** is the core component of Selenium. It provides a way to interact with web browsers programmatically.
    - It supports multiple browsers like Chrome, Firefox, Safari, and Edge.
    - You can write scripts in various programming languages like Python, Java, C#, Ruby, and JavaScript.
2. **Selenium IDE**:
    - **IDE** (Integrated Development Environment) is a browser extension for Chrome and Firefox.
    - It's used to record and playback user interactions with a web page.
    - Useful for creating simple scripts without writing code, but it's less flexible and powerful compared to WebDriver.
3. **Selenium Grid**:
    - **Grid** allows you to run your tests on different machines and browsers simultaneously.
    - It's useful for distributed testing and cross-browser testing.

### Basic Workflow of Using Selenium

1. **Set Up Selenium**:
    - Install the necessary browser driver (e.g., ChromeDriver for Chrome) and the Selenium package.
    - Example: For Python, you can install Selenium using `pip install selenium`.
2. **Initialize WebDriver**:
    - Start a WebDriver instance for the browser you want to automate.
3. **Navigate to a Web Page**:
    - Use the WebDriver to open a specific URL.
4. **Interact with Web Elements**:
    - You can locate elements on the web page using various methods like `id`, `name`, `class`, `CSS selectors`, `XPath`, etc.
    - Perform actions like clicking, typing, selecting options, and more.
5. **Perform Assertions**:
    - In testing, you can check whether the web page behaves as expected by making assertions.
6. **Close the Browser**:
    - Once the tasks are complete, you can close the browser using WebDriver.

### Example Use Cases

- **Automated Testing**: Test web applications automatically by simulating user interactions.
- **Web Scraping**: Extract data from web pages by navigating through them programmatically.
- **Repetitive Tasks**: Automate routine tasks like logging into a website, filling out forms, or downloading files.

### Basic Example of a Selenium Script (Python)

- **Open a browser**.
- **Navigate to a webpage**.
- **Find an element on the page and interact with it** (e.g., click a button or type in a search box).
- **Close the browser**.

Selenium is a powerful tool, and once you get familiar with its basics, you'll be able to automate complex workflows on the web.

### **Basics**

- **Installation**:
    - Install Selenium using pip: `pip install selenium`
    - Download the appropriate WebDriver (like ChromeDriver for Chrome) to enable browser automation.
- **Basic Setup**:
    - **Importing Selenium**:
        - Import WebDriver: `from selenium import webdriver`
        - Import Service: `from selenium.webdriver.chrome.service import Service`
    - **Setting up WebDriver**:
        - Define the path to the WebDriver: `service = Service('path/to/chromedriver')`
        - Initialize the WebDriver: `driver = webdriver.Chrome(service=service)`
- **Common Methods**:
    - **`driver.get(URL)`**: Opens the given URL in the browser.
    - **`driver.maximize_window()`**: Maximizes the browser window.
    - **`driver.find_element_by_id('id'`)**: Finds a web element by its ID.
    - **`driver.find_element_by_name('name')`**: Finds a web element by its name attribute.
    - **`driver.find_element_by_xpath('xpath')`**: Finds a web element by its XPath.
    - **`driver.quit()`**: Closes all browser windows and ends the WebDriver session.
    - **`driver.close()`**: Closes the current browser window.
- **Locating Elements**:
    - **By ID**: `driver.find_element_by_id('element_id')`
    - **By Name**: `driver.find_element_by_name('element_name')`
    - **By Class Name**: `driver.find_element_by_class_name('class_name')`
    - **By XPath**: `driver.find_element_by_xpath('xpath_expression')`
    - **By CSS Selector**: `driver.find_element_by_css_selector('css_selector')`
- **Interacting with Elements**:
    - **Clicking a Button**: `element.click()`
    - **Entering Text**: `element.send_keys('text')`
    - **Submitting a Form**: `element.submit()`
- **Handling Browser Actions**:
    - **`driver.back()`**: Navigates back in the browser history.
    - **`driver.forward()`**: Navigates forward in the browser history.
    - **`driver.refresh()`**: Refreshes the current page

### **WebDriver Manager Overview**

**WebDriver Manager**: WebDriver Manager is a Python package that helps manage browser drivers (like ChromeDriver, GeckoDriver, etc.) automatically. It simplifies the setup process by downloading the correct version of the WebDriver for your browser, eliminating the need for manual downloads and path configurations.

- **Installation**:
    - Install WebDriver Manager using pip: `pip install webdriver-manager`
- **Using WebDriver Manager with Selenium**:
    - **Import WebDriver Manager**:
        - Import the WebDriver and WebDriver Manager:
        `from selenium import webdriver`
        - `from webdriver_manager.chrome import ChromeDriverManager`
    - **Setup WebDriver**:
        - Use WebDriver Manager to automatically handle the driver setup:
        `driver = webdriver.Chrome(ChromeDriverManager().install())`
- **Benefits**:
    - **Automatic Updates**: Ensures you're always using the correct and most up-to-date WebDriver version compatible with your browser.
    - **No Path Setup**: Eliminates the need to manually download WebDriver binaries and set the path in your code.
    - **Cross-Browser Support**: Works with different browsers like Chrome, Firefox, Edge, and Opera by using the corresponding WebDriver Manager.
- **Example**:
    - The WebDriver Manager automatically downloads and sets up the ChromeDriver, allowing you to start using Selenium without worrying about compatibility issues:
    `driver = webdriver.Chrome(ChromeDriverManager().install())`
    - This command takes care of everything needed to start a Selenium session in Chrome.

### Locators

- In Selenium, locators are used to identify web elements on a page. Here are the 8 locators in Selenium, listed in order of priority based on their reliability and performance:
    1. **ID**:
        - `find_element_by_id("element_id")`
        - Most reliable as IDs are unique within the page.
    2. **Name**:
        - `find_element_by_name("element_name")`
        - Useful when elements do not have unique IDs but have unique names.
    3. **XPath**:
        - `find_element_by_xpath("//tagname[@attribute='value']")`
        - Very powerful, can locate elements based on various criteria. Slower than ID and Name.
    4. **CSS Selector**:
        - `find_element_by_css_selector("tagname[attribute='value']")`
        - Faster than XPath and very versatile, can select based on classes, IDs, attributes.
    5. **Class Name**:
        - `find_element_by_class_name("class_name")`
        - Good for selecting elements by their class attribute, though not unique.
    6. **Tag Name**:
        - `find_element_by_tag_name("tagname")`
        - Useful when you want to find elements with a specific tag (e.g., `div`, `span`).
    7. **Link Text**:
        - `find_element_by_link_text("link_text")`
        - Used for selecting links (anchor tags) by their exact visible text.
    8. **Partial Link Text**:
        - `find_element_by_partial_link_text("partial_link_text")`
        - Useful when the link text is long, and you want to match part of it.
    
    ### Priority Notes:
    
    - **ID** and **Name** are typically the fastest and most reliable locators.
    - **XPath** and **CSS Selector** are very powerful and flexible but generally slower.
    - **Class Name** and **Tag Name** are used when there are no unique identifiers.
    - **Link Text** and **Partial Link Text** are mainly used for hyperlinks but are less flexible.

### **Implicit Wait & Explicit Wait**

### Implicit Wait

- **Definition**: Implicit Wait is a type of wait that applies globally to all elements in the WebDriver instance. It tells WebDriver to wait for a certain amount of time when trying to locate an element if it is not immediately available. If the element is found within the wait time, it proceeds immediately. Otherwise, it waits for the duration before throwing an exception.
- **Syntax**: `driver.implicitly_wait(time_in_seconds)`
- **Usage**: This is useful when you want WebDriver to poll the DOM at regular intervals and continue only when the element is available, but without needing to specify the wait for each element explicitly.
- **Example**:
    - `driver.implicitly_wait(10)` will make WebDriver wait for up to 10 seconds for elements to be found.

### Explicit Wait

- **Definition**: Explicit Wait is a type of wait that allows you to specify a condition and maximum wait time for WebDriver to check before proceeding. This is more flexible compared to Implicit Wait because it allows you to wait for specific conditions (e.g., element to be clickable, element to be visible).
- **Syntax**:
    - `WebDriverWait(driver, timeout).until(condition)`
- **Usage**: This is useful when you want WebDriver to wait for a specific element or condition before proceeding, and you need more fine-grained control over the waiting.
- **Example**:
    - `WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.ID, 'submit_button')))` will make WebDriver wait up to 10 seconds for the element with the ID 'submit_button' to be clickable.

### Differences

1. **Scope**:
    - Implicit Wait applies globally to all elements in the WebDriver instance.
    - Explicit Wait is applied only to a specific element or condition.
2. **Usage**:
    - Implicit Wait is a simpler way to set a wait time for all elements.
    - Explicit Wait provides more control and is more flexible by allowing specific conditions to be defined.
3. **Control**:
    - Implicit Wait does not allow for conditions, it just waits for the element to appear.
    - Explicit Wait allows for conditions like visibility, clickability, etc.

- **For using implicit and explicit waits in your Selenium code, you'll need the following modules and setup:**
    
    ### Required Modules
    
    1. **`selenium.webdriver.common.by`**: Used to locate elements by specific strategies like ID, XPATH, CSS_SELECTOR, etc.
    2. **`selenium.webdriver.support.ui.WebDriverWait`**: Required for setting up explicit waits.
    3. **`selenium.webdriver.support.expected_conditions`**: Contains conditions like element visibility, clickability, etc., for explicit waits.
    4. **`webdriver_manager`**: To manage your WebDriver installations (e.g., ChromeDriver, GeckoDriver).
    
    ### Setting Up Implicit Wait
    
    - To apply an implicit wait globally across your WebDriver instance, use `driver.implicitly_wait(time_in_seconds)`.
    - Example:
        - `driver.implicitly_wait(10)` will make WebDriver wait up to 10 seconds for all elements to appear before throwing an exception.
    
    ### Setting Up Explicit Wait
    
    - To apply an explicit wait for a specific condition, use `WebDriverWait` along with `expected_conditions`.
    - Example:
        - `WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.ID, 'element_id')))` will make WebDriver wait up to 10 seconds for the element to become clickable.
    
    ### Full Code Example (Including Implicit and Explicit Waits)
    
    ```python
    pythonCopy code
    from selenium import webdriver
    from selenium.webdriver.chrome.service import Service
    from webdriver_manager.chrome import ChromeDriverManager
    from selenium.webdriver.common.by import By
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    import time
    
    # Setup WebDriver
    service = Service(ChromeDriverManager().install())
    driver = webdriver.Chrome(service=service)
    
    # Implicit wait: Applies globally to all elements
    driver.implicitly_wait(10)  # Wait up to 10 seconds for elements to be available
    
    # Navigate to Gmail login page
    driver.get("https://accounts.google.com/v3/signin/identifier?service=mail")
    
    # Maximize the window
    driver.maximize_window()
    
    # Explicit wait: Wait until the email input field is clickable
    WebDriverWait(driver, 10).until(EC.element_to_be_clickable((By.ID, "identifierId")))
    
    # Enter your email
    driver.find_element(By.ID, "identifierId").send_keys("your@gmail.com")
    
    # Click next button
    driver.find_element(By.XPATH, "/html/body/div[1]/div[1]/div[2]/c-wiz/div/div[3]/div/div[1]/div/div/button/span").click()
    
    # Additional wait for password field
    WebDriverWait(driver, 10).until(EC.visibility_of_element_located((By.NAME, "password")))
    
    # Input password and click next (Note: password element will be a placeholder here)
    driver.find_element(By.NAME, "password").send_keys("your-password")
    
    # Close the browser after pressing enter
    input("Press Enter to close...")
    
    driver.quit()
    
    ```
    
    ### Key Points
    
    1. **Modules**:
        - `webdriver`: For interacting with the browser.
        - `webdriver_manager`: For managing browser drivers.
        - `By`: For locating elements on the page.
        - `WebDriverWait`: For explicit wait.
        - `expected_conditions as EC`: For defining the condition to wait for.
    2. **Implicit Wait**: This waits for a set amount of time for every element interaction across the whole script.
    3. **Explicit Wait**: This waits for a specific condition (like an element being clickable) for a defined time only where it's applied.
    4. **Order of Usage**: Generally, use implicit waits for simple scripts where you want a global delay, and use explicit waits when you need specific conditions to be met before proceeding.

- When trying to log in to Gmail using Selenium, Google often **blocks automated login attempts due to security policies**. They can detect that a bot (Selenium) is attempting to log in, and as a result, they **flag the browser as "not secure."** This happens because Selenium uses WebDriver to automate the browser, which is recognized by websites as automated access.
    
    ### Here’s why you’re facing this issue:
    
    1. **Google Security**: Google has robust security mechanisms to prevent automated bots from accessing accounts. These mechanisms can detect WebDriver sessions and block the login attempts.
    2. **Automation Detection**: Selenium's WebDriver identifies itself in the user agent string or through other detectable means, which alerts Gmail to the automation.
    3. **Headless Mode**: Even though you’re running a visible browser, WebDriver can still be detected by advanced scripts running on websites like Google.
    
    ### Potential Solutions:
    
    1. **Use Undetected ChromeDriver**:
        - There is a Python library called `undetected-chromedriver` that aims to bypass detection mechanisms. It is specifically designed to make your WebDriver look more like a real user-controlled Chrome browser.
        
        ```python
        pythonCopy code
        import undetected_chromedriver as uc
        from selenium.webdriver.common.by import By
        import time
        
        # Use undetected chromedriver
        driver = uc.Chrome()
        
        driver.maximize_window()
        driver.get("https://accounts.google.com/v3/signin/identifier?service=mail")
        
        # submitting username
        driver.find_element(By.ID, "identifierId").send_keys("your@gmail.com")
        driver.find_element(By.XPATH, "//span[contains(text(),'Next')]").click()
        
        time.sleep(5)
        # submitting password
        driver.find_element(By.NAME, "password").send_keys("Your-Password")
        driver.find_element(By.XPATH, "//span[contains(text(),'Next')]").click()
        
        input("Press Enter to close...")
        driver.quit()
        
        ```
        
    2. **Manual Interaction**:
        - Another approach would be to perform the login manually and let Selenium take over after login. This way, you avoid automated login detection.
        - You could start the browser, log in manually, and then use Selenium to automate actions after the login is complete.
    3. **API Access**:
        - Instead of automating Gmail through Selenium, you can use Google's official APIs for interacting with Gmail. For example, the Gmail API can allow you to send, read, and manage emails programmatically without needing to use a browser.
    4. **Custom User Agent**:
        - Changing the user agent to simulate a real browser session can help sometimes, but it’s not guaranteed to bypass Google’s detection.
        
        ```python
        pythonCopy code
        from selenium import webdriver
        from selenium.webdriver.chrome.options import Options
        
        options = Options()
        options.add_argument("user-agent=Your custom user agent")
        driver = webdriver.Chrome(options=options)
        
        ```
        
    
    However, even with these methods, Google's detection system may still block you due to the strict security measures in place for accounts.
    
    ### Conclusion:
    
    While you can try the `undetected-chromedriver` library, the best practice is to avoid automating login processes for sensitive platforms like Gmail, as it may violate their terms of service. Using the Gmail API is a more reliable and recommended approach for interacting with Gmail programmatically.
    

### **Selenium Module: Functions and Methods**

The Selenium module provides tools to automate web browsers. Here's a breakdown of the key components, functions, and methods that you will use when working with Selenium:

---

### **1. WebDriver Class**

- **Purpose:** The main class for controlling and automating the web browser.

**Methods:**

- `get(url)`: Opens the given URL in the browser.
    
    Example: `driver.get("https://example.com")`
    
- `quit()`: Closes the browser window and ends the WebDriver session.
    
    Example: `driver.quit()`
    
- `close()`: Closes the current browser window without ending the session.
    
    Example: `driver.close()`
    
- `maximize_window()`: Maximizes the browser window.
    
    Example: `driver.maximize_window()`
    
- `minimize_window()`: Minimizes the browser window.
    
    Example: `driver.minimize_window()`
    
- `refresh()`: Refreshes the current page.
    
    Example: `driver.refresh()`
    
- `back()`: Navigates to the previous page in the browser history.
    
    Example: `driver.back()`
    
- `forward()`: Navigates to the next page in the browser history.
    
    Example: `driver.forward()`
    
- `find_element(By, value)`: Locates a single web element on the page using a locator strategy.
    
    Example: `driver.find_element(By.ID, "username")`
    
- `find_elements(By, value)`: Locates multiple web elements on the page.
    
    Example: `driver.find_elements(By.CLASS_NAME, "item")`
    
- `get_screenshot_as_file(filename)`: Takes a screenshot of the current window and saves it to the specified file.
    
    Example: `driver.get_screenshot_as_file("screenshot.png")`
    
- `get_window_size()`: Returns the dimensions (width and height) of the current window.
    
    Example: `driver.get_window_size()`
    
- `set_window_size(width, height)`: Resizes the window to the specified dimensions.
    
    Example: `driver.set_window_size(1024, 768)`
    
- `get_window_position()`: Returns the current position (x, y coordinates) of the window.
    
    Example: `driver.get_window_position()`
    
- `set_window_position(x, y)`: Moves the window to the specified position.
    
    Example: `driver.set_window_position(100, 200)`
    
- `switch_to.frame(frame_reference)`: Switches focus to the specified frame on the page.
    
    Example: `driver.switch_to.frame("frame1")`
    
- `switch_to.default_content()`: Switches back to the default content (main document).
    
    Example: `driver.switch_to.default_content()`
    
- `switch_to.alert`: Switches to the active alert dialog.
    
    Example: `alert = driver.switch_to.alert`
    

---

### **2. WebElement Class**

- **Purpose:** Represents a single web element on a page.

**Methods:**

- `click()`: Clicks on the element.
    
    Example: `element.click()`
    
- `send_keys(*value)`: Sends keystrokes to the element (e.g., input fields).
    
    Example: `element.send_keys("text input")`
    
- `clear()`: Clears the content of the element (used for input fields).
    
    Example: `element.clear()`
    
- `get_attribute(name)`: Retrieves the value of the specified attribute of the element.
    
    Example: `element.get_attribute("value")`
    
- `get_property(name)`: Retrieves the value of a JavaScript property of the element.
    
    Example: `element.get_property("textContent")`
    
- `text`: Returns the text content of the element.
    
    Example: `element.text`
    
- `is_displayed()`: Checks if the element is visible on the page.
    
    Example: `element.is_displayed()`
    
- `is_enabled()`: Checks if the element is enabled (can be interacted with).
    
    Example: `element.is_enabled()`
    
- `is_selected()`: Checks if the element is selected (for checkboxes, radio buttons, etc.).
    
    Example: `element.is_selected()`
    
- `submit()`: Submits a form (if the element is inside a form).
    
    Example: `element.submit()`
    
- `location`: Returns the location of the element on the page (x, y coordinates).
    
    Example: `element.location`
    
- `size`: Returns the size of the element (width, height).
    
    Example: `element.size`
    

---

### **3. `By` Class**

- **Purpose:** Provides various locator strategies to find elements on a page.

**Common Locators:**

- `By.ID`: Locates elements by the ID attribute.
    
    Example: `driver.find_element(By.ID, "element-id")`
    
- `By.NAME`: Locates elements by the name attribute.
    
    Example: `driver.find_element(By.NAME, "element-name")`
    
- `By.CLASS_NAME`: Locates elements by the class name.
    
    Example: `driver.find_element(By.CLASS_NAME, "class-name")`
    
- `By.TAG_NAME`: Locates elements by the tag name (e.g., `input`, `div`).
    
    Example: `driver.find_element(By.TAG_NAME, "input")`
    
- `By.CSS_SELECTOR`: Locates elements using CSS selectors.
    
    Example: `driver.find_element(By.CSS_SELECTOR, ".class > div")`
    
- `By.XPATH`: Locates elements using XPath expressions.
    
    Example: `driver.find_element(By.XPATH, "//div[@id='element-id']")`
    
- `By.LINK_TEXT`: Locates links by their text content.
    
    Example: `driver.find_element(By.LINK_TEXT, "Click here")`
    
- `By.PARTIAL_LINK_TEXT`: Locates links by a portion of their text content.
    
    Example: `driver.find_element(By.PARTIAL_LINK_TEXT, "Click")`
    

---

### **4. Options and Configuration**

- **`webdriver.ChromeOptions`**: Provides options for configuring Chrome WebDriver.

**Common Methods:**

- `add_argument(argument)`: Adds a command-line argument to Chrome.
    
    Example: `options.add_argument("--headless")`
    
- `add_experimental_option(name, value)`: Adds experimental options to Chrome.
    
    Example: `options.add_experimental_option("excludeSwitches", ["enable-automation"])`
    

---

### **5. Waiting Mechanisms**

- **Purpose:** Selenium provides ways to wait for certain conditions to be met (e.g., elements to be loaded) before continuing the script.

**Types of Waits:**

- **Implicit Waits:** Automatically waits for a certain amount of time for elements to be present before throwing an exception.
    
    `driver.implicitly_wait(10)` (Waits up to 10 seconds)
    
- **Explicit Waits:** Waits for a specific condition to be true before proceeding.
    
    ```python
    pythonCopy code
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    
    element = WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, "element-id"))
    )
    
    ```
    

---

### **6. Action Chains**

- **Purpose:** Used to perform complex actions such as hover, drag-and-drop, or multiple clicks.

**Methods:**

- `move_to_element(element)`: Moves the mouse to the center of the specified element.
    
    Example: `actions.move_to_element(element).perform()`
    
- `click_and_hold(element)`: Clicks and holds the mouse on the specified element.
    
    Example: `actions.click_and_hold(element).perform()`
    
- `release()`: Releases the mouse button.
    
    Example: `actions.release().perform()`
    
- `double_click(element)`: Double-clicks the specified element.
    
    Example: `actions.double_click(element).perform()`
    
- `drag_and_drop(source, target)`: Drags the source element to the target element.
    
    Example: `actions.drag_and_drop(source, target).perform()`
    

- **Selenium Grid** is a tool used to run Selenium tests in parallel across different browsers, operating systems, and machines. It allows you to distribute test execution across multiple environments to speed up your testing process.
    
    ### Key Concepts of Selenium Grid:
    
    - **Hub**: The central point where you load your tests. The hub manages test execution and routes the commands to the appropriate nodes.
    - **Node**: A machine that is registered with the hub to run tests. A node can run different browser sessions, and it can be on any machine, regardless of the operating system.
    - **Parallel Execution**: Multiple tests can be run simultaneously across different nodes.
    - **Cross-Browser Testing**: You can run tests on different browsers (e.g., Chrome, Firefox, Edge) across different nodes.
    
    ### How Selenium Grid Works:
    
    1. **Set Up Hub**: The hub is the server that distributes the tests to the nodes. You start by setting up a hub.
    2. **Set Up Nodes**: Nodes are the machines where the tests will be executed. Nodes are registered with the hub.
    3. **Test Execution**: The hub sends the test to the appropriate node based on the desired browser and operating system.
    
    ### Example Setup:
    
    1. **Start Hub**:
    Use the following command to start the hub:
        
        ```
        java -jar selenium-server-standalone.jar -role hub
        ```
        
        This will start the hub on the default port `4444`.
        
    2. **Register a Node**:
    Use the following command to register a node to the hub:
        
        ```bash
        java -jar selenium-server-standalone.jar -role node -hub http://localhost:4444/grid/register
        ```
        
        This will register the node with the hub running on `localhost`.
        
    3. **Configure Grid**: You can also configure the grid to specify the number of browser instances or other settings using a JSON configuration file.
    
    ### Example Selenium Code to Connect to Grid:
    
    ```python
    from selenium import webdriver
    from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
    
    # Set the desired capabilities (browser, version, etc.)
    capabilities = DesiredCapabilities.CHROME.copy()
    
    # Connect to the hub
    driver = webdriver.Remote(
        command_executor='http://localhost:4444/wd/hub',
        desired_capabilities=capabilities
    )
    
    # Run your test
    driver.get("https://example.com")
    print(driver.title)
    
    driver.quit()
    
    ```
    
    In this example, the test is run on a Chrome browser instance registered with the Selenium Grid hub.
    

### Example code from a project

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from webdriver_manager.chrome import ChromeDriverManager

# Setting up options for headless operation
chrome_options = Options()
chrome_options.add_argument("--headless")  # Runs Chrome in headless mode
chrome_options.add_argument("--disable-gpu")  # Disables GPU hardware acceleration
chrome_options.add_argument("--no-sandbox")  # Bypass OS security model
chrome_options.add_argument("--disable-dev-shm-usage")  # Overcome limited resource problems

# Initialize the Chrome WebDriver
service = Service(ChromeDriverManager().install())
driver = webdriver.Chrome(service=service, options=chrome_options)

# Take input:
input_file = input("Enter the filename with link: ")
output_file = input("Enter output filename: ")

# Open the file with links and the output file
with open(input_file, 'r') as links_file, open(output_file, "w") as final_file:
    links_content = links_file.readlines()

    for link in links_content:
        link = link.strip()  # Remove any extra whitespace or newline characters

        if link:
            try:
                # Navigate to the link
                print(f"Processing link: {link}")
                driver.get(link)

                # Wait until the folder name element is visible (increase wait time if necessary)
                wait = WebDriverWait(driver, 30)
                folder_name_element = wait.until(EC.visibility_of_element_located(
                    (By.CSS_SELECTOR, "span.not-loading.selectable-txt")
                ))

                # Extract folder name
                folder_name = folder_name_element.text.strip()

                # Format the output
                formatted_output = f"[{folder_name} - {link} \n]"

                # Write the formatted output to the final file
                final_file.write(formatted_output + "\n")

                print(f"Processed link: {link}")

            except Exception as e:
                # Handle any errors that occur and log them
                final_file.write(f"Failed to retrieve info for {link}:\n")
                print(f"Failed to retrieve folder name for {link}: {e}")

# Close the browser after processing all links
driver.quit()

```

# **Python Programming for Machine Learning**

### Anaconda & **Jupyter Notebook**

### **Anaconda**

Anaconda is a **distribution of Python and R** specifically designed for data science, machine learning, and scientific computing. It simplifies the installation and management of libraries and tools commonly used in these fields.

### **Key Features**:

1. **Package Management**: Comes with a package manager (`conda`) that makes it easy to install, update, and manage Python libraries like NumPy, Pandas, TensorFlow, etc.
2. **Pre-Bundled Libraries**: Anaconda includes hundreds of pre-installed libraries for data analysis, visualization, and machine learning.
3. **Virtual Environments**: Allows you to create isolated environments for different projects, so library conflicts are avoided.
4. **Integrated Tools**: Comes with **Jupyter Notebook**, **Spyder**, and other tools useful for development.

### **Use Case**:

Anaconda is perfect when you want an all-in-one solution to set up your Python environment for machine learning without worrying about manual installation of libraries and dependencies.

---

### **Jupyter Notebook**

Jupyter Notebook is a **web-based interactive computing environment**. It allows you to write and execute Python code in chunks called "cells," which makes it perfect for experimentation and data exploration.

### **Key Features**:

1. **Interactive Coding**: Write code and immediately see the output.
2. **Markdown Support**: Document your workflow with explanations, equations (LaTeX), and visualizations directly in the notebook.
3. **Data Visualization**: Integrates seamlessly with libraries like Matplotlib, Seaborn, and Plotly for plotting.
4. **Kernel Support**: Not limited to Python; supports multiple languages (like R, Julia).

### **Use Case**:

When working on machine learning or data science projects, Jupyter Notebook helps you **combine code, data visualization, and documentation in one place**. It’s widely used for prototyping and sharing analyses.

---

### **How They Work Together**

1. Install **Anaconda** (which includes Jupyter Notebook).
2. Launch **Jupyter Notebook** from Anaconda Navigator or via the terminal.
3. Start coding in a notebook to experiment with Python code, visualize data, and document your learning process.

### **NumPy Overview**

NumPy (Numerical Python) is a powerful library in Python used for numerical computations. It provides support for large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on them efficiently.

---

### **Key Features of NumPy**

1. **N-Dimensional Arrays**: Core data structure (`ndarray`) that can handle data in multiple dimensions.
2. **Fast Operations**: Optimized for performance compared to Python lists.
3. **Mathematical Functions**: Built-in support for operations like trigonometry, statistics, and linear algebra.
4. **Broadcasting**: Perform operations between arrays of different shapes.
5. **Interoperability**: Works well with other libraries like Pandas, SciPy, and TensorFlow.

---

### **Use Cases for NumPy**

- Performing **matrix operations** in machine learning algorithms.
- Handling large datasets efficiently.
- Generating random numbers for simulations or experiments.
- Preprocessing data for deep learning or statistical models.

---

### **Commonly Used NumPy Functions**

| Function | Description |
| --- | --- |
| `np.array()` | Creates an array from a list or another array-like structure. |
| `np.zeros()` / `np.ones()` | Generates arrays of zeros or ones of a specified shape. |
| `np.arange()` | Creates an array with evenly spaced values (like `range()` in Python). |
| `np.random.rand()` | Generates arrays of random numbers (uniformly distributed). |
| `np.mean()`, `np.median()` | Calculates the mean or median of an array. |
| `np.reshape()` | Changes the shape of an array without changing its data. |
| `np.dot()` / `np.matmul()` | Performs dot product or matrix multiplication. |
| `np.where()` | Conditional selection of elements from an array. |
| `np.sum()`, `np.prod()` | Calculates the sum or product of array elements. |

---

### **Example: Basic Array Operations**

```python
import numpy as np

# Creating an array
arr = np.array([1, 2, 3, 4, 5])

# Perform operations
print("Original Array:", arr)
print("Array Squared:", arr ** 2)  # Element-wise square
print("Sum of Array:", np.sum(arr))
```

---

### **NumPy Broadcasting Example**

Broadcasting allows operations on arrays of different shapes.

```python
# Example: Adding a scalar to an array
arr = np.array([1, 2, 3])
scalar = 5
print(arr + scalar)  # [6, 7, 8]

# Example: Adding arrays of different shapes
arr2 = np.array([[1], [2], [3]])  # 3x1
print(arr + arr2)
```

---

### Creating a row and a colum (Matrix)

```jsx
import numpy as np

print("Numpy Version: ", np.__version__)

vector_row = np.array([1,2,3])

vector_col = np.array([[1],[2],[3]])

print('1 x 3 Vector = ', vector_row)
print('3 x 1 Vector = ', vector_col)

# output:
# Numpy Version:  1.26.4
# 1 x 3 Vector =  [1 2 3]
# 3 x 1 Vector =  [[1]
#  [2]
#  [3]]
```

### **Links**

- [Official NumPy Documentation](https://numpy.org/doc/2.2/user/whatisnumpy.html)

### Pandas Overview

**Pandas** is a Python library widely used for data manipulation and analysis. It provides flexible and efficient tools for working with structured data like tables and time series.

---

### Key Features of Pandas

- **Data Structures**: Provides `Series` (1D) and `DataFrame` (2D) for handling data efficiently.
- **Data Manipulation**: Includes tools for filtering, reshaping, merging, and aggregating data.
- **Indexing**: Flexible indexing for aligning data from different sources.
- **Handling Missing Data**: Built-in methods to detect and handle missing values.
- **I/O Tools**: Supports reading from and writing to various file formats like CSV, Excel, SQL, and JSON.

---

### Use Cases for Pandas

- Cleaning and preparing datasets for analysis or machine learning.
- Performing exploratory data analysis (EDA).
- Handling time series data in financial applications.
- Data wrangling for statistical modeling.

---

### Commonly Used Pandas Functions

| **Functio** | **Description** |
| --- | --- |
| `pd.Series()` | Creates a one-dimensional array-like structure. |
| `pd.DataFrame()` | Creates a two-dimensional, table-like structure. |
| `df.head()` / `df.tail()` | Displays the first or last n rows of a DataFrame. |
| `df.describe()` | Provides summary statistics for numerical columns. |
| `df.info()` | Displays information about the DataFrame. |
| `df.isnull()` | Detects missing values. |
| `df.dropna()` | Removes missing values. |
| `df.fillna()` | Replaces missing values with a specified value. |
| `df.groupby()` | Groups data for aggregation or transformation. |
| `df.merge()` | Combines data from multiple DataFrames. |
| `df.apply()` | Applies a custom function to DataFrame elements. |
| `df.loc[]` / `df.iloc[]` | Selects data by label or position. |

---

### Example: Creating a DataFrame

```python
import pandas as pd

# Creating a DataFrame
data = {'Name': ['Alice', 'Bob', 'Charlie'],
        'Age': [25, 30, 35],
        'City': ['New York', 'Los Angeles', 'Chicago']}

df = pd.DataFrame(data)

# Viewing the DataFrame
print(df)
```

Output:

```markdown
markdown
Copy code
      Name  Age           City
0    Alice   25      New York
1      Bob   30  Los Angeles
2  Charlie   35       Chicago
```

---

### Example: Handling Missing Data

```python
# Adding missing data
df.loc[3] = [None, None, 'Boston']

# Filling missing values
df_filled = df.fillna({'Name': 'Unknown', 'Age': 0})
print(df_filled)
```

---

### Links

- [Official Pandas Documentation](https://pandas.pydata.org/docs/)

### Keras Overview

**Keras** is a high-level, open-source deep learning API written in Python. It is built on top of popular machine learning libraries like TensorFlow and is designed to enable fast experimentation with neural networks.

---

### Key Features of Keras

- **User-Friendly**: Simplifies the process of building and training deep learning models.
- **Modular**: Models are constructed using standalone, fully configurable modules.
- **Extensible**: Can be extended with custom layers, metrics, and losses.
- **Runs on Multiple Backends**: Compatible with TensorFlow, Theano, and CNTK.
- **Pre-Trained Models**: Includes access to state-of-the-art models for tasks like image recognition.

---

### Use Cases for Keras

- Building and training neural networks for classification, regression, and clustering.
- Experimenting with deep learning architectures in research and production.
- Transfer learning using pre-trained models for tasks like image or text analysis.

---

### Commonly Used Keras Functions

| **Function** | **Description** |
| --- | --- |
| `keras.Sequential()` | Creates a sequential model, layer by layer. |
| `keras.layers.Dense()` | Adds a fully connected (dense) layer to the model. |
| `keras.layers.Conv2D()` | Adds a convolutional layer for image processing. |
| `keras.layers.Dropout()` | Adds a dropout layer to prevent overfitting. |
| `model.compile()` | Configures the model for training by specifying loss, optimizer, and metrics. |
| `model.fit()` | Trains the model using the given data and labels. |
| `model.evaluate()` | Evaluates the model on test data. |
| `model.predict()` | Generates predictions from input data. |

---

### Example: Building a Neural Network with Keras

```python
from keras.models import Sequential
from keras.layers import Dense

# Create a sequential model
model = Sequential()

# Add layers
model.add(Dense(units=64, activation='relu', input_shape=(100,)))  # Input layer
model.add(Dense(units=10, activation='softmax'))  # Output layer

# Compile the model
model.compile(optimizer='adam',
              loss='categorical_crossentropy',
              metrics=['accuracy'])

# Summary of the model
model.summary()
```

---

### Example: Training a Model

```python
# Assume X_train, y_train are the training data and labels

# Train the model
history = model.fit(X_train, y_train,
                    epochs=10,
                    batch_size=32,
                    validation_split=0.2)
```

---

### Links

- [Official Keras Documentation](https://keras.io/)

### Steps for Training a Machine Learning Model for a Problem

### 1. **Loading Data**

- **Description**: Data can come from various sources (CSV, Excel, SQL databases, APIs, etc.) and formats (structured, unstructured, semi-structured).
- **Goal**: Load the data into your environment for analysis and processing.
- **Example**: Use libraries like `pandas` in Python to load a CSV file.
    
    ```python
    import pandas as pd
    data = pd.read_csv('dataset.csv')
    ```
    

---

### 2. **Preparing the Data**

- **Description**: Clean, transform, and prepare the data to make it suitable for training.
- **Steps**:
    - Handle **missing data** (e.g., fill or drop missing values).
    - Remove **outliers** and **noise**.
    - Normalize or scale features if needed (e.g., `MinMaxScaler` in `scikit-learn`).
    - Split the dataset into **training**, **validation**, and **test sets**.
- **Example**:
    
    ```python
    from sklearn.model_selection import train_test_split
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
    ```
    

---

### 3. **Selecting the Machine Learning Model**

- **Description**: Choose an appropriate ML algorithm based on the problem type:
    - **Regression**: Predict continuous outputs (e.g., house prices).
    - **Classification**: Predict categorical outputs (e.g., spam email detection).
    - **Clustering**: Group similar data points (e.g., customer segmentation).
- **Example**: For classification, you might select a Decision Tree, SVM, or Neural Network.
    
    ```python
    from sklearn.ensemble import RandomForestClassifier
    model = RandomForestClassifier()
    ```
    

---

### 4. **Training the Model**

- **Description**: Feed the training data into the model and adjust weights or parameters using optimization techniques.
- **Goal**: Minimize the loss function to improve the model’s accuracy.
- **Example**:
    
    ```python
    model.fit(X_train, y_train)
    ```
    

---

### 5. **Evaluating the Model**

- **Description**: Test the model's performance on unseen data (validation or test sets) and check its accuracy, precision, recall, F1 score, or other metrics.
- **Steps**:
    - Predict outcomes on the test set.
    - Compare predictions with the actual results using metrics like `accuracy_score` or `mean_squared_error`.
- **Example**:
    
    ```python
    from sklearn.metrics import accuracy_score
    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)
    print(f"Model Accuracy: {accuracy * 100:.2f}%")
    
    ```
    

---

These steps create a clear workflow for tackling a machine learning problem, from data collection to model evaluation.