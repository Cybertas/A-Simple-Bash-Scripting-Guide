# Globbing (Wildcard)
 - Wildcard can be used to match pattern with strings. <br>

    | Wildcard     | Description |
    | --------------  | -------------- |
    | *            | Matches any characters |
    | ?            | Matches any single character |
    | [Characters] | Matches any character that is a member of the set characters |
    | [!Characters]| Matches any character that is not a member of the set characters |
    | [[:Character Class:]]  | Matches any character that is a member of the specified class |

    **Table 1.1** - Wildcard and their meaning

    | Character Class | Description |
    | --------------- | -------------- |
    | [:alnum:]       | Matches any alphanumeric character |
    | [:alpha:]       | Matches any alphabetic character   |
    | [:digit:]       | Matches any numeral                |
    | [:lower:]       | Matches any lowercase letter       |
    | [:upper:]       | Matches any uppercase letter      |
    
    **Table 1.2** - Character Classes and their meaning 

   </br>

 - Below are examples of Globbing. 

    ```bash
    dev@dev: ls 
    file1 file2 file3 File4 TEST log.txt

    ## matching everything 
    dev@dev: echo *
    file1 file2 file3 File4 TEST

    ## matching any single characters
    dev@dev: echo ????
    TEST

    ## matching anything that has .txt as suffix
    dev@dev: echo *.txt
    log.txt

    ## matching any file that starts with the letter f
    dev@dev: echo [f]*
    file1 file2 file3 

    ## matching any file beginning with uppercase 
    dev@dev: echo [[:upper:]]*
    TEST
    ```


 

