# Quoting 
- Bash shell will expand certain keywords or characters thus quoting will prevent unwanted expansions 
    
    ```bash
    dev@dev: echo here is $100.00
    this is .00

    dev@dev: echo this is a line with big               space
    this is a line with big space
    ```

## Single Quotes 
- Anything that is place with the single quotes will lose their properties.

    ```bash
    dev@dev:echo 'this is $100.00'
    this is $100.00

    dev@dev:echo 'echo this is a line with big               space'
    this is a line with big               space
    ```

## Double Quotes 
- Most special characters used by the shell will lose their properties and are treated as ordinary characters
- With exception of ($), (\), (`)

    ```bash
    dev@dev: echo "this is $100.00"
    this is .00

    dev@dev: echo "show directory $(ls)"
    Desktop Documents Downloads ...
    ```

## Escaping Characters
- To unquote a special character use the (\) 
    ```bash
    dev@dev: echo "this is \$100.00"
    this is $100.00

    dev@dev: touch &file.txt
    touch: missing file operand
    ...

    dev@dev: touch \&file.txt && ls
    file.txt
    ```