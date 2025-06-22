# Linux-concepts-commands

This is not all the commands and are not in detail and explained enough , so it’s best to do your own research and dive deep into each of the commands using Google, Youtube and AI . And not limit yourself to these 

> Created by Salman Al Qureshi
Linkedin: Salman Qureshi
> 
> 
> http://www.linkedin.com/in/salman-qureshi-4aa41a247
> 

# Linux Deep Dive

## Concepts:

- linux is made by linus benedict tornvalds, first version was released in 1991 on the internet
- **Shell** in linux means a program that serves as a interface between the user and the computer OS . there are many linux shell types like bash, zsh, cshell, sh shell etc .
- linux file system is how linux stores files and folders and how it manages them

![Untitled](../Concepts%202193e043159d819a8333d6485cba16d5/Untitled.png)

- **Interpreted languages** takes the code and then an interpreter program reads the source code line by line, translates it to a format the computer understands, and executes it immediately., This process happens each time the code is executed that’s why these code needs an interpreter to be executed . Because of the on-the-fly translation, interpreted code can be slower than compiled code.
- **Compiled languages**  in these languages the program is converted into machine code and then saved in a file as an executable, This conversion happens once and this process is called compiling, once this process is done, the code can be sent to others without any need for compiler
- **Scripting** involves writing scripts or small programs to automate tasks or manipulate existing systems. It is characterized by its focus on rapid development and ease of use. Scripting languages such as Python, Perl, and JavaScript are commonly used for tasks like system administration, web development, and automation. Scripts are typically executed line by line by an interpreter without the need for compilation, allowing for quick testing and modification. The scripting development process often emphasizes rapid prototyping and iterative development, enabling developers to solve specific problems efficiently. Overall, scripting provides a flexible and efficient approach to automating tasks and simplifying complex operations.
- **Programming** encompasses a broader range of activities, including designing, implementing, and maintaining software systems. Unlike scripting, programming involves a more structured approach to software development. Programming languages such as C, C++, Java, and C# offer extensive control over system resources and performance optimization. Programs are typically compiled into machine code or bytecode before execution, which can provide better performance but may require additional steps in the development process. The programming development process involves various stages, including requirements analysis, design, testing, debugging, and maintenance. While scripting focuses on smaller, specialized tasks, programming addresses a wider range of software development needs, from applications and games to operating systems and databases.

## Syntax:

### ls

- **`ls -lh`** # will list the directories but the storage will be shown in formatted so in kb or mb rather then bytes

### cd

- `cd` # this is used to change directoy, 
cd ~ # this will move to the home directory of the current user 
cd .. # this will go back to the directory before this current directory 
cd - # this will go to the previous directoy 
Example: 
~/Documents/bash$ cd /var/
/var$ cd -
/home/ubuntu/Documents/bash
~/Documents/bash$

### pwd/realpath

- pwd OR realpath
# `pwd` will show the current directory while `realpath <file-name>` will show the full path ti the file specified

### tar

- **`tar -czvf filename.tar.gz ~/Documents`** # command will create a compressed archive (filename.tar.gz) of the ~/Documents directory
- **`tar -xzvf filename.tar.gz -C /path/to/target/directory`** # This command will extract the contents of **filename.tar.gz** into the specific directory

### zip/unzip

- **`zip filename.zip ~/Documents` #** this will make a .zip file named filename fro the documents folder

- **unzip** is a command-line utility in Linux used to extract files from a ZIP archive. ZIP is a common archive format that compresses files to save space.
    
    
    **`unzip archive.zip`**: Extract all the contents of `archive.zip` into the current directory.
    
    **`l`**: List the contents of a ZIP archive without extracting them.
    
    **`d`**: Specify a directory to extract files into.
    
    - *Example*: `unzip archive.zip -d /path/to/directory` extracts the contents of `archive.zip` into `/path/to/directory`.
    
    **`j`**: Junk paths. This option extracts all files to the current directory without creating subdirectories.
    
    **`o`**: Overwrite existing files without prompting.
    
    **`n`**: Never overwrite existing files. This is the opposite of `o`.
    
    **`q`**: Perform the extraction quietly, suppressing the output.
    
    **`v`**: Display detailed information during the extraction process (verbose).
    
    **`t`**: Test the integrity of a ZIP archive without extracting its contents.
    

### Output & input redirections

- **Output > and Input < redirection in linux**
    
    ### **`>` (Output Redirection)**
    
    - **Purpose**: Redirects the output of a command to a file, rather than displaying it on the terminal.
    - **Usage**: When you want to save the output of a command to a file.
    - **Syntax**: `command > file`
        - Example: `ls > filelist.txt` saves the list of files in the current directory to `filelist.txt`.
    - **Overwrites Existing Files**: If the specified file already exists, the `>` operator will overwrite its contents.
    - **Append**: Use `>>` to append the output to an existing file instead of overwriting.
        - Example: `echo "New line" >> filelist.txt` appends "New line" to `filelist.txt`.
    
    ### **`<` (Input Redirection)**
    
    - **Purpose**: Redirects the input of a command from a file, rather than taking input from the keyboard.
    - **Usage**: When you want to provide input to a command from a file.
    - **Syntax**: `command < file`
        - Example: `mail -s "Subject" user@example.com < message.txt` sends the content of `message.txt` as the body of an email.
    
    ### **Examples of Usage**:
    
    1. **Save the output of `ls` to a file**:
        - `ls > filelist.txt`
    2. **Append the output of `date` to an existing file**:
        - `date >> log.txt`
    3. **Use a file as input for a command**:
        - `sort < unsorted_list.txt`
    4. **Combine redirections**:
        - `command < input.txt > output.txt`
        - This command reads input from `input.txt` and writes the output to `output.txt`.

### cat

- **`cat file.txt | more`** # this will cat the file contants with pause future 
**`cat -b OR cat -n`** # this will cat the file with numbered list 
`cat file.txt` # this will display the contant of the file, it can also be used to write to a file OR create a file and write to it e.g —> <`cat >> file.txt`> to append to a file and <`cat > file.txt`> to overwrite a file , it will take your input  and then to finish press ctrl + d

### wc

- **`wc file.txt`  #** will say the word count for the file file.txt
`wc -l File.txt` # This will show the lines in file.txt

### chsh

- **`chsh`** # this command is used to change the shell permanently for the current user. it will ask for the shell path you have to provide the absolute path for example /bin/bash

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
    

### tr

- **`tr`**  # this is used to replace or delete a word in linux for example `echo "hello world" | tr 'a-z' 'A-Z’` This command converts all lowercase letters (a-z) in "hello world" to uppercase letters (A-Z) using the pipe ( | ) to send the output of echo as input to tr. You can also use `-d` to only delete something

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

### bc

- `bc` # this command is used for calculations in linux . You can also use | bc to simplify the data before |

### seq

- `seq 10`  # This command is used to display range of number. This will print numbers from 1 to 10 (1, 2, 3, ..., 10). < `seq 50 -5 10` > # this will print numbers from 50 to 10 subtracting 5 so the table of 5  NOTE: first number should be greater then the second to work

### echo

- `echo $?` is used to **print the exit status** of the most recently executed **foreground** pipeline or command. An exit status of 0 generally indicates successful execution, while a non-zero value suggests an issue

### cut

- `cut` command in Bash is used to extract sections from each line of input—usually from files or from the output of other commands. It is a powerful tool for handling text data and is often used in data processing tasks.
`-b`: Select only certain bytes.
`-c`: Select only certain characters.
`-d`: Specify a delimiter (default is tab).
`-f`: Select only certain fields, separated by the delimiter.
for example: `cat urls.txt | cut -d ":" -f 2` # -d ":" specifies the colon as the delimiter. -f 2 selects the second field after the delimiter.

`cat urls.txt | cut -d ":" -f 2-3 | tr -d "/"` # this will remove everything from the url https://google.com and make it to google.com

### who

- `who` # This will show the active users

### awk

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
    

# RHEL - Intensive

Make centos with the following partitions ( size can be any but not less )

- make partitions and selected ext4 or xfs for all
i made 7 partitions
7 partitions scheme with 20 Gb HD

server with gui
    
    /boot: 512 MB
    
    / (root): 2048 MB
    
    swap: 1024 MB (double the RAM of 5GB)
    
    /var: 4096 MB
    
    /tmp: 1024 MB
    
    /usr: 4096 MB
    
    /home: 1024 MB
    

## Concepts:

- In linux almost all commands are developed in C language & then converted to binary. In windows we call it exe & in linux we call it binary, In windows we call it restart & in linux we call it reboot. Windows have registry & in linux no registry but FS hierarchy. Windows have defrag & in linux no defrag because of the way how files are written. So anyways commands are atlast binary file which are kept in some path[location] from where we call them & run it as a command.

### inode

- **Inode** is a special data structure in a Unix-like filesystem that stores information about a file or a directory, but not its name or its actual data. Instead, it stores:
**Metadata**: Details like file size, permissions, owner, and timestamps.
**Data Pointers**: Locations of the actual data blocks on the disk.
every file has a unique inode number you can view with ls -i

### **Hard link and Soft link**:

- **Hard link and Soft link**:
hard links and soft links provide different ways to reference and manage files within a filesystem. Soft-link can cross and navigate through partitions but if the actual file(father file) gets deleted then the link will be of no use and will turn into an orphan link ( no father/actual file) , while hard-link cannot navigate through partitions but can still contain the data if the actual file(father file) gets deleted

### **Runlevels**

- **Runlevels** are a concept used in Unix and Linux operating systems to define different states or modes of system operation. Each runlevel represents a specific system configuration and allows the system to be in different modes

In traditional System V (SysV) init systems, runlevels are represented by numbers, typically from 0 to 6. Each runlevel has a standard purpose:
**Runlevel 0**: Halt (shutdown the system)
**Runlevel 1**: Single-user mode (for administrative tasks)
**Runlevel 2**: Multi-user mode without networking
**Runlevel 3**: Multi-user mode with networking (text mode, no graphical interface)
**Runlevel 4**: Undefined (customizable for user-defined purposes)
**Runlevel 5**: Multi-user mode with networking and graphical interface (GUI)
**Runlevel 6**: Reboot (restart the system)

