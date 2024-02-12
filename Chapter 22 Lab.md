# 22.3 Lab

Below is the provided script:

```
param (
    [string]$ComputerName = 'localhost',
    [int]$MaxEvents = 5000,
    [int]$maxIDs = 5,
    [int]$logonEventNum = 4624,
    [int]$logoffEventNum = 4647
)
$eventsAndIDs = Get-WinEvent -LogName security -MaxEvents $MaxEvents -ComputerName $ComputerName |
Where-Object {$_.id -eq $logonEventNum -Or $_.instandid -eq $logoffEventNum} |
Select-Object -Last $maxIDs -Property TimeCreated,MachineName,Message
foreach ($event in $eventsAndIDs) {
    $id = ($event |
    parseEventLogMessage |
    where-object {$_.fieldName -eq "Account Name"} |
    Select-Object -last 1).fieldValue
    $domain = ($event |
    parseEventLogMessage |
    where-object {$_.fieldName -eq "Account Domain"} |
    Select-Object -last 1).fieldValue
    $props = @{'Time'=$event.TimeCreated;
    'Computr'=$ComputerName;
    'ID'=$id
    'Domain'=$domain}
    $output_obj = New-Object -TypeName PSObject -Property $props
    Write-Output $output_obj
}
function parseEventLogMessage()
{
    [CmdletBinding()]
    param (
        [parameter(ValueFromPipeline=$True,Mandatory=$True)]
        [string]$Message
    )
    $eachLineArray = $Message -split "`n"
    foreach ($oneLIne in $eachLineArray) {
        write-verbose "line:_$oneLine_"
        $fieldName,$fieldValue = $oneLine -split ":", 2
            try {
                $fieldName = $fieldName.trim()
                $fieldValue = $fieldValue.trim()
            }
            catch {
                $fieldName = ""
            }
            if ($fieldName -ne "" -and $fieldValue -ne "")
            {
                $props = @{'fieldName'="$fieldName";
                'fieldValue'=$fieldValue}
                $output_obj = New-Object -TypeName PSObject -Property $props
                Write-Output $output_obj
            }
    }
}
Get-LastOn
```

This script was designed to retrieve the latest log in and log off logs (5 by default, but users can determine that using the `-maxIDs` parameter. But upon running the provided script, I was immediately faced with two errors as seen below:<br>
![i7nlAWf6xM](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/8d03c747-34c2-47b0-8c12-e366cb31a338)

First, I did not have the required permissions to perform a `Get-WinEvent` operation. Secondly, the last line of the script, `Get-LastOn` is not a recognized cmdlet. What I did to remedy this was to close my current powershell session, removed the last line of the script, and opened a new PowerShell session with elevated privileges (Run as administrator). Running the script again, however, I am faced with another error as seen below:<br>
![tHurKdhEYh](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/65e5f666-25f9-47f7-83db-7646bb07adbc)

My solution for resolving this error was to change the location of the `parseEventLogMessage` function. I moved this function in between the `param` block and the `$eventsAndIDs` block. The **new** script is as follows:

```
param (
    [string]$ComputerName = 'localhost',
    [int]$MaxEvents = 5000,
    [int]$maxIDs = 5,
    [int]$logonEventNum = 4624,
    [int]$logoffEventNum = 4647
)
function parseEventLogMessage()
{
    [CmdletBinding()]
    param (
        [parameter(ValueFromPipeline=$True,Mandatory=$True)]
        [string]$Message
    )
    $eachLineArray = $Message -split "`n"
    foreach ($oneLIne in $eachLineArray) {
        write-verbose "line:_$oneLine_"
        $fieldName,$fieldValue = $oneLine -split ":", 2
            try {
                $fieldName = $fieldName.trim()
                $fieldValue = $fieldValue.trim()
            }
            catch {
                $fieldName = ""
            }
            if ($fieldName -ne "" -and $fieldValue -ne "")
            {
                $props = @{'fieldName'="$fieldName";
                'fieldValue'=$fieldValue}
                $output_obj = New-Object -TypeName PSObject -Property $props
                Write-Output $output_obj
            }
    }
}
$eventsAndIDs = Get-WinEvent -LogName security -MaxEvents $MaxEvents -ComputerName $ComputerName |
Where-Object {$_.id -eq $logonEventNum -Or $_.instandid -eq $logoffEventNum} |
Select-Object -Last $maxIDs -Property TimeCreated,MachineName,Message
foreach ($event in $eventsAndIDs) {
    $id = ($event |
    parseEventLogMessage |
    where-object {$_.fieldName -eq "Account Name"} |
    Select-Object -last 1).fieldValue
    $domain = ($event |
    parseEventLogMessage |
    where-object {$_.fieldName -eq "Account Domain"} |
    Select-Object -last 1).fieldValue
    $props = @{'Time'=$event.TimeCreated;
    'Computr'=$ComputerName;
    'ID'=$id
    'Domain'=$domain}
    $output_obj = New-Object -TypeName PSObject -Property $props
    Write-Output $output_obj
}
```
Running this script in the elevated PowerShell session was now a success:<br>
![UgSz9KkqeZ](https://github.com/johnnyh209/PowerShell-Exercises/assets/33064730/59c1f27a-b521-4c04-a09d-e8a2bd7d6694)

