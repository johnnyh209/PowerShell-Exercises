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

# 7.7 Lab

1. Browse the PowerShell Gallery. Find a module or two that you think sounds interesting and install it.
![Screenshot 2023-12-18 184103](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/58bf76b0-b0e8-4a59-9d1a-a4ce4752a754)

2. Browse the available commands for the module you just downloaded.
![Screenshot 2023-12-18 184502](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/dd8b0689-882b-47c2-85cc-1d77d741ccbc)

3. Use the commands from section 7.2 to find and install (if needed) the latest version module by Microsoft for working with archives that contain the command `Compress-Archive`.
- I first used the help command to assist in figuring out what module the `Compress-Archive` command is part of (which is `Microsoft.Powershell.Archive`). 
![Screenshot 2023-12-18 184800](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/564b3e74-84a0-4e9a-b604-5fe0dd868fcb)

- Then I installed the module using the `Install-Module` command with the `-Name` parameter to specify what module I want installed.
![Screenshot 2023-12-19 123704](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/39bdd59e-cfb4-491c-b338-a7532abeb5b4)

- To check that I have installed the module, I used the `Get-Module` command. The `-ListAvailable` parameter is necessary because the module is not loaded.
![Screenshot 2023-12-19 123734](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/5dc42fbf-8e50-4d53-88e4-a085bba7e2be)

4. Import the module you just installed.
![Screenshot 2023-12-19 124245](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/4459da1b-085f-4f8c-969f-37591e5f2e89)

5. Create a Tests folder for the next step with 10 files in it, and name it ~/TestFolder.
- I used the `New-Item` command to create a new folder, using the `-ItemType` parameter to specify the item as a directory (folder).
![Screenshot 2023-12-19 124449](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/4413c7fe-b226-45be-9b23-2b73dcebf789)

- For easier management, I changed the directory in PowerShell to the TestFolder that I just created. Then I created 10 folders with 1 command. `("File1", "File2", "File3", "File4", "File5", "File6", "File7", "File8", "File9", "File10")` of the command specifies the name of the files that will be created. I then piped that to the `foreach` loop. This loop creates a new text file, and will be named based on what I have listed in the first part of this command (on the left side of the pipe). 
![Screenshot 2023-12-19 124928](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/499c3e8e-1bae-40d5-8d80-e47b0bf46a72)

6. Use `Compress-Archive` to create a zip of the contents of ~/TestFolder, and name the archive `TestFolder.zip`.
- Since I changed the directory to the TestFolder earlier, I need to go back to the previous directory. From there, I compressed `TestFolder` into a zip file.
![Screenshot 2023-12-19 162335](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/503f85ee-9ed0-4ef6-aa2a-e40e737f27d3)

7. Expand the archive to ~/TestFolder2
![Screenshot 2023-12-19 162628](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/cdc13337-e66d-4df7-bcdc-86c13fb09448)
![Screenshot 2023-12-19 162712](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8f600818-093b-441d-b75f-61335ec12499)

8. Use the `Compare-Object` and `Select-Object -ExpandProperty Name` to compare just the names of the files in the folders to verify you have the same files.

![Screenshot 2023-12-19 201936](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/239a49a7-1f54-43c1-a7b9-d846f8ccbf43)

# 8.10 Lab

1. Identify a cmdlet that produces a random number.
![Screenshot 2023-12-22 151204](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/6212999e-4bef-4b0c-b7e3-ae37e9ea1fa1)

2. Identify the cmdlet that displays the current date and time
![Screenshot 2023-12-22 152616](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/7eddc253-86b5-441d-a942-b75101c3112f)

3. What type of object does the cmdlet from task 2 produce? (What is the *TypeName* of the object produced by the cmdlet?)
![Screenshot 2023-12-22 152707](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/74ef4178-5d1e-468d-bb1a-557d63611bc4)

4. Using the cmdlet from task 3 and `Select-Object`, display only the current day of the week in a table.
![Screenshot 2023-12-22 154135](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/6b1ec0cb-633d-4f40-9b2d-ec09f1f9a45a)