You can change the runlevel using the init or telinit command. For example, to switch to runlevel 3, you can use:
sudo init 3
To see the current and previous runlevels, you can use the `runlevel` command
**Note:** 
Modern Linux distributions have largely transitioned to using `systemd` instead of the traditional SysV init system. In `systemd`, runlevels are replaced by "targets," which provide a more flexible way of defining system states.
if we do cat /etc/inittab it also shows us this 
systemd uses 'targets' instead of runlevels. By default, there are two main targets:
multi-user.target: analogous to runlevel 3
graphical.target: analogous to runlevel 5
To view current default target, run:
systemctl get-default
To set a default target, run:
systemctl set-default TARGET.target

### Systemd targets

- In CentOS 7, the concept of runlevels is managed by systemd targets. You can switch between targets using the `systemctl isolate` command and set the default target with `systemctl set-default`. This system allows you to manage the state of your system efficiently, whether you're aiming for a graphical interface or a multi-user command-line environment.
**Systemd Targets**: Modern replacement from runlevels in CentOS 7.
**Common Targets**:
`rescue.target` (Single user mode)
`multi-user.target` (Non-graphical, multi-user)
`graphical.target` (Graphical interface)
`reboot.target` (Reboot the system)
`poweroff.target` (Shut down the system)
**Switching Targets**: Use `sudo systemctl isolate TARGET`.
**Setting Default Target**: Use `sudo systemctl set-default TARGET`.

### TTYs

- **Introduction to TTYs:
Definition**: TTY stands for teletypewriter. In the context of Linux, it refers to the virtual consoles ( VCS) available for users to interact with the system, in runlevel 3 
**Usage**: TTYs allow multiple terminal sessions to be open and used simultaneously, even without a graphical user interface (GUI).
**Virtual Consoles:
Concept**: Linux systems provide multiple virtual consoles, typically accessed using the keyboard.
**Number of TTYs**: Most Linux distributions provide 6 virtual consoles by default (TTY1 to TTY6). Sometimes, TTY7 is reserved for the graphical interface.
**Drivers tty:**
in VCS when we are using the tty there are some drivers that are workingin the background,
like /dev/tty1 /dev/tty2 etc 
**Switching Between TTYs:**
To switch between consoles use `Alt + F(1..6)` # Here (1..6) means anything from f1 to f6 and each number corresponds to each console number so f5 = tty5 an so on

### **Splash Screen**:

An image or animation displayed during the boot process to provide user feedback and improve aesthetics.
**Systems**: Plymouth is the most common system used in modern Linux distributions for managing splash screens.
# we can also interrupt and use a console here to go to a different runlevel/systemd, default will still be the same as it has to be changed from the configuration files 

### File System

**A Filesystem** is a method used by an operating system to organize, store, and manage files and directories on a storage device like a hard drive or SSD. It keeps track of where data is located, how it is accessed, and includes information about file names, sizes, and permissions.
A filesystem (FS) is typically created for each partition or volume on a disk, rather than for each individual piece of data or for the entire disk as a single entity.
When a filesystem is created, it is done on a partition or a volume. This process involves formatting the partition with a filesystem type (e.g., ext4, NTFS, FAT32).
If you have multiple partitions, you can create a separate filesystem on each partition. Each partition will independently manage its data using its filesystem.
# Use tools like `fdisk`, `parted`, or graphical disk management utilities to create partitions on your disk.
Use commands like `mkfs.ext4` to create an ext4 filesystem on a specific partition, This process sets up the necessary data structures (like superblocks, inodes, and data blocks) on each partition.
Filesystems are created on partitions or volumes, but to use them, they need to be integrated into the directory structure.
Mounting connects the filesystem to a directory (the mount point) so that users and applications can access files and directories within that filesystem.
**Mounting**: The process of attaching a filesystem to a specific directory (mount point) in the Linux directory tree.
**Purpose**: To make filesystems accessible and integrate different storage devices into the directory structure.
Example:
To access a filesystem, you first need to create a directory that will serve as the mount point. For example, you can create a directory called `/mnt/external` by using the command `sudo mkdir /mnt/external`. This directory will be where you can access the contents of the filesystem once it is mounted. Next, you use the `mount` command to attach the filesystem to the mount point. For instance, if your device identifier is `/dev/sdb1`, you can mount the filesystem with the command `sudo mount /dev/sdb1 /mnt/external`. After executing this command, the files on the device will be accessible through the `/mnt/external` directory.
# But this is not permanent and will be delete after a reboot , to have a permanent follow the following instructions 
To make the mount permanent, you need root privileges to edit the **`/etc/fstab` which is a boot process file**  file. You can use any text editor, such as `nano` or `vim`, by running the command `sudo nano /etc/fstab`. Add a line at the end of the file with the details of the filesystem in the format: 
<`<device> <mount_point> <filesystem_type> <options> <dump> <pass>`>. 
For example, to make the `/dev/sdb1` mount to `/mnt/external` permanent, you might add: <`/dev/sdb1 /mnt/external ext4 defaults 0 2`>.
 Adjust the `filesystem_type` (e.g., `ext4`, `ntfs`) and options as needed. 
/dev/sdb1: The device identifier.
/mnt/external: The mount point.
ext4: The filesystem type.
defaults: The mount options (default options).
0: The dump value (not backed up by dump)
2: The pass value (checked by fsck after the root filesystem; 0 to skip check).

### Partition Table

A partition table is a data structure on a storage device such as a hard disk or solid-state drive that describes the layout of the disk's partitions. It provides information about the starting and ending points of each partition, the type of each partition, and other relevant metadata. This information is crucial for the operating system to correctly manage and access the different partitions on the disk.
most common types are:
**Master Boot Record (MBR)
GUID Partition Table (GPT)
Apple Partition Map (APM)**

- network can have multiple gateways but the default gateway can only be one

### IP aliasing

is a technique used to assign multiple IP addresses to a single network interface. This allows a single physical interface to be configured with multiple logical IP addresses, enabling it to handle traffic for multiple IP addresses. IP aliasing is commonly used in scenarios where multiple services need to run on a single machine with different IP addresses or for network management purposes.
IP aliasing is typically configured by creating additional network interface configurations, often named using a colon (`:`) to denote aliases, such as `eth0:0`, `eth0:1`, etc.Each alias is treated as a separate logical interface with its own IP address, even though they share the same physical hardware.

- All ports and services are mentioned in /etc/services
- There are 65535 total ports in which 1023 ports are privileged ports and the rest are non-privileged ports

### **RPM (Red Hat Package Manager)**

**RPM** is a powerful package management system used by Red Hat-based distributions (such as CentOS, Fedora, and RHEL) to manage software packages. It allows users to install, update, uninstall, verify, and query software packages.
Key Characteristics:
**Binary Format**: RPM packages are typically distributed in binary format with a `.rpm` extension.
**Dependency Management**: RPM handles software dependencies to ensure that all required libraries and packages are installed.
**Database of Installed Packages**: RPM maintains a database of installed packages to track and manage them efficiently.

### **DPKG (Debian Package Manager)**

**DPKG** is the package management system used by Debian-based distributions (such as Ubuntu and Debian itself) to manage software packages. It works with `.deb` packages and provides low-level functions for installing, updating, and removing packages.
Key Characteristics:
**Binary Format**: DPKG packages are distributed in binary format with a `.deb` extension.
**Basic Package Management**: DPKG focuses on basic package management functions, and higher-level tools like `apt` or `synaptic` are often used for dependency management
**Database of Installed Packages**: DPKG maintains a database of installed packages to track and manage them efficiently.

### Swap

**swap** refers to a space on a hard drive that is used as virtual memory when the physical RAM (Random Access Memory) is fully utilized. When the system runs out of physical memory, it can temporarily transfer data from RAM to the swap space on the disk. This process is called swapping.
it uses VFS file system 

### Buffers

**Buffers** are temporary storage areas in RAM used by the kernel to hold data that is in the process of being moved from one place to another. Specifically, they are used for data that is in transit, such as data being written to or read from disk.
**Purpose**: The primary purpose of buffers is to optimize disk I/O operations. By using buffers, the system can accumulate multiple disk I/O requests and process them in one go, which reduces the overhead of multiple, smaller I/O operations.

### Cache

**Cache** refers to memory used by the kernel to store data that has been read from disk and might be read again soon. The idea is to keep frequently accessed data in RAM so that the system can access it quickly without having to read from disk each time.
**Types of Cache**:
**Page Cache**: Stores actual file data that has been read from disk.
**Dentries and Inodes Cache**: Stores metadata about files and directories.
**Purpose**: The primary purpose of the cache is to speed up data access and improve overall system performance by reducing the need for repeated disk access.

### Logical Volume Manager (LVM)

LVM allows for flexible disk management, enabling the resizing of logical volumes as needed. 
Tip: Whenever you  need to add/make a disk or mount point first make a volume group and then add to that cuz with that you can always add more disk/storage to that vg and then create lv(logical volumes ) , and you can directly add a disk or make patitions from the disk and then add that partitions its upto you, how to do that ? the process is in linux commands notes 

### Pathing

**Patching** is the process of updating software to fix vulnerabilities, improve performance, or add features. It is essential for security, stability, and efficiency. The patching process involves identification, assessment, deployment, and verification to ensure systems remain protected and functional. Regular patching is a critical component of effective system and software management.

### Permission Bits

File permissions in Unix-like systems use a 3-bit binary number to represent each set of permissions (owner, group, others). Each bit corresponds to a specific permission:
**Read (r)**: Represented by the highest bit, which has a value of 4 (2^2 = 4)
**Write (w)**: Represented by the middle bit, which has a value of 2 (2^1 = 2).
**Execute (x)**: Represented by the lowest bit, which has a value of 1 (2^0 = 1).

### Special permissions:

