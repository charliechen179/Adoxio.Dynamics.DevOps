
# New-CrmPackage

## Synopsis
Creates a Package Deployer package for use with the Dynamics CRM Package Deployer.

## Description
This function creates a package for use with the Dynamics CRM Package deployer included in the Dynamics 365 SDK. The Package Deployer documentation is located online at https://msdn.microsoft.com/en-us/library/dn688182.aspx. A package is prepared from a ConfigurationMigration tool data zip file and one or more solution zip files. The package is by default stored in a folder named `Adoxio.Dynamics.ImportPackage` within the PackageDeployer folder included in the Dynamics 365 SDK.

## Parameters
| Parameter  | Type | Description | Required? | Default Value |
|---|---|---|---|---|
| DataZipFile | String | The path and filename to a Configuration Migration tool generated zip file. | false | |
 | SolutionZipFiles | String[] | A list file paths to solution zip files to be imported. The order is significant controls the order in which solutions will be imported into the CRM. | true | |
 | ImportData | SwitchParameter | Whether the data import should be performed by Package Deployer. Default is `$true`. | false | True |
 | PackageDllFile | String | The file path of the assembly (.dll) containing the package definition. Do not supply a value to use the default behavior of using `Adoxio.Dynamics.ImportPackage.dll` included in this module. | false | |
 | PackageFolder | String | The folder path to the package to import. Do not supply a value to use the default behavior of using the `Adoxio.Dynamics.ImportPackage` folder inside the CRM SDK's PackageDeployer folder. | false | `"$(GetPackageDeployerFolder)\Adoxio.Dynamics.ImportPackage"` |
 | OverwriteUnmanagedCustomizations | SwitchParameter | Whether to overwite unmanaged customizations to all solutions during import. Default is `$false`. | false | False |

## Examples

## Example 1
This example creates a package from a data zip file and 2 solution files.
```powershell
New-CrmPackage -DataZipFile 'C:\temp\packed\AdventureWorksData.zip' -SolutionZipFiles 'C:\temp\solutions\AdventureWorksEntities.zip','C:\temp\solutions\AdventureWorksProcesses.zip'
```

## Example 2
This example creates a package from 2 solution files. No data will be imoprted.
```powershell
New-CrmPackage -SolutionZipFiles 'C:\temp\solutions\AdventureWorksEntities.zip','C:\temp\solutions\AdventureWorksProcesses.zip'
```

## Example 3
This example creates a package uses the `-ImportData` switch to disable the data import from being performed by Package Deployer.
```powershell
New-CrmPackage -DataZipFile 'C:\temp\packed\AdventureWorksData.zip' -SolutionZipFiles 'C:\temp\solutions\AdventureWorksEntities.zip','C:\temp\solutions\AdventureWorksProcesses.zip' -ImportData:$false
```

## Example 4
This example creates a package and supplies a path to	 `-PackageDllFile` to change which DLL assembly Package Deployer will use when performing an import, and it supplies a path to `-PackageFolder` to control the output location of the solution zip files, data zip file, and generated `ImportConfig.xml` file.
```powershell
New-CrmPackage -DataZipFile 'C:\temp\packed\AdventureWorksData.zip' -SolutionZipFiles 'C:\temp\solutions\AdventureWorksEntities.zip','C:\temp\solutions\AdventureWorksProcesses.zip' -PackageDllFile 'C:\temp\MyCrmPackage.dll' -PackageFolder 'C:\temp\PackageOutput'
```
