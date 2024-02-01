# 4.10 Lab

1. Display a list of running processes.
- Get-Process

2. Test the connection to google.com or bing.com without using an external command like ping.
- Test-Conenction -TargetName google.com

3. Display a list of all commands that are of the cmdlet type.
- Get-Command -CommandType cmdlet

4. Display a list of all aliases
- Get-Alias

5. Make a new alias, so you can run `ntst` to run `netstat` from a PowerShell prompt.
- new-alias -name ntst -value netstat

6. Display a list of processes that begin with the letter `p`.
- get-process -name p*

7. Make a new folder (aka directory) using the `New-Item` cmdlet with the name of MyFolder1. Then do it again and call it MyFolder2.
- new-item -path C:\Users\Admin\Desktop -itemtype folder -name MyFolder1
- new-item -path C:\Users\Admin\Desktop -itemtype folder -name MyFolder2

8. Remove the folders from step 7 in a single command.
- remove-item -path C:\Users\Admin\Desktop\MyFolder*
