# Exotica - Other Useful Concepts in Bash
 - Below are some interesting topics in Bash.
    - [Grouping Commands](#grouping-commands---group-command)
    - [SubShell](#subshell---grouping-commands)
    - [Exit Status](#exit-status)
    - [Control Operators](#control-operators)
## Grouping Commands - Group Command
 - Bash allows commands to be grouped together, allows results of several commands into a single stream which is helpful when working with redirection and pipelines.
 - This can be achieved using the group command which is represented by braces - `{}`.
 - Syntax of group command below:
    
    ```bash
    { commands; command1; command2; ...}

    ## Note: there will need to be a white space after and before each brace and each command needs to be separated with semi colon 
    ```

- Example of grouping commands:

    ```bash
    ## write data to output.txt without group command
    dev@dev: ls -l > output.txt
    dev@dev: echo "Hello World!" >> output.txt
    dev@dev: cat /etc/passwd >> output.txt 
    

    ## write data to output.txt using group command
    ## combines all the output of three different commands into one steam and using redirection to write into output.txt file
    dev@dev: { ls -l; echo "Hello World!"; cat /etc/passwd; } >> output.txt
    ```

## SubShell - Grouping Commands
 - Another way to group commands together in Bash is using SubShell.
 - As name suggests SubShell execute all its commands in a child copy of the current shell whereas a group command executes all of its commands in the current shell.
 - For SubShell the environment is copied and given to a new instance of the shell and when the SubShell exits, the copy of the environment is lost so any changes made to the SubShell's environment are lost. 
 - In most cases group command is preferable since is faster and requires less memory.
 - Syntax of SubShell below:

    ```bash
    (commands; command1; command2; ...)

    ## Note: syntax for SubShell is more lenient, no need for white space before and after the curly brackets.
    ```   

 - Example below:
    
    ```bash
    ## example on grouping commands using SubShell
    dev@dev: (ls -l; echo "Hello World!"; cat /etc/passwd) >> output.txt

    ## example on SubShell properties
    dev@dev: { var=1; echo $var; }
    1
    dev@dev: echo $var
    1
    dev@dev: (var=2; echo $var) ## SubShell only modified the value in the new SubShell
    2 
    dev@dev: echo $var ## thus the value is still 1
    1
    ``` 

## Exit Status 
 - Commands including scripts and shell function returns a value to the system when they terminate called an exit status. 
 - This value indicates the success or failure of the command's execution.
 - Exit status value ranges from 0 - 255, by convention a value of zero indicates success and any other value indicates failure. 
 - The shell provides a parameter that can be used to examine the exit status - `$?`.
 - Example below:
    
    ```bash
    dev@dev: ls -d /usr/bin ## this command executed without any error
    /usr/bin
    dev@dev: echo $? ## thus returns 0 as exit status
    0 
    
    dev@dev: ls -d /bin/usr ## this command executed with error 
    ls: cannot access /bin/usr: No such file or directory
    dev@dev: echo $? ## thus return non zero exit status
    ```

## Control Operators
 - Bash provides two control operators that can perform branching. 
 - The `&&` (AND) and `||` (OR) operators work like the logical operators in the test command.
 - The control operators allows multiple commands to be executed in series if conditions are met.
 - Syntax below:
    
    ```bash
    ## command2 will be executed only command1 executed successfully 
    command1 && command2

    ## command 2 will be executed even if command1 executed unsuccessfully
    command1 || command2
    ```
- Examples below:

    ```bash
    ## second command failed to execute due to first error from the first command
    dev@dev: cat /etc/shadow && ls
    cat: /etc/shadow: Permission denied

    ## second command get to execute regardless of the error from the first command
    dev@dev: cat /etc/shadow || ls
    Downloads Desktop ...
    ```