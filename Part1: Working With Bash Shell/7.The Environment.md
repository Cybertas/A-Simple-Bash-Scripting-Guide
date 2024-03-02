# The Shell Environment 

- The shell keeps track of information during a shell session called the environment.
- Programs use data stored in the environment to determine the system's configurations. 

## Types of Shell Environment Data


- Shell stores two basic types of data in the environment.<br>

    1. Environment variables: Used to pass information between processes or configure the behavior of programs. Accessible to all processes spawned from the shell.
    2. Shell variables: Used to store temporary data within a shell script or session. Not visible to external programs or other shell instances. 


    ```bash
        ## shell variables 
        dev@dev: greetings="Hello World!"

        ## environment variables 
        dev@dev: PATH=$PATH:$HOME/bin ## adding additional directory for PATH

        dev@dev: HOME=/dev/home/bin ## changing the home directory 
    ```

## Establishing the Shell Environment

- When bash starts, it reads a series of configuration script files called startup files, defining the default environment shared by all users.
- The sequence of startup files depends on the type of shell session being started: non-login or login shell session.

 - Below are two types of sessions:
    - A non-login shell session: A shell session via terminal emulator. 
    - A login shell session: A shell that prompts for username and password i.e. SSH session. 
    
    </br>
    
    | File             | Description |
    | ---------------  | --------------  |
    | /etc/bash.bashrc | A global config script that applies to all users                                            |
    | ~/.bashrc | A user's personal startup file         |
    
    &nbsp; &nbsp; **Table 2.1** - Startup Files for Non-Login Shell Sessions 

    </br>


    | File            | Description |
    | --------------- | -------------- |
    | /etc/profile    | A global config script that applies to all users                                            |
    | ~/.bash_profile | A user's personal startup file   |
    | ~/.bash_login   | If ~/.bash_profile is not found, bash will attempt to read this instead                    |
    | ~/.profile      | If neither ~/.bash_profile nor ~/.bash_login is found, bash attempts to read this file |

    &nbsp; &nbsp; **Table 2.2** - Startup Files for Login Shell Sessions

    

## Update the Startup Files
- To add directories to PATH or define additional environment variables, place changes in <code>.bash_profile</code> or equivalent (depending on the Distro). For other changes, use <code>.bashrc</code>.

- Below is an example on a modified startup file. 

    ```bash
    ## in the .bashrc file 
    ## to add additional alias
    alias cl='clear' ## instead of typing clear to clear terminal, type cl

    ## in terminal 
    dev@dev: source ~/.bashrc ## update the change
    ```


## Interacting with the Shell Environment 
- <code>set</code>: Prints values for both shell and environment variables, and displays defined shell functions.
- <code>printenv</code>: Only show environment variables.
- <code>alias</code>: Displays and allows the declaration of aliases.

    ```bash
    ##  a snippet of set command output
    dev@dev: set
    ...
    TERM=xterm-256color
    UID=1000
    USER=dev
    USERNAME=dev
    VTE_VERSION=6800
    WAYLAND_DISPLAY=wayland-0
    ...

    ## list all the environment variables
    dev@dev: printenv 
    USER=dev
    PAGER=less
    LSCOLORS=Gxfxcxdxbxegedabagacad
    XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/usr/share/upstart/xdg:/etc/xdg
    ...

    ## a snippet of alias command output
    dev@dev: alias
    ...
    alias grep='grep --color=auto'
    alias l='ls -CF'
    alias la='ls -A'
    alias ll='ls -alF'
    alias ls='ls --color=auto'

    ## echo can also be used to display value of environment variables
    dev@dev: echo $PWD
    /home/dev

    dev@dev: echo $USER
    dev
    ```




