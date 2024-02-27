# Permissions 
- Linux has the capability to provide access to multiple users. Thus permissions are essential for security and access control.  
- Permissions represent the access rights granted to users, groups and other entities for files and directories. 

## Permission Types & Categories 
- There are 3 types of permissions: 
    1. Read (r): This permission allows the file to be opened and read as well as allows the contents of directories to be listed. 
    2. Write (w): This permission allows the file to be modified or deleted and allows files within the directory to be created, deleted or renamed.  
    3. Execute (x): This permission allows the file to be executed. For directories, it allows access and directories within the directory. 
- There are three different categories which permission can be applied to: 
    1. Owner (a user): This category represents the user who created the file or directory, or the user who is currently the owner. 
    2. Group: By default, only one group can be associated with a folder or directory. Permission applied to a group will be applied to all users in that group. 
    3. Other (everyone else): This category represents all other users who are not the owner or part of the group. 
- File type strings
    1. "-" indicates a regular file.
    2. "d" indicates a directory.
    3. "l" indicates a symbolic link.
    4. "c" indicates a character special file.
    5. "b" indicates a block special file.
    6. "p" indicates a named pipe (FIFO).
    7. "s" indicates a socket.

    ```bash
    ## list all items and its permission in a directory 
    dev@dev: ls -l
    drwxr-xr-x  2 dev dev 4096 Dec  7 07:39 dir1
    drwxr-xr-x  3 dev dev 4096 Feb 14 23:38 dir2
    drwxr-xr-x  4 dev dev 4096 Feb 26 20:59 dir3
    -rw-rw-r--  1 dev dev    0 Feb 27 16:45 file1
    -rw-rw-r--  1 dev dev    0 Feb 27 16:45 file2
    -rw-rw-r--  1 dev dev    0 Feb 27 16:45 file3
    ```

Interacting with Permissions