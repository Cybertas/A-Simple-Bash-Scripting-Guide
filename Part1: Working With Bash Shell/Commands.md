# Commands - What are they?
- Commands can take several forms:
    - An executable program
    - A built-in command to the shell
    - A shell function
    - An alias of a command
- A command provides instructions to the underlying system to carry out specific tasks.
- Bash acts as an interface between a user and the operating system, allowing users to interact with the underlying system by executing commands in Bash.


## Options
- Commands often accept flags or options, which modify or provide additional features to the original command.
- Let's take the <code>ls</code> command as an example: by default, it lists the contents of the current directory.
- Additionally, the <code>ls</code> command accepts options that provide additional capabilities.
- To view all the options available for a command, use the <code>man</code> command.
- Below is a snippet of the <code>ls</code> command with additional flags:

    ```bash
    ## output directory contents in list format
    dev@dev: ls -l

    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file1
    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file2
    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file3

    ## output all directory contents in list format
    dev@dev: ls -la
    ```

## The "Get Help" Commands
- The "Get Help" commands are useful when you want to quickly learn about a command or understand its specific functionalities.
- <code>type</code>  
    - The 'type' command provides information on a name and how it is interpreted in the shell. 
    - It is able to distinguish alias, built-in command, external command, shell function, hashed command or a reserved word. 

    ```bash
    ## output from the type command
    dev@dev: type cd
    cd is a shell builtin

    dev@dev: type ls
    ls is aliased to 'ls --color=auto'

    dev@dev: type do
    do is a shell keyword
    ```
- <code>man</code> 
    - The <code>man</code> command displays manual pages for various commands, providing detailed information about their usage, options, and behavior.
     - While <code>man</code> does not directly display built-in commands, you can check under the Bash manual page for information on built-in commands.

    ```bash
    ## output from the man command
    dev@dev: man ssh
    NAME
     ssh — OpenSSH remote login client
    ...
    ```
- <code>help</code> 
    - The <code>help</code> command provides information about built-in shell commands. It is particularly useful for understanding the functionality of built-in commands.
    - You can use the <code>type</code> command to determine if a command is a built-in command and then use <code>help</code> to learn more about it.

    ``` bash
    ## output from the help command
    dev@dev: help cd
    cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
    ...
    ```

