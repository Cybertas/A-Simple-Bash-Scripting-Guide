### List Users 
- Example on list existing users.

    ``` bash
    ## /etc/passwd/ stores info on all users on the system
    dev@dev: cat /etc/passwd
    root:x:0:0:root:/root:/bin/bash
    ...

    ## root is the username of the user.
    ## x indicates that the password is stored in the /etc/shadow file.
    ## 0 is the user ID (UID) of the root user.
    ## 0 is the group ID (GID) of the root user.
    ## root is additional information about the user.
    ## /root is the home directory of the user.
    ## /bin/bash is the login shell of the user.
    ```

### Create Users 
- Example on creating new users.
    - By default, <code>useradd</code> does not set the password for the new user. To set a password use <code>passwd</code> command.

    ``` bash
    ## adding a new user named user1
    dev@dev:  sudo useradd user1 

    ## adding a new user with home directory 
    dev@dev: sudo useradd -m user2
    dev@dev: ls /home 
    dev user2
    dev@dev: ls home/user2
    Downloads Desktop ...
    
    ## adding a new user with a different shell
    dev@dev: sudo useradd -s /bin/bash user3
    ```
    
### Set/Update Password
- Example on setting or updating passwords.

    ``` bash
    dev@dev: sudo passwd user1 ## will prompt to enter a new password
    ```

### Delete Users 
- Example on deleting users.

    ``` bash
    ## removing a user
    dev@dev: sudo userdel user1

    ## removing a user and their home directory 
    dev@dev: sudo userdel -r user2
    ```

### Switch Users 
- Example on login into other users.

    ``` bash
    dev@dev: su user1 ## prompts for password

    user1@dev: whoami
    user1
    ```

### Update Users
- Example on updating user information.

    ```bash
    ## renaming username for user1 to user1_new
    dev@dev: usermod -l user1_new user1

    ## set an account expiry date for user1_new
    dev@dev: usermod -e 2025-01-01 user1_new

    ## update user's home directory and move all contents in the existing directory to the updated home directory
    dev@dev: usermod -m -d /home/shared user1_new
    ```