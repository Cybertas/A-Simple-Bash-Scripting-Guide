### List Groups 

```bash
## /etc/group/ stores info on all groups on the system
dev@dev: cat /etc/group
...
test_group:x:0:test_user,dev
...

## test_group is the name of the group
## x is a placeholder for password for the group 
## 0 is the group ID (GID) of the group
## test_user, dev are the members of the group
```

### Create Groups

```bash
## create a new group named group1
dev@dev: sudo groupadd group1
```
    
### Update Group Information 

```bash
## rename group from group1 to group_new
dev@dev: sudo groupmod -n group_new group1

## update group id (GID) for group_new
dev@dev: sudo groupmod -g 1005 group_new
```

### Update Group Users

```bash
## add new user to group
## where -a is to append user to -g group specified
dev@dev: sudo usermod -a -G group_new dev

## remove user from group
dev@dev: sudo deluser dev group_new
Removing user `test_user' from group `group1' ...
Done.
```

### Delete Groups

```bash
## delete a group
sudo groupdel group_new
```


