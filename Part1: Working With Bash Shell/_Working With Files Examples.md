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