# PowerShell-Exercises

Lab questions from *Learn PowerShell in  a Month of Lunches*

# 3.8 Lab

2. Can you find any cmdlets capable of converting other cmdlets' output into HTML?
- get-command -noun *html*

3. Are there any cmdlets that can redirect output into a file?
- get-command -noun *file*
- The cmdlet that can do this is Out-File

4. How many cmdlets are availble for working with processes?
- get-command -noun *process*

5. What cmdlet might you use to set to a PowerShell breakpoint?
- help Set-PS*
- get-command -noun *breakpoint* 

6. You've learned tha aliases are nicknames for cmdlets. What cmdlets are available to create, modify, export, or import aliases?
- help *alias*
- get-command -noun *alias*

7. Is there a way to keep a transcript of everything you type in the shell, and save that transcript to a text file?
- Start-Transcript and Out-File

8. Getting all processes can be overwhelming. How can you get processes by the name of the process?
- get-process -name [process name]

9. Is there a way to tell Get-Process to tell you the user who started the process?
- Use the -IncludeUserName parameter
- Example: Get-Process -name firefox -IncludeUserName

10. Is there a way to run a command on a remote host?
- Invoke-Command

11. Examine the help file for the Out-File cmdlet. The files created by this cmdlet default to a width of how many characters? Is there a parameter that would enable you to change that width?
- Default width: 80 characters
- Parameter to use to set the width: -Width

12. By default, Out-File overwrites any existing file that has the same filename as what you specify. Is there a parameter that would prevent the cmdlet from overwriting an existing file?
- Parameter: -NoClobber

13. How could you see a list of all aliases in PowerShell?
- Command: Get-Alias

14. Using both an alias and abbreviated parameter names, what is the shortest command line you could type to retrieve a list of commands with the word process in the name?
- gmc -na *process*

15. How many cmdlets are available that can dea with generic objects?
- gcm -noun *object*
- There are 10 cmdlets 

16. This chapter briefly mentioned arrays. What help topic could tell you more about them?
- help array

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

# 5.6 Lab

1. Create a new directory called Labs.
- New-Item -path C:\Users\Admin\Desktop -itemtype directory -name Labs

2. Create a zero-length file named /Labs/Test.txt.
- new-item -path C:\Users\Admin\Desktop\Labs -itemtype file -name Test.txt

3. Is it possible to use `Set-Item` to change the contents of /Labs/Test.txt to `-TESTING`? Or do you get an error? If you get an error, why?
- It is not possible. `Set-Item` cannot be used to change/modify the contents of a file.

4. Using the Environment provider, display the value of the system environment variable `PATH`.
- Set-Location Env: -> Get-ChildItem
or 
- Get-Item Env:Path

5. Use help to determine what the differences are between the `-Filter`, `-Include`, and `-Exclude` parameters of Get-ChildItem.
- For `-Filter`, the only installed provider that supports this parameter is the `FileSystem` provider. `-Recurse` needs to be used with `-Include` and `-Exclude`.
