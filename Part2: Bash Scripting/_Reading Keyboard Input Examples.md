### Options Read Command
- Below are the options for the read command

    | Option | Description |
    | -------------------------------- | -------------------------------- |
    | -a <em>array</em> | Assign the input to an array.                   |
    | -d <em>delimiter</em>            | The first character in the string is used to indicate the end of input instead of a newline character.     |
    | -e                               | Use Readline to handle input which permits input editing in the same manner as the command line.                       |
    | -i <em>string</em>               | Use a string as a default reply if no input, require -e option.          |
    | -n <em>num</num>                 | Read a number of characters of input.                             |
    | -p <em>prompt</em>               | Display a message prompt for input.                             |
    | -r                               | Raw mode, do not interpret backslash characters as escapes.                           |
    | -s                               | Silent mode, do not echo characters to the display.                       |
    | -t <em>seconds</em>              | Timeout, terminate input after seconds with non-zero exit status if an input times out.                      |
    | -u <em>fd<em>                    | Use input from file descriptor fd, rather than standard input.        |
    

### Read Command Examples
 - Blow are examples on the options of the read command:

    ```bash
    ## the -a option
    dev@dev: read -a myArray
    Hi this is input
    dev@dev: echo $myArray
    Hi
    dev@dev: echo ${myArray[@]}
    Hi this is input

    ## the -d option
    dev@dev: read -d '/' myInp
    This # enter key
    is #enter key
    input/ #end input with custom delimiter /
    dev@dev: echo $myInp 
    This is input
    
    ## the -e option
    dev@dev: read -d '/' myInp
    Thiss^?^?/ ## read command reads in all input even when you enter delete, -e provides the ability edit 

    dev@dev: read -ed '/' myInp
    This/ ## doesnt capture delete 

    ## the i option
    dev@dev: read -ie "What is your name? default: $USER" myInp ## if you hit enter the value stored in myInp will be the string 
    What is your name? default: dev
    dev@dev: echo $myInp
    What is your name? default: dev

    ## you can customize the input as you wish
    dev@dev: read -ie "What is your name? default: $USER" myInp
    What is your name? My name is dev ## enter

    dev@dev: echo $myInp
    What is your name? My name is dev

    ## the n option
    ## read command exits when n length of input is met
    dev@dev: read -n 3 myInp
    yes
    dev@dev: echo myInp 
    yes 

    ## the p option
    dev@dev: read -p "What is your name?: " myInp
    What is your name?: dev ## prompts for input with string as message
    dev@dev: echo $myInp
    dev
    ```