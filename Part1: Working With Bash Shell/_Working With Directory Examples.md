 ### List Directory Contents
 ```bash
## list content of current directory 
dev@dev: ls
Downloads Desktop Documents Media ...

## list content of directory using absolute filepath
dev@dev: ls /home/dev/Downloads
file1 file2 file3

## list two directories at same time
dev@dev: ls . /home
.:
Downloads Desktop Documents Media ...

/home:
dev user1 user2 user3
```

### Create Directory

```bash
## create a directory 
dev@dev: mkdir test_dir


## create nested directory 
dev@dev: mkdir -p test_dir/child_dirs
```

### Delete Directory 

```bash
## remove a directory and their contents recursively
dev@dev: rm -r test_dir 


## remove an empty directory 
dev@dev: rm -d child_dirs
```

### Move Directory Contents

```bash
## list contents of /dev and /usr directory 
dev@dev: ls /home/dev /home/usr
/dev: 
file_dev

/usr:
file_usr


## mv file_usr to dev
## syntax: mv from_dir to_dir
dev@dev: mv /home/usr/file_usr /home/dev/
```


### Rename Directory

```bash
## mv command can also be used to remove files and directory
## syntax: mv old_name new_name
dev@dev: mv /home/usr/file_usr /home/user
```