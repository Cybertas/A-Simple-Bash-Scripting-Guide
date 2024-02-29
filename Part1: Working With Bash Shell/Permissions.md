# Permissions 
- Linux has the capability to provide access to multiple users. Thus permissions are essential for security and access control.  
- Permissions represent the access rights granted to users, groups and other entities for files and directories. 
- Overview:
    - [Permission Types & Identities](#permission-types--identities)
    - [Modify Permissions - Change File Permission](#modify-permissions---change-file-permission)
    - [Modifying Identifies - Change Owner and Group](#modifying-identifies---change-owner-and-group)
    - [Modifying Identities - Change Group Ownership](#modifying-identities---change-group-ownership)
    - [Other Permission Concepts](#other-permission-concepts)

## Permission Types & Identities
- There are three types of permissions: 
    1. Read (r): This permission allows the file to be opened and read as well as allows the contents of directories to be listed. 
    2. Write (w): This permission allows the file to be modified or deleted and allows files within the directory to be created, deleted or renamed.  
    3. Execute (x): This permission allows the file to be executed. For directories, it allows access and directories within the directory. 
- There are three different identities which permission can be applied to: 
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
    drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 dev group2 4096 Feb 27 16:45 file1
    
    ## dir1 is a directory has "d" as most left bit
    ## dir1 allows read, write and execute for owner
    ## dir1 allows read and execute for group
    ## dir1 allows execute for everyone else 
    ## dir1 has group1 as group 

    ## file1 is a file has "-" as most left bit
    ## file1 allows read and write for owner
    ## file1 allows read and write for group
    ## file1 allows read only for everyone else
    ## file1 has group2 as group
    ```
    
## Modify Permissions - Change File Permission
- The <code>chmod</code> command can be used to modify the permission for each category. 
- There are two modes that can be used to set permissions.
    1. Symbolic Mode
        - Symbolic Mode uses letters to set the permissions.
    
            | Letter | Description |
            | --------------- | -------------- |
            | u               | Represents file or directory owner |
            | g               | Represents group owner             |
            | o               | Represent others                   |
            | a               | Represents all, including u,g,o    |

    2. Numeric Mode 
        - Numeric Mode uses Octal to set the permissions.

            |   Octal  |      Binary   |  File Mode |
            |----------| ------------- | ---------- |
            | 0        |  000          | ---        |
            | 1        |  001          | --x        |
            | 2        |  010          | -w-        |
            | 3        |  011          | -wx        |
            | 4        |  100          | r--        |
            | 5        |  101          | r-x        |
            | 6        |  110          | rw-        |
            | 7        |  111          | rwx        |

    ```bash
    ## list contents in a directory 
    dev@dev: ls -l
    drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 dev group2 4096 Feb 27 16:45 file1
    
    ## there are two main ways to assign permission 
    ## Symbolic Mode and Numeric Mode
    ## owner(u), group(g), other(o), all(a)


    ## Symbolic Mode
    ## add execute permission for others on file1
    dev@dev: chmod u+x file1 

    ## remove execute permissions on owner,group and other on dir1
    dev@dev: chmod ugo-x dir1

    ## remove all execute permissions on dir1
    dev@dev: chmod a-x dir1

    ## set readonly permission for group
    dev@dev: chmod g=r file1

    ## Numeric mode 
    ## provide read,write and execute permission to owner, group and others
    dev@dev: chmod 777 file1

    ## provide read,write and execute to owner
    ## provide read, write to group
    ## provide read only to others
    dev@dev: chmod 764 file1
    ```
## Modifying Identifies - Change Owner and Group
- The <code>chown</code> command can be used to change the owner and group (optionally) for a file or directory. 
-  Syntax: chown owner_change_to:group_change_to file_name

    ```bash
    ## list contents in a directory 
    dev@dev: ls -l
    drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 dev group2 4096 Feb 27 16:45 file1
    
    ## change owner to test_user for file1
    dev@dev: sudo chown test_user file1 && ls -l
    drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 test_user group2 4096 Feb 27 16:45 file1

    ## change owner and group to test_user and test_group for dir1
    dev@dev: sudo chown test_user:test_group dir1 && ls -l
    drwxr-xr-x  2 test_user test_group 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 test_user group2 4096 Feb 27 16:45 file1

    ## change group ownership to dev for dir1
    dev@dev sudo chown test_user:dev dir1 && ls -l
    drwxr-xr-x  2 test_user dev 4096 Dec  7 07:39 dir1
    -rw-rw-r--  1 test_user group2 4096 Feb 27 16:45 file1
    ```


## Modifying Identities - Change Group Ownership 
- The <code>chgrp</code> command can be used to change the group for folder or directory. 

    ```bash
        ## list contents in a directory 
        dev@dev: ls -l
        drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
        -rw-rw-r--  1 dev group2 4096 Feb 27 16:45 file1

        ## change group ownership to test_group for file1 
        dev@dev: sudo chgrp test_group file1; ls -l
        drwxr-xr-x  2 dev group1 4096 Dec  7 07:39 dir1
        -rw-rw-r--  1 dev test_group 4096 Feb 27 16:45 file1
    ```
## Other Permission Concepts
 - setuid
 - setgid
 - sticky bit