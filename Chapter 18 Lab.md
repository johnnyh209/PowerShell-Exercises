# 18.6 Lab
<br>
1. Close all open sessions in your shell.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/0cca376f-e990-478a-924b-858a770c222a" Width="700" />
<br>
<br>
2. Establish a session to a remote computer. Save the session in a variable named `$session`.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/079668f0-e712-464f-aa93-3c5a8dae8b57" Width="700" />
<br>
<br>
3. Use the `$session` variable to establish a one-to-one remote shell session with the remote computer. Display a list of processes and then exit.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/31da1ab3-5350-469e-91cb-ba9b9e4eae3a" Width="700" />
<br>
<br>
4. Use the `$session` variable with `Invoke-COmmand` and list the time zone of the remote machine.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/ad13cc6d-a548-4be6-a132-855290be70d9" Width="700" />
<br>
<br>
5. If you are on a Windows client, use `Get-PSSession` and `Invoke-Command` to get a list of the 20 most recent security event log entries from the remote computer.
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f3da9ac7-7c56-49eb-ab0b-e0dc2a67d986" Width="700" />
<br>
<br>
6. If you are on a macOS or Linux client, count the number of items in the `/var` directory.
- I do not have either client currently.
<br>
<br>
7. Use `Invoke-Command` and your `$session` variable to load the `ServerManager` module on the remote computer.
8. Import the `ServeManager` module's commands from the remote computer to your computer. Add the prefix `rem` to the imported commands' nouns.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/e84ce00c-064c-4018-b360-9a6ac352ae8c" Width="700" />
<br>
<br>
9. Run the imported `Get-WindowsFeature` command.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/e69fd00a-d6c5-4502-82d8-fdc395a59373" Width="700" />
<br>
<br>
10. Close the session that's in your `$session` variable.<br>
<img src="https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8a09c1f4-ff28-49fa-be47-9011c7c47ea9" Width="700" />
