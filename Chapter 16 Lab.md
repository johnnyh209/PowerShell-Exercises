# 16.10 Lab

**Disclaimer:** Using VirtualBox, I was unable to get WinRM to work. While successfully enabling WinRM, anytime I try to use `Enter-PSSession`, an error is always returned. Thus for this, I chose to do everything locally because the concept is still the same. Though, I will provide a command that does fulfill what the question asks.

1. Create a background job that gets all processes that start with `pwsh` from two computers.

`Invoke-Command -ComputerName name1,name2 -ScriptBlock {Get-Process -Name pwsh} -asjob`<br>
![7L3SDzjVDP](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/0793b78e-9ada-46cb-9301-dfec3444a6b4)

2. When the job finishes running, receive the results of the job into a variable.<br>
![zwIzRR1LGB](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/c43097fd-0664-4918-a37b-dee3fca2cfcd)

3.  Display the contents of that variable.<br>
![kv7PMFmubb](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/2e8f4442-2633-4939-a3dd-0f4da6ed1afb)

4.  Export the variable's contents to a CLIXML file.<br>
![twJkSlNi6V](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/04e5bf85-e4b9-4f4b-b6d7-fd3738b6f5b0)

5. Get a list of all the services currently running on your local machine and save it in a variable `$services`.
![vNnmoJlbC3](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/6862b3e3-3b50-4185-97f3-b94abb21ba74)

6. Replace `$services` with just the bits and print spooler service. + 7. Display the contents of `$services`.<br>
**Disclaimer:** `-ErrorAction SilentlyContinue` was needed because running `Get-Service` returned errors because it was not able to query a handful of services.<br>
![wSCEpyMiJs](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/472ab280-4d5e-4607-8091-f6f533ff43cc)

8. Export `$services` to a CSV file.<br>
![gGFM3spFg9](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/355453a0-4bae-4ea2-b6c9-e8c2cb8d6316)
