# LINUX Week 06

### nmap  

* Use to scan the machine and get the information, first get your ip adddress(192.168.157.156) 
* A sudo apt-get install nmap 
* Or 
* A sudo apt install nmap 
* Second scan with nmap, 
* A nmap -A 192.158.157.0/24 
* Now you can get the ip address(192.168.157.128) of the target machine 
* A ssh user1@192.168.157.128 --> now you can try the password of user1 
* Or 
* Using hydra 

### hydra  

* A sudo apt install hydra 
* A gedit  
* A hydra -L user.txt -P passwords.txt -t 4 192.168.157.128 ssh 
* -L user.txt, the file contain user's name, -P passwords.txt, the file of possible passwords you want to try with 
* -t 4 , mean open 4 線程 to run to make it faster 

A whoami 
* To show which user you are, normal or super 

A hostname 
* To know which machine you are 

A pwd 
* Mean print working directory, it will show the directory path 
* Or 

A echo $PWD 
* Will show where you are now 

> ~ , this symbol mean home directory 

A cd ~ 
* Change to home directory 
* Or 
* A cd 

A cd .. 
* Previous layer directory 

A cd - 
* Previous directory 

A w 
* Who are on the systems 
* Is like who but provide more information, like what they are doing, what kind of resources are been used by them, where they from and when 

or </br>
A who 
* Who are on the system 
* tty is terrminal on the machine 
* pts is like 遠端 terminal login, like putty 

A w | grep pts | head -n 1 | awk '{print $8}' 
* grep pts, mean take the row that contain pts  
* head -n 1, mean get the first data from the top 
* awk '{print $8}' , mean print out the 8th column of the row. 

A echo $SHELL 
* To check what kind of shell that you are using 

A ls -l 
* Show file 

A ls -l -h 
* More information 

A ls -l -h -a 
* Show hidden files 
* File's name start with "." mean is a hidden file 
* A ls -ahl , is same with ls -l -h -a , is another format 

A man ls 
* Show manual page of ls 

A ls -alh /home 
* Show files and hidden files under the home directory 

A adduser tom 
* Add a new user --tom 

A "su - tom"  or "su tom" 
* Become user --tom, su : super user, it can change to different user to do something. 

A passwd 
* To change password 
* Normal user only can change the password for themselves, but super user can change password of any user "passwd user'sname" , simply use the command passwd and follow by the user's name 

A echo "12345678" | passwd --stdin tom 
* Change password for user --tom to 12345678 
* In centos, ubuntu not support 

### Console terminal 

* Ctrl + Alt + F1~F6 (to enter) 
* Have 6 virtual terminals 
* This will show 'pts' in "who" command, normal will show 'tty' , in Centos 

A shutdown -h +10 
* Shutdown after 10 mins 

A shutdown -r +10 
* Reboot after 10 mins 

A rm -rf * 
* rm: remove  
* -r: recursive, 子目錄, mean all directory(sub directory) 
* -f: force, no more interaction with user 
* *: mean all file 

192.168.60.3  </br>
/root/flag.txt ? </br>
Password generator 

Linux's file system 
* Everything is file, include physical device(hard disk) and software 
* Start from "/" (only 1 root)-> dev,bin,home,usr,var,sbin… 
* dev: c is character device, b is block device, device's directory 
* bin: common command, like ls is stored here, executable file, for normal user 
*  sbin: for super user 
* usr: Unit resource, 第三方系統軟體, third party software will be stored here. 
* var: 可變動性的資料 (web server, email server), variable kind of data will be stored here. 
* /etc: system 配置檔, server configuration file, system configuration file. 
    * resolv.conf , file that contain domain lane setting, you can change the domain lane server here. 

A cd /proc   
*  proc mean processor  
* A cat cpuinfo 
    * Show cpu's information 
* /pro/sys/net/ipv4 
* A cat ip_forward 
    * 0 mean not router function, 1 mean got router function 
    * cat mean check the content of it 