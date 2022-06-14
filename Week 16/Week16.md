# LINUX Week 16

## process
* When the program is executed, the program code will be written into the memory, and the program running at this time can also be called a stroke.
* Cutting the available time of a CPU into small units allows the CPU to perform multiple tasks. Because the time to switch processes is fast enough, it feels a lot like multitasking.
* The system uses `fork()`, so that multiple itineraries can be generated. The first itinerary is called the parent itinerary, and the generated itinerary is called the child itinerary.
* The first sub-stroke executed by the early system was init, but it has now been replaced by systemd, because init starts slowly and starts one by one, while systemd uses parallel (related strokes can be generated in parallel), only a few steps can be started. The PID (process id) of the first sub-stroke of the system is 1
* When Linux bash receives an external command (ELF 64-bit LSB executable), it usually `fork()` out a sub-stroke, and then use `exec()` to switch to the self-stroke to execute the command. And [internal commands](https://www.ibm.com/docs/zh-tw/aix/7.1?topic=shell-list-bourne-built-in-commands) (POSIX shell script) like `cd` , it will not use `fork()`, but will execute it in the `bash` process
* `type -a [command]` : can know whether command is an external command or an internal command
* Add ` &` after the command to make the code run in the background. If you want to know how long a command is executed, you can add `time` in front of the command
* `ctrl+c` can interrupt the current process, and `ctrl+z` will stop the current process and put it into the background for execution
* `ps -l`: show all information about itinerary
* The itinerary will have a priority (PRI). The smaller the PRI, the higher the priority. The CPU will give him more timestamps.
* PRI, the default is 80, he will add the NI value to become the final PRI value
* `cd proc pid`: You can jump to the folder where the process is executed, then `cd fd`, you can see that there are 0, 1, 2, 255 in it, 0 means stdin, 1 means stdout, 2 means stderr.

## driver

1. Write directly into the operating program (the driver is directly loaded)

2. It needs to be put into the operating system (driver modularization), which will reduce the code of the kernel

Hardware manufacturers will need to use drivers to control the hardware, which is more difficult than web design and the like, but the salary is also much higher

## Linux Command

* [`pstree`](https://blog.gtwang.org/linux/linux-pstree-command-tutorial/): You can see the itinerary tree

* `top`: You can view the system's itinerary and work, you can see the system usage, you can also use `uptime` (display the top line of the top), view users and usage time

* `free -m`: View memory usage, -m changes the unit to a nicer form

* `ps`: process status, you can view the information of the itinerary, ps will generate (`fork()`) a child process 'ps' in bash, and then use `exec(ps)`, after executing ps, ps's process will disappear, switch back to bash

* `ps -ef`: usually use the way the ps command will input, you can also input `ps aux`, `-f`: you can see the current user's PID and PPID (parent process id)

* `ps aux | grep [c]ron`:

  * The itinerary will be displayed. Adding a middle exclamation mark here means that the itinerary displayed because of grep is not displayed. The medium exclamation mark is the same whether it is added in front or behind.
  * If you don't add (`ps aux | grep cron`), it will show one more grep itinerary
  * cron is a "time-related" command, mostly used in scheduling (scheduling), which can automate the program

* `ps o comn,pid,ni`: You can display the content of the itinerary according to the following things

* `ps -l`: show all information about itinerary

* `sudo nice -n -3 sleep 100 & `: Change the NI of this trip to -3, the default NI is 0, this value will affect PRI (PRI = PRI + NI), the smaller the PRI, the higher the priority

* `echo $$`: Display the id of the current itinerary, usually an important pid is stored in a file on the server

* `kill pid`: you can kill the pid, followed by a number, this is a very gentle kill

  * `kill -l`: view the parameters of kill
  * `kill -1 httpd_pid`: do not let the server disconnect, and can change the configuration file
  * `kill -9 pid`: kill uncontrolled processes very violently

* `pkill name`: You can kill multiple trips, followed by the relevant name of the input trip, and the trip that contains the name will be deleted

* `jobs`: view background execution jobs

* `fg 1`: throw the first work performed by the background to the foreground

* `bg 1`: let the first work executed in the background continue to execute

* `sleep 60`: make the program pause for 60 seconds, you can use `sleep 60 &` to make the program run in the background

* `sudo !!`: !! represents the previous command