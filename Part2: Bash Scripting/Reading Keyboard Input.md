# Reading Keyboard Input
 - In Bash, the built-in `read` command can be used to read a single line of standard input. It can be used to read keyboard input or take redirection from a file.
 - Syntax: read [-options] [variables]
    - `options` : additional options for the read command - [Read Options Table](./_Reading%20Keyboard%20Input%20Examples.md#Options%20Read%20Command)
    - `variable` : variable(s) to store inputs
    - `REPLY`: if no variables are listed after the read command, a shell variable REPLY will be assigned with all inputs.
    - For more examples - [Reading Keyboard Input Examples](./_Reading%20Keyboard%20Input%20Examples.md#read%20command%20examples)

    ```bash
    ## -- a script that takes user inputs
    #!/bin/bash

    basicInput(){
        echo -n "Enter input: " ## echo -n allows input to be on the same line as the output
        read inp ## inp is the variable that stores the user input
        echo "this is the input: $inp"

        ##input: hello
        ##output: this is the input: hello
    }


    multipleInputs(){
        echo -n "Enter one or more inputs: " ## echo -n allows input to be on the same line as the output
        read inp1 inp2 inp3 ## stores keyboard inputs in three variables
        echo "this is the input: $inp1 $inp2 $inp3"

        ##input: 1 2 3 
        ##output: this is the input: 1 2 3
    }


    readDefaultValue(){
        echo -n "Enter one or more values: "
        read
        echo "REPLY = '$REPLY'"

        ##input: hello
        ##output: REPLY = hello 
    }

    readPrompt(){
        ## -p option 
        read -p "Enter one or more values: " inp1 inp2 inp3
        echo "this is the input: $inp1 $inp2 $inp3"
        ##input: 1 2 3 
        ##output: this is the input: 1 2 3
    }

    ## uncomment below to test functionality
    #basicInput 
    #multipleInputs
    #readDefaultValue
    #readPrompt 
    ```
    
