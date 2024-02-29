Need to link to Globbing for filename matching
# Files and Directories 
- In Linux, files are organized in a hierarchical directory structure. Linux is a single file system tree where the structure starts from the root directory and branch downwards. 

     ```bash
    ## use df command to examine the filesystem structure
    ## all filesystem is mounted on the root (/)
    dev@dev: df -h
    Filesystem      Size  Used Avail Use% Mounted on
    tmpfs           1.6G  2.8M  1.6G   1% /run
    /dev/sda2       XXXG   XXXG  XXXG  XX% /
    tmpfs           X.XG  XXXM  X.XG   X% /dev/shm
    efivarfs        XXXK  XXXK  XXXK  XX% /sys/firmware/efi/efivars
    /dev/sda1       XXXM  XXXM  XXXM   X% /boot/efi
    ...
    ```
## Directory Navigation
- The current directory is called the working directory. 
- Use <code>pwd</code> to display the working directory. 
- Use <code>cd</code> to change directory. 
- There are two methods to refer to a directory 
    1. **Absolute Pathnames**: An absolute pathname begins with the root directory and follows the tree branch by branch until the path to the desired directory or file is completed.
    2. **Relative Pathnames**: uses special notions to navigate. </br>
    The "." notion refers to the working directory.
    The ".." notion refers to the parent directory of the working directory. 
    ```bash
    ## pwd shows that we are in the home directory of user dev
    dev@dev: pwd
    /home/dev

    ## absolute pathname navigation
    ## navigating to the Downloads directory where the Downloads directory is the child of dev directory
    dev@dev: cd /home/dev/Downloads

    ## relative pathname navigation
    dev@dev: cd ./Downloads

    ## navigating to the parent directory of dev
    dev@dev: cd .. 
    dev@dev: pwd
    /home
    ```
## Working With Directories  
 - To list contents in a directory or directories, use the <code>ls</code> command. 
- Use <code>mkdir</code> command to make a new directory. 
- Use <code>rm</code> command to remove a directory.
- Use <code>mv</code> command to move files between directories
- Examples on working with directories:
    - [List Directory Contents](./_Working%20With%20Directory%20Examples.md#list-directory-contents)
    - [Create Directory](./_Working%20With%20Directory%20Examples.md#create-directory)
    - [Delete Directory](./_Working%20With%20Directory%20Examples.md#delete-directory)
    - [Move Directory Contents](./_Working%20With%20Directory%20Examples.md#move-directory-contents)
    - [Rename Directory](./_Working%20With%20Directory%20Examples.md#rename-directory)

## Working With Files
 - To list/view content of a file: 
    - <code>cat</code>: The <code>cat</code> command prints the file content to terminal. 
    - <code>less</code>: The <code>less</code> command allows you to view the contents of a file one screen at a time, provides an easier way to read and navigate through large files. 
    - <code>vim</code>: it is a built-in text editor for CLI. 
- To create a new file:
    - <code>touch</code>: The <code>touch</code> command can be used to create new empty file.
    - <code>echo</code>:  The <code>echo</code> command prints string to terminal, combine with redirection can be used to create new file. 
- To remove a file, use <code>rm</code> command.
- To rename a file, use <code>mv</code> command.
- Examples on working with files:
    - [View File Contents](./_Working%20With%20Files%20Examples.md#view-file-contents)
    - [Create File](./_Working%20With%20Files%20Examples.md#create-file)
    - [Delete File](./_Working%20With%20Files%20Examples.md#delete-file)
    - [Rename File](./_Working%20With%20Files%20Examples.md#rename-file)

