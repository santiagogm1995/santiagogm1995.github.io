## Logging into Cloud Foundry with a custom script.

---

### Prerequisites.

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

If ($user -eq [String]::Empty) { $user = "santiago.gonzalez.mota@everis.com" }

cf login -a $url -u $user -p $pass
```
