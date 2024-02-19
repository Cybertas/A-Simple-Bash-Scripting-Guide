# The Shell Environment 
- The shell keeps track of information during a shell session called environment.
- Programs use data stored in the environment to determine the system's configurations. 
- Shell stores two basic types of data in the environment.<br>
    - Environment variables: Environment variables are used to pass information between processes or to configure the behavior of programs.  They are accessible to all processes that are spawned from the shell.
    - Shell variables: Shell variables are used to store temporary data within a shell script or session. They are not visible to external programs or other shell instances. 

    ```bash
        ## shell variables 
        dev@dev: greetings="Hello World!"

        ## environment variables 
        dev@dev: PATH=$PATH:$HOME/bin ## adding additional directory for PATH

        dev@dev: HOME=/dev/home/bin ## changing the home directory 
    ```

## How is the Shell Environment Established
 - When bash starts on boot it reads a series of configuration script files called startup files, which defines the default environment shared by all users. This is followed by more startup files in the user home directory which defines the user personal environment. 
 - The exact sequence depends on the type of shell session being started. 
 - Below are two kinds of sessions:
    - A non-login shell session: A shell session via terminal emulator. 
    - A login shell session: A shell that prompts for username and password i.e. SSH session. 
    
    </br>

    | File             | Description |
    | ---------------  | --------------  |
    | /etc/bash.bashrc | A global config script that applies to all users                                            |
    | ~/.bashrc | A user's personal startup file         |
    
    **Table 2.2** - Startup Files for Non-Login Shell Sessions

    </br>


    | File            | Description |
    | --------------- | -------------- |
    | /etc/profile    | A global config script that applies to all users                                            |
    | ~/.bash_profile | A user's personal startup file   |
    | ~/.bash_login   | If ~/.bash_profile is not found, bash will attempt to read this instead                    |
    | ~/.profile      | If neither ~/.bash_profile nor ~/.bash_login is found, bash attempts to read this file |

    **Table 2.1** - Startup Files for Login Shell Sessions

    

## Update the Startup Files
- As a general rule, to add directories to PATH environment variable or define additional environment variables, place changes in <code>.bash_profile</code> or equivalent. For everything else place changes in <code>.bashrc</code>.
- Below are some examples that can be added to the Startup files to customize the user environment. 
    ```bash
    ## in the .bashrc file 
    ## to add additional alias
    alias cl='clear' ## instead of typing clear to clear terminal, type cl


    ## in terminal 
    dev@dev: source ~/.bashrc ## update the change
    ```


## Interacting with the Shell Environment 
- <code>set</code>
    -  The 'set' command prints values for both the shell and environment variables. It also displays any defined shell functions. 
    - It is a built-in command. 
- <code>printenv</code>
    - The 'printenv' command will only show environment variables.
- <code>alias</code>
    - The 'alias' command will display all aliases in the environment and allows you to declare new aliases. 
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




