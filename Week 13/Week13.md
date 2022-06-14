# LINUX Week 13

## 3 Most important command in linux 
```
`seg` 
`awk` 
`grep` 
``` 
```
`echo "hello world" | cat - 
`echo "hello world" | cat 
``` 
```
`cat /etc/passwd | grep "h$" 
`cat /etc/passwd | grep "^h" 
`cat httpd.conf | grep -v "^$" | grep -v "^#" 
```
```
`cat /etc/passwd | grep "^[hr]" 
`cat /etc/passwd | grep "[hr]$" 
`cat /etc/passwd | grep "^ro*" 
`cat /etc/passwd | grep "^r.*h$" 
```
```
`cat /etc/passwd | egrep "^ro?" 
`cat /etc/passwd | egrep "^ro+" 
```
```
`cat /etc/passwd | egrep "root|user" 
``` 

> Normal mode -> Edit mode 

```
`i,o,a` 
```
> Edit mode -> Normal mode 

```
`esc key` 
```

> Normal mode -> Command mode 

```
`:` 
```

In command mode 
```
`w` : write 
`q` : quit 
`wq` : write and quit 
`q!` : quit and give 
 up modified things 
``` 
## Command Pipeline

> Command Pipeline == |

* A pipe can connect a series of commands, meaning that the output of the first command will be used as the input of the second command, which will be piped to the second command, and the output of the second command will be used as the input of the third command. , and so on.
* e.g.  
```
ls /etc | wc -w
```
> View the number of files under etc (one file name counts as one word)
```
ls | grep "test"
```
> See if there is a test in the ls result
```
ifconfig ens33 | grep inet | grep -v inet6 | awk '{print $2}'
```
```
grep -v 
```
> Does not contain the following content
```
awk '{print $2}'
```
> Print the contents of the second column to the screen

```
`echo "tom" | passwd --stdin tom`
```
> Not everything can be piped (|), some require extra instructions to execute

## write system scripts

> checkuser.sh

Use 
```
which bash
``` 
to view the location of bash, which contains system scripts

```
#!/usr/bin/bash

id $1 1>/dev/null 2>&1    ## id 
result='echo $?'   ## result

if [ $result -eq 0 ]     ## result == 0 
then
	echo "$1 exists"   
else
	echo "$1 no exists"
fi
```

> usage

```
chmod +x ./checkuer.sh  ## give executable permission
./checkuser.sh user ## user exit
./checkuser.sh tom  ## tom doesn't exit
```

> getip.sh

```
#!/usr/bin/bash

ip=`ifconfig $1 | grep inet | grep -v inet6 | awk '{print $2}'`
eth=`ifconfig $1 | grep inet | grep -v inet6 | awk '{print $2}'`

echo "ip: $ip"
echo "mac: $eth"
```

> usage

```
chmod +x getip.sh
./getip.sh enp0s8  ## Put interface card name
```

## Find File

```
which
```
> Only find the executable file, the search file will only be found from the environment variable ($PATH).

    whereis

> Similar to "which", but "whereis" will give more information , more less to be use

    locate
> You can query any file, you can use part of the name to do the query, he is asking for the content of the database, so before executing, usually enter the

    updatedb
    updatedb
> Synchronize system data with database

    find
> Go to the disk to find one by one, you can search in any kind, provide the most functions, but also take the most time

    find /home -name jack

> Find the exact matching file/directory

    find /home -iname jack

> Adding the -i parameter can make the query case-insensitive. In many commands, -i represents this meaning

Use
```
-type d
```
> to specify the file type to look for
  * `d`: find directory
  * `i`: find link file
  * `f`: Find general files
```
find / -type f -name "*.txt"
```
> Find files in the current directory that are txt files
```
find . -type f -perm 0777
```
> Find files with all permissions open
  * rwx (4+2+1=7)、rw- (4+2=6)、r-x (4+1=5)、r-- (4)、-w- (2)、--x (1)
  * The preceding 0 means that `suid, sgid, and sticky` are not enabled (suid (4), sgid (2), stick(1)), which means special permissions
    * suid: Represents the highest authority when executing the file, and returns to its original identity after execution
    * sgid: applied in the general directory, in the directory with sgid permission, the creator and the file belong to the group of the directory
    * sticky: means that anyone can read and write the file, but the creator must have permission to delete it
    * The above function with rwx wide open can be written as 
    ```
    find . -type f -perm 7777
    ```
```
find . -type d -empty -exec rm -f {} \;
```
> Find all empty files, delete them all, {} represents the set of files found by the previous command, and you need to add `;` at the end, because it is a special symbol, you need to add a backslash

    find . -type f -name "*.txt" -exec chmod 644 {} \;`

> Find all .txt files, change permissions

    find . -type f -name ".*"

> Find hidden files

    find . -mtime +7 -mtime -14

> Modification time more than 7 days and less than 14 days

    find . -mmin -60

> Find files changed in the last hour, if you want to detect whether they have been accessed, use `-amin`

    find . -size +100M

> Find files larger than 100M

### cat file will change the access time of the file, which can be viewed with `stat filename`

</br>

**"the content in it will be executed first, and the value will be put in it. You can also use $() to indicate"**

## Linux Command

```
ls /tmp 1>dev/null 2>&1
```

> Put all the outputs of 2 (error and output to the screen) and 1 (correct and output to the screen) to the trash. This command only determines whether the previous command (before 1) can be executed normally or not.

    echo $?

> Whether it is executed correctly, non-0 means execution error

    id user

>  Check if this user exists

    chmod -x file

> Add executable permission to code

    echo "tom" | passwd --stdin tom

> passwd requires additional instructions to complete the pipeline

    chmod 777 filename

> All delegate permissions are enabled

* rwx (4+2+1=7)、rw- (4+2=6)、r-x (4+1=5)、r-- (4)、-w- (2)、--x (1)
* `ll` = `ls -l`

```
touch {a..z}.txt
```

> Create a.txt, b.txt, c.txt........z.txt

```
stat
```

> You can view the detailed information of the file, including the access time and modification time, and you can see if anyone has moved the data

