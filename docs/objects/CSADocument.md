# CSADocument

This object gives access to a ChronoScan document object.

A ChronoScan document contains documents and his data (pages and fields).

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
			for (int x = 0; x < Batch.DocumentsCount; x++)
			{
				CSADocument Doc = Batch.GetDocument(x);
				if (Doc != null)
				{
					Console.WriteLine("\t\t\t\tGuid: {0}", Doc.Guid);
					Console.WriteLine("\t\t\t\tPages: {0}", Doc.PageCount);
					Console.WriteLine("\t\t\t\tSrcDoc: {0}", Doc.GetFieldValue("SrcDoc"));

					if (Doc.ValState == "OK")
						Console.WriteLine("\t\t\t\tDocument VALIDATED");
					else 
						Console.WriteLine("\t\t\t\tDocument with ERRORS: "+Doc.ValStateInfo);
				}
			}
		}
	}
}
```
---
## CSADocument methods
---
### method::GetFieldValue
>Get a named field value
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|FieldName			|Field name to retrieve|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
### method::SetFieldValue
>Set field value of the specified value.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|FieldName			|Field name to retrieve|
|Value				|New value|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|
---
## CSADocument properties
---
### prop::Guid (get,string)
>Get batch name.
### prop::ValState (get,string)
>"OK" if the document is validated
### prop::ValStateInfo (get,string)
>A string describing the document status
### prop::PageCount (get,bool)
>Number of pages of the document
### prop::Pages (get,array)
>An array of [CSAPage](./objects/CSAPage) objects
