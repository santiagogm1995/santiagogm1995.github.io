## Logging into Cloud Foundry with a custom script.

A couple of days I made a script that I used to log into Cloud Foundry. I created this script to automate the process of logging.

---

### Prerequisites.

You'll need to install the folowing:

- Cloud Foundry CLI (In my case i used [Cloud Foundry CLI v6.0.0]) : It's needed to login to the cloud foundry.
- Obviously you'll need to have a cloud foundry account.

#### Script code:

```powershell
#Login in account
Param (
    [string] $user = $null
) 

$url = "https://api.cf.eu10.hana.ondemand.com"

$pass = [System.Environment]::GetEnvironmentVariable('CF_PASSWORD')

if ($pass -eq $null -or $user -ne [String]::Empty) {
    $pass = Read-Host 'What is your password?' -AsSecureString
    $pass = [Runtime.InteropServices.Marshal]::PtrToStringAuto(
        [Runtime.InteropServices.Marshal]::SecureStringToBSTR($pass))
}

If ($user -eq [String]::Empty) { $user = "youUser@gmail.com" }

cf login -a $url -u $user -p $pass
```
