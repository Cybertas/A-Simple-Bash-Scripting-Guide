# Commands - What are they?
- Commands can be:
    - An executable program
    - A built-in command to the shell
    - A shell function
    - An alias of a command
- A command provides instructions to the underlying system to carry out.
- Bash acts as an interface between a user and the operating system, whereby a user evokes commands in Bash to interact with the underlying operating system. 


## Options
- Often commands accept flags or options, which modifies or provides additional features of the original command. 
- Use the <code>ls</code> command as an example, the <code>ls</code> command lists contents of the current directory by default. 
- In addition, the <code>ls</code> command accepts options which provides additional capabilities.
- To list all the options of a command use the <code>man</code> command.
- Below is a snippet of the <code>ls</code> command with additional flags.

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
- The "Get Help" commands are helpful when you want to have a quick look at a command or you want to discern the specific of what a command can do.
- <code>type</code>  
    - The 'type' command provides information on a name and how it is interpreted in the shell. 
    - It is able to distinguish alias, built-in command, external command, shell function, hashed command or a reserved word. 

    ```bash
    dev@dev: type cd
    cd is a shell builtin

    dev@dev: type ls
    ls is aliased to 'ls --color=auto'

    dev@dev: type do
    do is a shell keyword
    ```
- <code>man</code> 
    - The 'man' command display the manual pages for various commands.
    - The manual pages provide detailed information about the usage, options and behavior. 
    - The 'man' does not display built-in commands directly however you can check under the Bash manual page for built-in commands. 

    ```bash
    dev@dev: man ssh
    NAME
     ssh — OpenSSH remote login client
    ...
    ```
- <code>help</code> 
    - The 'help' command provides information about built-in commands.
    - Can use 'type' to find out which type a command is if it is built-in commands then use 'help' to find more.

    ``` bash
    dev@dev: help cd
    cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
    ...
    ```

