
# Expand-CrmData

## Synopsis
Extracts and unpacks a Configuration Migration tool generated zip file to individual files.

## Description
This function extracts a Configuration Migration tool generated zip file and unpacks the .xml files into separate files and folders, where each entity is stored in its own folder and each record is stored in its own .xml file inside the entity folder.

## Parameters
| Parameter  | Type | Description | Required? | Default Value |
|---|---|---|---|---|
| ZipFile | Object | The path and filename to the Configuration Migration tool generated zip file. | false | |
| Folder | Object | The folder path to store the unpacked records. | false | |

## Examples

## Example 1
This example extracts the data zip file exported from the AdventureWorks organization and unpacks the contents to the specified `-Folder`.
```powershell
Expand-CrmData -ZipFile 'C:\temp\export\AdventureWorksData.zip' -Folder 'C:\temp\data\AdventureWorks'
```