**SUID (Set User )**: if this is set on a file then whoever runs this file will be executing it with owners permissions , so if the owner’s permission was rwx then the user will also have these permissions when executing the file  # IMP TOPIC
**Example**: The `passwd` command lets users change their passwords. Normally, changing a password requires modifying system files, which need root permissions. By setting the SUID bit on `passwd`, any user can run it with root privileges, but only for the scope of changing passwords.
**SGID (Set Group ID):** if this is set on a file then whoever runs this file will be executing it with Group permissions , so if the group’s permission where rwx then the user will also have these permissions when executing the file 
**Sticky Bit:**
**Purpose**: Prevents users from deleting or renaming files in a directory unless they own the file or directory.
**Real-World Example**: The `/tmp` directory is writable by all users, but you don't want users to delete each other's files.
**Scenario**: You have a directory `/public` where everyone can write files, but only file owners can delete their files.

**sudoers:** Allows specific users or groups to perform administrative tasks without giving them full root access. This minimizes security risks associated with providing full root access to multiple users.
The `sudoers` file is a configuration file for the `sudo` command on Unix-like operating systems.
 The file is located at `/etc/sudoers`.

umask: This is the defult permission given to a file/directory made 

- The admin in linux are the users how has the uid of 0 and root user has uid 0 thats why he is the super user

### Kernel:

its the Engine or brain of the OS , it’s stored in /boot and is around 4,6 mb 
it uses drivers which are stored in /lib/modules/<kernel-version>/kernel/  and are called kernel drivers , these drivers use .ko extentions which stands for kernel object 

- Types of kernel 
**Monolithic Kernel**: Combines all services and drivers into a single large block of code running in a single address space. It offers better performance but at the cost of potential stability and maintenance challenges.
**Microkernel**: Strips the kernel down to its most fundamental parts, with other services running in user space. This design improves stability and security but may suffer from performance overhead due to more complex communication.

Kernel tuning involves adjusting various parameters and settings of the kernel to optimize the performance, stability, and behavior of a Linux system. This process can help ensure that the system operates efficiently under specific workloads and conditions.
- Peripheral Component Interconnect (PCI) is **a local computer bus for attaching hardware devices in a computer** and is part of the PCI Local Bus standard

### AWS Services

![aws services.png](../Cloud%20&%20SysOps%202193e043159d819897a1ff2b1ecadcd3/aws_services.png)

![Untitled](../Cloud%20&%20SysOps%202193e043159d819897a1ff2b1ecadcd3/2024-07-01_20_18_47-(623)_Introduction_to_AWS_Services_-_YouTube.png)

- Global Infrastructure (GI) is the overall picture of how many Regions and AZs AWS has deployed worldwide.
- Regions are like geographically distinct "zones" with complete AWS services.
- Availability Zones (AZs) are like individual data centers within a Region, offering high availability.
- **Infrastructure as a Service (IaaS):** This is the most basic layer. With IaaS, you rent virtual servers, storage, networking, and other fundamental computing resources. You have complete control over these resources, just like managing your own data center, but with the benefit of scalability and pay-as-you-go pricing offered by AWS.
- **Platform as a Service (PaaS):** PaaS provides a platform for developing, deploying, and managing applications. It eliminates the need to manage the underlying infrastructure (servers, storage, networking) as AWS takes care of that. You focus on building and deploying your applications on the platform.
- **Software as a Service (SaaS):** This offers ready-made applications delivered over the internet. You don't need to manage infrastructure or the platform; you simply access and use the software application for your specific needs. Popular examples of SaaS applications include Gmail, Dropbox, and Salesforce.
- EC2 instances come in various configurations, categorized into families based on their core functionalities. These families help you choose the instance type that best suits your workload's needs.
**Compute Optimized:** These instances are powerful in terms of CPU processing power, ideal for compute-intensive workloads like scientific simulations or video editing.
**Memory Optimized:** These instances offer large amounts of memory, making them suitable for applications requiring in-memory databases or large datasets.
**Storage Optimized:** These instances come with significant storage capacity, perfect for storing large amounts of data or running databases.
**General Purpose:** These instances offer a balanced mix of CPU, memory, and storage, suitable for a wide range of applications that don't have specific resource demands.
- AWS offers a variety of storage solutions to cater to different data storage needs. Here's a breakdown of the main storage types:
**Block Storage: Amazon Elastic Block Store (EBS)
Concept:** EBS provides persistent block storage volumes that behave like traditional hard disk drives (HDDs) or solid-state drives (SSDs). You can attach these volumes to your EC2 instances and use them to store data that persists even after instance termination.

**Object Storage: Amazon Simple Storage Service (S3)
Concept:** S3 is a highly scalable object storage service designed for storing and retrieving any amount of data, from a few kilobytes to petabytes. Data is stored as objects with unique identifiers, making it efficient for unstructured data like backups, archives, media files, and static website content.

**File Storage:
Amazon Elastic File System (EFS):** Provides a scalable, managed file system service for sharing data between EC2 instances in a single Availability Zone. It allows you to mount file systems to multiple instances simultaneously for collaborative editing and application access.
- Simple Monthly Calculator:
This is a calculator where we can check what services will cost, just google aws pricing calculator
- Amazon Inspector: Your Automated Security Guard
**Amazon Inspector** is a cloud-based security assessment service that helps you automatically assess the security of your applications deployed on AWS. It acts like an automated security auditor, continuously scanning your workloads for vulnerabilities and deviations from security best practices.
**Automated Vulnerability Scanning**
    
    **Network Exposure Assessment**
    
    **Security Best Practice Checks**
    
    **Continuous Security Monitoring**
    
    **Detailed Findings and Recommendations**
    

- NFS Network file sharing  service, port 2049, UDP protocol, standard is Linux to Linux, doesnt ask for username password # Add the Folder you want to share in /etc/exports
- Samba file sharing  service uses 137/139/335 port, tcp protocol, linux to lix OR linux to windows,  requires username & password

### **SELinux (Security-Enhanced Linux**

- **SELinux (Security-Enhanced Linux)** is a security module integrated into the Linux kernel that provides a mechanism for supporting access control security policies. It was originally developed by the NSA and is now a standard part of many Linux distributions, especially RHEL/CentOS and Fedora.

### **named**

- **`named`** (pronounced as "name-dee") is the **BIND (Berkeley Internet Name Domain) DNS server** daemon. It stands for "name daemon" and is a crucial component of the BIND package, which is the most widely used DNS server software on the Internet. **`named`** provides DNS resolution services, translating domain names into IP addresses (and vice versa). 
The main configuration file for `named is /etc/named.conf`

### httpd

- **`httpd`** is the executable name for the Apache HTTP Server daemon, which is one of the most popular and widely used web server software applications. It is part of the Apache HTTP Server Project and provides a robust, full-featured web server for serving web pages and other content over HTTP and HTTPS protocols.
IMP Files:
**`/etc/httpd/conf/httpd.conf`: T**he main configuration file for the Apache HTTP Server.
**`/etc/httpd/conf.d/`:**  Directory containing additional configuration files that are included in the main configuration.
**`/var/www/html/`:** Default document root directory where web content is stored.

### **Virtual Hosts** (vhosts)

### **Virtual Hosts** (vhosts)

in Apache HTTP Server allow you to host multiple websites on a single server. This is achieved by using different configurations for each site, such as different domain names or IP addresses. Virtual hosts can be configured to serve different content based on the requested URL, making it possible to host multiple websites on a single server instance.

### Understanding Rolling Releases and `lsb_release`

### Rolling Releases

In the world of Linux distributions, there are two primary release models:

1. **Fixed Release Model:** This is the traditional model where a distribution releases a new version at specific intervals (e.g., Ubuntu every two years). Users upgrade to the new version when it's available.
2. **Rolling Release Model:** In this model, the distribution is constantly updated with the latest software packages. There's no fixed release schedule, and users are always running the most recent stable versions.

### `lsb_release` Command

The `lsb_release` command provides information about the Linux Standard Base (LSB) and the distribution you're using.

**Commonly used options:**

- **`lsb_release -a`:** Displays all available information.
- **`lsb_release -d`:** Displays the distribution description.
- **`lsb_release -r`:** Displays the release number.
- **`lsb_release -c`:** Displays the codename (if available).

**Example:**

Bash

`lsb_release -a`

This command might output something like:

`Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Release:        22.04
Codename:       jammy`

In this example, Ubuntu follows a fixed release model with the codename "jammy" for the 22.04 LTS release.

**However, for a rolling release distribution like Arch Linux, the output would be different:**

Bash

`Distributor ID: Arch
Description:    Arch Linux
Release:        rolling
Codename:       n/a`

Here, the `Release` field shows "rolling," indicating a continuous update model

### **Name Servers (NS Records)**

You’re almost correct about the role of name servers! Let’s clarify the process step by step:

1. **Client Requests a Domain:**
    - Someone types `example.com` into their browser.
    - The browser doesn't know the IP address of `example.com`, so it asks the **recursive DNS resolver** (often provided by your ISP or set up in your device).
2. **Resolver Queries the Root Name Servers:**
    - The resolver starts at the **root name servers**. These servers know which name servers are responsible for the **Top-Level Domain (TLD)**, like `.com`.
3. **Resolver Queries the TLD Name Servers:**
    - The `.com` name servers point the resolver to the **authoritative name servers** for `example.com`.
    - These are the **Route 53 name servers** provided when you created your hosted zone.
4. **Route 53 Name Servers Respond:**
    - The Route 53 name servers store the DNS records (like A, CNAME, or Alias records) for `example.com`.
    - The resolver retrieves the IP address for `example.com` (from the A or AAAA record).
5. **Resolver Sends the IP to the Browser:**
    - The browser now knows the IP address of the server hosting `example.com`.
    - The client (browser) connects to that IP address to load the website.

---

### **Key Takeaway for Name Servers**

- Name servers (NS records) are the **authoritative source** for your domain's DNS information.
- They store the IP address for your domain or instructions to find it (e.g., through Alias or CNAME records).

---

### **What is This Process Called?**

This entire flow is part of **DNS resolution** or **DNS lookup**.

- The DNS resolver plays detective, starting at the root and following a chain of servers until it finds the IP address for the domain.
- Think of Route 53 name servers as the "final stop" where the actual DNS information for your domain is stored.

