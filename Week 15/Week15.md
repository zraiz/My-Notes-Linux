# LINUX Week 15

* find the files that have been changed 6 days ago but within14 days. Also the file size should be less than 1M. When you find those files copy them into /tmp. (One command to do the above mentioned job) 

<img src="1.jpeg" alt="1" title="1" width="900" />

* 2. find the files 
    * under /etcthat contains "localhost". 

<img src="2.jpeg" alt="2" title="2" width="900" />

* Counting accounts    

<img src="3.jpeg" alt="3" title="3" width="900" />

* Counting online user 

<img src="4.jpeg" alt="4" title="4" width="900" />

* Counting users in the system 

<img src="5.jpeg" alt="5" title="5" width="900" />

* `find` normally finding filename 
* `grep` normally grep file's ------content 

> Adding "mary" into group "rd" 

* `groupadd rd` 
* `useradd -g rd mary` 

> Adding "peter wang" 

<img src="12.jpeg" alt="12" title="12" width="900" />

* `useradd -c "peter wang" -g rd -G manager -u 1010 peter` 
* "-c" is for annotation  
* "-u" is for uid 
* "-g" is main group 
* "-G" is

* `awk`

<img src="6.jpeg" alt="6" title="6" width="900" />

* `-F:` is the column separate by ":" 

<img src="7.jpeg" alt="7" title="7" width="900" />

<img src="8.jpeg" alt="8" title="8" width="900" />

## Permission 

<img src="9.jpeg" alt="9" title="9" width="900" />

<img src="10.jpeg" alt="10" title="10" width="900" />

* If you want to delete the file, see if the directory has w

<img src="11.jpeg" alt="11" title="11" width="900" />
 
## Changing owner of file/directory 

* `chgown -R user.user test1` 

## Cracking password and user 

* https://kknews.cc/zh-tw/code/3vpeby3.html 
* https://snapcraft.io/install/john-the-ripper/centos 
* Installing john the ripper 

```
`sudo yum install epel -release` 
`sudo yum install snapd` 
`sudo systemctl enable --now snapd.socket` 
`sudo ln -s /var/lib/snapd/snap /snap` 
`sudo snap install john-the-ripper` 
```

//`sudo yum install *ssl -dev* 

* Combining shadow and passwd 
* Use john-the-ripper to crack password(need wordlists)  