# simple_shell

## Description
* Our simple shell is a simple UNIX command line interpreter that reads arguments or input from user, takes input using stdin, parses the input into an array of strings and finally executes the arguments.
* Program must have same output as sh (/bin/sh).
* Program must also have same error output.
* Printing an error, argv[0] first argument must be identical to the name of the program.

## Compilation
* The shell is compiled by the following:
```
git clone https://github.com/berhanez/simple_shell
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh
```
## Instructions
* After compilation, start program by typing ``` ./hsh ```
* Type in a typical command like ``` ls ``` or ``` cat <filename> ```
* When you are done, simply exit by typing ``` exit ```
* To see the authors of the project, type in ``` bash generate_authors.sh ```

### Testing
#### Interactive Mode
```
$ ./hsh
($) /bin/ls
hsh main.c shell.c
($)
($) exit
$
```

#### non-interactive mode:
```
$ echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
$
$ cat test_ls_2
/bin/ls
/bin/ls
$
$ cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
$
```
### Allowed Functions in this project
 | ALLOWED FUNCTIONS |
 | ----------------------------- |
 | access (man 2 access) |
 | chdir (man 2 chdir) |
 | close (man 2 close) |
 | closedir (man 3 closedir) |
 | execve (man 2 execve) |
 | exit (man 3 exit) |
 | _exit (man 2 _exit) |
 | fflush (man 3 fflush) |
 | fork (man 2 fork) |
 | free (man 3 free) |
 | getcwd (man 3 getcwd) |
 | getline (man 3 getline) |
 | getpid (man 2 getpid) |
 | isatty (man 3 isatty) |
 | kill (man 2 kill) |
 | malloc (man 3 malloc) |
 | open (man 2 open) |
 | opendir (man 3 opendir) |
 | perror (man 3 perror) |
 | read (man 2 read) |
 | readdir (man 3 readdir) |
 | signal (man 2 signal) |
 | stat (__xstat) (man 2 stat) |
 | lstat (__lxstat) (man 2 lstat) |
 | fstat (__fxstat) (man 2 fstat) |
 | strtok (man 3 strtok) |
 | wait (man 2 wait) |
 | waitpid (man 2 waitpid) |
 | wait3 (man 2 wait3) |
 | wait4 (man 2 wait4) |
 | write (man 2 write) |
 
 ### Environment
Upon invocation, **simple_shell** receives and copies the environment of the parent process in which it was executed. This environment is an array of *name-value* strings describing variables in the format *NAME=VALUE*. A few key environmental variables are:
* **HOME**
The home directory of the current user and the default directory argument for the **cd** builtin command.

* **PWD**
The current working directory as set by the **cd** command.

* **OLDPWD**
The previous working directory as set by the **cd** command.

* **PATH**
A colon-separated list of directories in which the shell looks for commands. A null directory name in the path (represented by any of two adjacent colons, an initial colon, or a trailing colon) indicates the current directory.

### Variable Replacement
**simple_shell** interprets the `$` character for variable replacement.
* `$ENV_VARIABLE`
  * `ENV_VARIABLE` is substituted with its value.
* `$?`
  * `?` is substitued with the return value of the last program executed.
* `$$`
  * The second `$` is substitued with the current process ID.
  
### Operators
**simple_shell** specially interprets the following operator characters:
* `;` - Command separator
  * Commands separated by a `;` are executed sequentially.
* `&&` - AND logical operator
  * `command1 && command2`: `command2` is executed if, and only if, `command1` returns an exit status of zero.
* `||` - OR logical operator
  * `command1 || command2`: `command2` is executed if, and only if, `command1` returns a non-zero exit status.

The operators `&&` and `||` have equal precedence, followed by `;`.

## PROJECT TASKS
* ``` 0-getppid.c ``` - Prints PID of parent process ID,
	Parent Process ID doesn't change when program executed repeatedly.
	Echo $$ yields same value as getppid(parent PID) because $$ is defined to return the process ID of the parent in a subshell; from the man page under "Special Parameters":
* ``` 1-pid_max ``` - shell script that prints the maximum value a process ID can be.
	Invoked by "cat /proc/sys/kernel/pid_max" in a LINUX terminal.
* ``` 0-av.c ``` - Prints all arguments without using ac
* ``` 1-read_line.c ``` - program prints "$ ", wait for the user to enter a command then prints it on the next line. Utilizes getline
```
man 3 getline
```
* ``` 2-command_line_to_av.c ``` - Function that splits a string and returns an array of each word of the string.
```
man strtok
```
* ``` exec.c ``` - Executing a program. The system call execve allows a process to execute another program (man 2 execve).
* ``` fork.c ``` - The system call fork (man 2 fork) creates a new child process, almost identical to the parent (the process that calls fork).
* ``` wait.c ``` - The wait system call (man 2 wait) suspends execution of the calling process until one of its children terminates. Using the return value of fork, it is possible to know if the current process is the father or the child: fork will return 0 to the child, and the PID of the child to the father.
* ``` fork+wait+execve.c ``` - Executes the command ``` ls -l /tmp ``` in 5 different child processes.

## Authors
* Berhane Zerabruk Desta
<[berhanez](https://github.com/berhanez)><birhanez@gmail.com>
* Efrata Dagnachew
<[Ruthael](https://github.com/Ruthael)><efrata.dagnu@gmail.com>

## Acknowledgements
**simple_shell** emulates basic functionality of the **sh** shell. 
