** Need a navigation table, large file
** practice website - https://regexr.com/


# Regular Expression (Regex)
 - Regular expressions are symbolic notations used to identify patterns in text. 
 - Regular expressions are supported by many command line tools and most programming languages for text manipulation purposes.

## Regex using Grep 
- <code>grep</code> - grep searches text files for input patterns and outputs any matches to the standard output. 
- Regex can be used for pattern matching with grep.
- Below are simple use cases: 
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

    | Metacharacters | Description |
    | --------------- | -------------- |
    | .               | Matches any single character |
    | ^               | Matches a character at the start of a line (Anchor)          |
    | $               | Matches a character at the end of a line (Anchor)          |
    | [character]     | Matches any single character in the bracket           |

    
    &nbsp; &nbsp; **Table 3.1** - Regex Metacharacters

    | Character Class | Description |
    | --------------- | ---------------------------------- |
    | [:alnum:]       | The alphanumeric characters, [A-Za-z0-9]       |
    | [:word:]        | Same as [:alnum:] with addition of underscore (_)    |
    | [:alpha:]       | The alphabetic characters, [A-Za-z]          |
    | [:blank:]       | Includes the space and tab character         |
    | [:cntrl:]       | The ASCII control codes            |
    | [:digit:]       | The numerals 0 - 9                 |
    | [:graph:]       | The visible characters             |
    | [:lower:]       | The lowercase letters              |
    | [:punct:]       | The punctuation characters, [-!"#$%&'()*+,./:;<=>?@[\\\]_`{|}~]                             |
    | [:print:]       | Same as [:space:] plus the space character         |
    | [:space:]       | Contains whitespace characters including space, tab, carriage return, newline, vertical tab and form feed, [ \t\r\n\v\f]                       |
    | [:upper:]        | The uppercase characters          |
    | [:xdigit:]       | Character used to express hexadecimal numbers, [0-9A-Fa-F]                       |

    &nbsp; &nbsp; **Table 3.2** - Regex Character Classes 

    | Quantifiers     | Description |
    | --------------- | -------------- |
    | ?               | Match an Element Zero or One time  |
    | *               | Match an Element Zero or More time |
    | +               | Match an Element One or More       |
    | {}              | Match an Element a Specific number of Times          |
    
    &nbsp; &nbsp; **Table 3.2** - Regex Character Classes 

## Regex Examples 
 - Using the TEST file in test_dir for Regex practice. 
    ```bash
    dev@dev: cat TEST
    apple
    pear
    orange 
    pineapple
    watermelon
    banana
    car

    ## Dot
    dev@dev: grep '.a.' TEST
    pear
    orange 
    pineapple
    watermelon
    banana
    PEACH
    LEMON
    car

    ## Anchors 
    dev@dev: grep '^apple' TEST
    apple

    dev@dev: grep 'apple$' TEST ## find word apple where it occurs at the end of the line
    apple
    pineapple 

    ## Bracket Expressions
    dev@dev: grep '[abc]a' TEST
    banana
    car

    dev@dev: grep '[^abc]a' TEST ## negation, first character in bracket expression is ^
    pear
    orange 
    pineapple
    watermelon
    banana

    ## Character Classes
    dev@dev: grep '^[[:upper:]]*$' TEST ## find string with all uppercase
    PEACH
    LEMON

    ## Quantifiers
    dev@dev: grep -E '\b[a-z]{3}\b' TEST ## -E enables extended regular expression, allows the use of quantifiers 
    car

    ```