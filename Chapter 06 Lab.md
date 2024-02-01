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

2. What happens if you run `Get-Command | Export-CSV commands.CSV | Out-File` from the console? Why does that happen?<br>
- Running that command gives an error. This is because for the `Out-File` command, the user is required to provide a name for the file that is to be created. Furthermore, having `Out-File` in the command above is redundant because we are already creating a CSV file using the `Export-CSV` command.<br>
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
