# Flow Control: While and Until Loop
 - While loop is similar to for loop the difference is that typically a while loop iterate on a boolean value (true or false) and for loop iterate through numbers or list of items. 

 - Below is syntax on while loop:
    
    ```bash
    while [ CONDITION ]; do
        COMMANDS
    done
    ```
- `while` evaluates the CONDITION and if CONDITION is true then execute COMMANDS
- After COMMANDS have been executed while moves on to the next loop which then goes back to evaluate the CONDITION.
- The loop will be terminated if the CONDITION is false.

## Examples on While Loop
- While loop can be constructed in a way to work like a for loop.

    ```bash
    ## display a series of numbers
    count=1
    while [[ "$count" -le 5 ]]; do
        echo "$count"
        count=$((count + 1))
    done
    echo "Finished."
    ```

- While loop that terminates on false. 

    ```bash
    ## displays a message using while
    bool=true
    while $bool; do
        echo "Hello World."
        bool=false
    done
    ```

## Breaking Out a Loop
 -  There are two built-in commands to control program flow inside loop `break` and `continue`.
 - The `break` command immediately terminates the loop and moves to the next command in the script.

    ```bash
    ## example on break
    ## display a series of numbers
    ## break command will stop the loop at first iteration
    count=1
    while [[ "$count" -le 5 ]]; do
        echo "$count"
        count=$((count + 1))
        break
        done
    echo "Finished."
    ```

 - The `continue` command will ignore the rest of the loop and move on to the next loop.

    ```bash
    ## example on continue
    ## display message on every loop
    count=1
    while [[ "$count" -le 5 ]]; do
        count=$((count + 1))
        ## if count is 3 then we will skip this loop
        ## anything else after this if statement in the loop will not run
        if [[ $count -eq 3 ]]; then
            continue
        fi
        ## this command will not be executed when loop is 3
        echo "this is loop number:  ${count}"
        
        done
    echo "Finished."
    ```

 ## Until Loop 
 - The until loop is much like while loop however it continues the loop when the condition is false and loop terminates when the condition is true.
 - Below is example on until loop
    
    ```bash
    # until-count: display a series of numbers
    count=1
    until [[ "$count" -gt 5 ]]; do
        echo "$count"
        count=$((count + 1))
    done
    echo "Finished."
    ```