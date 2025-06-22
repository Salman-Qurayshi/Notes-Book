# BASH

# **BASH**

- #!/bin/bash  # this is shibang use this so if your shell is not default for bin bash this will still make it run

- echo hello world  # this is used to print something on the screen 
Flags:
-e —> is used to interpret blackslash escape for example \n for a new line will work if echo has an -e flag e.g echo -e “here \n a new line “ OR echo -e “the value for \$a is: $a”
- cat file.txt # this will display the contant of the file, it can also be used to write to a file OR create a file and write to it e.g —> <cat >> file.txt> to append to a file and <cat > file.txt> to overwrite a file , it will take your input  and then to finish press ctrl + d
- # hi this is a commment # this is used for commenting a line in bash 
: ‘ this is used for multiple line comments ‘
>> any_value 
this is also used for multiple line comments
any_value
- `$variable` # To call a variable use dollar sign $ for example `a=10  echo $a`
Note : if you call a variable using `${var1}` method then this method is usefull for modifying the variable , So in other words you can use this way to modify and call a variable for Example: echo `“${name:0:3}”` will output the value of name but from index 0 to index 3 OR for Example echo ${MESSAGE/learning/Reading} this will replace learning with reading in the value
- `a=10`  # to assign a variable  Note that you cannot use space when signing a variable for example a = 10 this will not work and will generate an error

### capture the output of a command and store it in a variable

- The syntax **`$(command)`** is used in Bash scripting to capture the output of a command and store it in a variable. for example **`a=$(ls)`**, the **ls** command lists the files and directories in the current directory, and its output is captured and stored in the variable **a**. so `echo $a` will list everything that was stored in the directory when the variable was signed

### read

- `read name` # ( Read is used to take input from the user ). this will take the input and make a variable named name for example hello from terminal
**`read -p "Enter your name: " name` #** this is a command to take an input . <read> is used for taking input <-p> is used to display the message before taking input and <name> is then signing a value to the taken input
- echo `$name` this will print the value of name that is hello in the terminal # if you have used read without arguments then use echo $reply

### Debugging mode

