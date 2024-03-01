### Background & Foreground Process

```bash
## first start a http server using python, turns a directory to a local web server 
## this command will be running in the foreground indefinitely until it is terminated 
## however it can be sent to the background to run, which frees the current terminal window, allow other commands to be executed
dev@dev: python3 -m http.server 
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...

## command can be launched directly in the background 
dev@dev: python3 -m http.server & 
[1] 10753
dev@dev: Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...


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

### Terminate Process
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