
# Export-CrmSolutions

## Synopsis
Exports a list of solutions from a CRM organization.

## Description
This function exports a list of solutions from a CRM organization.

## Parameters
| Parameter  | Type | Description | Required? | Default Value |
|---|---|---|---|---|
| CrmConnectionParameters | Hashtable | A `[hashtable]` of parameters to construct a `[Microsoft.Xrm.Tooling.Connector.CrmServiceClient]` object. See `Get-CrmConnection` for the available parameters. | true | |
| PublishCustomizations | SwitchParameter | Publishes the customizations prior to exporting solutions when set to `$true`. | false | True |
| Solutions | PSObject[] | An array of `[PSCustomObject]` objects describing the solutions to export. See the examples for the data structure to create for each `[PSCustomObject]`. | false | |

## Examples

## Example 1
This example prepares connection parameters for the `-CrmConnectionParameters` parameter, an array of PSCustomObject objects for defining the solutions to export, and then passing them to the Export-CrmSolutions function.
```powershell
$CrmConnectionParameters = @{
    OrganizationName = 'contoso'
    ServerUrl = 'http://dyn365.contoso.com'
    Credential = [PSCredential]::new("contoso\administrator", ("pass@word1" | ConvertTo-SecureString -AsPlainText -Force))
}

$Solutions = @(
    [PSCustomObject]@{
        SolutionName = 'AdventureWorks'
        Managed = $false
        ZipFile = 'C:\temp\export\AdventureWorks.zip'
    },
    [PSCustomObject]@{
        SolutionName = 'AdventureWorks'
        Managed = $true
        ZipFile = 'C:\temp\export\AdventureWorks_managed.zip'
    }
)

Export-CrmSolutions -CrmConnectionParameters $CrmConnectionParameters -Solutions $Solutions
```
