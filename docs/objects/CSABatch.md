# CSABatch

This object gives access to a ChronoScan batch object.

A ChronoScan batch contains documents and his data.

## Example
```cs
var JobName = "Sample Job Name";

CSAClient client = new CSAClient();

if (client.CreateClient() == 1)
{
	CSAJob Job = client.Job(JobName);

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
### method::AddFileToBatch
>Add a file to current batch
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|File			|full path to a file|
|Pages			|(optional defaul "1-") Pages to extract when multipage (tiff/pdf) "1-"(all) "2-5" "1,2,8" "2-5,8,15-20"|
|Mode			|(optional defaul "auto") mode when pdf "auto", "extract"(extract images), "convert"(render)|
|Color			|(optional defaul 0) Color when render pdf, 0=Color, 1=B&W|
|Dpi			|(optional defaul 200) Dpi when render pdf|
|ExtractText		|(optional defaul 1) Extract text from pdf text layer, 1 = true, 0 = false|
|ExtractTextOmitInImages|(optional defaul 1) Omit pdf text layer when extracting images, keep when render, 1 = true, 0 = false|
|SavePdfPage		|(optional defaul 0) Save each pdf page attached to the ChronoScan page, it can be used when export, 1 = true, 0 = false|
|SavePdfDoc		|(optional defaul 0) Save pdf document attached to the ChronoScan document, it can be used when export, 1 = true, 0 = false|
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
|Operations|If empty default operations on the job will be executed. A list of custom operations can be send using ; as separator ex: "DESKEW;OCR;LANG_DETECT"|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|

>Check [CSADocument](./objects/CSADocument) for a complete list of operations.

---
### method::ProcessBatch
>Process all documents in the batch.
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|Document			|0 based index of the document|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|null|invalid document index|
|[CSADocument](./objects/CSADocument)|The document object|


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
