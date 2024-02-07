# 19.8 Lab

The following command is for you to add a script. You should first identify any elements that should be parameteriezed, such as the computer name. Your final script should define the parameter, and you should create comment-based help within the script. Run your script to test it, and use the `Help` command to make sure your comment-based help works properly. Don't forget to read the help files referenced within this chapter for more information. Here's the command:

```
Get-CimInstance -classname Win32_LogicalDisk -Filter "drivetype=3" |
Where {($_.FreeSpace / $_.Size) -lt .1} |
Select -Property DeviceID,FreeSpace,Size
```

<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f507c2a9-6a5a-4be8-aec9-138191c7239f" Width="700" />
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8be4b074-763e-4dfb-937c-93839b729ae7" Width="700" />
