# Redirection & Pipeline
- The shell has the ability to redirect input and output of commands to and from files, as well as connect multiple commands together into command pipelines.  
- Standard streams consist of standard input, output, and error, which are the communication channels between a program and its environment. 
    - **Standard input (stdin)**: A stream which a program reads input. By default, it is connected to the keyboard, but it can be redirected to read from files or other sources.
    - **Standard output (stdout)**: A stream which a program writes its output. By default, it is connected to the terminal, but similar to stdin, it can be redirected to write to files or other destinations. 
    - **Standard Error (stderr)**: A stream which a program write its error messages and diagnostic output. By default, it is connected to the terminal but can be redirected separately from stdout.

## Redirecting Standard Output 
- Redirection allows us to redefine where standard output goes. To redirect standard output to a file instead of the screen, use the <code>></code> redirection operator followed by the name of the file. 

    ```bash
    ## output to default stdout stream, to terminal 
    dev@dev: cat TEST 
    apple
    pear
    orange 
    pineapple
    watermelon
    ...

    ## change the stdout to a file 
    dev@dev: cat TEST > TEST_output
    dev@dev: cat TEST_output
    apple
    pear
    orange 
    pineapple
    watermelon
    ...
    ```

## Redirecting Standard Error 
- To redirect standard error, we must refer to the file descriptor. 
- The file descriptor for standard input, output, and error streams is 0, 1, and 2 respectively. 
- Shell provides a notation for redirecting files using the file descriptor number. 
- A program can produce output on any of several numbered file streams which means that standard output and error can be redirected together. 

    ```bash
    ## testing stderr using a non-existent file
    ## the file descriptor "2" is placed before the redirection operator to perform the redirection of standard error
    dev@dev: cat test 2> TEST_error
    cat: test: No such file or directory
    
    ## redirecting standard output and standard error to one file
    ## first redirect standard output using '>' then redirect standard error using '2>&1' 
    dev@dev: cat test > TEST_error 2>&1

    ## another notation for combined redirection 
    dev@dev: cat test &> TEST_error
    cat: test: No such file or directory

    ## suppress error or output message
    ## /dev/null is a file that accepts input and does nothing with it
    dev@dev: cat test &> /dev/null
    ```

## Redirecting Standard Input 
- The <code>cat</code> accepts standard input with <code><</code> operator. With <code><</code> operator, it is possible to change the standard input from the keyboard to a file. 

    ```bash
    dev@dev: cat < TEST 
    apple
    pear
    orange 
    pineapple
    watermelon
    ...    
    ```

## Pipelines
- Pipelines provide the ability to pass standard output of one command into the standard input of another command. 
- Pipelines are used to pass data from one command to another while redirection occurs between a command and a file.

```bash
    ## pass standard output from echo command to cut command 
    dev@dev: echo "123456789" | cut -c 1-5
    12345

    ## pass standard output from cat command to grep command 
    dev@dev: cat TEST | grep car
    car
```