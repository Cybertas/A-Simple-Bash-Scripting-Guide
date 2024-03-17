### Passing Positional Parameter to Functions
 - Below is an example on passing positional parameter to functions.
 - Content of script file

    ```bash
    #!/bin/bash
    # a script to demonstrate $* and $@
    print_params () {
    echo "\$1 = $1"
    echo "\$2 = $2"
    echo "\$3 = $3"
    echo "\$4 = $4"
    }
    pass_params () { 
    echo -e "\n" '$* :'; print_params $* ## using $* to expand the positional parameters
    echo -e "\n" '"$*" :'; print_params "$*" ## using "$*" to expand the positional parameters
    echo -e "\n" '$@ :'; print_params $@ ## using $@ to expand the positional parameters 
    echo -e "\n" '"$@" :'; print_params "$@" ## using "$@" to expand the positional parameters
    }
    pass_params "word" "words with spaces" ## passing in two positional parameters to function pass_params()
    ```
 - Output of script file

    ```bash
    dev@dev: ./script.sh
    $* : ## $* and $@ provides the same results where both expands into a list of positional parameters delimited by space.  
    $1 = word
    $2 = words
    $3 = with
    $4 = spaces

    $@ :
    $1 = word
    $2 = words
    $3 = with
    $4 = spaces

    "$*" : ## expands into one string containing all of the positional parameters 
    $1 = word words with spaces
    $2 =
    $3 =
    $4 =
    
    "$@" : ## expands into the original input
    $1 = word
    $2 = words with spaces
    $3 =
    $4 = 
    ```