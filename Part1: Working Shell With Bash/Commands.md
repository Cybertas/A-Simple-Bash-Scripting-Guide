# Commands - What are they?
- Commands can be:
    - An executable program
    - A built-in command to the shell
    - A shell function
    - An alias of a command
- A command provides instructions to the underlying system to carry out.
- Bash acts as an interface between a user and the operating system, whereby a user evokes commands in Bash to interact with the underlying operating system. 
- For a list of useful commands - [Commands Example](./_Commands%20Examples.md#other-useful-commands)
- Below is a snippet of a command (ls), which lists all files in the working directory. 

    ```bash
    #Note: Bash takes input literally meaning (Ls) does not equal to (ls)
    dev@dev: ls 

    file1 file2 file3

    dev@dev: Ls
    Ls: command not found
    ```

## Options
- Often commands accept flags or options, which modifies or provides additional features of the original command. 
- Below is a snippet of command (ls) with additional flag (-l).
- Lists all the files in the working directory with outputing the result as list format. 

    ```bash
    dev@dev: ls -l

    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file1
    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file2
    -rw-rw-r-- 1 dev dev 5 Jan 28 18:20 file3
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
    - The 'man' does not display built-in commands directly however you can check under the Bash manual page. 

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

