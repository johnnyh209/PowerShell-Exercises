# 7.7 Lab

1. Browse the PowerShell Gallery. Find a module or two that you think sounds interesting and install it.<br>
![Screenshot 2023-12-18 184103](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/58bf76b0-b0e8-4a59-9d1a-a4ce4752a754)

2. Browse the available commands for the module you just downloaded.<br>
![Screenshot 2023-12-18 184502](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/dd8b0689-882b-47c2-85cc-1d77d741ccbc)

3. Use the commands from section 7.2 to find and install (if needed) the latest version module by Microsoft for working with archives that contain the command `Compress-Archive`.<br>
- I first used the help command to assist in figuring out what module the `Compress-Archive` command is part of (which is `Microsoft.Powershell.Archive`).<br>
![Screenshot 2023-12-18 184800](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/564b3e74-84a0-4e9a-b604-5fe0dd868fcb)

- Then I installed the module using the `Install-Module` command with the `-Name` parameter to specify what module I want installed.<br>
![Screenshot 2023-12-19 123704](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/39bdd59e-cfb4-491c-b338-a7532abeb5b4)

- To check that I have installed the module, I used the `Get-Module` command. The `-ListAvailable` parameter is necessary because the module is not loaded.<br>
![Screenshot 2023-12-19 123734](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/5dc42fbf-8e50-4d53-88e4-a085bba7e2be)

4. Import the module you just installed.<br>
![Screenshot 2023-12-19 124245](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/4459da1b-085f-4f8c-969f-37591e5f2e89)

5. Create a Tests folder for the next step with 10 files in it, and name it ~/TestFolder.<br>
- I used the `New-Item` command to create a new folder, using the `-ItemType` parameter to specify the item as a directory (folder).<br>
![Screenshot 2023-12-19 124449](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/4413c7fe-b226-45be-9b23-2b73dcebf789)

- For easier management, I changed the directory in PowerShell to the TestFolder that I just created. Then I created 10 folders with 1 command. `("File1", "File2", "File3", "File4", "File5", "File6", "File7", "File8", "File9", "File10")` of the command specifies the name of the files that will be created. I then piped that to the `foreach` loop. This loop creates a new text file, and will be named based on what I have listed in the first part of this command (on the left side of the pipe).<br> 
![Screenshot 2023-12-19 124928](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/499c3e8e-1bae-40d5-8d80-e47b0bf46a72)

6. Use `Compress-Archive` to create a zip of the contents of ~/TestFolder, and name the archive `TestFolder.zip`.<br>
- Since I changed the directory to the TestFolder earlier, I need to go back to the previous directory. From there, I compressed `TestFolder` into a zip file.<br>
![Screenshot 2023-12-19 162335](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/503f85ee-9ed0-4ef6-aa2a-e40e737f27d3)

7. Expand the archive to ~/TestFolder2<br>
![Screenshot 2023-12-19 162628](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/cdc13337-e66d-4df7-bcdc-86c13fb09448)
![Screenshot 2023-12-19 162712](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8f600818-093b-441d-b75f-61335ec12499)

8. Use the `Compare-Object` and `Select-Object -ExpandProperty Name` to compare just the names of the files in the folders to verify you have the same files.<br>
![Screenshot 2023-12-19 201936](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/239a49a7-1f54-43c1-a7b9-d846f8ccbf43)
