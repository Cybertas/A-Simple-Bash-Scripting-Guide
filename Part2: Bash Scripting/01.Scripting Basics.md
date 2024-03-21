# Scripting - Bash Scripting Basics
- A shell script is a file containing a serious of commands. 
- The shell reads a script file and carries out the commands as though been entered directly to the command line. 
- Shell acts as a command line interface to the underlying system and a scripting language interpreter. 

## Writing a Shell Script 
- Writing a bash script will require consideration on below: 
    - Script Format
    - Script Permission
    - Script Location

## Script Format 
 - A Bash script should contain an interpreter declaration (shebang) and Bash file extension (.sh). 
 - `#!` - shebang: the shebang construct is used to tell the kernel the name of the interpreter that should be used to execute the script that follows. Every shell script should include this as its first line.
 - `.sh` - Bash extension: Helps with organization and readability. 

    ```Bash
    ## example of content script file 
    #!/bin/Bash - shebang
    echo "Hello from script" - command
    ```

## Script Permission
 - In order to run a script, the file must be executable. 
 - For more details on file permission - [Permission](../Part1:%20Working%20With%20Bash%20Shell/06.Permissions.md)

    ```Bash
    ## script file permission 
    dev@dev: ls -l script.sh
    -rwxrwxr-x 1 dev dev 13 Mar 11 18:07 /usr/bin/test.sh
    ```


## Script Location 
 - Bash script can be executed by calling the file via absolute or relative filepath. 
 - Bash script can also be executed by calling the name of the file directly. However the the file needs to be placed in a directory listed in the PATH environment variable. 
    - PATH environment variable contains a list of directory that the system searches for executable programs. 

    ```Bash
    ## view directories stored in the PATH environment variable
    dev@dev: echo $PATH 
    /home/me/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    
    
    ## calling script in working directory 
    dev@dev:./script.sh
    Hello from script

    ## calling script that is in a directory in the PATH environment variable
    dev@dev: script.sh
    Hello from script
    ```
 