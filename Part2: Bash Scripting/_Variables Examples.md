## Local Variable in Function
 - Below is example on Local vs Global variables.
 - Content of a script file below: 
    ```bash
    #!/bin/bash
    # local-vars: script to demonstrate local variables
    foo="This is global variable" # global variable foo

    funct_1 () {
        local foo # variable foo local to funct_1
        foo=1
        echo "local variable from function1: foo = $foo"
    } 

    funct_2 () {
        local foo # variable foo local to funct_2
        foo=2
        echo "local variable from function2: foo = $foo"
    }

    echo "global: foo = $foo"
    funct_1
    echo "global: foo = $foo"
    funct_2
    echo "global: foo = $foo"
    ```
- Result of script below: 
    
    ```bash
    global: foo = This is global variable
    funct_1: foo = 1
    global: foo = This is global variable
    funct_2: foo = 2
    global: foo = This is global variable
    ```

## Here Documents
 - Here Documents (Here Doc) A form of I/O redirection allows us to embed a body of text in a script and pass it to the standard input of a command. 
 - Syntax of Here Doc: </br>
    **&nbsp; Command << token </br>**
    **&nbsp; <=== text ===> </br>**
    **&nbsp; token**
- Command: Command is the name of command that accepts standard input 
- Token: Token is a string used to indicate the end of the embedded text. 

    ```bash
    #!/bin/bash

    cat << _EOF_
        <html>
            <head>
                <title>"This is a test page"</title>
            </head>
            <body>
                <h1>**Hello World**</h1>
            </body>
        </html>
    _EOF_
    ```

- Result of script below: 
    
    ```bash
    <html>
        <head>
            <title>"This is a test page"</title>
        </head>
        <body>
            <h1>**Hello World**</h1>
        </body>
    </html>
    ```