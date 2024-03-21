# Flow Control: For Loop
  - For loop is a way to execute a command over a number of times based on a condition. 
  - In Bash for loop takes two forms, one is iterating through a list of items similar to `for in` in python while the other one is iterating through numbers for example starting from 0 and increment by 1 and ending with upper limit. 
- Below is syntax of for loop in Bash.

    ``` bash
    for [ CONDITION ]; do
        COMMANDS
    done; 
    ```
- `for` evaluates the CONDITION and if CONDITION is true then execute COMMANDS.
- After COMMANDS have been executed `for` moves on to the next loop which then goes back to evaluate the CONDITION.
- The loop will be terminated if the CONDITION is false.

## For Loop - Iterating Through List of Items
- Using `for in` is similar to python `for in` loop where the loop iterates through all items in an array for instance.
- The number of time that the for loop will run depends on the total items in a list of items.
- Within each loop commands can be executed to perform some work. 
- Below is example on iterating through an array using for in. 
        
    ```bash
    ## form 1:
    for variable [in words]; do 
        commands
    done
    ## where variable represents a single item in words and words can be an array or a file containing lines of array
    ## commands is the command that will be executed in every iteration

    ## example 
    ## array that contains 7 elements
    days=([0]=Mon [1]=Tue [2]=Wed [3]=Thu [4]=Fri [5]=Sat [6]=Sun)

    ## for each element in the array execute the command echo
    for day in ${days[@]}; do
        echo $day;
    done

    Mon
    Tue
    Wed
    Thu
    Fri
    Sat
    Sun
    ```

## For Loop - Iterating Through Numbers
- Iterating through numbers in Bash is similar to for loops in C which has a starting number and an upper limit then it increments or decrements until the the limit is reached. 
- When iterating through an array the elements are accessed by index. 

    ```bash
    ## form 2:
    for (( expression1; expression2; expression3 )); do
        commands
    done

    ## example with numbers
    ## declares the starting number of the loop, in this case loop starts with 0
    ## then checks if i is less then 5 if not i + 1
    ## if i is 5 or greater then done
    for (( i=0; i<5; i++ )); do
        echo "loop: ${i}" 
    done


    ## example using array
    days=([0]=Mon [1]=Tue [2]=Wed [3]=Thu [4]=Fri [5]=Sat [6]=Sun)

    for(( i=0; i<7; i++ ));do
        echo ${days[$i]}
    done

    Mon
    Tue
    Wed
    Thu
    Fri
    Sat
    Sun
    ```

