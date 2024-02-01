# 9.5 Lab

1. This exercise will be about secrets management. DevOps engineers should be very familiar with this concept. The idea is simple: We have a bunch of sensitive information (passwords, connection strings, etc.) that we need to use in our commands, but we need to keep those secrets in a secure location. We also may want to share those secrets with other members on our team---and an email is not secure enough, folks!
The PowerShell team has recently been working on a module called Secrets Management to do just this. It's a generic module for interacting with any secret store that supports it. Some will be local secret stores like the macOS Keychain, and others will be cloud services like Azure Key Vault and HashiCorp Vault. Your goal is to grap this module, store a secret in yoru secret store of choice, and then retrieve it. If you use a cloud-based secret store, try to retrieve the secret from a different machine as the ultimate test.

* I started off with finding a module that deal with secrets management. Entering in `Find-Module *Secret*` showed the following:<br>
![Screenshot 2023-12-26 170906](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/03873e60-4222-49cd-88a4-45731a80863f)

* Recognizing that `Microsoft.PowerShell.SecretManagemnt` is the module I need, I installed said module:<br>
![Screenshot 2023-12-26 171023](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/cff36829-1001-430f-9b88-75de04b3f586)

* With the module installed, I needed to look at what commands it contains. At this point, I am looking for a command that allows me to setup a vault to store my secrets in.<br>
![Screenshot 2023-12-26 171209](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8b8edde5-b96e-49e2-a7b5-a38bf32bde63)

* Based on how self-explanatory its name is, I identified `Register-SecretVault` as the command needed to establish the vault. Though I am unsure of what parameters it has, I use the `Help` function to get a better understanding of its parameters and syntax.<br>
![Screenshot 2023-12-26 172023](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/35f7153d-6c98-47c4-83fa-711035e64f39)

* Looking through the help page, I figured that the `-Name` parameter would be all I need to successfully make a vault. However, I ran into an error because I did not have Microsoft.PowerShell.SecretStore. And so, I proceeded to install the missing module. SecretStore is needed because it is used to store secrets locally, which is my goal.<br>
![Screenshot 2023-12-26 172037](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/78c97b16-4f05-4ebb-bd6d-5ba01ba70efb)<br>
![Screenshot 2023-12-26 172111](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f55a1fbd-79b6-420b-9366-649c259c1c48)

* I ran the `Register-SecretVault` command again, this time with the `-ModuleName` parameter pointing to SecretStore. I am naming this vault `PracticeVault` to easily identify its purpose.<br>
![Screenshot 2023-12-26 172616](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/f7198b06-6267-4c3f-b295-023deffa62fd)

* I ran the `Get-SecretVault` command to make sure that the vault was created successfully.<br>
![Screenshot 2023-12-26 172657](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/1f8529d7-0ccc-44dc-9a39-c80348b26b32)

* I then ran the `Get-SecretStoreConfiguration` command to set a password for the vault.<br>
![Screenshot 2023-12-26 172744](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b82d3b80-ee1b-4e42-a8e7-afe9bf890cef)

* After that, I used the `Set-Secret` command to put a secret into the vault.<br>
![Screenshot 2023-12-26 173410](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/b3c09e2c-35d0-4683-8fd3-e0cdac4648b1)

* To retrieve the secret I just put into the vault, I used the `Get-Secret` command.<br>
![Screenshot 2023-12-26 173611](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/04a09fe4-e9ba-4c39-bc06-a979129003c1)
