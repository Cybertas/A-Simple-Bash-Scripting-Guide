### View File Contents
```bash
## displays the content of file
dev@dev:  cat .bashrc
...
case $- in
    *i*) ;;
    *) return;;
esac
...

## using less, less takes user input which allows user to scroll up and down
dev@dev: less .bashrc
...
case $- in
    *i*) ;;
    *) return;;
esac
...
: ## waiting for user input 

## using vim, vim allows editing files over command line.
## to quit, enter ":q"
dev@dev: vim .bashrc
...
case $- in
    *i*) ;;
    *) return;;
esac
...
".bashrc" 117L, 3771B                           1,1           Top
```

### Create File

```bash
## create a new file using touch 
dev@dev: touch new_file

## create a new file using echo 
dev@dev: echo "" > new_file1

dev@dev: ls 
new_file new_file1
```

### Delete File

```bash
## remove a file
dev@dev: rm file

## remove multiple files
dev@dev: rm new_file new_file1
```

### Rename File

```bash
## mv can be used to rename file as well move files to another directory
## syntax: mv old_name new_name
dev@dev: mv new_file new_name
```