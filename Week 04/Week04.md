# LINUX Week 04

Linux system </br>
3 layer style: kernel—>shell—>application 
 
Different type of Shell and applications become different type of distribution(Linux system), </br>
for examples: Ubuntu, centos, redhat, fedora, suse… 
 
Linux official website: kernel.org </br>
Mainline : latest version </br>
Stable : secure </br>
Long term : maintenance on going
 
A uname -r </br>
—> to check version of kernel  </br>
A uname-a </br>
—> more specific and information  of the system 

X86_64 : 64 bits operating system </br>
i386, i486, i586, i686 : 32 bits operating system 
 
A cd /boot </br>
A ls </br>
A ls vmlinuz* -l </br>
(vmlinuz*: * means wild chart characters（any word）,-l mean show in long version , so the whole command means everything start with vmlinuz in long version) 
 
vmlinuz -3.10.0-1127.el7.x86_64 </br>
-3.10.0 is kernel version </br>
-1127 is patch number, 1160 is new than 1127( 1160 have less bug than 1127) 
 
Default setting won’t install original code to user computer, only file after compilation. 
 
Shell is the middle of application and kernel, change the input of user to the language of kernel. 
 
A echo $SHELL </br>
—> To check shell version </br>
A echo $USER </br>
—> to check user </br>
A echo $PWD </br>
—> environmental status </br>
Example: a=6 , echo $a , will show ”6” 
 
**command in Linux system are space and case sensitive.  
 
Centos use to set up server. </br>
Ubuntu use to do research. 
 
Centos : yum install httpd  </br>
Ubuntu : apt install apache2 </br>
Both means install a web server.(some commands are different) 
 
Use yum install app name(after compilation, cannot edit) </br>
Download source code and set by ur own  
 
Red Hat is a company, help Fedora and Centos communities. </br> 
Redhat : purpose is stable, something happens can pay for the service of Red Hat. </br>
Fedora : find new things, test new things. </br>
Centos : purpose is stable, something happens u need to fix urself.  
 
Script development (Linux shell programming)： 
 
A gedit a.sh &(&Delegate executes in the background, whole command mean create a file with name a.sh and run at background ) 
 
A bash a.sh </br>
Or </br>
A chmod +x a.sh (mean change mode, plus execute permission to file a.sh) </br>
A ./a.sh (execute file a.sh) 
 
Linux The file extension is used for reference </br>
A ls -l a.sh(file name)  </br>
—> to check file permissions </br>
—> -rw-rw-r- -      </br>
—> first 3 means owner permission, middle 3 means group permission, last 3 means other ppl permission </br>
—> rw mean read and write, x mean execute permission. 
 
A cat a.sh </br>
—> to check content of file a.sh </br>
A > a.sh </br>
—> to clean file a.sh (put empty into file a.sh) </br>
A mv a.sh /home/user/bin </br>
—> move file into /home/user/bin
 
A echo $PATH </br>
—> show the paths of execution progress. </br>
When execute the command file, check /usr/local/bin if not found then check /usr/local/sbin and keep checking until found or not found. If command is include in Shell then it can be execute. 
 
A passwd  </br>
—>to change user password </br>
If super user  </br>
A passwd user’s-name </br>
—> to change any password of users. </br>
A useradd tom  </br>
—> to add a user with username tom  </br>
 
A ssh tom@localhost </br>
—> Login tom user at local host machine. 
