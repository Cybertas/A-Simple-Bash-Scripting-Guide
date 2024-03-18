# Variables in Bash
 - When shell encounters a variable it automatically creates it, no need to declare or define the variable. 
 - When shell encounters a new variable it gives a default value of nothing or empty. 

   ``` Bash
      dev@dev: echo $var

   ```

 ## Variables Naming Convention 
  - Below are some rules about variable names: 
    - Variable names may consist of alphanumeric characters and underscore characters. 
    - The first character of a variable name must be either a letter or an underscore. 
    - Spaces and punctuation symbols are not allowed. 
    - A common convention for constant declaration is to use uppercase letters.


 ## Variable Types
 - Bash provides a way to declare different data types for variable using the `declare` builtin command. 
 - Below are some common variable types in Bash:  
    - String 
    - Integer 
    - Constant 
    - Local 
    - Boolean
    - Array & Associate Array (Nested Array)


 ### String Variable Type
 - In Bash regardless the value assigned to a variable it will be considered as a string. 
 - Multiple variable assignments can be done in a single line.
 - Examples on string variable assignments:
    
    ```bash
    a=z # assign the string "z" to variable a.
    b="a string" # embedded spaces must be within quotes.
    c="a string and $b" # other expansions such as variables can be expanded into the assignment.
    d="$(ls -l foo.txt)" # assign results of a command.
    e=$((5 * 7)) # assign arithmetic expansion.
    ```

 ### Integer Variable Type 
 - To declare an integer variable in Bash use `declare -i`.
- However it is not necessary since Bash provides ways to work with integers in string format. 
 - Examples on string variable assignments:

    ```bash
    ## declare an integer variable
    dev@dev: declare -i num=10


    ## declare an integer as string
    dev@dev: var1=5
    dev@dev: var2=6
    dev@dev: echo $(($var2-$var1)) ## using arithmetic expansion
    1
    ```
 
 ### Constant Variable Type  
 - To declare a constant variable in Bash using the `declare` command use `declare -r`. 
 - It is also possible to declare a const variable following the naming standard where all letters are uppercase.
 - Examples on constant variable assignments:

    ```bash
    ## declare a constant variable following the naming convention 
    IP=192.168.0.0
    VAR="This is a constant variable" 

    ## declare a constant variable using the declare command
    dev@dev: declare -r CONST="Read Only" 
    dev@dev: CONST=123
    bash: CONST: readonly variable
    ```

 ### Boolean Variable Type 
 - While Bash doesn't have a Boolean type but variables can be used to store true/false values directly. 
 - Examples on string variable type:

    ```bash
    dev@dev: bool=true
    dev@dev: echo $bool
    true
    ```

 ### Local Variable Type 
 - To declare a local variable use the `local`.
 - Local variable are only accessible within the shell function in which they are defined and cease to exist once the shell function terminates. 
 - More details on [Functions]() & details example on [local variable](./_Variables%20Examples.md##local%20variable%20in%20function).
 - Examples on local variable type:

    ```bash
    ## to declare a local variable
    local var="This is a local variable"
    ```


 ### Array & Nested Array
 - Please visit the [Arrays](./Arrays.md) Page for more detail.


### Accessing Variable Values
 - To access the value assigned to a variable use `$`, more detail visit [Expansions - Parameter Expansion](../Part1:%20Working%20With%20Bash%20Shell/08.Expansion.md#%20Parameter%20Expansion).

### Checking Variable Types and Value
 - To check for the value and type of a variable use `declare -p`.

    ```bash
    ## checking a variable "CONST"
    dev@dev: declare -r CONST="Read Only" 
    dev@dev: declare -p CONST
    declare -r CONST="Read Only"
    
    ## checking a variable that hasn't been declared using declare 
    dev@dev: declare -p test
    bash: declare: test: not found
    ```

