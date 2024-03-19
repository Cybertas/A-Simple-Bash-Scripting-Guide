### File Comparison Operators
- Below is table for file comparison operators:

    | Operators       | Is True If: |
    | --------------- | -------------- |
    | file1 -ef file2 | file1 and file2 have the same inode number where two files are hard linked.                           |
    | file1 -nf file2 | file 1 is newer than file2.            |  
    | file1 -of file2 | file1 is older than file2.             |
    | -b file         | file exists and is block(device) file. |
    | -c file         | file exists and is character-special(device) file.             |
    | -d file         | file exists and is a directory.        |
    | -e file         | file exists.                           |
    | -f file         | file exists and is a regular file.     |
    | -g file         | file exists and is set-Group-ID.       |
    | -G file         | file exists and is owned by the effective group I.          |
    | -k file         | file exists and has a "sticky bit" se                |
    | -L file         | file exists and is a symbolic link.             |
    | -O file         | file exists and is owned by the effective user ID.          |
    | -p file         | file exists and is a named pipe.       |
    | -r file         | file exists and is readable.           |
    | -s file         | file exists nad has a length greater than zero.             |
    | -S file         | file exists nad is a network socket.           |
    | -t fd           | where fd is a file descriptor directed to/form the terminal. Can be used to determine if there is any redirection.      |
    | -u file         | file exists and is setuid.             |
    | -w file         | file exists and is writable.           |
    | -x file         | file exists nad is executable.         |

### String Comparison Operators
- Below is table for string comparison operators:

    | Operators       | Description |
    | --------------- | -------------- |
    | string          | string in not null.                        |
    | -n string       | the length of string is greater than zero. |
    | -z string       | the length of string is zero.              |
    | str1 = str2 or str1 == str2  | str1 and str2 are equal, the second form is preferred.                                      |
    | str1 != str2    | str1 and str2 are not equal.               |
    | str1 > str2     | str1 is longer than str2. (compares lexicographically)                                             | 
    | str1 < str2     | str1 is shorter than str2. (compares lexicographically)                                             |


### Integer Comparison Operators
- Below is table for integer comparison operators:

    | Operators       | Description |
    | --------------- | -------------- |
    | int1 -eq int2   | int1 is equal to int2.             |
    | int1 -ne int2   | int1 is not equal to int2.         |
    | int1 -le int2   | int1 is less than or equal to int2              |
    | int1 -lt int2   | int1 is less than int2             |
    | int1 -ge int2   | int1 is greater than or equal to int2              |
    | int1 -gt int2   | int1 is greater than int2          |

