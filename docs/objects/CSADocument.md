# CSADocument

This object gives access to a ChronoScan document object.

A ChronoScan document contains documents and his data (pages and fields).

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

### method::ProcessDocument
>Process a document
#### Parameters
|Name|Description|
|---|---|
|Operations|If empty default operations on the job will be executed. A list of custom operations can be send using ; as separator ex: "DESKEW;OCR;LANG_DETECT"|

##### Available operations for ProcessDocument

|Name|Description|
|---|---|
|DESKEW|Deskew the document page images|
|IMGPREPRO|Process the document page images|
|OCR|OCR the document pages with the configured engines|
|LANG_DETECT|Detect the document language|
|FULLTEXT|Prepara document for full text search|
|DOCCLASS|Excecute document classification module|
|PRETRIGGERS|Execute triggers before document type|
|PATTERNBTREAD|Search iTags before document type|
|TYPESPLIT|Split on known document types|
|TYPEDETECT|Detect document type|
|CLOUDPAT|Read eTags|
|PATTERNREAD|Read iTags after document type|
|FIELDREAD|Read OCR Zones|
|XGRIDREAD|Read line items grids|

#### Return value

|Value| Description|
|---|---|
|number|1 = ok, 0 = error|


---
### method::GetFieldValue
>Get a named field value
#### Parameters

|Name|Description|
|---|---|
|FieldName			|Field name to retrieve|

#### Return value

|Value| Description|
|---|---|
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
### prop::Barcodes (get,array)
>An array of [CSABarcode](./objects/CSABarcode) objects with barcodes found on current document.
