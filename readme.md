*********************
 Sudo for PowerShell
*********************

Automatic Installation
============
1. Run a Powershell as an administrator

2. Paste the following script

```powershell
$script_path="$HOME\Documents\Scripts"; if (!(test-path $script_path)) {New-Item -ItemType directory $script_path} if (!(test-path $profile)) { new-item -path $profile -itemtype file -force }". $script_path\sudo.ps1" | Out-File $profile -append; "function sudo(){if (`$args.Length -eq 1){start-process `$args[0] -verb `"runAs`"} if (`$args.Length -gt 1){start-process `$args[0] -ArgumentList `$args[1..`$args.Length] -verb `"runAs`"}}" | Out-File $script_path\sudo.ps1; powershell
```


3. Enjoy

Manual Installation
============
1. From PowerShell, create a $profile if you don't have one::
```powershell
    if (!(test-path $profile)) { new-item -path $profile -itemtype file -force }
```
2. Open the profile in notepad::
```powershell
    notepad.exe $profile
```   
3. Add the following line and save the file::
```powershell
   . /path/to/sudo.ps1
```   
4. sudo will be available in all new PowerShell windows

Usage
=====
``sudo application [arguments ...]``

![alt text](./img/powershell_sudo_notepad.PNG?style=centerme)

This repo is forked from 
=======
| https://github.com/stephenn/powershell_sudo

Original Author
=======
| Stephen Norum
| stephen@mybunnyhug.org
| http://www.mybunnyhug.org/

The only change made was adding the script to auto create sudo.ps1


