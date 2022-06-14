# LINUX Week 17

## Internal and external commands

* `type -a echo`: Check whether the following command is an internal command or an external command (if it is an internal command, it will display shell builtin), the internal command will be executed prior to the external command
* `a=5; echo a${a}a`: This will display `a5a`, if no big exaggeration is added, the following aa will be treated as a variable

````sh
[user@localhost ~]$ a=5; echo $a
5
[user@localhost ~]$ (a=10; echo $a)
10
[user@localhost ~]$ echo $a
5
````

The above result is displayed because Linux bash usually `fork()` a sub-stroke when receiving an external command (ELF 64-bit LSB executable), and then use `exec()` to switch to the self-stroke Excuting an order. And [internal commands](https://www.ibm.com/docs/zh-tw/aix/7.1?topic=shell-list-bourne-built-in-commands) (POSIX shell script) like `cd` , it will not use `fork()`, but will be executed in the `bash` process. Generally, the use of echo is an external command, but after wrapping it with (), echo becomes an internal command. It will `fork()` to make a stroke, and it will be discarded after execution, so finally `echo $a` will display 5\



## Linux special symbols

| Symbol | Meaning | Example |
| ---- | -------------------------------------------- --------- | --------------------- |
| $$ | process id, you can use this record in the shell to a new file | `echo $$ > tmp/mypid` |
| $? | Determine whether the previous command was successful, return 0 for success, and return a non-zero value for failure | `echo $?` |
| $# | The parameter followed by the shell, usually used in the shell | |
| $1 | represents the first parameter, $2 represents the second, and so on | |
| $_ | | |
| $@ | From the first parameter to the last parameter | |
| !! | | |

Here's a shell that can render the usage of special symbols

````sh
#!/usr/bin/bash

echo $#
echo $$ > /tmp/mypid
echo '$0' $0
echo '$1' $1
echo '$2' $2
echo '$3' $3

for var in '$@'
do
echo $var
done

while true
do
sleep 1
done
````

Execute the above shell

````
[user@localhost ~] ./a.sh 1 2 3 4 5
5
$0: ./a.sh
$1: 1
$2: 2
$3: 3
1
2
3
4
5
````



## zombie process

When the parent process fork() a new child process, the child process has been executed, but bash deliberately does not recycle the child process, the executed child process will become a zombie process

````c
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
int main() {
  pid_t child_pid;
  // Create a process, child_pid greater than 0 means parent process
  // Equal to -1 means an error occurred, the others are part of the child process
  child_pid = fork();
  if (child_pid > 0) {
    /* This is the parent process. Sleep for a minute. */
    sleep(60);
  } else {
    // Let the child process execute immediately, because the parent process is still sleeping
    // So child process immediately becomes zombie process
    exit (0); // exit command
  }
  return 0;
}
````



When encountering zombie process, delete it for parent process, use: `kill -9 pid`.



## orphan process

When the parent process finishes executing before the child process, and then the parent process dies, the child process becomes the orphan process. The operating system will set the orphan process to be received by the first fork() process of the system (init or systemd)

````c
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
int main() {
  pid_t child_pid;
  // Create a process, child_pid greater than 0 means parent process
  // Equal to -1 means an error occurred, the others are part of the child process
  child_pid = fork();
  if (child_pid > 0) {
    // Let the parent process exit immediately, the child process has no parent and becomes an orphan process
    exit(0);
  } else {
    /* This is the child process. Sleep for a minute. */
    // orphan process will be received by systemd
    sleep(60);
  }
  return 0;
}
````



## firework

Reference webpage: [CentOS Linux 7 uses firewalld command to set firewall rules tutorial](https://blog.gtwang.org/linux/centos-7-firewalld-command-setup-tutorial/)

Firework can make different settings according to different environments, simple settings in a safe network environment, complex settings in a dangerous network environment

The set rules are only temporary and will be reworked when the system is restarted. If you want to save it permanently, you need to add the parameter `--permanent`, which will be written into config.

> Firewall settings, so that http can connect

* trusted means all permissions are open
* public represents the default permissions of the open system

````sh
firewall-cmd --zone=trusted --list-all # View all trusted permissions
firewall-cmd --set-default-zone=trusted # Set the zone to trusted so that outside computers can connect to
firewall-cmd --set-default-zone=public
````



Reload is to re-read the configuration, it will not cause the server to be disconnected, and restart will restart the system. Reload is not equal to restart. If you can use reload, use reload as much as possible.

## Linux Command

* `ls /tmp && ls /temp`: && means that if the execution of the previous instruction fails, the subsequent instructions will not be executed, and if they are successful, they will be executed
* `ls /etmp && echo 1 || echo 0`: execute the third command if the first command fails, otherwise execute the second command
* `set`: can be used to display the system's environment brightening and its own defined variables
* `env`: display system enviromental variables
* `su -`: This is the same as `su` to switch to super user, but the environment variables will be different