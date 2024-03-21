## Flow Control: Branching With Case 
 - In Bash, multiple-choice compound command is called case.
 - Instead of using `if` command to check for user input the `case` command provides an easier way to interact with a set of commands based on fixed user inputs. 
 - It has below syntax:
  
    ```bash
    case WORD in
        PATTERN) 
            COMMANDS
        ;;
        PATTERN) 
            COMMANDS
        ;;
        ...
    ```
 - `case` is the command and WORD is user input where it is used to matched against PATTERN. 
 - COMMANDS are the commands that are going to executed when the WORD matches with the specific PATTERN.

## Example on Case
- Below is a script displays system information based on user input using case.
    ```bash
    #!/bin/bash
    # case-menu: a menu driven system information program
    
    read -p "Enter selection [0-3] > "
    case "$REPLY" in
    0) echo "Program terminated."
    exit
    ;;
    1) echo "Hostname: $HOSTNAME"
    uptime
    ;;s
    2) df -h
    ;;
    3) echo "Working Directory: $PWD"
    ;;
    *) echo "Invalid entry" >&2
    exit 1
    ;;
    esac
    ```
- Below is a script that incorporated while which allows user to continuously enter options to displays system information.
    ```bash
    ## incorporated while, allows user to continuously to enter an option
    bool=true
    while $bool; do
        echo "
        Please Select:
        A. Display Hostname
        B. Display Disk Space
        C. Display Home Directory
        Q. Quit
        " 
        read -p "Enter selection [A, B, C or Q] > " 
            case "$REPLY" in
            q|Q) echo "Program terminated."
            bool=false
            exit
            ;;
            a|A) echo "Hostname: $HOSTNAME"
            uptime
            ;;
            b|B) df -h
            ;;
            c|C) echo "Working Directory: $PWD"
            ;;
            *) echo "Invalid entry" >&2
            bool=false
            exit 1
            ;;
            esac
    done
    ```

## Multiple Matches with Case
 - If you would like to match multiple patterns in case, use `;;&` instead of `;;` see below example: 

    ```bash
    ## check 
    read -n 1 -p "Type a character > "
    echo
    case "$REPLY" in
    [[:upper:]]) echo "'$REPLY' is upper case." ;;&
    [[:lower:]]) echo "'$REPLY' is lower case." ;;&
    [[:alpha:]]) echo "'$REPLY' is alphabetic." ;;&
    [[:graph:]]) echo "'$REPLY' is a visible character." ;;&
    esac

    ##output
    'a' is lower case.
    'a' is alphabetic.
    'a' is a visible character.
    ```