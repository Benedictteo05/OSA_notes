**Help**
- `man`

**Display text**
- `echo`

| Sub-directory | Description |
| ---- | ---- |
| `/bin` | Contains user executable programs. For example, the `ls` program is located in `/bin`. |
| `/sbin` | Contains system executable programs used by the root user and the system. For example, the **clock** program is located in `/sbin`. |
| `/lib` | Contains shared library files used by `/bin` and `/sbin`. |
| `/dev` | Contains special file system entries for devices attached to the system. |
| `/boot` | Contains the Linux kernel and bootloader programs. The Linux kernel program is typically known as "vmlinuz" |
| `/etc` | Contains system configuration files. Files contain user account information are located here. |
| `/proc` | Contains special files pertaining to the state of the running Linux system. These files are virtual files. |
| `/mnt` | Contains temporarily mounted file systems. |
| `/usr` | Contains programs that can be run any users of the system. |
|  |  |



**Print working directory**
- `pwd`

**List directory contents**
- `ls`

**VIM**
- **Quit** 
	- `:q!`

**Processes snapshot**
- `ps`

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
