# Functions
 - Shell functions can be used to break the script down into modular pieces. 
 - In other words, they are mini scripts that are located inside a script and can act as autonomous programs. 
 - Shell function syntax: 
    
    ```bash
    ## there are two types of syntax
    # 1. More formal form
    function name{
        commands
        return
    }
    # 2. More preferred form
    name(){
        commands
        return
    }
    ```

## Function Examples
- More examples on [Functions](./_Functions%20Exmaples.md) and below is an example on function: 

    ```bash
    #!/bin/bash 
    ## a custom function to add a new user
    ## first will ask user to enter a new user name and check if exists
    ## if user does not exist then create a user and generate a password file in the working directory 
    addUser(){
        echo "Creating new user..."
        read -p "Please enter username: " username
        if  id "$username" &> /dev/null; then ## check if username has been used
            echo "User $username exists, please try a new username" 
        else ## create user
            ## add user account with home directory 
            useradd "$username" -m
            echo "$username has been created"

            ## set user password
            passwd=$username
            passwd+=$RANDOM 
            passwd=$(echo $passwd | md5sum | cut -c 1-32)
            echo "$username:$passwd" | chpasswd	
            echo $passwd > password.txt
            echo "Password has been generated, please check the password.txt file at working directory" 
        fi	
    }

    main(){
        ## calling function from main
        addUser
    }

    ```