
# Remove-CrmOrganization

## Synopsis
Deletes an existing on-premise CRM organization from a local CRM server.

## Description
This function deletes an on-premise CRM organization on a local CRM server by deleting the CRM organization and deleting the SQL database.

## Parameters
| Parameter  | Type | Description | Required? | Default Value |
|---|---|---|---|---|
| Name | String | The name of the database and organization to delete | true | |
 | SqlServerName | String | The name of the SQL server to perform the database deletion operation on | true | |

## Examples

## Example 1
This example shows how to delete an organization named Northwind on the SQL server named dyn365.contoso.com.
```powershell
Remove-CrmOrganization -SqlServerName dyn365.contoso.com -OrganizationName Northwind
```