- To reset root pass in 7 or 8 version:
RHEL 7/8 passwrd reset while booting
go to splash screen interupt
press e
linux 16
rd.break
ctrl x
SH# mount -o remount rw/sysroot
SH# chroot /sysroot
SH passwd root
SH# touch /.autorelabel
exit
exit

## Syntax:

- `ln` # This is used for making a hyperlink Syntax: < ln filename linkfilename > # use -s for softlink default is hardlink
- `find . -inum <inode number>` # This will show all the files having the same given inode number

### Chattr

- `chattr -i <filename>` # this is change attribute command which will make this fill non-deletable even by root 
The `chattr` and `lsattr` commands are used in Linux to manage and view file(lsattr) attributes on ext2, ext3, and ext4 filesystems. These commands provide additional control over how files can be manipulated, beyond the standard file permissions.
The `chattr` command is used to change file attributes on a Linux file system. These attributes can be used to make files immutable, append-only, etc.
    
    ### Common Options
    
    **`+`**: Adds an attribute to the file.
    
    **`-`**: Removes an attribute from the file.
    
    **`=`**: Sets the attribute (removes all other attributes).
    
    ### Common Attributes
    
    **`a`**: Append-only. The file can only be opened in append mode for writing.
    
    **`i`**: Immutable. The file cannot be modified, deleted, renamed, or linked.
    
    **`d`**: No dump. The file will not be included in the backups made by the `dump` program.
    
    **`A`**: No atime updates. Do not update the file's last access time.
    
    **`S`**: Synchronous updates. Changes are written synchronously to disk.
    
    **`u`**: Undelete. When a file with this attribute set is deleted, its contents are saved, allowing the file to be recovered later.
    

### setfacl

- `setfacl` # set file access control lists , used to set specific perm for specific users 
Syntax:  setfacl -m u:usrname:rwx filename # -m is for modify and u is for user and then the username the perm to set and the file name

### getfacl

- `getfacl filename` # this is used to check the perm for the file , get file acces control list

### fdisk

- `fdisk < path-to-disk/dev/sdb >` # This will open the fdisk console/terminal, where we can do alot with disks like create partitions delete it view it etc , use m to view help and n to create a new partition

### parted

- `parted` # This is also used for disk managment and it can also tell what type of partition table we are using

### mkfs

- `mkfs.ext4 /dev/sdb1` # This will create a filesystem

### mount

- `mount /dev/sdb1 /tomcat` # This will mount the sdb1 partition in /tomcat

- pts while in runlevel 5 GUI there’s a pts and pts terminals which can also go to 400 terminals simultaniously

### startx

- `startx` # This will run GUI in runlevel 3 , an run pkill x to return to CLI , this won’t wok in minimal install which dosen’t intall GUI

### gzip/bzip2

- `gzip/bzip2 file` # This will compress the file and make it file.gz/.bz2

### gunzip/bunzip2

- `gunzip/bunzip2 file.gz` # This will extract the gz/bz2 compressed file

### zcat

- `zcat file.gz` # This command is used to read the contant of a compressed file there’s also a bzcat for bz files

### file

- `file filename` # This is used to determine the file type

### rsync

- **`rsync`**  # used to copy/backup files or folders , This is an IMPORTANT command as it can be used to copy/take-backup and also is intelligent so it doesn’t override everything 
`rsync` is a powerful and versatile command-line utility for synchronizing files and directories between two locations over a remote and local machine. It is particularly efficient because it only transfers the differences between the source and the destination, which makes it much faster than traditional file copy methods for incremental backups and updates.
Syntax: rsync [options] source destination
**`a`**: Archive mode, which combines several options to preserve file system attributes. (recursive, links, permissions, times, group, owner, devices).
**`v`**: Verbose, increases verbosity to show detailed output.
**`z`**: Compress file data during the transfer to reduce bandwidth usage.
**`r`**: Recursive, copy directories recursively (included in `a`).
**`-p`**: Preserve permissions, ensures that the file permissions are preserved during the transfer.
**`u`**: Update, skip files that are newer on the receiver.
**`h`**: Human-readable, output numbers in a human-readable format.
**`-delete`**: Delete extraneous files from the destination that are not present in the source.
**`-progress`**: Show progress during transfer.
**`e`**: Specify the remote shell program to use, typically `ssh`.
**`-exclude`**: Exclude files matching the specified pattern.

### stat

- `stat  filename` # This will show the statistics of the file in detail

### fsck

- **`fsck`**: A general tool for checking and repairing file systems.
**`e2fsck`**: A specialized tool for checking and repairing ext2, ext3, and ext4 file systems.
**Concept**: Both tools ensure file system integrity by fixing inconsistencies, preventing data loss and system instability.

### badblocks

- `badblocks -v < device/path/ >` # This command will check for disk corruptions

### lsblk/blkid

- `lsblk OR blkid /dev/sdb1` # This is used to get the info of the disk/drivers and mapping of mount points and also the  UUID ( **Universally Unique Identifier ) AND** type(ext3,2,4) of the specified device

### Performance monitoring tools:

- The following are some tools used for performance monitoring and analysis:
    
    **`top`**: Display real-time system summary information, including CPU usage, memory usage, and process list. # like task manager in windows 
    
    **`htop`**: An interactive process viewer for Unix systems, similar to `top`, but with a more user-friendly interface.
    
    **`sar`**: Collect, report, or save system activity information, providing insights into CPU, memory, I/O, and network performance.
    
    **`iostat`**: Report CPU and I/O statistics, showing how system devices are being utilized and their throughput.
    
    **`vmstat`**: Report virtual memory statistics, including processes, memory, paging, block I/O, traps, and CPU activity.
    
    **`iperf`**: Network bandwidth measurement tool, used to measure the maximum TCP and UDP bandwidth performance.
    
    **`tcpdump`**: Command-line packet analyzer, capturing and displaying packet headers for network troubleshooting and analysis.
    

### lspci

- `lspci` # This will list all the pci devices < lspci -vvv > to see all the devices/drivers you can also use grep -i audio/ether to get the ethernet or audio device

### netstat

- **Netstat** is a valuable tool for network administrators and users who need to monitor and troubleshoot network issues. It provides detailed insights into network connections, routing, and interface statistics, helping to diagnose connectivity problems and understand network activity on a system. Although `netstat` is being replaced by tools like `ss` in some modern Linux distributions, it remains widely used due to its comprehensive output and familiar syntax.

### RPM/DPKG

- **RPM**: Used by Red Hat-based distributions. Handles installation, updating, removal, verification, and querying of packages.
RPM Commands
**`i`**: Install a package. < `sudo rpm -i package.rpm` >
**`U`**: Upgrade a package. < `sudo rpm -U package.rpm` >
**`e`**: Remove a package. < `sudo rpm -e package_name` >
**`q`**: Query a package to verify if it is installed. < `rpm -q package_name` >
**`qa`**: Query all installed packages. < `rpm -qa` >
**`ql`**: List files installed by a package. < `rpm -ql package_name` >
**`qR`**: List dependencies of a package. < `rpm -qR package_name` >
**`qi`**: Display package information. < `rpm -qi package_name` >
**`V`**: Verify a package. < `rpm -V package_name` >
`-qf`: tells us from which pakage is the file comming from < `rpm -qf /boot/vmlin….` >
- **DPKG**: Used by Debian-based distributions. Handles installation, updating, removal, and querying of packages. Higher-level tools like `apt` are often used for more advanced package management.
DPKG Commands
**`i`**: Install a package. < `sudo dpkg -i package.deb` >
**`r`**: Remove a package. < `sudo dpkg -r package_name` >
**`P`**: Purge a package, including configuration files. < `sudo dpkg -P package_name` >
**`l`**: List all installed packages. < `dpkg -l` >
**`L`**: List files installed by a package. < `dpkg -L package_name` >
**`s`**: Show information about a package. < `dpkg -s package_name` >
**`S`**: Search for a file in installed packages. < `dpkg -S filename` >
**`configure`**: Reconfigure an unpacked package. < `sudo dpkg --configure package_name` >
**`p`**: Display details about a package. < `dpkg -p package_name` >

### yum/apt

- `yum` (Yellowdog Updater, Modified) is a package management utility for RPM-based Linux distributions such as Red Hat Enterprise Linux (RHEL), CentOS, and Fedora. It is used to install, update, remove, and manage software packages on the system.
**`yum install`**: Install a package. < `sudo yum install package_name` >
**`yum update`**: Update all packages to the latest version. < `sudo yum update` >
**`yum remove`**: Remove a package. < `sudo yum remove package_name` >
**`yum list`**: List all available and installed packages. < `yum list` >
**`yum search`**: Search for a package by keyword. < `yum search keyword` >
**`yum info`**: Display detailed information about a package. < `yum info package_name` >
**`yum clean`**: Clean up temporary files and cache. < `sudo yum clean all` >
**`yum repolist`**: List all enabled repositories. < `yum repolist` >
**`yum history`**: Show the history of yum transactions. < `yum history` >
**`yum groupinstall`**: Install a group of packages. < `sudo yum groupinstall "group_name"` >
**`yum history`**: View transaction history.
**`yum history list`**: List the history of yum transactions.
**`yum history info <transaction_id>`**: Get details of a specific transaction.
**`yum history undo <transaction_id>`**: Undo a specific transaction.
**`yum history redo <transaction_id>`**: Redo a specific transaction.
`yum` simplifies the process of managing software packages on RPM-based systems by automating tasks like dependency resolution and providing a user-friendly command set for installing, updating, and removing packages.

`dnf`  this is the better/faster version of yum , it has the same commands 
# it is used in RHEL and centos from version 8

