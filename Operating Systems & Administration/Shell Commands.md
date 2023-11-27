**Copy and Paste**
To copy and paste from CMD, use Mark (Ctrl + M), Copy (Enter), Paste (Ctrl + V)

**Clear screen**
`cls`

**Why are there 2 entries when `dir` command is used?**
- The directory with `.` refers to the current directory.
- The directory with `..` refers to the parent directory.

**Help**
`help | more` or `[dir | md] /?`

**Delete**
- Files: `del`
- Directory: `rd`

**Create**
- Directory: `md`
- File: `echo hello > hello.txt`

**Copy**
- Files: `copy hello.txt hello.bak`

**Sort**
- Sort input in descending order: `sort /r sort_data.txt`
- Sort input starting from 5th position: `sort /+5 sort_data.txt`

**Rename**
`rem`

**Redirecting outputs**
- Redirect to standard output: `1>`
- Redirect to standard error: `2>`

**Redirecting to devices**
- Input/ Output: `CON`
- Input/ Output (NUL device, suppress unwanted output): `NUL`

**Multiple Commands**
- Run commands in sequence, cmd1 then cmd2: `cmd1 & cmd2`
- Run cmd1 and if cmd1 is successful, then run cmd2: `cmd1 && cmd2`
- Run cmd1 and if cmd1 unsuccessful, then run cmd2: `cmd1 || cmd2`
- Group multiple commands: `()`
- Use to separate command parameters: `;` or `,`

| Shortcut| Description|
|----------|-----|
|`[datetime]`| Date or time|

