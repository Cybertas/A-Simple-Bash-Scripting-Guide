# The "Get Help" Commands
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
# Other Useful Commands
## Command - (cd)

## Command - (ls)

## Command - (echo)

## Command - (rm)

## Command - (pwd)