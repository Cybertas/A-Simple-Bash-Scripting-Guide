## Array Operations Example    

### Append New Element
 - Appending new element to an array:

    ```bash
     ## add element to array, to the end
    dev@dev: my_array=(1 2 3)
    dev@dev: my_array+=(4)
    dev@dev: echo ${my_array[@]}
    1 2 3 4 
    ```

### Remove Array Element
- Remove an element from an array:

    ```bash
    ## remove an element from an array
    dev@dev: my_array=(1 2 3 4)
    dev@dev: unset my_array
    dev@dev: echo ${my_array[@]}
    1 3 4 
    ```

### Slicing Array
 - Slicing an array:

    ```bash
    ## slice an array
    dev@dev: my_array=(1 2 3 4 5)
    dev@dev: my_array+=(4)
    dev@dev: echo ${my_array[@]:1:3}
    2 3 4
    ```

### Joining Elements in Array 
 - Joining elements in array to a string:

    ```bash
    ## join elements to a string
    dev@dev: my_array=("Hello" "World")
    dev@dev: result=$(IFS=' '; echo "${my_array[*]}") ## where IFS is delimiter in the shell environment
    dev@dev: echo "$result"  
    Hello World
    ```


### Sorting Array elements 
 - Sort elements in an array:

    ```bash
    ## sort array element
    dev@dev: my_array=(3 1 4 2)
    dev@dev: sorted_array=($(printf "%s\n" "${my_array[@]}" | sort -n))
    dev@dev: echo "${sorted_array[@]}" 
    1 2 3 4
    ```

### Deleting Array
 - Delete an array:

    ```bash
    ## delete an array
    dev@dev: my_array=(1 2 3 4)
    dev@dev: declare -p my_array
    declare -a my_array=([0]="1" [1]="2" [2]="3" [3]="4" [4]="5")
    dev@dev: unset my_array
    dev@dev: declare -p my_array
    bash: declare: my_array: not found
    ```