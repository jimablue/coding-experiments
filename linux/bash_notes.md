# Bash Scripts Notes   

### Commands

```
history
ctrl-R //reverse search
```

### Shell

for login shell(first time in)
    /etc/profile sets up the environment configuration for all users.
    if .bash_profile exists, execute ( usually for env variable ) [then calls .bashrc]
    if not, look for .bash_login and .profile
for non-login 
    every non-login read .bashrc first 


#### Manage FIle system
wildcards

`
 *
 ?  
 []
`

```
mv -b directory1 directory2 //make a backup of the overwritten file

mkdir -p books/hemmingway/favorites //make subdir too
find /home -name puppies.jpg

```
#### Text
```
echo sometext > text.txt // >> for append
cat < peanuts.txt > banana.txt
ls /fake/directory > peanuts.txt 2>&1 //stdin stdout stderr
ls /fake/directory &> peanuts.txt
ls /fake/directory 2> /dev/null

ls -la /etc | less 
ls | tee peanuts.txt

cut -f 1 -d ";" sample.txt

env | grep -i User
ls /somedir | grep '.txt$'
```
cut (1)              - remove sections from each line of files  
paste (1)            - merge lines of files
head (1)             - output the first part of files  
tail (1)             - output the last part of files // -f to see realtime updates to the file
expand, unexpand

### System User 

```
useradd [OPTIONS] USERNAME
useradd -m username //create home dir  
passwd username
useradd -D
usermod -s SHELL USER //change usr shell

```
link for [usermod command](https://linuxize.com/post/usermod-command-in-linux/)
