# CSAClient

This object gives access to a ChronoScan Desktop/Enterprise Jobs&Batches and Configurations.

A client will always create a ***CSAClient*** object in order to access a ChronoScan configuration.

## Example
```cs
CSAClient client = new CSAClient();

if (client.CreateClient("ChronoScan.CHRONOSCAN_DOCS", "", "") == 1)
{
	Console.WriteLine("Connected!!");
}
else
{
	Console.WriteLine("Error: " + client.LastError);
}
```
---
## CSAClient methods
---
### method::CreateClient
>Create a client for the default or named configuration.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|**Configuration**	|*[optional]* Name of the ChronoScan configuration on ProgramData directory.	|
|**Username**		|*[optional]* Username for Enterprise edition connections.						|
|**Password**		|*[optional]* Password for Enterprise edition connections.						|

#### Return value

| Value				| Description		|
|-------------------|-------------------|
|1|Connection OK|
|0|Connection Error|

---
### method::Job
>Get an instance of the specified Job
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|**JobName**	|Job Name or Job Id as show in JobIds properties, a job id is a job name + a guid (Ex: "Sample Job Name@D096A2FA-D5DC-435C-B734-E44916AE01EA")|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|null|Error|
|[CSAJob](./objects/CSAJob)|A CSAJob object of the specified job|

---
## CSAClient properties
---
### prop::LastError (get,string)
>Get client last error description
---
### prop::Version (get,string)
>Get current API version
---
### prop::Directory (get,string)
>Get current configuration directory
---
### prop::Enterprise (get,bool)
>True if connected to an entreprise version
---
### prop::JobIds (get,string array)
>Get a list of configuration job Id's

Example:
```cs
var JobIds = client.JobIds;
foreach (String JobId in JobIds)
{
    Console.WriteLine("\t{0}", JobId);
}
```
---
### prop::ConfigurationsList (get,string array)
>Get a list of station available ChronoScan configurations

Example:
```cs
var Cfgs = client.ConfigurationsList;
foreach (String Cfg in Cfgs)
{
    Console.WriteLine("\t{0}", Cfg);
}
```
