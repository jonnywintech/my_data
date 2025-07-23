command for listing files and owners read,write and execute permissions
```bash
ls -l
```
>>>> echo
drwxrwxr-x 2 nana nana 4096 Mai

d rwx  rwx   r-x
x xxx| xxx | xxx |
Owner|Group|Other
>>> legend

- regular file
d directory
c character device file
l symbolic link
  etc.

>>> permissions
|-----|
|r w x|
|-----|
r - read
w - write 
x - execute
- - no permission



also hidden files and folders
```bash
ls -la
```

change owner of file 
```bash
chown <user>:<groupname> <filename>
```
for changing some files is needed sudo command

changing reading writing and executing permissions
```bash
chmod -x api
```
>>> it removed execute permission for all users and groups

changing permission for specific user
```bash
sudo chmod g-w config.yml
```
>>> removed write permsission for group

so basicly u - user  g - group o - other

adding permissions with sign + 
removing permissions with sign -

change whole block of permission taking group for example 
```bash
sudo chmod g=rwx config.yml
```

most common is adding numeric values
we have 3 blocks user, group, other
0 - no permission - symbol >>> ---
1 - execute       - symbol >>> --x
2 - write         - symbol >>> -w-
3 - execute+write - symbol >>> -wx
4 - read          - symbol >>> r--
5 - read+execute  - symbol >>> r-x
6 - read+write    - symbol >>> rw-
7 - read+write+ex - symbol >>> rwx

```bash
#example
sudo chmod 777 config.yml
```


