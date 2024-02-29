# Shell Expansion 
- When shell receives a command, bash performs several processes upon the input before it carries out of the command.
- With expansion, when we type something and it is expanded into something else before the shell acts upon it.

- Below is the list of expansions:
    - [Pathname Expansion](#pathname-expansion)
    - [Tilde Expansion](#tilde-expansion)
    - [Arithmetic Expansion](#arithmetic-expansion)
    - [Brace Expansion](#brace-expansion)
    - [Parameter Expansion](#parameter-expansion)
    - [Command Substitution](#command-substitution)

## Pathname Expansion
- Bash supports three simple wildcards:
    1. &nbsp; \* &nbsp; - &nbsp; Matches any strings, including the null string.
    2. &nbsp; ? &nbsp; - &nbsp; Matches any single character.
    3. &nbsp; [...] &nbsp; - &nbsp; Matches any one of the enclosed characters.  
      <br />
    ```bash
    ## trying to match everything in the working directory with * character
    dev@dev: ls * 
    Desktop Documents Downloads ...


    ## create a file called '1' and match it with ? character
    dev@dev: touch 1 && echo ? 
    1 

    ## create files 1 123 a and match with case [123a]
    dev@dev: touch 1 123 a && echo [123a]
    1 a
    ```


## Tilde Expansion
- Tilde (~) represents your home directory in bash shell.

  ```bash
  ## change directly to your home directory 
  dev@dev: cd ~ && pwd
  /home/dev

  ## set your home directory to another directory 
  dev@dev: HOME=/home/dev/Desktop
  dev@dev: echo ~
  /home/dev/Desktop

  ## checking previous directory 
  dev@dev: pwd; cd ..
  /home/dev/Desktop
  dev@dev: echo ~-
  /home/dev/Desktop

  ## checking current directory 
  dev@dev: pwd
  /home/dev
  dev@dev: echo ~+
  /home/dev
  ```

## Arithmetic Expansion
- Numerical calculations using bash.
  - $(&nbsp;(&nbsp;expression&nbsp;)&nbsp;) &nbsp; 

  ```bash
    ## Addition - (+) 
    dev@dev: echo $((12+42))       ## output: 54

    ## Subtraction - (-)
    dev@dev: echo $((10-1))        ##output: 9
    
    ## Multiplication - (*) 
    dev@dev: echo $((2*2))         ##output: 4
    
    ## Division (Integer Only) - (/) 
    dev@dev: echo $((6/2))         ##output: 3
    
    ## Modulo - (%)
    dev@dev: echo $((9%3))         ##output: 0
    
    ## Exponentiation - (**)
    dev@dev: echo $((2**6))        ##output: 64
  ```

## Brace Expansion
- Manipulating strings and names using pattern.
  - {&nbsp; expression &nbsp;}
  - Patterns to be expanded may contain a prefix and suffix called preamble and postscript. 
  - The brace expression itself may contain either a comma-separated list of strings or a range of integers of single characters. 

  ```bash
  ## create 5 files from 1 to 5
  dev@dev: touch file{1..5} && ls
  file1 file2 file3 file4 file5 something.txt

  dev@dev: rm file{1..5} && ls
  something.txt

  dev@dev: touch prefix-{X,Y,Z}-suffix.txt
  prefix-X-suffix.txt prefix-Y-suffix.txt prefix-Z-suffix.txt
  ```

## Parameter Expansion
- Variables substitution in bash. 
  - (&nbsp;$&nbsp;) - references the value of a variable.

  ```bash
  dev@dev: echo $PWD
  /home/dev

  dev@dev: var="Hello World!
  dev@dev: echo $var
  ```

## Command Substitution
- Allow the use of output of a command as an expansion. 
    ```bash
    dev@dev: ls $(cd ~)
    Desktop Downloads Documents ...

    dev@dev: ls -l $(type -p bash)
    -rwxr-xr-x 1 root root 1396520 Jan  7  2022 /usr/bin/bash
    ```