- For Debian-based systems, the equivalent of `yum` is `apt`, which is a command-line package management tool for managing .deb packages. `apt` is a front-end for `dpkg` and provides a simpler and more intuitive way to handle package management.
**`apt update`**: Update the package index. < `sudo apt update` >
**`apt upgrade`**: Upgrade all installed packages to their latest versions. < `sudo apt upgrade` >
**`apt install`**: Install a package. < `sudo apt install package_name` >
**`apt remove`**: Remove a package. < `sudo apt remove package_name` >
**`apt purge`**: Remove a package along with its configuration files. < `sudo apt purge package_name` >
**`apt autoremove`**: Remove unnecessary packages that were automatically installed to satisfy dependencies for other packages and are no longer needed. < `sudo apt autoremove` >
**`apt search`**: Search for a package in the repositories. < `apt search keyword` >
**`apt show`**: Display detailed information about a package. < `apt show package_name` >
**`apt list`**: List packages based on criteria (installed, upgradable, etc.). <`apt list --installed`>
**`apt clean`**: Clean up local repository of retrieved package files. < `sudo apt clean` >

### LVM

- Logical Volume Manager (LVM)
LVM allows for flexible disk management, enabling the resizing of logical volumes as needed. Here's a step-by-step guide to creating an LVM partition, adding storage, and removing storage.

Use `sudo lvs`, `sudo vgs`, and `sudo pvs` to display logical volumes, volume groups, and physical volumes, respectively.

`resize2fs` is used for ext2/ext3/ext4 filesystems. Use appropriate commands for other filesystem types (e.g., `xfs_growfs` for XFS).

Here’s hw you can create one 
1. first make a partition 
2. change its id to lvm linux which is 8e ( this is best practice )
3. then use `partprobe -s /dev/sdb` to add it to partition table 
4. create a pv(Physical volume) using `pvcreate /dev/sdb1` # you can now this see using pvdisplay
5. now create a vg(volume group) using < `sudo vgcreate myvg /dev/sdb1` > where myvg is the vg name you want to make  # you can also extend to this if you create another partition using < `vgextend myvol sdb2` > 
6. now create a lv(logical volume) using < `lvcreate -L 500M -n myvol myvg` > where -L 500M specifies the storage -n myvol specifies the name of the lv and myvg the volume group # you can now see using lvdisplay and can also extend this volume using < `lvextend -L +500M /path/to/volume/dev/myvol/vl1` >
7. now create a filesytem < `sudo mkfs.ext4 /dev/myvg/mylv` > OR for xfs FS < `sudo mkfs.xfs /dev/myvg/mylv` >
8. and then mount it 

**Command summary**
1. Create a partition < `sudo fdisk /dev/sdb` >
2. Change partition type to LVM (ID 8e) < `sudo fdisk /dev/sdb` > (Inside fdisk, use 't' to change partition type, then enter '8e' for Linux LVM)
3. Add partition to partition table < `sudo partprobe -s /dev/sdb` >
4. Create a physical volume < `sudo pvcreate /dev/sdb1` >
5. Create a volume group < `sudo vgcreate myvg /dev/sdb1` > # Extend the volume group with another partition (if needed) < `sudo vgextend myvg /dev/sdb2` >
6. Create a logical volume < `sudo lvcreate -L 500M -n myvol myvg` > # Extend the logical volume (if needed) < `sudo lvextend -L +500M /dev/myvg/myvol` >
7. Create a filesystem (ext4) on the logical volume < `sudo mkfs.ext4 /dev/myvg/mylv` > OR for xfs FS < `sudo mkfs.xfs /dev/myvg/mylv` >
8. Create a mount point and mount the filesystem < `sudo mkdir /mnt/mydata` > < `sudo mount /dev/myvg/mylv /mnt/mydata` >
Verify the mount < `df -h /mnt/mydat`a > 

# You can use lv pv vg display to see each , Example: < `lvdisplay` >

**To remove space/storage:**
Un-mount the filesystem < `sudo umount /mnt/mydata` >
Reduce the logical volume < `sudo lvreduce -L -500M /dev/myvg/mylv` >
< `sudo resize2fs /dev/myvg/mylv` >
Remove the physical volume from the volume group < `sudo vgreduce myvg /dev/sdd` >
< `sudo pvremove /dev/sdd` >
Mount the filesystem again < `sudo mount /dev/myvg/mylv /mnt/mydata` >
- To take a snapshot of the lvm < `lvcreate -L 1G -s -n bck_lv /dev/myvol/lv1` >

### **What is LVM? ( with steps Cleaner doc )**

**LVM** allows flexible disk management by abstracting storage into layers:

| Component | Full Form | Description |
| --- | --- | --- |
| **PV** | Physical Volume | The actual hard drive or partition. |
| **VG** | Volume Group | Pool of PVs combined into one storage unit. |
| **LV** | Logical Volume | Virtual partitions carved out from VGs. |

---

### 🧠 **Why use LVM?**

- Resize volumes easily (grow/shrink).
- Combine multiple disks.
- Snapshots (backup states).
- Dynamic partitioning without rebooting.

---

## : ' Task 1: Create an LVM Setup '

### 🧱 Step-by-step with Commands

### 🧱 1. Create **Physical Volumes (PVs)**

```bash
sudo pvcreate /dev/sdb /dev/sdc
```

📘 *Prepares these disks for LVM use.*

### 🧱 2. Create a **Volume Group (VG)**

```bash
sudo vgcreate my_vg /dev/sdb /dev/sdc
```

📘 *Combines both PVs into one volume group called `my_vg`.*

### 🧱 3. Create a **Logical Volume (LV)**

```bash
sudo lvcreate -L 5G -n my_lv my_vg
```

📘 *Creates a 5GB LV named `my_lv` from VG `my_vg`.*

### 🧱 4. Format the LV and Mount It

```bash
 /dev/my_vg/my_lv
sudo mkdir /mnt/mydata
sudo mount /dev/my_vg/my_lv /mnt/mydata
```

📘 *Makes the LV usable like any normal partition.*

---

## : ' Task 2: Resize Logical Volume '

### 🔄 Increase LV Size (Online)

```bash
sudo lvextend -L +2G /dev/my_vg/my_lv
sudo resize2fs /dev/my_vg/my_lv
```

📘 *Adds 2GB more space to the LV.*

### 🔄 Reduce LV Size (Careful!)

```bash
sudo umount /mnt/mydata
sudo e2fsck -f /dev/my_vg/my_lv
sudo resize2fs /dev/my_vg/my_lv 3G
sudo lvreduce -L 3G /dev/my_vg/my_lv
```

📘 *Always unmount and check filesystem before shrinking.*

---

## : ' Task 3: Remove or Clean LVM '

### ❌ Unmount and Remove LV

```bash
sudo umount /mnt/mydata
sudo lvremove /dev/my_vg/my_lv
```

### ❌ Remove VG and PVs

```bash
my_vg
sudo pvremove /dev/sdb /dev/sdc
```

---

## 📄 **LVM Status Commands**

| Command | Purpose |
| --- | --- |
| `pvs` / `pvdisplay` | View physical volumes |
| `vgs` / `vgdisplay` | View volume groups |
| `lvs` / `lvdisplay` | View logical volumes |
| `lvscan` | Scan for LVs |
| `vgextend` | Add PV to VG |
| `lvextend` / `lvreduce` | Resize LVs |
| `lvremove` / `vgremove` | Delete LV or VG |

---

## 🧠 Real Example (Mini Story Style)

**Scenario**: You have 2 disks (`/dev/sdb` and `/dev/sdc`), and you want to create a 10GB data volume with LVM.

1. Create PVs → Combine into VG → Slice LV → Format → Mount.
2. Later, you buy another disk. Add it to VG with `vgextend`, and grow the LV with `lvextend`.
3. All done live, no reboots—flexibility at its best.

### Alias

- `alias list=ls` # this is used to nickname a command now list will do what ls does 
`unalias list` # this will remove nickname
    
    **Permanent Aliases:** These are saved for future sessions. The method to create them varies based on your shell. For Bash, you typically edit the `.bashrc` file in your home directory.
    
    ### Example of a Permanent Alias in Bash:
    
    1. Open the `.bashrc` file:
        
        Bash
        
        `nano ~/.bashrc`
        
    2. Add the alias:
        
        `alias ll='ls -la'`
        
    3. Save and close the file.
    4. Source the file to apply the changes:
        
        Bash
        
        `source ~/.bashrc`
        

### User Managment / sudoers

- **USER Managment** :
`adduser <username>` # create a user OR can also use `useradd` 
`passwd <username>` # to change pass for user
`userdel <username>`# to delete a user , you can use `-r` to also delete the user with his home directory 
`chown -R aadmin:aadmin .ssh` # This will change the own of .ssh and the -R flag is used to al change the sub-files and directories owner

`useradd` is a native binary that is always included with a Linux system, while `adduser` is a Perl script that uses the useradd binary in the back-end.
User-friendliness: `adduser` is more user-friendly and interactive compared to `useradd`. 

# go can now go to home and `ls -lah` and it will show you info about users OR `cat /etc/passwd`
`groupadd <groupname>` # To add a gc  
`usermod -g <groupname> <username>` # To add a user to  primary group , You can use -G to add the user to a secondary group 
`passwd -l <username>` # To lock a user 
`passwd -u <username>` # To unlock a user 

ADVANCE PERMISSIONS:
chmod u+s # To set **SUID (Set User)**
chmod g+s # To set **SGID (Set Group ID)**
chmod o+t # To set **Sticky Bit**

suid —> 4
sgid —> 2
Stickybit —> 1
**#** You can also use numerical form e.g 7777 where first 7 is for the special permissions and other for rwx OR 6755 

**sudoers:** Allows specific users or groups to perform administrative tasks without giving them full root access. This minimizes security risks associated with providing full root access to multiple users.
The `sudoers` file is a configuration file for the `sudo` command on Unix-like operating systems.
 The file is located at `/etc/sudoers`.
use < `visudo`> to edit the sudoers file 
example < `thepen ALL=/sbin/fdisk` >
# Now the user can use the command with sudo and it will get executed 

**Basic Syntax**:
The general syntax for an entry in the `sudoers` file is:
user    host = (runas_user) command

**user**: The username or group name.

**host**: The hostname where the rule applies (usually `ALL`).

**runas_user**: The user as whom the command should be run (usually `ALL` or `root`).

**command**: The command(s) that can be run.

Example Entries:

