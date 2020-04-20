# Instructions to install the what-if PS module

## Install preview version

To install the preview module, run:
```PowerShell
Install-Module Az.Resources -RequiredVersion 1.12.1-preview -AllowPrerelease
```

## Uninstall alpha version
If you previously installed an alpha version of the what-if module, uninstall that module. The alpha version was only available to users who signed up for an early preview. If you didn't install that preview, you can skip this section.

1. Run PowerShell as administrator
2. Check your installed versions of the Az.Resources module.
```PowerShell
Get-InstalledModule -Name Az.Resources -AllVersions | select Name,Version
```

3. If you have an installed version with a version number in the format 2.x.x-alpha, uninstall that version.
```
Uninstall-Module Az.Resources -RequiredVersion 2.0.1-alpha5 -AllowPrerelease
```

4. Unregister the what-if repository that you used to install the preview.
```
Unregister-PSRepository -Name WhatIfRepository
```
