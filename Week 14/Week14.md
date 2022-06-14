# LINUX Week 14

## Mount USB in Linux (exfat) 
* `lsblk -f` : to check the format 
* <img src="1.png" alt="1" title="1" width="900" />
* https://helloworld.pixnet.net/blog/post/47458574-centos-linux-mount-exfat-格式硬碟 

## format 

* `lsblk -f` 
* `yum install epel-release -y` : to install others software 
* `yum install ntfs-3g -y` 
* * <img src="2.png" alt="2" title="2" width="900" />

## Mount new storage disk in linux 

* Setting -> Storage -> SATA  
* <img src="3.png" alt="3" title="3" width="900" />
* Then click the disk with + and done the step 
* Checking: 
    * `dmesg | grep sd` 
    * Need to do partition --> format --> mount before use 
    * Partition: 
    * `fdisk /dev/sdb`
    * `n` 
    * `p` 
    * `1` 
    * Enter to select default(2048) 
    * `+5G` , default is to use full storage 
    * Done 
    * `p` to check 
    * `w` to save 
    * `q` to quit 
* Format: 
    * `mkfs -t xfs /dev/sdb1` 
    * `mkfs -t xfs -f /dev/sdb2` 
* Mount: 
    * `mount -t xfs /dev/sdb1 /media` 
    * `mount -t xfs /dev/sdb2 /media`     

## Chapter 7

<img src="4.png" alt="4" title="4" width="900" />

> gid=1000(user) is the main group, only user that join "10(wheel)" can access to super user 

<img src="5.jpeg" alt="5" title="5" width="900" />

> First line need to tell the shell, can use `which bash` </br>
`$1` mean the first parameter , `>/dev/null` cause don’t want to see the result </br>
`[ $? -eq 0 ]` means ($?==0) 

* Create user and password without interactive with terminal 

<img src="6.jpeg" alt="6" title="6" width="900" />

* Example of creating several user  

<img src="7.jpeg" alt="7" title="7" width="900" />

* In centos system 
    * "uid <1000" is system account 
    * "uid >= 1000" is normal user account 

<img src="8.jpeg" alt="8" title="8" width="900" />