**Granting Full Root Privileges**:

Allow a user `johndoe` to run any command as any user.
johndoe ALL=(ALL) ALL

### Group Management

- **Groups** in Linux are used to manage sets of users who share the same permissions. There are two types:
    - **Primary group** (default group of a user)
    - **Secondary groups** (additional groups a user belongs to)

---

## 📘 Basic Group Commands

```bash

groupadd <groupname>       # Create a new group
groupdel <groupname>       # Delete an existing group
groupmod -n <newname> <oldname>  # Rename a group
```

📌 **Examples:**

```bash
groupadd devs              # Create a group called "devs"
groupdel testgroup         # Delete the "testgroup"
groupmod -n engineers devs # Rename "devs" to "engineers"
```

---

## 👥 Viewing Group Info

```bash
cat /etc/group             # Lists all groups and their members
groups <username>          # Lists groups a user belongs to
id <username>              # Shows UID, GID, and all group membershi
```

📌 **Example:**

```bash
groups johndoe
```

Shows: `johndoe : johndoe sudo docker`

---

## 👤 Adding Users to Groups

```bash
usermod -g <group> <user>     # Set primary group for a user
usermod -aG <group> <user>    # Add user to secondary group (append, don’t replace!)
gpasswd -a <user> <group>     # Another way to add user to a group
```

📌 **Examples:**

```bash
usermod -g devs alice         # Make "devs" Alice's primary group
usermod -aG docker alice      # Add Alice to the "docker" group (secondary)
gpasswd -a bob wheel          # Add Bob to the "wheel" group
```

⚠️ **Warning:** Without `-a`, `usermod -G` will **replace** all secondary groups!

---

## 🔐 Removing Users from Groups

```bash
gpasswd -d <user> <group>     # Remove user from a group
```

📌 **Example:**

```bash
gpasswd -d bob wheel
```

Removes user `bob` from the group `wheel`.

---

## 🔒 Group Passwords (Rarely used)

```bash
gpasswd <groupname>           # Set or change password of a group
```

This lets users join the group using the password if configured that way.

---

## 📄 Group Files

- `/etc/group`: Main file that lists all groups and members.
    - Format: `group_name:x:GID:user1,user2,...`
- `/etc/gshadow`: Stores secure group information (e.g., passwords).

---

## 🧠 Summary

| Command | Purpose |
| --- | --- |
| `groupadd` | Add new group |
| `groupdel` | Delete group |
| `groupmod` | Modify/rename group |
| `usermod -aG` | Add user to **secondary** group |
| `usermod -g` | Change user's **primary** group |
| `gpasswd -a/d` | Add or remove users from group |
| `cat /etc/group` | See all groups |
| `groups`, `id` | Show user’s group memberships |

### Group-Based File Permissions

### Checking File Ownership

```bash
ls -l file.txt
```

Example:

```
diff
CopyEdit
-rw-rw-r-- 1 alice devs 0 Jun 15 11:05 file.txt
```

- `alice`: file owner
- `devs`: group
- `rw-rw-r--`: user (`rw`), group (`rw`), others (`r--`)

So **members of `devs` group** can read and write this file.

---

### 🟢 Changing Group Ownership of Files

```bash
chgrp devs file.txt   # Change group ownership
```

Or for multiple files:

```bash
chgrp -R devs /shared/project
```

---

### 🔵 Ensuring Group Access

If you want other group members to **access or edit** files, use `chmod`:

```bash
chmod 770 file.txt     # rwx for user, rwx for group, none for others
```

Or:

```bash
chmod g+w file.txt     # Give write access to group
```

---

### 🟣 Setgid on Directories for Group Inheritance

If you want **new files** in a shared directory to always belong to the same group:

```bash
chmod g+s /shared/project
```

Then any file created inside `/shared/project` will inherit that folder’s group (e.g. `devs`), not the creator's primary group.

You’ll see the `s` in directory permissions:

```bash
drwxrws--- 2 alice devs 4096 Jun 15 11:15 project
```

### Driver/module managment

- Driver/module Managment Commands:
insmod
modprobe # Add and remove modules from the Linux Kernel
rmmod # To remove a module from ram 
depmod
modinfo # Show information about a Linux Kernel module
lsmod # To list the drivers in ram/active
# These commands are used for driver managment , drivers are also called module 
# TO make the changes of the driver persistant then add the changes to the file < /etc/modprobe.d/dist.conf >

### lspci

- `lspci` # To list the pci devices 
Peripheral Component Interconnect (PCI) is **a local computer bus for attaching hardware devices in a computer** and is part of the PCI Local Bus standard

### curl ifconfig.me

- `curl ifconfig.me` # This command is used to get the public ip

### hostnamectl

- `hostnamectl set-hostname <name> - -static` # this will change the machine hostname - -static is for permanent for rhel 7 and up for 6 use this < `hostname <name>` > and to make it permanent add to `/etc/sysconfig/network`

### **Systemd Services & `systemctl` Commands**

Systemd is the **init system and service manager** used by many Linux distributions (like Ubuntu, CentOS, RHEL, Fedora). The command `systemctl` is used to **manage systemd services**, control the system state, and inspect logs.

---

- `systemctl <start | stop | restart | enable | disable > < service-name >` # This command is ussed to start stop retart the services, the enable disable is used to permanently modify it so it will start with boot if it is enabled 
`systemctl --type=service --state=running # This is used to list the running services` 
`systemctl < service-name > < is-active | is-enabled >` # this is used to check if service-name is active or enabled
 `systemctl list-unit-files | grep -i ftp` # This will show info about the service if used with grep

---

### **Common `systemctl` Commands for Services**

| **Action** | **Command** | **Explanation** |
| --- | --- | --- |
| Start | `systemctl start <service>` | Starts the service immediately. |
| Stop | `systemctl stop <service>` | Stops the service immediately. |
| Restart | `systemctl restart <service>` | Stops and then starts the service. |
| Reload | `systemctl reload <service>` | Reloads the config without restarting (if supported). |
| Enable | `systemctl enable <service>` | Enables service to start at **boot**. |
| Disable | `systemctl disable <service>` | Disables service from auto-start at boot. |
| Status | `systemctl status <service>` | Shows current status, uptime, and logs. |
| Reload + Restart | `systemctl reload-or-restart <service>` | Reload if possible, else restart. |
| Mask | `systemctl mask <service>` | Prevent service from starting **manually or at boot**. |
| Unmask | `systemctl unmask <service>` | Removes the mask so it can be started again. |

---

### **Examples**

```bash
sudo systemctl start apache2          # Start Apache server
sudo systemctl stop apache2           # Stop it
sudo systemctl enable apache2         # Start on system boot
sudo systemctl disable apache2        # Disable auto-start
sudo systemctl restart ssh            # Restart SSH
sudo systemctl status ssh             # View status of SSH
```

---

### **Check All Services & States**

```bash
systemctl list-units --type=service       # List all active services
systemctl list-units --all --type=service # All services, including inactive
```

---

### **Viewing Boot-Time Services**

```bash
systemctl list-unit-files --type=service
```

Shows all installed service unit files with their enablement state (enabled/disabled/static).

---

### **Working with Targets (Runlevels)**

| **Command** | **Purpose** |
| --- | --- |
| `systemctl get-default` | Shows current default target (e.g., `graphical.target`) |
| `systemctl set-default multi-user.target` | Sets default target (similar to runlevel 3 in older systems) |
| `systemctl isolate rescue.target` | Switches immediately to rescue (single-user) mode |

---

### **Other Useful Commands**

```bash
sudo systemctl daemon-reload         # Reload systemd configs (after editing unit files)
sudo journalctl -u ssh               # View logs for a specific service
```

---

### **Understanding Unit Files**

Systemd services are defined by **unit files** stored in:

- `/etc/systemd/system/` (custom/overrides)
- `/lib/systemd/system/` (default distro services)
- `/run/systemd/system/` (temporary runtime)

To edit a unit file:

```bash
sudo vim /etc/systemd/system/myservice.service
sudo systemctl daemon-reexec         # Re-execute systemd if needed
```

---

### sharing files using NFS

- Server:
1. Install NFS Server Packages:
`sudo yum install nfs-utils -y`  # For RHEL/CentOS
`sudo apt-get install nfs-kernel-server -y`  # For Debian/Ubuntu

2. Create the Export Directory:
`sudo mkdir -p /srv/nfs/shared`
`sudo chown nobody:nogroup /srv/nfs/shared`

3.  Edit the Export File:
Add the export directory to `/etc/exports` file:
`sudo vi /etc/exports`
Example entry to share `/srv/nfs/shared` directory with read/write permissions
`/srv/nfs/shared  *(rw,sync,no_subtree_check)`

4. Export the Shared Directory:
`sudo exportfs -a`

5. Start and Enable NFS Services:
`sudo systemctl start nfs-server`
`sudo systemctl enable nfs-server`

# Other:

- Client
1. Install NFS Client Packages:
`sudo yum install nfs-utils -y`  # For RHEL/CentOS
`sudo apt-get install nfs-common -y`  # For Debian/Ubuntu

2. Create a Mount Point:
`sudo mkdir -p /mnt/nfs/shared`

3. Mount the NFS Share:
`sudo mount -t nfs < ip OR Hostname >:/srv/nfs/shared /mnt/nfs/shared`

4. Verify the mount: 
`df -h /mnt/nfs/shared`

5. Make the Mount Permanent:
Add the following line to `/etc/fstab`:
sudo vim /etc/fstab

Example entry for `/etc/fstab`:
192.168.1.10:/srv/nfs/shared /mnt/nfs/shared nfs defaults 0 0

6. Mount All Filesystems (to apply changes):
`sudo mount -a`

### find

