# Instructions to install the what-if PS module
* Make sure you have access to https://dev.azure.com/AzDeploymentWhatIf/WhatIfModules
* Create a [PAT (Personal Access Token)](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops) to get command-line access to Azure DevOps Services
* Open PowerShell as administrator
* Run the following commands:

```PowerShell
$password = ConvertTo-SecureString "YOUR PAT FROM THE CREATING THE PREVIOUS STEP" -AsPlainText -Force
```


```PowerShell
$credential = New-Object System.Management.Automation.PSCredential "YOUR EMAIL FOR AZURE DEVOPS SERVICES", $password
```

```PowerShell
Register-PSRepository -Name WhatIfRepository -SourceLocation https://pkgs.dev.azure.com/AzDeploymentWhatIf/WhatIfModules/_packaging/WhatIfFeed/nuget/v2 -PackageManagementProvider Nuget -InstallationPolicy Trusted -Credential $credential
```

```PowerShell
Install-Module -Name Az.Resources -Repository WhatIfRepository -RequiredVersion 2.0.1-alpha1 -AllowPrerelease -AllowClobber -Credential $credential
```

* If you want to switch back to another installed version, simply run:
```PowerShell
Import-Module Az.Resources -RequiredVersion <version_number>
```

* To check if there's a newer version, do:
```PowerShell
Find-Module -Name Az.Resources -Repository WhatIfRepository -AllVersions -AllowPrerelease -Credential $credential
```

* If you are done testing the package, you may uninstall it by running:
```PowerShell
Uninstall-Module -Name Az.Resources -RequiredVersion 2.0.1-alpha1 -AllowPrerelease
```
