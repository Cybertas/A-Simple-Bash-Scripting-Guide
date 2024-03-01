# Processes 
- A process in Linux is a program in execution, representing a running instance of a program.
- Processes are how Linux organizes different programs to be executed by the CPU.
- The kernel maintains information about each process, with each process assigned a unique number called a Process ID (PID).

## Processes States
- Processes in Linux can be in different states, indicating what the process is currently doing or waiting for.
- Below are the common process states:
    
    ```bash
    ## Information on process states can be retrieved using the `man ps` command

    dev@dev: man ps
    ...
        D    uninterruptible sleep (usually IO)
        I    Idle kernel thread
        R    running or runnable (on run queue)
        S    interruptible sleep (waiting for an event to complete)
        T    stopped by job control signal
        t    stopped by debugger during the tracing
        W    paging (not valid since the 2.6.xx kernel)
        X    dead (should never be seen)
        Z    defunct ("zombie") process, terminated but not reaped by its parent

        ...
        ## additional stat flags
        <    high-priority (not nice to other users)
        N    low-priority (nice to other users)
        L    has pages locked into memory (for real-time and custom IO)
        s    is a session leader
        l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
        +    is in the foreground process group
    ...
    ```

## View Processes 
- <code> ps</code> : Displays processes associated with the current terminal session.
    - <code> ps x</code> : Displays all processes running on the system.
  - `ps aux`: Displays detailed information about all processes running on the system, including processes owned by other users. 
- <code> top</code> : Display information about running processes in real-time. 

    ```bash
    ## ps by default 
    dev@dev: ps
        PID TTY          TIME CMD
    6964 pts/1    00:00:00 zsh
    9241 pts/1    00:00:00 bash
    9247 pts/1    00:00:00 ps

    ## ps using "x" flag
    dev@dev: ps x
        PID TTY      STAT   TIME COMMAND
    2271 ?        Ss     0:00 /lib/systemd/systemd --user
    2272 ?        S      0:00 (sd-pam)
    2278 ?        S<sl   0:00 /usr/bin/pipewire
    2279 ?        Ssl    0:00 /usr/bin/pipewire-media-session
    ...

    ## ps using "aux" flag
    dev@dev: ps aux
    USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
    root           1  0.0  0.0 166932 11376 ?        Ss   09:07   0:01 /sbin/init splash
    root           2  0.0  0.0      0     0 ?        S    09:07   0:00 [kthreadd]
    root           3  0.0  0.0      0     0 ?        I<   09:07   0:00 [rcu_gp]
    root           4  0.0  0.0      0     0 ?        I<   09:07   0:00 [rcu_par_gp]
    root           5  0.0  0.0      0     0 ?        I<   09:07   0:00 [slub_flushwq]
    ...

    ```

## Background & Foreground Processes
- Terminals allow programs to run in either the foreground or background. 
- In the foreground, the terminal is occupied by the running program until it is terminated. 
- In the background, other commands can be executed in the terminal while the program runs.
- For example, a Python HTTP Server can be demonstrated to run in either background or foreground mode.
- Example of demonstration using Python HTTP Server.
    - [Background & Foreground Processes Example](./_Processes%20Examples.md#background%20&%20foreground%20process)

## Terminating Processes
- Use the <code>kill</code> command to terminate processes.
- The <code>kill</code> command sends signals, which are a way for the operating system to communicate with programs. 
- The default signal is <code>TERM</code>, which instructs the process to terminate.
- Example of terminating processes:
    - [Terminate Processes](./_Processes%20Examples.md#terminate-process)
