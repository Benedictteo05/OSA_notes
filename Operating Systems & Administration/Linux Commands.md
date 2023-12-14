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
drwxr-xr-x. 2 student student 40 Aug
>> chmod g-rw meNot
drwx--xr-x. 2 student student 40 Aug 24 2019

'g' - Group user
'-[r|w|x]' - remove permission 

drwx

```