- **`find` Overview**
The `find` command is a powerful utility in Linux used for searching files and directories in a directory hierarchy based on various criteria, such as name, type, size, permissions, modification time, etc. It’s widely used in system administration for locating files and performing actions on them.
    
    ### **Syntax**
    
    `find [path] [expression]`
    
    - **path**: The directory where the search should start. If not specified, the current directory is used.
    - **expression**: The criteria or conditions to match files and directories. This can include options, tests, and actions.
    
    ### **Common Options**
    
    - `name`: Searches for files with a specific name pattern.
    - `type`: Searches for files of a specific type (e.g., regular file, directory).
    - `size`: Searches for files of a specific size.
    - `perm`: Searches for files with specific permissions.
    - `mtime`: Searches for files modified a certain number of days ago.
    - `exec`: Executes a command on the found files.
    
    ### **Common Tests and Examples**
    
    ### 1. **Search by Name**
    
    - **Description**: Finds files or directories by their name.
    - **Syntax**: `find [path] -name "pattern"`
    - **Example**: `find /home/user -name "*.txt"`
        - Finds all `.txt` files in `/home/user` and its subdirectories.
    
    ### 2. **Search by File Type**
    
    - **Description**: Finds files based on their type.
    - **Syntax**: `find [path] -type [type]`
    - **Example**: `find /var/log -type f`
        - Finds all regular files in `/var/log`.
    
    **Common File Types**:
    
    - `f`: Regular file
    - `d`: Directory
    - `l`: Symbolic link
    - `b`: Block device
    - `c`: Character device
    
    ### 3. **Search by File Size**
    
    - **Description**: Finds files based on their size.
    - **Syntax**: `find [path] -size [size]`
    - **Example**: `find / -size +100M`
        - Finds files larger than 100 MB on the system.
    
    **Size Suffixes**:
    
    - `b`: 512-byte blocks (default)
    - `c`: Bytes
    - `k`: Kilobytes
    - `M`: Megabytes
    - `G`: Gigabytes
    
    ### 4. **Search by Permissions**
    
    - **Description**: Finds files with specific permissions.
    - **Syntax**: `find [path] -perm [mode]`
    - **Example**: `find /etc -perm 644`
        - Finds files in `/etc` with permissions `644`.
    
    **Mode**:
    
    - The permission mode can be specified in symbolic (e.g., `u+x`) or numeric format (e.g., `755`).
    
    ### 5. **Search by Modification Time**
    
    - **Description**: Finds files based on when they were last modified.
    - **Syntax**: `find [path] -mtime [n]`
    - **Example**: `find /var/log -mtime -7`
        - Finds files in `/var/log` that were modified in the last 7 days.
    
    **Time Units**:
    
    - `mtime n`: Files modified exactly `n` days ago.
    - `mtime +n`: Files modified more than `n` days ago.
    - `mtime -n`: Files modified less than `n` days ago.
    
    ### 6. **Executing Commands on Found Files**
    
    - **Description**: Executes a command on the files found by `find`.
    - **Syntax**: `find [path] [expression] -exec [command] {} \;`
    - **Example**: `find /tmp -type f -name "*.log" -exec rm {} \;`
        - Finds all `.log` files in `/tmp` and deletes them.
    - **Example**: `find /home/user -type f -exec chmod 644 {} \;`
        - Changes the permissions of all regular files in `/home/user` to `644`.
    
    ### 7. **Combining Multiple Conditions**
    
    - **Description**: Combines multiple conditions using operators like `and` or `or`.
    - **Syntax**: `find [path] [expression1] -and [expression2]`
    - **Example**: `find / -type f -name "*.conf" -and -size +1M`
        - Finds `.conf` files larger than 1 MB on the system.
    
    ### 8. **Search by User and Group**
    
    - **Description**: Finds files owned by a specific user or group.
    - **Syntax**: `find [path] -user [username] -group [groupname]`
    - **Example**: `find /home -user alice`
        - Finds files owned by the user `alice` in `/home`.
    
    ### 9. **Search by Access Time**
    
    - **Description**: Finds files based on when they were last accessed.
    - **Syntax**: `find [path] -atime [n]`
    - **Example**: `find /tmp -atime +10`
        - Finds files in `/tmp` that were accessed more than 10 days ago.
    
    ### 10. **Search by Inode Number**
    
    - **Description**: Finds files by their inode number.
    - **Syntax**: `find [path] -inum [inode_number]`
    - **Example**: `find / -inum 123456`
        - Finds the file with inode number `123456` on the system.
    
    ### **Combining Conditions Using `and`**
    
    - **Description**: Find files that match multiple criteria.
    - **Example**: `find /home/user -type f -name "*.txt" -and -size +1M`
        - This command finds `.txt` files larger than 1 MB in the `/home/user` directory.
    
    ### **Combining Conditions Using `or`**
    
    - **Description**: Find files that match any of the given criteria.
    - **Example**: `find /home/user -type f -name "*.jpg" -or -name "*.png"`
        - This command finds all `.jpg` or `.png` files in the `/home/user` directory.
    
    ### **Negating Conditions Using `!`**
    
    - **Description**: Find files that do not match a specific condition.
    - **Example**: `find /var/log -type f ! -name "*.log"`
        - This command finds all files in `/var/log` that do not have the `.log` extension.
    
    find ./ -type d -name  dir_name # This will search for all directories named dir_name 
    
    find ./ -type f -name  file_name # This will search for all files named file_name 
    
    find . -type f -not -name '*cvs' -print | xargs rm -rf
    

### Tmux

- Here’s an overview of `tmux` commands and features in the inline format for your notes:
    
    **TMUX Commands**
    
    - **`tmux`**: Start a new tmux session. < e.g., `tmux` >
    - **`tmux new-session -s session_name`**: Create a new session with a specific name. < e.g., `tmux new-session -s mysession` >
    - **`tmux attach -t session_name`**: Attach to an existing session by name. < e.g., `tmux attach -t mysession` >
    - **`tmux detach`**: Detach from the current session (use prefix key `Ctrl-b`, then press `d`).
    - **`tmux ls`**: List all tmux sessions.
    - **`tmux kill-session -t session_name`**: Kill a specific session by name. < e.g., `tmux kill-session -t mysession` >
    - **`tmux rename-session -t old_name new_name`**: Rename an existing session. < e.g., `tmux rename-session -t mysession newname` >
    
    **Window Management**
    
    - **`Ctrl-b c`**: Create a new window.
    - **`Ctrl-b n`**: Switch to the next window.
    - **`Ctrl-b p`**: Switch to the previous window.
    - **`Ctrl-b &`**: Close the current window.
    - **`Ctrl-b ,`**: Rename the current window.
    - **`Ctrl-b w`**: List all windows and select one to switch.
    
    **Pane Management**
    
    - **`Ctrl-b %`**: Split the current pane vertically.
    - **`Ctrl-b "`**: Split the current pane horizontally.
    - **`Ctrl-b o`**: Switch to the next pane.
    - **`Ctrl-b x`**: Close the current pane.
    - **`Ctrl-b {`**: Move the current pane to the previous position.
    - **`Ctrl-b }`**: Move the current pane to the next position.
    
    **Session Management**
    
    - **`tmux new-session`**: Start a new session.
    - **`tmux attach-session -t session_name`**: Attach to an existing session.
    - **`tmux list-sessions`**: List all tmux sessions.
    - **`tmux kill-session -t session_name`**: Kill a specific session.

### Vim

- **VIM Commands**
    - **`i`**: Enter insert mode. This allows you to start editing the text.
    - **`Esc`**: Exit insert mode and return to normal mode.
    - **`:w`**: Save the current file. < e.g., `:w` >
    - **`:q`**: Quit Vim. < e.g., `:q` >
    - **`:wq`**: Save and quit. < e.g., `:wq` >
    - **`:q!`**: Quit without saving changes. < e.g., `:q!` >
    - **`:x`**: Save and quit, similar to `:wq`. < e.g., `:x` >
    - **`yy`**: Copy (yank) the current line.
    - **`p`**: Paste the copied (yanked) line below the cursor.
    - **`dd`**: Delete the current line.
    - **`u`**: Undo the last change.
    - **`Ctrl-r`**: Redo the last undone change.
    - **`/text`**: Search for `text` in the file. < e.g., `/error` >
    - **`n`**: Move to the next occurrence of the search term.
    - **`N`**: Move to the previous occurrence of the search term.
    - **`gg`**: Move to the beginning of the file.
    - **`G`**: Move to the end of the file.
    - **`:set number`**: Display line numbers in the file.
    - **`:set nonumber`**: Hide line numbers in the file.

### check if port is open or closed

- To check if a port is open or not use these commands:
`nc <ip> <port>` e.g `nc 127.0.0.1 21`  OR
same but nc will be telnet  OR
`ss -tulnp | grep -i 21`

### ldd

- `ldd /user/sbin/vsftpd` # ldd This command shows the dependencies of the binary

- Uncommenting `PasswordAuthentication Yes` in the file path: `/etc/ssh/sshd_config` file allows password-based authentication for SSH connections.

### ps command

The `ps` command is used for process management and monitoring in Linux, helping you view running processes and their statuses

- **ps**: Display information about processes running in the current shell session. < `ps` >
- **ps -A**: Show information about all running processes. < `ps -A` >
- **ps -u username**: Display processes for a specific user. < `ps -u username` >
- **ps -e**: Show all running processes in the system. < `ps -e` >
- **ps aux**: Show detailed information about all processes, including user, CPU, memory usage, etc. < `ps aux` >
- **ps -ef**: Display all running processes in a full-format listing, including PPID (Parent Process ID). < `ps -ef` >
- **ps -el**: Show all running processes in a long format with detailed columns such as priority and flags. < `ps -el` >

### Task — Scheduled Jobs with `cron` and `crontab`

The `cron` system is used in Linux to **schedule tasks** (commands or scripts) to run **automatically at specified times/dates**.

---

### 📌 What is `cron`?

- A **daemon** (`cron`) that runs in the background and checks if there are scheduled jobs.
- Uses **`crontab` files** to know *what* to run and *when*.

---

### 🛠️ Basic Crontab Commands

| Command | Description |
| --- | --- |
| `crontab -e` | Edit the current user’s crontab |
| `crontab -l` | List your current cron jobs |
| `crontab -r` | Remove your crontab (all jobs) |
| `crontab -u <user> -e` | Edit another user's crontab (root only) |

---

### 🧾 Crontab Format

