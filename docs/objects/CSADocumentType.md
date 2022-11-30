# CSADocumentType

This object gives access to a ChronoScan document type object.

A ChronoScan document type contains OCR zones and info to process an specific document type, named also as document template.

## Example
```cs
var JobName = "Sample Job Name";

CSAClient client = new CSAClient();

if (client.CreateClient() == 1)
{
	CSAJob Job = client.Job(JobName);

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
