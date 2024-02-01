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

# 6.7 Lab

1. Create two similar, but different, text files. Try comparing them by using `Compare-Object`. Run something like this: `Compare-Object -Reference (Get-Content File1.txt) -Different (Get-Content File2.txt)`.

Contents of File 1:
`This is a text file.
What is a text file?
Why is a text file?`

Contents of File 2:
`This is a text file.
Where is a text file?
Why is a text file?`

![Screenshot 2023-12-15 160712](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/fe8f48d0-696b-47e1-8ed7-2657082191b8)

2. What happens if you run `Get-Command | Export-CSV commands.CSV | Out-File` from the console? Why does that happen?
- Running that command gives an error. This is because for the `Out-File` command, the user is required to provide a name for the file that is to be created. Furthermore, having `Out-File` in the command above is redundant because we are already creating a CSV file using the `Export-CSV` command.

![Question2](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/39bcde3f-d128-4362-a2b3-9b3d6756c4c7)

3. Apart from getting one or more jobs and piping them to `Stop-Job`, what other means does `Stop-Job` provide for you to specify the job or jobs you want to stop? Is is possible to stop a job without using `Get-Job` at all?
- It is possible to stop a job wihtout using `Get-Job`. `Stop-Job` has the parameter `-name` that you can use to stop a job. This means that you need to know the name of the job that you want to stop.

4. What if you want to create a pipe-delimited file instead of a CSV file? You'd still use the `Export-CSV` command, but what parameters would you specify?
- You would use the `-delimiter` parameter. By default, a comma will be used but you can specify `|`: `-Delimiter "|"`.

5. How do you include the type information in the # comment line at the top of an exported CSV file?
- You would use the -IncludeTypeInformation parameter.

6. `Export-Clixml` and `Export-CSV` both modify the system because they can create and overwrite files. What parameter would prevent them from overwriting an existing file? What parameter would ask whether you were sure before proceeding to write the output file?
- To prevent the overwriting of an existing file, use the `-NoClobber` parameter.
- To ask whether you were sure before proceeding to write the output file, use the `-Confirm` parameter.

7. The operating system maintains several regional settings, which include a default list separator. On US systems, that separator is a comma. How can you tell `Export-CSV` to use the system's default separator rather than a comma?
- You can use the `-UseCulture` parameter to use the system's default separator.


