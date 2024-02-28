# Processes 
- A process in Linux is a program in execution, it is running instance of a program. Progresses are how Linux organizes different programs to be executed by the CPU.  
- The kernel maintains information about each process. Each process is assigned a number called a process ID (PID).

## View Processes 
- <code> ps</code> : Displays processes associated with the current terminal session.
    - <code> ps x</code> : Displays all processes running on the system.
    - <code> ps aux</code> : Displays detailed information about all processes running on the system, including processes owned by other users.   
- <code> top</code> : Display information about running processes in real-time. 

    ```bash
    ## below are info on process states, info can be retrieved using man ps 
    dev@dev: man ps
    ...
    PROCESS STATE CODES
        Here are the different values that the s, stat and state output specifiers (header "STAT" or "S") will display to describe the state of a process:

                D    uninterruptible sleep (usually IO)
                I    Idle kernel thread
                R    running or runnable (on run queue)
                S    interruptible sleep (waiting for an event to complete)
                T    stopped by job control signal
                t    stopped by debugger during the tracing
                W    paging (not valid since the 2.6.xx kernel)
                X    dead (should never be seen)
                Z    defunct ("zombie") process, terminated but not reaped by its parent

        For BSD formats and when the stat keyword is used, additional characters may be displayed:

                <    high-priority (not nice to other users)
                N    low-priority (nice to other users)
                L    has pages locked into memory (for real-time and custom IO)
                s    is a session leader
                l    is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)
                +    is in the foreground process group
    ...

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
- Terminal allows program to be run in foreground and background. When a program runs in foreground no other input is allowed in the terminal session until its terminated. When a program runs in background terminal session will allow other programs to be executed. 
- Below is a demonstration using python http server. 

    ```bash
    ## first start a http server using python, turns a directory to a local web server 
    ## this command will be running in the foreground indefinitely until it is terminated 
    ## however it can be sent to the background to run, which frees the current terminal window, allow other commands to be executed
    dev@dev: python3 -m http.server 
    Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...

    ## command can be launched in the background 
    dev@dev: python3 -m http.server & 
    [1] 10753
    dev@dev: Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...

    dev@dev: echo "Hello" 
    Hello 

    ## set command to run in background 
    ## enter ctrl+Z to suspend the process 
    dev@dev: python3 -m http.server
    Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
    ^Z
    [1]  + 11008 suspended  python3 -m http.server

    ## to see all the jobs running in the background of the current shell session 
    dev@dev: jobs -l 
    [1]  + 11008 suspended  python3 -m http.server

    ## use command bg to run http server in the background
    dev@dev: bg %1
    [1]  - 11008 continued  python3 -m http.server

    ## to bring it to foreground 
    dev@dev: fg %1
    [1]  + 11008 running    python3 -m http.server

    ```

## Terminating Processes
- Use the <code> kill</code> command to terminate processes. 
- The <code> kill</code> command sends signals. Signals are one of several ways that a OS communicates with programs. Ctrl-C and Ctrl-Z are signals. 
- The default signal is <code>TERM</code> which means to terminate. 

    ``` bash
    ## below is part of a list of signals, retrieved using man 7 signal 
    dev@dev: man 7 signal
    ...
    Standard signals
        Linux supports the standard signals listed below.  The second column of the table indicates which standard (if any) specified the signal: "P1990" indicates that the signal is de‐
        scribed in the original POSIX.1-1990 standard; "P2001" indicates that the signal was added in SUSv2 and POSIX.1-2001.

        Signal      Standard   Action   Comment
        ────────────────────────────────────────────────────────────────────────
        SIGABRT      P1990      Core    Abort signal from abort(3)
        SIGALRM      P1990      Term    Timer signal from alarm(2)
        SIGBUS       P2001      Core    Bus error (bad memory access)
        SIGCHLD      P1990      Ign     Child stopped or terminated
        SIGCLD         -        Ign     A synonym for SIGCHLD
        SIGCONT      P1990      Cont    Continue if stopped
    ...

    ## terminate a process 
    dev@dev: jobs -l
    [1]  + 12742 running    python3 -m http.server

    dev@dev: kill 12742 ## kill a process on it's PID
    [1]  + 12742 terminated  python3 -m http.server  

    ## terminate multiple processes 
    dev@dev: python3 -m http.server 8000 &; python3 -m http.server 8001 &;python3 -m http.server 8002 &

    dev@dev: jobs
    [1]    running    python3 -m http.server 8000
    [2]  - running    python3 -m http.server 8001
    [3]  + running    python3 -m http.server 8002

    dev@dev: killall python3
    [1]    13310 terminated  python3 -m http.server 8000
    [2]  - 13311 terminated  python3 -m http.server 8001
    [3]  + 13312 terminated  python3 -m http.server 8002
    ```