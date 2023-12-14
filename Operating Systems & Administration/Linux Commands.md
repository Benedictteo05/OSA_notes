**Help**
- `man`

**Display text**
- `echo`

**Print working directory**
- `pwd`

**List directory contents**
- `ls`

**Move/Rename**
- `mv`

**Switch user**
- `su`

**Change password**
- `passwd`

**Command in root**
- `sudo`

**Date**
- `date`

| Commands| Description|
|-------------|---------|
|`%a`|Weekday (e.g. Sun)|
|`%A`|Weekday (e.g. Sunday)|
|`%b`|Month (e.g. Jan)|
|`%B`|Month (e.g. January)|
|`%d`|Day (e.g. 21)|

**Arithmetic**
- `bc`
- Change decimal point:
	- `scope=n`

**History**
- `history`
- Repeat last command:
	- `!!`

**File permissions**

|Permissions|command|
|---|--|
|Read|r|
|Write|w|
|Execute|x|

|Users|Description|
|---|----|
|User|u|
|Group|g|
|Others|u|

|Character|FileType|
|----|----|
|d|Directory|
|-|File|
|\||Link|

**Example:**
```
>> ll
drwxr-xr-x. 2 student student 40 Aug

'd' - Directory
'rwx' - User permission
'r-x' - Group permission
'r-x' - Others permission
'.' - no presence of ACL ('+' if there is) 
'2' - no. of hard links

```

**Change mode**
- `chmod`
```
drwxr-xr-x. 2 student student 40 Aug 24 2019 Desktop
>> chmod g-rx Desktop
>> OR
>> chmod 705 Desktop
drwx---r-x. 2 student student 40 Aug 24 2019 Desktop

'g' - Group user
'-[r|w|x]' - remove permission 

//shortcut to adding permissions
>> chmod g+x Desktop
```

**Hard Links**
- Pointer to the data
- `ln`

**Soft Link (Symbolic Link)**
- Pointer to the file 
- `ln -s`