- in Debugging mode it will first show the line of code and then its working to enable or disable debugging mode one can use this —> set -x # debugging mode on OR set +x # debugging mode off. AND it will also show the error in the line it self 
example:  
echo when it is on
when it is on
./bash: line 40: syntax error near unexpected token (' ./bash: line 40: echo Vs when it is off (bellow)' # it shows the error right in the output line and the syntax used

### `tr` command

- **tr**  # this is used to replace or delete a word in linux for example echo "hello world" | tr 'a-z' 'A-Z’ This command converts all lowercase letters (a-z) in "hello world" to uppercase letters (A-Z) using the pipe ( | ) to send the output of echo as input to tr # You can also use -d to only delete something

### **Conditional Statements in Bash**

Conditional statements in Bash allow you to execute commands based on conditions. They follow a specific syntax and use `if`, `elif`, `else`, and `fi` to define the logic flow.

---

### **Basic `if` Statement Syntax**

```bash
if [ condition ]; then
    # Commands to execute if the condition is true
fi
```

- `[ condition ]` is used to evaluate an expression inside the brackets.
- `then` marks the start of the commands to be executed when the condition is true.
- `fi` (reverse of `if`) marks the end of the conditional block.
- `;` is used when `then` is on the same line, if `then` is on the next line then there is no need for `;`

---

### **Full `if-elif-else` Structure**

```bash
if [ condition ]; then
    # Commands to execute if condition is true
elif [ condition2 ]; then
    # Commands to execute if condition2 is true
else
    # Commands to execute if none of the conditions are true
fi
```

---

### **Alternative Syntax Using Double Brackets (`[[ ... ]]`)**

```bash
if [[ condition ]]; then
    # Commands to execute if condition is true
fi
```

- `[[ ... ]]` is preferred over `[ ... ]` because it provides additional features such as pattern matching (`=~`) and better handling of logical operators.
- more info about this ‣

---

### **One-Liner `if` Statement**

```bash
if [ condition ]; then echo "Condition met"; fi
```

- When writing simple conditions, you can place everything on one line.

---

### **Common Conditions Used in Bash**

### **Comparing Numbers**

| Condition | Meaning |
| --- | --- |
| `-eq` | Equal to |
| `-ne` | Not equal to |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal to |
| `-le` | Less than or equal to |

Example:

```bash
if [ "$num" -gt 10 ]; then
    echo "Number is greater than 10"
fi
```

---

### **Comparing Strings**

| Condition | Meaning |
| --- | --- |
| `=` | Equal to |
| `!=` | Not equal to |
| `-z` | String is empty |
| `-n` | String is not empty |

Example:

```bash
if [ "$name" = "Alice" ]; then
    echo "Hello, Alice!"
fi
```

---

### **File Checks**

| Condition | Meaning |
| --- | --- |
| `-f` | File exists |
| `-d` | Directory exists |
| `-e` | File or directory exists |
| `-s` | File is not empty |
| `-r` | File is readable |
| `-w` | File is writable |
| `-x` | File is executable |

Example:

```bash
if [ -f "file.txt" ]; then
    echo "File exists"
fi
```

---

### **Logical Operators in Conditions**

| Operator | Meaning |
| --- | --- |
| `&&` | Logical AND (both conditions must be true) |
| ` |  |
| `!` | Logical NOT (negates a condition) |

Example:

```bash
if [[ $age -ge 18 && $citizen = "yes" ]]; then
    echo "You are eligible to vote"
fi
```

### **Differences Between `[ ]` and `( )` in `if` Statements and the Use of Quotes in Bash**

---

### **Square Brackets `[ ]`**

- **Test Expressions:** Used to enclose test expressions in `if` statements and other conditional constructs.
- **Comparison Operators:** Supports operators like `=`, `!=`, `lt`, `gt`, `le`, `ge`, `eq`, and `ne` for value comparison.
- **File Tests:** Allows checking file properties, such as existence, directory type, or readability.

### **Example:**

```bash
if [ "$x" -eq 5 ]; then
    echo "x is equal to 5"
fi
```

---

### **Parentheses `( )`**

- **Command Grouping:** Groups multiple commands into a single execution unit.
- **Subshells:** Creates a separate execution environment where commands run independently from the main shell.
- **Pipelines:** Useful for executing commands in sequence and passing output as input to the next command.

### **Example:**

```bash
if ( ls -la | grep "myfile.txt" ); then
    echo "myfile.txt exists"
fi
```

---

### **Quotes in Bash**

### **Single Quotes `' '`**

- Treats everything inside as a **literal string**, including special characters.
- Useful for preserving the exact contents of a string.

### **Example:**

```bash
e" = 'hello' ]; then
    echo "Variable contains 'hello'"
fi
```

### **Double Quotes `"`**

- Allows **variable expansion** and **command substitution** within the string.
- Ensures variables and commands are evaluated before being used.

### **Example:**

```bash
filename="myfile.txt"
if [ -f "$filename" ]; then
    echo "$filename exists"
fi
```

---

### **Key Differences**

| Feature | `[ ]` (Square Brackets) | `( )` (Parentheses) |
| --- | --- | --- |
| **Usage** | Conditional expressions & file tests | Grouping commands, subshells, and pipelines |
| **Effect** | Evaluates conditions directly | Runs commands in a subshell |
| **Example** | `[ "$x" -eq 5 ]` | `( ls -la |

| Feature | `' '` (Single Quotes) | `"` (Double Quotes) |
| --- | --- | --- |
| **Behavior** | Preserves literal text | Allows variable expansion & command substitution |
| **Example** | `'Hello $name'` (remains `$name`) | `"Hello $name"` (expands `$name`) |

### **Additional Notes regarding conditional statments**

- **Quoting:** Always enclose variables in double quotes (`"$variable"`) to avoid unexpected behavior.
- **Logical Operators:** Use `&&` for AND and `||` for OR to combine multiple conditions.
- **Nested Conditionals:** You can nest conditional statements within each other for more complex logic.
- **Case Statements:** For multiple comparisons against a single value, consider using a `case` statement.
    
    **`[[ ]]` vs. `[ ]`:**
    
    Both `[ ]` and `[[ ]]` can be used for conditional statements in Bash, but there are some key differences:
    
- **Quoting:** `[[ ]]` is more flexible when it comes to quoting. You can often omit quotes for variables and strings, making the syntax cleaner.
- **Regular Expressions:** `[[ ]]` supports direct use of regular expressions for pattern matching.
- **Pattern Matching Operators:** `[[ ]]` offers additional pattern matching operators like `=~` (matches a regular expression) and `!~` (does not match a regular expression).

### **Positional Positional Parameters in Bash**

**Positional parameters** allow scripts to handle command-line arguments dynamically. When a script is executed, Bash assigns each argument a special variable:

- `$1` represents the first argument, `$2` the second, `$3` the third, and so on.
- There are **nine** primary positional parameters: `$1` to `$9`.
- The script itself is assigned to `$0`, which stores its **name or path**.
- These parameters allow scripts to process user inputs dynamically.

### **Example Usage:**

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "Total number of arguments: $#"
```

If the script is executed as:

```bash
./script.sh apple banana
```

The output will be:

```
Script name: ./script.sh
First argument: apple
Second argument: banana
Total number of arguments: 2
```

---

### **Common Positional Parameters**

| Parameter | Description |
| --- | --- |
| `$0` | The **name** of the script being executed |
| `$1` - `$9` | Arguments **passed from the command line** |
| `$#` | **Total number of arguments** passed |
| `$*` | Displays all arguments as a **single string**, separated by the first character of `IFS` |
| `$@` | Displays all arguments as **separate quoted strings**, useful when passing arguments to another command |
| `$$` | **Process ID (PID)** of the current shell instance |
| `$?` | **Exit status** of the last executed command |

---

### **Difference Between `$*` and `$@`**

| Feature | `$*` | `$@` |
| --- | --- | --- |
| **Behavior** | Expands all arguments into a **single string** | Expands each argument as a **separate string** |
| **Usage** | `"$*"` treats all arguments as one | `"$@"` preserves each argument separately |
| **IFS Handling** | Arguments are **joined** using the first character of `IFS` | Arguments are treated as **distinct entities** |

### **Example to See the Difference:**

```bash
#!/bin/bash
echo "Using \"\$*\":"
for arg in "$*"; do
    echo "$arg"
done

echo "Using \"\$@\":"
for arg in "$@"; do
    echo "$arg"
done
```

**Running the script with arguments:**

```bash
./script.sh apple banana "cherry pie"
```

**Output:**

```
Using "$*":
apple banana cherry pie

Using "$@":
apple
banana
cherry pie
```

**Key Takeaway:**

- `$*` treats everything as **one string**.
- `$@` treats each argument **separately**, preserving spacing.

---

### **Special Parameters: `$$` and `$?`**

| Parameter | Description |
| --- | --- |
| `$$` | **Process ID** of the script (useful for logging and managing background processes) |
| `$?` | **Exit status** of the last command (0 for success, non-zero for failure) |

### **Example:**

```bash
echo "Current script PID: $$"
ls /nonexistentpath
echo "Exit status of previous command: $?"
```

**Output:**

```
Current script PID: 12345
ls: cannot access '/nonexistentpath': No such file or directory
Exit status of previous command: 2

```

### **Internal Field Separator (IFS) in Bash**

The **Internal Field Separator (IFS)** is a special shell variable in Bash that defines the character(s) used to **split** a string into words or fields. It determines how Bash reads and separates input, making it useful for parsing and handling data in scripts.

- **Default Behavior:**By default, the value of IFS includes **space**, **tab**, and **newline** characters. This means it splits input on any whitespace by default.

### **Example: Using IFS for CSV Parsing**

Suppose we want to read and process data from a CSV file. The following script demonstrates how IFS can be used to split each line of the file into separate fields (columns).

```bash
#!/bin/bash
while IFS=',' read -r col1 col2 col3
do
    echo "Column 1: $col1, Column 2: $col2, Column 3: $col3"
done < file.csv
```

### **Explanation:**

1. **`IFS=','`**
    
    This command sets the Internal Field Separator to a **comma** (`,`). It tells Bash to split the line at each comma when reading the file.
    
2. **`while IFS=',' read -r col1 col2 col3`**
    
    The **`read`** command reads a line from the file, using the defined IFS to split the input into fields. The fields are assigned to variables **`col1`**, **`col2`**, and **`col3`**.
    
3. **`echo`**
    
    Inside the loop, **`echo`** is used to print out the values of the three columns for each line of the file. This gives you an easy-to-read output for processing CSV data.
    
4. **File Input**
    
    The `< file.csv` part redirects the contents of the `file.csv` file into the loop.
    

### **Sample Output:**

Assuming the `file.csv` has the following content:

```
John,Doe,30
Alice,Smith,25
Bob,Johnson,35
```

The output of the script would be:

```
Column 1: John, Column 2: Doe, Column 3: 30
Column 1: Alice, Column 2: Smith, Column 3: 25
Column 1: Bob, Column 2: Johnson, Column 3: 35
```

### **Key Notes on IFS:**

- **Custom Separators:** You can change the IFS to any character that suits your data format. For example, use `IFS=";"` for semicolon-separated values.
- **Resetting IFS:**
    
    After modifying IFS, it’s a good practice to **restore** it to its default value to avoid unintended behavior in other parts of the script:
    
    ```bash
    IFS=$' \t\n'
    ```
    

This ensures that the default IFS (whitespace) is used again.

### **Summary:**

- **IFS** is a powerful tool for splitting strings into fields based on a separator.
- It’s commonly used with the **`read`** command to process files like CSVs.
- By modifying IFS, you can control how your script splits input data.

### Shift command

- The **shift** command in Bash is used to shift the positional parameters to the left. This means that the value of each positional parameter is replaced by the value of the next positional parameter. After shifting, **$1** becomes **$2**, **$2** becomes **$3**, and so on. The last positional parameter is lost. This is particularly useful in scripts for processing command-line arguments.

### **Loops in Bash ( For Loop, While Loop, Until Loop, Select (Case) Loop )**

Loops in Bash are a fundamental control structure that allows a sequence of instructions to be repeated until a certain condition is met. There are various types of loops in Bash, each serving different purposes. The main types are:

- **For Loop**
- **While Loop**
- **Until Loop**
- **Select (Case) Loop**

---

### **1. For Loop**

The **for loop** is commonly used to iterate over a range of values, such as a list or a sequence.

### **Syntax:**

```bash
for variable in list
do
    statement
done
```

### **Explanation of Each Part:**

1. **`for var in {1..10}`**
    - **`for:`** This keyword initiates the loop.
    - **`var:`** This is the variable that holds the value during each iteration of the loop.
    - **`in:`** Separates the loop variable from the list of items to iterate over.
    - **`{1..10}`:** This is a sequence range that generates values from 1 to 10. Alternatively, you can use `seq 1 10` for the same result.
2. **`do:`**
    
    This marks the beginning of the code block that will be executed during each iteration of the loop.
    
3. **`echo hello-$var:`**
    
    **`echo:`** This command is used to print the text to the console.
    
    **`hello-$var:`** This will print the string "hello-" followed by the current value of `var` in each iteration.
    
4. **`done:`**
    
    This marks the end of the loop.
    

### **Example:**

```bash
for var in {1..10}
do
    echo hello-$var
done
```

This will print:

```
hello-1
hello-2
hello-3
...
hello-10

```

---

### **2. While Loop**

The **while loop** repeatedly executes a block of code as long as the specified condition remains true.

### **Syntax:**

```bash
while [condition]
do
    statement
done
```

### **Example:**

```bash
num=1
while [[ num -le 10 ]]
do
    echo "This is $num"
    ((num++))  # Increment the number
done
```

**Explanation:**

- The loop continues as long as **`num`** is less than or equal to 10.
- The `((num++))` increments the variable `num` during each iteration.
- The loop terminates when the condition is no longer true.

### **Using `read` inside a While Loop:**

You can also use the **`while`** loop in combination with the **`read`** command to read input line by line.

```bash
while read -r line
do
    echo "$line"
done < input.txt
```

**Explanation:**

- The **`read`** command reads one line from the input (or a file) and assigns it to the variable `line`.
- The **`r`** option prevents backslashes from being treated as escape characters.
- The loop continues until the end of the file (`EOF`) is reached.

---

### **3. Until Loop**

The **until loop** is the opposite of the **while loop**. It runs until the specified condition becomes true.

### **Syntax:**

```bash
until [condition]
do
    statement
done
```

**Example:**

```bash
num=1
until [[ num -gt 10 ]]
do
    echo "This is $num"
    ((num++))
done
```

In this example, the loop will run **until** `num` exceeds 10. Similar to the **while loop**, the condition is checked at the start of each iteration, and the loop executes until the condition becomes true.

---

### **4. Select (Switch/Case) Loop**

The **select** loop, often used as a menu-driven program, allows users to select options from a list. It's typically used for simple user interactions.

### **Syntax:**

```bash
select var in option1 option2 option3
do
    statement
done
```

**Example:**

```bash
#!/bin/bash

echo "Please enter a number between 1 to 3"
read num

case $num in
    1)
        echo "You entered the number one";;
    2)
        echo "You entered the number two";;
    3)
        echo "You entered the number three";;
    *)
        echo "Sorry, you entered the wrong number";;
esac
```

**Explanation:**

- **`select`**: The **select** loop presents a list of options and prompts the user to select one.
- **`case $num`**: Based on the number entered by the user, different blocks of code are executed.

**Sample Output:**

```
Please enter a number between 1 to 3
2
You entered the number two
```

---

### **Summary of Loop Types**

- **For Loop:** Used to iterate over a fixed range or list.
- **While Loop:** Repeats as long as the condition remains true.
- **Until Loop:** Repeats until the condition becomes true.
- **Select (Case) Loop:** Used for creating interactive menus, commonly used in user-driven programs.

### Array

- Array is a collection of elements 
Syntax:
nums=(2 4 6 7 8 9 0)
`echo "${nums[*]}"` # this will list all the values of nums if you want specific values use the index instead of *

### **Functions in Bash**

- A **function** in Bash is a reusable block of code that you can define once and call multiple times within your script. Functions help in organizing and modularizing your code, making it more readable and maintainable.

### **Syntax:**

```bash
function_name() {
  # code to be executed
}

# Calling the function
function_name
```

- **`function_name`** is the identifier that represents the function. You can choose any valid name for your function.
- Inside the curly braces `{ }`, you define the set of instructions or commands that will be executed when the function is called.
- You can then call the function simply by writing its name followed by `()` (no need to use `function` keyword again).

---

### **Function with Arguments**

- Functions can also accept parameters (arguments), making them more dynamic.

### **Syntax:**

```bash
function_name() {
  # Access arguments with $1, $2, ..., $n
  echo "First argument: $1"
  echo "Second argument: $2"
}

# Calling the function with arguments
function_name "Hello" "World"
```

- **$1, $2, ..., $n**: These special variables represent the arguments passed to the function. `$1` is the first argument, `$2` is the second, and so on.

---

### **Return Values from Functions**

- By default, Bash functions return an exit status code (an integer from 0 to 255), which you can access using the special variable `$?`. However, if you want to return more complex data like strings or numbers, you need to use a workaround, such as **echo** or **output redirection**.

### **Example of Return Code:**

```bash
my_function() {
  echo "This function returns an exit status"
}

my_function
echo "Exit status: $?"
```

### **Example of Return with Data:**

```bash
my_function() {
  result="Hello from function"
  echo "$result"
}

output=$(my_function)
echo "Function output: $output"
```

- In this example, the function **`my_function`** returns a string, and we capture the output using command substitution (`$(...)`).

---

### **Function with Default Values**

- You can also set default values for function parameters, ensuring that the function works even if no arguments are provided.

### **Example with Default Values:**

```bash
greet_user() {
  local name="${1:-Guest}"  # If no argument is passed, default to "Guest"
  echo "Hello, $name!"
}

greet_user "John"    # Output: Hello, John!
greet_user           # Output: Hello, Guest!
```

- In this example, the **`${1:-Guest}`** syntax ensures that if no argument is provided, the function uses "Guest" as the default value for the name.

---

### **Function with Local Variables**

- You can use the **`local`** keyword to declare variables within a function that are only accessible inside that function.

### **Example with Local Variables:**

```bash
increment() {
  local num=$1
  num=$((num + 1))
  echo $num
}

result=$(increment 5)
echo "Incremented value: $result"
```

- The **`local`** keyword ensures that the **`num`** variable is scoped only to the **`increment`** function, so it doesn't affect other parts of the script.

### Grep

- `grep` is a powerful command-line utility in Unix and Linux used for searching text using patterns. The name stands for "Global Regular Expression Print." It searches through files or input provided to it, looking for lines that match the specified pattern and outputs those lines
    
    
    Some Flags used in Grep:
    
    **`-i`**: Perform a case-insensitive search.
    `-**v**`: Invert the match, showing lines that do not match the pattern.
    
    **`-r` or `-R`** : Recursively search directories.
    
    **`-l`**: List only the names of files with matching lines.
    
    **`-L`**: List only the names of files without matching lines.
    
    **`-n`**: Prefix each line of output with the line number within its input file.
    
    **`-c`**: Print only a count of matching lines per file.
    
    **`-w`**: Match only whole words.
    
    **`-o`**: Show only the part of a matching line that matches the pattern.
    
    **`-A`**: Print N lines of trailing context after matching lines.
    
    **`-B`**: Print N lines of leading context before matching lines.
    
    **`-C`**: Print N lines of output context.
    
    **`-E`**: Use extended regular expressions.
    
    **`-f`**: Obtain patterns from the specified file.
    
    **`-h`**: Suppress the prefixing of file names on output.
    `history | grep 'touch\|nano\|vim\|mkdir’` # this is used to select multiple words 
    

### Awk

- `awk` is a powerful text-processing tool in Linux and Unix that is used for pattern scanning and processing. It allows users to extract and manipulate text from files or command outputs. `awk` works on a line-by-line basis and can process text using fields, conditions, and actions.
    
    ### **Key Concepts**:
    
    - **Fields**: `awk` divides each line of text into fields, where `$1`, `$2`, etc., represent the first, second, and subsequent fields.
    - **Records**: Each line in the input is considered a record.
    - **Patterns**: Patterns are used to specify which lines or records to process.
    - **Actions**: Actions define what to do with matching records, such as printing or modifying them.
    
    Syntax: 
    `cat file.txt | awk options ‘pattern {action}’` OR `awk 'pattern {action}' filename.txt`
    
    **Pattern**: Specifies a condition for selecting lines or records. < e.g., `/pattern/` >
    
    **Action**: Specifies what to do with matching lines or records. < e.g., `{print $1}` >
    
    awk options :- 
    `-F` : Field saperator # Delimeter
    `-f` : filename you need to specify
    `NR` —> Number of reccords # lines 
    `NF` —> number of Fields  
    
    awk variables:
    $0, $1, $2, $3, $4, so on
    
    **AWK Patterns and Actions**
    
    - **Pattern**: Specifies a condition for selecting lines or records.
        - `awk '/pattern/' file`This command selects lines in `file` that match `pattern`. For example, `awk '/error/' log.txt` will print lines in `log.txt` containing the word "error".
    - **Action**: Specifies what to do with matching lines or records.
        - `awk '/pattern/ {print $1}' file`This command prints the first field (`$1`) of lines that match `pattern`. For example, `awk '/error/ {print $1}' log.txt` will print the first word from lines containing "error".
    - **$n**: Represents the nth field of a record.
        - `awk '{print $1}' file`This command prints the first field of each line in `file`. For example, `awk '{print $1}' data.txt` will print the first word of each line in `data.txt`.
    - **$0**: Represents the entire line or record.
        - `awk '{print $0}' file`This command prints the entire line for each line in `file`. For example, `awk '{print $0}' data.txt` will print every line exactly as it is in `data.txt`.
    - **BEGIN**: Specifies an action to be executed before any input lines are processed.
        - `awk 'BEGIN {print "Start processing"} {print $0}' file`This command prints "Start processing" before processing any lines in `file` and then prints each line.
    - **END**: Specifies an action to be executed after all input lines have been processed.
        - `awk 'END {print "Done processing"}' file`This command prints "Done processing" after all lines in `file` have been processed.
    - **NR**: Number of Records. Represents the current record number.
        - `awk '{print NR, $0}' file`This command prints the record number followed by the line for each line in `file`. For example, `awk '{print NR, $0}' data.txt` will prepend line numbers to each line in `data.txt`.
        # This will print the number of that reccords before printing the reccord
    - **NF**: Number of Fields. Represents the number of fields in the current record.
        - `awk '{print NF}' file`This command prints the number of fields for each line in `file`. For example, `awk '{print NF}' data.txt` will print the number of fields (columns) in each line of `data.txt`.
    - **FS `-F`**: Field Separator. Sets the character that separates fields.
        - `awk -F "," '{print $1}' file`This command sets the field separator to a comma and prints the first field. For example, `awk -F "," '{print $1}' data.csv` will print the first column from a comma-separated file.
    - **RS**: Record Separator. Sets the character that separates records (lines by default).
        - `awk 'BEGIN {RS=","} {print $0}' file.csv` This command sets the record separator to a comma and prints each record. For example, if `file.csv` has comma-separated values like `1,John,85`, it will treat each value (e.g., `1`, `John`, `85`) as a separate record and print each one on a new line.
        
        This usage illustrates how changing the `RS` can break up records based on a different delimiter (in this case, a comma) rather than the default newline, resulting in individual fields being treated as separate records.
        
    - **OFS**: Output Field Separator. Sets the character to separate fields in the output.
    `OFS` sets the **output** field separator, which controls how fields are separated when `awk` prints them.
        
        **`OFS` Example** (Output Field Separator):
        
        - Command: `awk 'BEGIN {OFS=";"} {print $1, $2}' data.csv`
        - What it does: Joins the first and second fields in the output with a semicolon instead of the default space.
        - `awk 'BEGIN {OFS="\t"} {print $1, $2}' file`This command sets the output field separator to a tab and prints the first and second fields. For example, `awk 'BEGIN {OFS="\t"} {print $1, $2}' data.txt` will separate fields in the output with tabs.
    - **ORS**: Output Record Separator. Sets the character to separate records in the output.
    # Same as OFS but it was for Fields and this is for reccords
        - `awk 'BEGIN {ORS="\n\n"} {print $0}' file`This command sets the output record separator to two newlines and prints each record. For example, `awk 'BEGIN {ORS="\n\n"} {print $0}' data.txt` will separate records in the output with a blank line.
    
    - **gsub(pattern, replacement)**: Global substitution in the current record.
        - `awk '{gsub(/old/, "new"); print}' file`This command replaces all occurrences of `old` with `new` in each line and prints the modified line. 
        For example, `awk '{gsub(/error/, "warning"); print}' log.txt` will replace "error" with "warning" in each line of `log.txt`.
    - **sub(pattern, replacement)**: Substitution for the first match in the current record.
        - `awk '{sub(/old/, "new"); print}' file`This command replaces the first occurrence of `old` with `new` in each line and prints the modified line. For example, `awk '{sub(/error/, "warning"); print}' log.txt` will replace only the first "error" with "warning" in each line of `log.txt`.
    - **match(string, pattern)**: Matches the string against the pattern and sets `RSTART` and `RLENGTH` variables.
        - `awk '{match($0, /pattern/); print RSTART, RLENGTH}' file`This command matches `pattern` in each line and prints the starting position (`RSTART`) and length (`RLENGTH`) of the match. For example, `awk '{match($0, /error/); print RSTART, RLENGTH}' log.txt` will print the position and length of "error" in each line of `log.txt`.
        **# This will match the word then tell in which line and from which index the word starts and how long it it**
    - **split(string, array, delimiter)**: Splits a string into an array based on the delimiter.
        - `awk '{split($0, arr, ","); print arr[1]}' file`This command splits each line into an array `arr` using a comma as the delimiter and prints the first element of the array. For example, `awk '{split($0, arr, ","); print arr[1]}' data.csv` will print the first column value of each line.
        #This command takes the entire line (`$0`), splits it into an array `arr` using a comma as the delimiter, and prints the first element of the array (i.e., the value in the first column)
        
        **`split($0, arr, ",")`**:
        
        - **`$0`**: Refers to the entire line of input.
        - **`arr`**: The name of the array that will store the split values.
        - **`,`**: The delimiter used to split the string. In this case, it's a comma.
        - `split` function divides the line into parts wherever the delimiter is found, storing those parts in the array `arr`. The array indexes start from `1`, so `arr[1]` represents the first part.
    - **print**: Prints the specified fields or entire record.
        - `awk '{print $1, $2}' file`This command prints the first and second fields of each line in `file`. For example, `awk '{print $1, $2}' data.txt` will print the first and second columns from `data.txt`.
    - **printf(format, ...)**: Formats and prints the output.
        - `awk '{printf("%s\t%d\n", $1, $2)}' file`This command formats the output with a string followed by a tab and a number. For example, `awk '{printf("%s\t%d\n", $1, $2)}' data.txt` will print the first field as a string and the second field as an integer, separated by a tab.
        **Example:
        INPUT:**
        Alice 30
        Bob 25
        Charlie 35
        **Command**: `awk '{printf("%s\t%d\n", $1, $2)}' data.txt`
        **OUTPUT**:
        Alice   30
        Bob     25
        Charlie 35
        **Explanation**:
            
            **`%s`**: Formats the first field (`$1`), which is the name, as a string.
            
            **`\t`**: Inserts a tab between the name and age.
            
            **`%d`**: Formats the second field (`$2`), which is the age, as an integer.
            
            **`\n`**: Ensures that each record is printed on a new line.
            
    
    `cat ips.txt | awk '{print $1}'` # This prints the first field Default delimeter is space that’s why its showing full data
    apache,192.168.1.2
    sftp,192.168.1.3
    nginix,192.168.1.4  # to change the delimeter use <`cat ips.txt | awk -F ',' '{print $1}'`>
    
    `cat ips.txt | awk 'NR==1{print}'` # This will print the first line from the file
    
    **OFS: Output Field Separators**
    `date | awk '{print $2,$3,$4}'`
    16 July 2022
    # `date | awk 'OFS="-" {print $2,$3,$4}'`
    16-July-2022
    # `date | awk 'OFS="/" {print $2,$3,$4}'`
    16/July/2022
    
    `cat /etc/shadow/ | awk -F “:” ‘$3 >= 1000 {print $1,$3,$6}’`  # this will only show users who have a uid of more then 1000 which are created users 
    
    `cat users.txt | awk -F ":" 'NR == 20 || NR == 19 {print$1}'` # This prints 1st column of line number 20 and 19 
    
    `cat -n users.txt | awk ' NR >=3 && NR <=15  {print $0}'`  # This will print lines from 3 to 15  
    
- awk command in scripting 
AWK script syntax:-
 filname | awk 'BEGIN {start_action} condition {action} END {stop_Action}' filename | awk -f <filename.awk>

OFS: Output Field Separators
date | awk '{print $2,$3,$4}'
16 July 2022
# date | awk 'OFS="-" {print $2,$3,$4}'
16-July-2022
# date | awk 'OFS="/" {print $2,$3,$4}'
16/July/2022

### sed

- **`sed` Overview**
`sed` (Stream Editor) is a powerful command-line tool used for text manipulation and transformation. It processes text line by line, allowing you to perform operations like **substitution, deletion, insertion, and search on text files or streams.**
    
    ### **Key Concepts**
    
    - **Pattern Space**: This is the internal buffer where `sed` reads each line of input for processing.
    - **Hold Space**: A secondary buffer that you can use to temporarily store data.
    
    ### **Syntax**
    
    `sed [options] 'script' file`
    
    - **Options**: Command-line options that control `sed` behavior (e.g., `n`, `i`, etc.).
    - **Script**: The `sed` command or set of commands (enclosed in single quotes) to be applied to the input text.
    - **File**: The input file to be processed by `sed`.
    
    ### **Common Options**
    
    - `n`: Suppresses automatic printing of lines. Use with `p` (print) to print only the modified lines.
    - `i`: Edits the file in place (modifies the original file).
    - `e`: Allows multiple `sed` scripts to be executed in the same command.
    - `f`: Reads `sed` commands from a file instead of from the command line.
    
    ### **Common Commands and Examples**
    
    ### 1. **Substitution (`s`)**
    
    - **Description**: Replaces occurrences of a pattern with a replacement string.
    - **Syntax**: `sed 's/pattern/replacement/flags' file`
    - **Example**: `sed 's/old/new/' file`
        - Replaces the first occurrence of "old" with "new" in each line of `file`.
    
    **Flags**:
    
    - `g`: Global replacement (replaces all occurrences in a line).
    - `p`: Prints the line if a substitution is made.
    - `i`: Case-insensitive replacement.
    
    **Example**:
    
    - `sed 's/old/new/g' file` replaces all occurrences of "old" with "new" in each line of `file`.
    
    ### 2. **Deletion (`d`)**
    
    - **Description**: Deletes lines that match a pattern.
    - **Syntax**: `sed '/pattern/d' file`
    - **Example**: `sed '/error/d' file`
        - Deletes all lines containing the word "error" in `file`.
    
    ### 3. **Printing (`p`)**
    
    - **Description**: Prints lines that match a pattern.
    - **Syntax**: `sed -n '/pattern/p' file`
    - **Example**: `sed -n '/error/p' file`
        - Prints only the lines that contain "error".
    
    ### 4. **Inserting Lines (`i`)**
    
    - **Description**: Inserts a line before the matching pattern.
    - **Syntax**: `sed '/pattern/i\New line text' file`
    - **Example**: `sed '/error/i\Log start' file`
        - Inserts the text "Log start" before each line containing "error".
    
    ### 5. **Appending Lines (`a`)**
    
    - **Description**: Appends a line after the matching pattern.
    - **Syntax**: `sed '/pattern/a\New line text' file`
    - **Example**: `sed '/error/a\Log end' file`
        - Appends the text "Log end" after each line containing "error".
    
    ### 6. **Changing Lines (`c`)**
    
    - **Description**: Replaces an entire line matching a pattern with new text.
    - **Syntax**: `sed '/pattern/c\New line text' file`
    - **Example**: `sed '/error/c\Error found' file`
        - Replaces lines containing "error" with the text "Error found".
    
    ### 7. **Range of Lines**
    
    - **Description**: Processes a range of lines based on line numbers or patterns.
    - **Syntax**: `sed 'start,end command' file`
    - **Example**: `sed '1,5d' file`
        - Deletes lines 1 through 5 in `file`.
    - **Example**: `sed '/start/,/end/d' file`
        - Deletes all lines between the first occurrence of "start" and "end".
    
    ### 8. **In-place Editing (`i`)**
    
    - **Description**: Edits the file directly without creating a new file.
    - **Syntax**: `sed -i 's/pattern/replacement/' file`
    - **Example**: `sed -i 's/old/new/g' file`
        - Replaces all occurrences of "old" with "new" directly in `file`.
    
    ### 9. **Multiple Commands (`e`)**
    
    - **Description**: Allows executing multiple commands in one `sed` invocation.
    - **Syntax**: `sed -e 'command1' -e 'command2' file`
    - **Example**: `sed -e 's/old/new/' -e '/pattern/d' file`
        - Replaces "old" with "new" and deletes lines containing "pattern" in `file`.
    
    ### 10. **Transform (`y`)**
    
    - **Description**: Transforms characters by replacing them with other characters (works like `tr`).
    - **Syntax**: `sed 'y/abc/ABC/' file`
    - **Example**: `sed 'y/aeiou/AEIOU/' file`
        - Transforms lowercase vowels to uppercase vowels in `file`.
    
    ### **Advanced Usage**
    
    ### 1. **Hold and Pattern Space**
    
    - **Description**: `sed` allows storing data temporarily using the hold space (`h`) and later retrieving it using the get command (`g`).
    - **Example**: Swap two lines in a file:
        - `sed -e 'N; s/\(.*\)\n\(.*\)/\2\n\1/' file`
        - This command reads two lines at a time, then swaps their positions.
    
    ### **Examples Recap**
    
    - **Substitution**: `sed 's/apple/orange/g' fruits.txt` replaces all occurrences of "apple" with "orange".
    - **Deletion**: `sed '/error/d' log.txt` deletes all lines containing "error".
    - **Inserting**: `sed '/header/i\This is a new line' file.txt` inserts a new line before the lines matching "header".
    - **Appending**: `sed '/header/a\This is an appended line' file.txt` appends a new line after lines matching "header".
    - **In-place Editing**: `sed -i 's/foo/bar/' file.txt` replaces "foo" with "bar" directly in the file.
    
    **Display Data OR Find Data:**
    `sed ' ' filename.txt`  # This will print every line in the data # To print only lines containing the word "pattern": < `sed -n '/pattern/p' filename.txt` >This will search for pattern in file.txt
    
    **Replace data:**
    use the s (substitute) command. The basic syntax for replacing text is `s/pattern/replacement/global`.
    `sed 's/old/new/g' filename.txt` # This will replace the word old with new , the g is for global so all ocurrance not just the first one 
    `sed '3d' inputfile.txt` # This is used to remove a specific line from data in this case its 3 
    
    **Modify Data**: 
    Use commands like i (insert), a (append), d (delete), and c (change) with patterns to modify data.
    
    `cat users.txt | sed -n '3,7p’` # this will print the lines from 3 to 7   line only in users.txt
    
    `sed -i ‘/^#/d’ file.txt` # This will remove all the # from the file .txt , < -i > is used to insert into file so it will change the file.txt < ‘/^#/d’ > in this /^#  will select the # and /d will delete , you can change these option for example you can use p instead of d to print etc 
    
    `sed -n ‘5,$p’ file1`
    n: Suppresses automatic printing of pattern space. Normally, sed prints each line of input by default. With n, sed only prints what is explicitly specified.
    '5,$p': Specifies the range and action.
    5,: Indicates starting from the 5th line.
    $: Indicates up to the last line of the file.
    p: Prints the lines in the specified range (from the 5th line to the last line).
    

### xargs

- **`xargs**` is like a **helpful assistant** who takes a bunch of stuff (data) from one place (command output) and hands it out (as arguments) to another program (another command), one by one (or in small groups).  Both `|` (pipe) and `xargs` are used to send the output of one command to another command, but they work in slightly different ways and have different purposes
Example: `ls *.txt | xargs gzip`  # Compress all .txt files with gzip, `ls *.sh | xargs chmod +x`  # Make all .sh files executable
- **xargs Command**
    - **`xargs`** is like a **helpful assistant** that takes a bunch of items (data) from one command’s output and passes them as arguments to another command. It helps in handling large amounts of data efficiently, especially when the output of one command needs to be processed in batches by another command.
    - **Why Use `xargs`?**
        - Some commands do not accept input via **pipes (`|`)**, so `xargs` is used to pass the output as arguments.
        - It helps in processing a large number of arguments that exceed the shell’s limit.
        - It enables batch processing (e.g., deleting, compressing, or modifying files in chunks).
    
    ---
    
    ## **Basic Syntax**
    
    ```bash
    command1 | xargs command2
    ```
    
    - `command1` generates a list of arguments.
    - `xargs` takes those arguments and passes them to `command2` for processing.
    
    ---
    
    ## **Examples of `xargs` in Action**
    
    ### **1. Compress All `.txt` Files Using `gzip`**
    
    ```bash
    ls *.txt | xargs gzip
    ```
    
    📌 **Explanation:**
    
    - `ls *.txt` lists all `.txt` files.
    - `xargs gzip` passes them as arguments to `gzip`, compressing all `.txt` files.
    - Equivalent to: `gzip file1.txt file2.txt file3.txt`
    
    ---
    
    ### **2. Make All `.sh` Files Executable**
    
    ```bash
    s chmod +x
    ```
    
    📌 **Explanation:**
    
    - `ls *.sh` lists all shell scripts.
    - `xargs chmod +x` applies `chmod +x` to each file, making them executable.
    - Equivalent to: `chmod +x file1.sh file2.sh file3.sh`
    
    ---
    
    ### **3. Remove All `.log` Files in a Directory**
    
    ```bash
    -name "*.log" | xargs rm
    ```
    
    📌 **Explanation:**
    
    - `find /var/log -name "*.log"` finds all `.log` files in `/var/log`.
    - `xargs rm` removes them efficiently.
    
    🔴 **⚠️ Caution:** If filenames contain spaces, use `-print0` with `find` and `-0` with `xargs`:
    
    ```bash
    -name "*.log" -print0 | xargs -0 rm
    ```
    
    This prevents issues with spaces in filenames.
    
    ---
    
    ### **4. Count Lines in Multiple Files**
    
    ```bash
    ls *.txt | xargs wc -l
    ```
    
    📌 **Explanation:**
    
    - Lists all `.txt` files and counts the number of lines in each file.
    - Equivalent to: `wc -l file1.txt file2.txt file3.txt`
    
    ---
    
    ### **5. Copy Multiple Files to Another Directory**
    
    ```bash
    gs -I {} cp {} /backup/images/
    ```
    
    📌 **Explanation:**
    
    - `I {}` tells `xargs` to replace `{}` with each filename.
    - Copies all `.png` files to `/backup/images/`.
    - Equivalent to: `cp file1.png /backup/images/`, `cp file2.png /backup/images/` …
    
    ---
    
    ### **6. Using `xargs` with `echo` to Format Output**
    
    ```bash
    echo "apple banana cherry" | xargs -n 1
    ```
    
    📌 **Explanation:**
    
    - `n 1` ensures each word is printed on a new line.
    
    🔹 **Output:**
    
    ```
    apple
    banana
    cherry
    ```
    
    ---
    
    ## **Common `xargs` Options**
    
    | Option | Description | Example |
    | --- | --- | --- |
    | `-n N` | Pass `N` arguments at a time | `ls |
    | `-I {}` | Replace `{}` with argument in command | `echo "file1 file2" |
    | `-0` | Handle filenames with spaces (used with `find -print0`) | `find . -name "*.log" -print0 |
    | `--max-args=N` | Limit the number of arguments per execution | `ls |
    
    ---
    
    ## **When Not to Use `xargs`**
    
    - If a command **already supports multiple arguments** via standard input, `xargs` is unnecessary.
    - Example: Instead of `ls *.txt | xargs cat`, use `cat *.txt`.
    
    ---
    
    ## **Conclusion**
    
    - `xargs` is a powerful tool for efficiently processing command output as arguments.
    - It handles large datasets, batch operations, and commands that do not accept input via pipes.
    - Best used with **find**, **ls**, **echo**, and **grep** to manipulate files and text data efficiently.