Each line in a crontab file follows this format:

```bash
* * * * * command-to-execute
│ │ │ │ │
│ │ │ │ └─ Day of the week (0-6) (Sunday=0)
│ │ │ └─── Month (1-12)
│ │ └───── Day of the month (1-31)
│ └─────── Hour (0-23)
└───────── Minute (0-59)
```

---

### 📚 Examples

```bash
# Run script.sh every day at 2am
0 2 * * * /home/user/script.sh

# Run a backup every Sunday at 3:30am
30 3 * * 0 /home/user/backup.sh

# Run every 15 minutes
*/15 * * * * /path/to/task.sh

# Run only in January
0 10 * 1 * /path/to/january-task.sh
```

---

### 📁 Crontab File Locations

- User-specific: `crontab -e` edits per-user files in `/var/spool/cron/crontabs/`
- System-wide:
    - `/etc/crontab`
    - `/etc/cron.d/`
    - `/etc/cron.daily/`, `/weekly/`, `/hourly/`, `/monthly/`

---

### ⚠️ Things to Remember

- Always use **absolute paths** in cron commands.
- Add environment variables if needed (like `PATH` or `MAILTO`).
- Redirect output to avoid errors:
    
    ```bash
    * * * * * /my/script.sh > /tmp/output.log 2>&1
    ```
    

---

---

### 🖊️ Choosing a Text Editor for `crontab`

By default, when you run:

```bash
crontab -e
```

Linux opens the crontab in your system's **default editor**. This is often:

- `nano` on Ubuntu/Debian
- `vi` or `vim` on CentOS, RHEL, Rocky, etc.

---

### 🔄 Changing the Crontab Editor Temporarily

You can **temporarily override** the editor for just one command using:

```bash
EDITOR=vim crontab -e
```

Or:

```bash
ontab -e
```

📌 This doesn't affect system-wide defaults — only for that instance.

---

### 🧑‍🔧 Setting a Permanent Default Editor for Crontab

To make a specific editor (e.g., `vim`) your default **permanently**, add this to your `~/.bashrc` or `~/.zshrc`:

```bash
export VISUAL=vim
export EDITOR=vim
```

Then reload your shell:

```bash
source ~/.bashrc
```

Or for ZSH:

```bash
source ~/.zshrc
```

Now every time you use `crontab -e`, it will open in `vim`.

---

### SSH Management & Key-Based Authentication

---

### **What is SSH?**

- **SSH (Secure Shell)** is a cryptographic protocol used to securely connect to remote systems over an insecure network.
- It **encrypts** the session to prevent sniffing and **authenticates** users via password or keys.

---

### 🛠️ Task 1: Generate SSH Keys

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

📌 **Explanation**:

- `t rsa` → Key type = RSA.
- `b 4096` → 4096-bit key (recommended for security).
- `C` → Adds a comment (email or label).

⏳ **When prompted**:

- **Press Enter** to save in default: `~/.ssh/id_rsa` (private) and `~/.ssh/id_rsa.pub` (public).
- Optionally set a **passphrase** for added security.

🧠 **Note**: The `.ssh/` directory and its keys must have correct permissions:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```

---

### 🚀 Task 2: Copy Public Key to Remote Server

There are two options:

---

### ✅ **Option 1: Using `ssh-copy-id`**

```bash
ssh-copy-id username@remote_host
```

- Automatically appends your public key to the remote user’s `~/.ssh/authorized_keys` file.
- Sets proper file permissions automatically.

---

### ✅ **Option 2: Manual Copy**

```bash
rsa.pub
```

1. Copy the output manually.
2. SSH into remote server:

```bash
ssh username@remote_host
```

1. On the remote server:

```bash
mkdir -p ~/.ssh
echo "your_copied_public_key" >> ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

---

### 🔑 Task 3: Login Without a Password

Once key is copied:

```bash
ssh username@remote_host
```

✅ If configured properly, no password will be asked.

---

### 📁 Important SSH File Summary

| File | Description | Permissions |
| --- | --- | --- |
| `~/.ssh/id_rsa` | Private key (Keep secret) | 600 |
| `~/.ssh/id_rsa.pub` | Public key (Shareable) | 644 |
| `~/.ssh/authorized_keys` | List of accepted public keys | 600 |
| `~/.ssh/config` | Optional SSH client config file | 644 |

---

### 🧩 Optional: Using a Specific Identity File

```bash
my_custom_key username@remote_host
```

---

### 🖊️ Set Default SSH Editor (if needed)

To ensure you use your preferred editor (e.g., `vim`) with SSH or crontab:

```bash
export VISUAL=vim
export EDITOR=vim
```

---

### 🧠 Pro Tip: SSH Config File for Easier Commands

Create or edit:

```bash
vim ~/.ssh/config
```

Example config:

```bash
Host myserver
    HostName 192.168.1.50
    User admin
    IdentityFile ~/.ssh/id_rsa
```

Now you can simply do:

```bash
ssh myserver
```

### 🔥 **Firewall in Linux: Overview**

---

A **firewall** controls incoming/outgoing network traffic by allowing or blocking specific connections. On Linux, common firewall tools include:

| Tool | Common On | Description |
| --- | --- | --- |
| **UFW** | Debian/Ubuntu | Simplified wrapper for `iptables`. User-friendly. |
| **firewalld** | RHEL, CentOS, Fedora | Modern, zone-based firewall. Uses `iptables`/`nftables` underneath. |
| **iptables** | All distros | Low-level packet filter framework. Powerful but complex. |

---

### ✅ **UFW – Uncomplicated Firewall (Debian/Ubuntu)**

### 📌 Enable & Check Status

```bash
sudo ufw enable           # Enables firewall
sudo ufw disable          # Disables firewall
sudo ufw status           # Check current firewall rules
```

### 📌 Allow or Deny Traffic

```bash
sudo ufw allow ssh                  # Allow SSH (port 22)
sudo ufw allow 80/tcp               # Allow HTTP
sudo ufw allow from 192.168.1.0/24  # Allow subnet
sudo ufw deny 23                    # Deny Telnet
sudo ufw delete allow 80/tcp        # Remove rule
```

### 📌 Application Profiles

```bash
sudo ufw app list                  # Show known apps
sudo ufw allow "Apache Full"       # Allow predefined app profile
```

---

### 🔥 **firewalld (RHEL, CentOS, Fedora)**

### 📌 Basic Commands

```bash
sudo systemctl start firewalld
sudo systemctl enable firewalld
sudo firewall-cmd --state           # Check if running
```

### 📌 Manage Zones

Zones define trust levels for network interfaces (public, internal, dmz...).

```bash
sudo firewall-cmd --get-active-zones
sudo firewall-cmd --zone=public --add-interface=eth0
```

### 📌 Open Ports

```bash
sudo firewall-cmd --zone=public --add-port=80/tcp --permanent
sudo firewall-cmd --reload         # Apply changes
```

### 📌 Allow Services

```bash
sudo firewall-cmd --zone=public --add-service=http --permanent
```

---

### ⚙️ **iptables (Advanced & Scriptable)**

Use when you want **fine-grained** control or if firewalld/ufw are not available.

### 📌 Common Rules

```bash
sudo iptables -L                         # List current rules
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT   # Allow SSH
sudo iptables -A INPUT -j DROP           # Drop all other incoming
```

### 📌 Save Rules

```bash
sudo iptables-save > /etc/iptables/rules.v4   # Debian/Ubuntu
sudo service iptables save                    # RHEL
```

### 📌 Reset Rules

```bash
sudo iptables -F     # Flush all rules
```

---

### 🧠 Summary

| Use When... | Tool |
| --- | --- |
| You want simple CLI firewall | `ufw` |
| You're on RHEL/CentOS/Fedora | `firewalld` |
| You want low-level control | `iptables` |

### **Secure File Deletion Using `shred`**

## ' Task 1: Understand Normal Deletion '

### ❌ **Why Regular `rm` or Delete Isn’t Secure**

When you run:

```bash
rm sensitive.txt
```

It does **not** remove the file's actual contents. Instead:

- It **removes the pointer** to the file in the file system (like erasing the file name from a table of contents).
- The actual **data blocks** stay on disk until overwritten.
- Recovery tools can read that leftover data and **recover the file**.

---

## : ' Task 2: How Files Can Be Recovered '

### 🔁 **Steps Tools Use to Recover Deleted Data**

1. **Scan disk sectors** for orphaned data blocks.
2. Tools like:
    - `testdisk`
    - `photorec`
    - `extundelete` (for ext3/ext4)
3. Recover files that have no directory reference but still live on disk.

---

## : ' Task 3: Use `shred` to Securely Delete Files '

### 🛡️ What `shred` Does:

- Overwrites file content **multiple times with random data**.
- Then **optionally deletes the file**.
- Makes file recovery **virtually impossible**.

---

### ✅ **Basic Command**

```bash
shred -u filename.txt
```

- `u`: Truncates and removes the file after shredding.

---

### 🔁 **With Multiple Overwrites (for More Security)**

```bash
shred -n 5 -u filename.txt
```

- `n 5`: Overwrite 5 times (default is 3, higher is safer).
- `u`: Delete after overwriting.

---

### 🔒 **Force overwrite and hide shred patterns**

```bash
shred -n 5 -z -u filename.txt
```

- `z`: Adds a final overwrite with zeros (to hide that shredding was done).

---

### 📁 **Example in a Secure Deletion Script**

```bash
#!/bin/bash
file="$1"
if [ -f "$file" ]; then
    shred -n 5 -z -u "$file"
    echo "File securely deleted."
else
    echo "File not found."
fi
```

Run it with: `bash secure_delete.sh myfile.txt`

---

## ⚠️ **Limitations of `shred`**

- Works best on **regular files in non-journaled file systems** (like ext2/ext3).
- Less effective on:
    - SSDs (because of wear leveling)
    - Files on journaling FS (ext4, XFS) or copy-on-write (like Btrfs)
    - Files in cloud or remote storage

---

## 🔒 **Best Practice**

For SSDs or cloud: Use **full disk encryption** + discard keys.