5. Identify a cmdlet that will show you all the times in a directory.
![Screenshot 2023-12-22 154942](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/d91f68ef-37d7-466a-8565-e4163fd663de)

6. Using the cmdlet from task 5, display all the times in the directory of your choice. Then extend the expression to sort the list by the time the items were created and display only the filename(s) and the date created. Rememeber that the column headers shown in a command's default output aren't necessarily the real property names---you'll need to look up the real property names to be sure.
![Screenshot 2023-12-22 155720](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f152df4b-c91c-4eb2-b65c-67bd714a6446)

7. Repeat task 6, but this time sort the items by the last write time; then display the filename, creation tme, and the last write time. Save this in a CSV file and an HTML file.
![Screenshot 2023-12-22 160523](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/92aa8c99-54a1-401b-a571-7c51f7acbd11)

# 9.5 Lab

1. This exercise will be about secrets management. DevOps engineers should be very familiar with this concept. The idea is simple: We have a bunch of sensitive information (passwords, connection strings, etc.) that we need to use in our commands, but we need ot keep those secrets in a secure location. We also may want to share those secrets with other members on our team---and an email is not secure enough, folks!
The PowerShell team has recently been working on a module called Secrets Management to do just this. It's a generic module for interacting with any secret store that supports it. Some will be local scret stores like the macOS Keychain, and others will be cloud services like Azure Key Vault and HashiCorp Vault. Your goal is to grap this module, store a secret in yoru secret store of choice, and then retrieve it. If you use a cloud-based secret store, try to retrieve the secret from a different machine as the ultimate test.

* I started off with finding a module that deal with secrets management. Entering in `Find-Module *Secret*` showed the following:
![Screenshot 2023-12-26 170906](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/03873e60-4222-49cd-88a4-45731a80863f)

* Recognizing that `Microsoft.PowerShell.SecretManagemnt` is the module I need, I installed said module:
![Screenshot 2023-12-26 171023](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/cff36829-1001-430f-9b88-75de04b3f586)

* With the module installed, I needed to look at what commands it contains. At this point, I am looking for a command that allows me to setup a vault to store my secrets in.
![Screenshot 2023-12-26 171209](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8b8edde5-b96e-49e2-a7b5-a38bf32bde63)

* Based on how self-explanatory its name is, I identified `Register-SecretVault` as the command needed to establish the vault. Though I am unsure of what parameters it has, I use the `Help` function to get a better understanding of its parameters and syntax.
![Screenshot 2023-12-26 172023](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/35f7153d-6c98-47c4-83fa-711035e64f39)

* Looking through the help page, I figured that the `-Name` parameter would be all I need to successfully make a vault. However, I ran into an error because I did not have Microsoft.PowerShell.SecretStore. And so, I proceeded to install the missing module. SecretStore is needed because it is used to store secrets locally, which is my goal.
![Screenshot 2023-12-26 172037](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/78c97b16-4f05-4ebb-bd6d-5ba01ba70efb)
![Screenshot 2023-12-26 172111](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f55a1fbd-79b6-420b-9366-649c259c1c48)

* I ran the `Register-SecretVault` command again, this time with the `-ModuleName` parameter pointing to SecretStore. I am naming this vault `PracticeVault` to easily identify its purpose.
![Screenshot 2023-12-26 172616](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f7198b06-6267-4c3f-b295-023deffa62fd)

* I ran the `Get-SecretVault` command to make sure that the vault was created successfully.
![Screenshot 2023-12-26 172657](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/1f8529d7-0ccc-44dc-9a39-c80348b26b32)

* I then ran the `Get-SecretStoreConfiguration` command to set a password for the vault.
![Screenshot 2023-12-26 172744](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b82d3b80-ee1b-4e42-a8e7-afe9bf890cef)

* After that, I used the `Set-Secret` command to put a secret into the vault.
![Screenshot 2023-12-26 173410](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b3c09e2c-35d0-4683-8fd3-e0cdac4648b1)

* To retrieve the secret I just put into the vault, I used the `Get-Secret` command.
![Screenshot 2023-12-26 173611](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/04a09fe4-e9ba-4c39-bc06-a979129003c1)

