# Regular Expression (Regex)
 - Regular expressions are symbolic notations used to identify patterns in text. 
 - Regular expressions are supported by many command line tools and most programming languages for text manipulation purposes.

## Regex using Grep 
- <code>grep</code> - grep searches text files for input patterns and outputs any matches to the standard output. 
- Regex can be used for pattern matching with grep 
- Below are simple use cases 
    ```bash
    dev@dev: cat TEST
    apple
    pear
    orange 
    pineapple
    watermelon
    car
    
    ## grep for word car in the file TEST
    dev@dev grep car TEST
    
    ## grep for word car in all files in the working directory
    dev@dev grep car *
    TEST:car
    ```

## Regex Syntax 
- In additional searching files using direct strings, A Regex pattern consists of one or more character literals, operators, or constructs. 

    | Character Class | Description |
    | --------------- | -------------- |
    | [:alnum:]       | Matches any alphanumeric character |
    | [:alpha:]       | Matches any alphabetic character   |
    | [:digit:]       | Matches any numeral                |
    | [:lower:]       | Matches any lowercase letter       |
    | [:upper:]       | Matches any uppercase letter       |
    
    &nbsp; &nbsp; **Table 3.1** - Startup Files for Non-Login Shell Sessions
