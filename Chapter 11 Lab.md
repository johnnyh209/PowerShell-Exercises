# 11.10 Lab

1. Display a table of processes that includes only the process names, IDs, and whether they're responding to Windows (the `Responding` property has that information). Have the table take up as little horizontal room, but don't allow any information to be truncated.<br>
![Screenshot 2024-01-03 143319](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/e153b1e0-9710-412e-968e-d79847f415b8)

2. Display a table of processes that includes the process names and IDs. Also inlcude columns for virtual and physical memory usage expressing thosde values in megabytes (MB).<br>
![Screenshot 2024-01-03 143826](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/92a684be-1262-48da-8f2a-40927f2e42ce)

3. Use `Get-Module` to get a list of loaded modules. Format the output as a table that includes, in this order, the module name and the version. The column headers must be `ModuleName` and `ModuleVersion`.<br>
![Screenshot 2024-01-03 145106](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b71e79af-f865-442f-bfff-1502c1a17fca)

4. Use `Get-AzStorageAcount` and `Get-AzStorageContainer` to display *all* of your storage containers so that a separate table is displayed for storage containers that are accessible to the publi and storage containers that are not.<br>
- Get-AzStorageAccount | Get-AzStorageContainer | Format-Table -GroupBy PublicAccess

5. Display a four-column-wide list of all directories in the home directory.<br>
![Screenshot 2024-01-03 145737](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/07a9a6fc-e782-4bb0-a2bb-f2dfd5a682fe)

6. Create a formatted list of all .dll files in `$pshome`, displaying the name, version information, and file size. Powershell uses the `Length` preoperty, but to make it clearer, your output should show `Size`.<br>
![Screenshot 2024-01-03 181552](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/55e15396-83a0-4686-8fa2-37e0d110afb9)
