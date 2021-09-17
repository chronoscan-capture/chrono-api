# CSADocumentType

This object gives access to a ChronoScan document type object.

A ChronoScan document type contains OCR zones and info to process an specific document type, named also as document template.

## Example
```cs
var JobId = "Sample Job Name@D096A2FA-D5DC-435C-B734-E44916AE01EA";

CSAClient client = new CSAClient();

if (client.CreateClient() == 1)
{
	CSAJob Job = client.Job(JobId);

	if (Job != null)
	{
		var DocTypes = Job.DocumentTypesList();
		if (DocTypes != null)
		{
			
		}
	}
}
```
---
## CSADocumentType methods

### method::Zones
>Get a Zones object with all capture zones in the document type.
#### Parameters
|Name|Description|
|---|---|
|||

#### Return value

|Value| Description|
|---|---|
|number|1 = ok, 0 = error|

---
## CSADocument properties
---
### prop::Id (get,string)
>Type Guid
### prop::Name (get,string)
>Document type name
