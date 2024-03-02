# Users and Groups
- In Linux, users refer to individuals who interact with the system by logging in, executing commands, accessing files, and performing various tasks.
- In a shared computing environment, multi-users allow granular access control, resource sharing, environment customization, and much more. 
- Each user account on a Linux system is associated with a unique username and user ID, which is used to identify and differentiate each user. 
- Users can belong to one or more user groups, which provide an easier way to organize users and access control.

## User Administration 
- The <code>useradd</code> command can be used to created new user.
    - By default, <code>useradd</code> does not set the password for the new user. To set a password, use the <code>passwd</code> command.
- The <code>userdel</code> command can be used to delete users. 
- The <code>passwd</code> command can be used to change password.
- The <code>usermod</code> command can be used to modify a user account.
- Examples on user administration in Linux.
    - [List Users](./_User%20Admin%20Examples.md#list-users)
    - [Create Users](./_User%20Admin%20Examples.md#create-users)
    - [Update Password](./_User%20Admin%20Examples.md#set-password) 
    - [Delete Users](./_User%20Admin%20Examples.md#delete-users) 
    - [Switch Users](./_User%20Admin%20Examples.md#switch-users)
    - [Update Users](./_User%20Admin%20Examples.md#update-users)

## Group Administration
- The <code>groupadd</code> command can be used to created new group.
- The <code>groupdel</code> command can be used to delete groups. 
- The <code>usermod</code> command can be used to update users in a group.
- The <code>groupmod</code> command can be used to modify information of a group.
- Examples on group administration in Linux.
    - [List Group](./_Group%20Admin%20Examples.md#list-groups)
    - [Create Groups](./_Group%20Admin%20Examples.md#create-groups)
    - [Update Groups Information](./_Group%20Admin%20Examples.md#update-group-information)
    - [Update Groups Users](./_Group%20Admin%20Examples.md#update-group-users)
    - [Delete Groups](./_Group%20Admin%20Examples.md#delete-groups)