# 10.9 Lab

1. Would the following command work to retrieve a list of commands from modules that star with Microsoft.* on the current machine? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
   ` Get-Command -Module (Get-Module -ListAvailable -Name Microsoft.* | Select-Object -ExpandProperty name)`
- This command should work. Starting within the parenthesis, the `Get-Module` command will return a list of modules (found in the PSModulePath) using the `-ListAvailable` parameter with names starting with Microsoft. using the `-Name` parameter. What is returned is then piped into `Select-Object` with the `-ExpandProperty` parameter with the value `name` assigned to it. This should then return the names of the modules from the list created by `Get-Module`. What we then effectively get is `Get-Command -Module [Array of the names of modules with that starts with Microsoft.]` and the `-Module` parameter "specifies an array of modules" according to Microsoft's documentation.

2. Would this alternative command work to retrieve the list of commands from the same modules? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
   `Get-Module -ListAvailable -Name Microsoft.* | Get-Command
- This will not work because the values by `Get-Module` does not make sense to `Get-Command`.
![Screenshot 2023-12-29 114104](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/a380e53c-f903-4a5d-8ba0-5f288c10529d)

3. Would this set the subscription in the Azure context? Consider if `Get-AzSubscription` retrieves multiple subscriptions.
   `Get-AzSubscription | Select-AzSubscription`
- The given command will set the subscription. If Get-AzSubscription returns multiple subscriptions and the user does not specify one for Select-AzSubscription using the `-SubscriptionName` parameter, the last subscription on the list will be the one that is set.

4. Write a command that uses pipeline parameter binding to retrieve the first subscription and set that in the Azure context. Don't use parentheses.
- Get-AzSubscription | Select-Object -First 1 | Select-AzSubscription

5. Write a command that uses pipeline parameter binding to retrieve the first subscriptioin and set that in the Azure context. Don't use pipeline input; instead, use a parenthetical command.
- Select-AzSubscription -SelectionObject (Get-AzSubscription | Select-Object -First 1)

6. Sometimes someone forgets to add a pipeline parameter binding to a cmdlet. For example, would the following command work to set the subscription in the Azure context?
  `mySubscriptionName | Select-AzSubscription`
- The above command will not work. If you look at the help for `Select-AzSubscription` you will see that the `-Subscription` parameter does not support/accept pipeline input.
![Screenshot 2023-12-29 153246](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/62baa4c0-fd10-4996-b153-93e3efeb842b)

# 11.10 Lab

1. Display a table of processes that includes only the process names, IDs, and whether they're responding to Windows (the `Responding` property has that information). Have the table take up as little horizontal room, but don't allow any information to be truncated.
![Screenshot 2024-01-03 143319](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/e153b1e0-9710-412e-968e-d79847f415b8)

2. Display a table of processes that includes the process names and IDs. Also inlcude columns for virtual and physical memory usage expressing thosde values in megabytes (MB).
![Screenshot 2024-01-03 143826](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/92a684be-1262-48da-8f2a-40927f2e42ce)

3. Use `Get-Module` to get a list of loaded modules. Format the output as a table that includes, in this order, the module name and the version. The column headers must be `ModuleName` and `ModuleVersion`.
![Screenshot 2024-01-03 145106](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b71e79af-f865-442f-bfff-1502c1a17fca)

4. Use `Get-AzStorageAcount` and `Get-AzStorageContainer` to display *all* of your storage containers so that a separate table is displayed for storage containers that are accessible to the publi and storage containers that are not.
- Get-AzStorageAccount | Get-AzStorageContainer | Format-Table -GroupBy PublicAccess

5. Display a four-column-wide list of all directories in the home directory.
![Screenshot 2024-01-03 145737](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/07a9a6fc-e782-4bb0-a2bb-f2dfd5a682fe)

6. Create a formatted list of all .dll files in `$pshome`, displaying the name, version information, and file size. Powershell uses the `Length` preoperty, but to make it clearer, your output should show `Size`.
![Screenshot 2024-01-03 181552](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/55e15396-83a0-4686-8fa2-37e0d110afb9)
