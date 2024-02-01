# 10.9 Lab

1. Would the following command work to retrieve a list of commands from modules that star with Microsoft.* on the current machine? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
   ` Get-Command -Module (Get-Module -ListAvailable -Name Microsoft.* | Select-Object -ExpandProperty name)`
- This command should work. Starting within the parenthesis, the `Get-Module` command will return a list of modules (found in the PSModulePath) using the `-ListAvailable` parameter with names starting with Microsoft using the `-Name` parameter. What is returned is then piped into `Select-Object` with the `-ExpandProperty` parameter with the value `name` assigned to it. This should then return the names of the modules from the list created by `Get-Module`. What we then effectively get is `Get-Command -Module [Array of the names of modules with that starts with Microsoft.]` and the `-Module` parameter "specifies an array of modules" according to Microsoft's documentation.

2. Would this alternative command work to retrieve the list of commands from the same modules? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.
   `Get-Module -ListAvailable -Name Microsoft.* | Get-Command
- This will not work because the values by `Get-Module` does not make sense to `Get-Command`.
![Screenshot 2023-12-29 114104](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/a380e53c-f903-4a5d-8ba0-5f288c10529d)

3. Would this set the subscription in the Azure context? Consider if `Get-AzSubscription` retrieves multiple subscriptions.
   `Get-AzSubscription | Select-AzSubscription`
- The given command will set the subscription. If Get-AzSubscription returns multiple subscriptions and the user does not specify one for Select-AzSubscription using the `-SubscriptionName` parameter, the last subscription on the list will be the one that is set.

4. Write a command that uses pipeline parameter binding to retrieve the first subscription and set that in the Azure context. Don't use parentheses.
- Get-AzSubscription | Select-Object -First 1 | Select-AzSubscription

5. Write a command that uses pipeline parameter binding to retrieve the first subscription and set that in the Azure context. Don't use pipeline input; instead, use a parenthetical command.
- Select-AzSubscription -SelectionObject (Get-AzSubscription | Select-Object -First 1)

6. Sometimes someone forgets to add a pipeline parameter binding to a cmdlet. For example, would the following command work to set the subscription in the Azure context?
  `mySubscriptionName | Select-AzSubscription`
- The above command will not work. If you look at the help for `Select-AzSubscription` you will see that the `-Subscription` parameter does not support/accept pipeline input.
![Screenshot 2023-12-29 153246](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/62baa4c0-fd10-4996-b153-93e3efeb842b)
