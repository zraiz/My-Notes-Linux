# LINUX Week 11

集縮比 
* For more efficient network usage 

PT test 
* 滲透測試 
* Test your system security leak 

堆疊(stacking) 
* Can have more bandwidth and FT at the same time 

<img src="1.png" alt="1" title="1" width="900" />

Base64 encoding(c.txt) 
* End with a "=" sign 

Start ssh in kali linux 
* A systemctl start sshd (fail) 
* A /etc/init.d/ssh start (starting) 

a.zip 
* Using kali 
* Fcrackzip -v -b -u -l 3-8 -cl a.zip 
* Wait till done 

Example of executing a file in linux 
* A echo "echo hi" > a.sh //put "echo hi" in a.sh file 
* A chmod +x a.sh // add executable permission to the file a.sh 
* A ./a.sh //execute the file a.sh 
   *  "./" is for secure purpose, means execute the file in current directory  

A file 
* To tell you what attributes of the file 
```
ex:`file a.sh`
```
* will show a.sh: ASCII text 

A which 
```
`which date` 
``` 
* will show the path of the executable file "date" 
* Only for executable file 

A echo $PATH 
* Will search for every default directory only, if you create a new directory you need to use absolute path to execute the file 

Or 
```
`export PATH=$PATH:/home/user/mybin`   
```
 
```
`gedit .bashrc`  

Put `export PATH=$PATH:/home/user/mybin` 
```
And now you can use at every terminator 
```
`. .bashrc` to let the recently changes on `.bashrc` work.  
```

A df -h 
* Will use familiar unit(M,G), if only
```
`df`  
```
* will use no unit 
* To check partition usages 

A du 
* To check the directory usages 
```
`du -sh /home/user` 
```
will show the summary(s), in familiar unit(h) of the directory (/home/user) 

0,1,2 in linux 
* 0: Standard input 
* 1: Standard output 
* 2: Standard Error output 