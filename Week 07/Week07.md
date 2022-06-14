# LINUX Week 07

### /etc 
* Most important file in linux system 
* Like: etc/passwd(su , cd etc , more passwd) , user's information, ex:  
    * user(username):x:1000(P id):1000(G id):user(fullname):/home(家目錄)/user:/bin(SHELL)/bash 

* etc/shadow , user's hashed password, hash is 1 way encryption,  
    * user(username):xmo21C@Ck3o2X#@(hashed password): 
* A cat /etc/resolv.conf 
    * A place to edit the DNS setting 

### /usr 
* User resource , place to put third party software 
* /usr/bin 
    * "exe" file store here 

A awk -F: '{print $1,$7}' /etc/passwd 
* A awk default is separate by space or tab, by setting "-F:" mean separate by ":" 

john the ripper 
* A application for decryption 

A pwd or echo $PWD 
* To know where you are 
* pwd is command 
* echo $PWD is environmental variable (環境變量) 

Changing the port number of server 
* Method 1 
    * Install with "yum install httpd" 
    * Start the serverwith  "systemctl start httpd" 
    * Then go and change the Listen80 to Listen8080 in the file with command "/etc/httpd/conf/httpd.conf" 
* Method 2 
    * "cd /etc/httpd" , "ls" , "cd conf" to enter the file that store server's information , use "gedit" to edit the port at Listen 

"cd /etc/" , "cat inittab" 
* A file to know when start the computer will enter which mode, text:graphical 

A netstat -tunlp | grep 80 
* To check network status, t: tcp connection result , n: show in number(without n will show name) 

"mkdir testdir" 
* Create a directory name testdir 
* "sudo yum install tree" 
* "tree testdir" 
* "chmod 500 testdir" , from dr --> dr-x 
* "chmod 700 testdir", from dr-x --> drwx 

Ctrl + c </br>
"sudo kill -9 15132" 
* -9 means force 
* 15132 is pidid 

"touch a" :create a file 'a' (if there is not file 'a'),also can use to change the file's time </br>
"ls -l a" </br>
"ln a link" </br>
"ls -l a link" </br>
* "ls -l a" 
    * Will show 2  

"ln -s zz softlink" 
* Will show 1 , is a symbolic link 

"cp" 
* Use to copy and paste file 
* "cp a b" , copy 'a' and paste it and rename to 'b' 
* Also can use with relative path, like "cp ./a ../../tmp/b" 
* Use "cp -r testdir/ /tmp" , to copy the whole 'testdir' directory and paste into 'tmp' directory, "-r" is recursive 

"mv" 
* Rename a file name 

"rm" 
* Remove a file, system will ask sure? 
* Add -f (force) like, "rm -f a" will remove 'a' file without asking 
* "rm -rf /tmp/testdir" , force to remove a directory, '-r' including everything under the directory 
* "rmdir" use to remove empty directory 

"cat /etc/passwd more" 
* Only next, only scroll down 

"cat /etc/passwd less" 
* Can be next and previous, can scroll up and down 

"tail -f a" 
* '-f' is follow, if file 'a' get changes, it will show immedially  

FTP 
* <img src="1.png" alt="1" title="1" width="900" />
* Port:21 , passwd: user1234 