# CSAJob

This object gives access to a ChronoScan job.

A ChronoScan Job contains main working parameters, like recognition modules, user fields, document types 
that allows to generate and process batches.

A client must use the method "Job" of the client object to access a job object (Ex: client.Job(JobId)).

## Example
```cs
var JobId = "Sample Job Name@D096A2FA-D5DC-435C-B734-E44916AE01EA";

CSAClient client = new CSAClient();

if (client.CreateClient() == 1)
{
	CSAJob Job = client.Job(JobId);

	if (Job != null)
	{
		Console.WriteLine("\t\tJob Name: {0}", Job.Name);
		Console.WriteLine("\t\tJob Id: {0}", Job.Id);
		Console.WriteLine("\t\tJob WorkDir: {0}", Job.WorkDir);
		Console.WriteLine("\t\tJob Description: {0}", Job.Description);
		Console.WriteLine("\t\tJob chrono_version: {0}", Job.chrono_version);
		Console.WriteLine("\t\tJob Base batch_name: {0}", Job.batch_name);
		Console.WriteLine("\t\tJob task_OnProcessing_cfg: {0}", Job.task_OnProcessing_cfg);

		Console.WriteLine("\t\tJob UserFields:");
		var Fields = Job.UserFields;
		if (Fields != null)
		{
			foreach (CSAUserField Field in Fields)
			{
				Console.WriteLine("\t\t\tField: {0}[{2}] ({1})", Field.Name, Field.DisplayName,Field.TypeName);
			}
		}

		Console.WriteLine("\t\tBatches list:");
		var Batches = Job.BatchesList();
		if (Batches != null)
		{
			foreach (CSABatch Batch in Batches)
			{
				Console.WriteLine("\t\t\tBatch Name: {0} ({1} document(s))", Batch.Name, Batch.DocumentsCount);
			}
		}
	}
}
```
---
## CSAJob methods
---
### method::BatchesList
>Get the list of batches of this Job.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|**Filter**	|*[optional]* Allows to filter the list.	|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|string array|An array of the found batches names|
---
### method::LoadBatch
>Load a batch by name
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|Batch name			|Batch name|
|allowsCreate		|option, default value = 0, allows system to create the batch if the name doesn't exist|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|null|Error|
|[CSABatch](./objects/CSABatch)|The batch object|
---
---
### method::CreateBatch
>Create a new batch on this job
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|BatchName			|New batch name. NOTE: Job "batch base name" will be used with this string to generate new batch name.|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|null|Error|
|[CSABatch](./objects/CSABatch)|The batch object|
---
## CSAJob properties
---
### Name (get,string)
>Get job name
### Id (get,string)
>Get job guid
### WorkDir (get,string)
>Get job working directory (where batches are stored for this job)
### Description (get,string)
>Job description
### chrono_version (get,string)
>ChronoScan version how saved this file
### batch_name (get,string)
>Base batch name for new batches
### task_OnProcessing_cfg (get,string)
>String showing the current job processing configuration
### UserFields (get,[CSAUserField](./objects/CSAUserField) array)
>Get a list of user fields for this job
