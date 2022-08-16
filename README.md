# Azure Role Based Access Control (RBAC)
# For Developers
## Morten la Cour




### Get Token from within a VM with Managed Identity

```powershell
Clear-Host;
$scope = "https://servicebus.azure.net/";

$token = Invoke-WebRequest "http://169.254.169.254/metadata/identity/oauth2/token?resource=$scope&api-version=2018-02-01" -Headers @{ "metadata" = "true" } | 
	Select-Object -ExpandProperty Content | 
	ConvertFrom-Json | 
	Select-Object -ExpandProperty access_token
	;
$token;
$token | Set-Clipboard;


```