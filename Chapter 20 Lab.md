# 20.7 Lab

This lab requires you to recall some of what you learned in chapter 19, because you'll be taking the following command, parameterizing it, and turning it into a script---just as you did for the lab in chapter 19. But this time, we also want you to make the `-ComputerName` parameter mandatory and give it a `host` alias. Have your script display verbose output before and after it runs this command too. Remember, you have to parameterize the computer name---but that's the only thing you have to parameterize in this case.

Be sure to run the command as if before you start modifying it, to make sure it works on your system:

```
Get-CimInstance win32_networkadapter -ComputerName localhost |
Where {$_.PhysicalAdapter} |
Select MACAddress,AdapterType,DeviceID,Name,Speed
```

To reiterate, here's your complete task list:
- Make sure the command runs as is before modifying it.
- Parameterize the computer name.
- Make the computer name parameter mandatory.
- Give the computer name parameter an alias, hostname.
- Add comment-based help with at least one example of how to use the script.
- Add verbose output before and after the modified command.
- Save the script as Get-PhysicalAdapters.ps1.

<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8f6c007f-3aa2-41bb-8e93-fce3fa72543e" Width="700" />
  
