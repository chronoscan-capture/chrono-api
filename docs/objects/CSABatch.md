# CSABatch

This object gives access to a ChronoScan batch object.

A ChronoScan batch contains documents and his data.

## Example
```cs
var JobId = "Sample Job Name@D096A2FA-D5DC-435C-B734-E44916AE01EA";

CSAClient client = new CSAClient();

if (client.CreateClient() == 1)
{
	CSAJob Job = client.Job(JobId);

	if (Job != null)
	{
		var Batch = Job.LoadBatch("BatchName_1");
		if (Batch != null)
		{
			// Do your stuff
		}
	}
}
```
---
## CSABatch methods
---
### method::LoadFS
>Reload all data from disk from current batch
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
### method::Delete
>Delete current batch
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
### method::Save
>Save changes on disk.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
### method::Close
>Close&unlock current batch.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
### method::GetDocument
>Returns a [CSADocument](./objects/CSADocument) object of the specified document.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|Document			|0 based index of the document|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|null|invalid document index|
|[CSADocument](./objects/CSADocument)|The document object|
---
## CSABatch properties
---
### prop::Name (get,string)
>Get batch name.
### prop::DocumentsCount (get,number)
>Number of documents in the batch.
### prop::EntBatchStatus (get,string)
>Status of the batch on the Enterprise edition.
### prop::SplitManual (get,put,bool)
>Split documents manually.
### prop::SplitOnEachFile (get,put,string)
>Split documents each time source file changes.
### prop::batch_name (get,string)
>Base batch name for new batches
