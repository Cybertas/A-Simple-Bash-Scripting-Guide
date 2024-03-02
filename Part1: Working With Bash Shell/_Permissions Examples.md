### Permission Mode Table
----------------------------
1. Symbolic Mode: Uses letters to set the permissions.

    | Letter | Description |
    | --------------- | -------------- |
    | u               | Represents file or directory owner |
    | g               | Represents group owner             |
    | o               | Represent others                   |
    | a               | Represents all, including u,g,o    |

2. Numeric Mode: Uses Octal to set the permissions.

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

------------------------------------------------------

### chgrp Example
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

### Setuid Example
    
```bash
## the passwd command has the setuid bit set so regular users can change their passwords without needing root privileges.
dev@dev: ls -l /usr/bin/passwd
-rwsr-xr-x 1 root root 59976 Feb  6 23:54 /usr/bin/passwd


## man setuid for more info
dev@dev: man setuid
```



### Setgid Example

```bash
## The user has to be included in the group first.
## Does not allow the owner to run the program with the group permission.

## test using a bash file
## creating a file with user called dev
dev@dev: echo 'echo "testing" >> ./test.sh' > test.sh

## view permission
## login to user test_user
test_user@dev: whoami
test_user
test_user@dev: ls -l
-rwxrwxr-x 1 dev       test_group           8 Mar  1 10:52 test.sh

## run test.sh, permission denied error as expected 
test_user@dev: ./test.sh
./test.sh: line 1: ./test.sh: Permission denied

## add setgid bit which then allows other user to have the group permission
## the user must have the group owner membership
dev@dev: whoami 
dev
dev@dev: chmod g+s ./test.sh; ls -l
-rwxrwsr-x 1 dev       test_group          28 Mar  1 10:54 test.sh

## run script again as test_user
## allows user to write to the script 
test_user@dev: ./test.sh 2> /dev/null && cat ./test.sh
testing 


## man setgid for more info
dev@dev: man setgid
```



### Sticky Bit Example
```bash
## view directory permission
dev@dev: ls -ld /shared
drwxrwxrwx 2 dev       test_group 4096 Feb 27 18:10 shared

## add sticky bit
dev@dev: chmod +t shared; ls -l

drwxrwxrwt 2 dev       dev        4096 Mar  1 12:46 shared
```