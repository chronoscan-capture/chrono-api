# Objects

This objects gives access to common functions in ChronoScan.

## Automation objects

### Main objects

|Object|Description|
|---|---|
|[CSAClient](./objects/CSAClient)|Give access to a ChronoScan client configuration|
|[CSAJob](./objects/CSAJob)|The job object contain user fields, document types and working parameters|
|[CSABatch](./objects/CSABatch)|This object gives access to a job batch, a "Batch" is a set of documents in ChronoScan|
|[CSADocument](./objects/CSADocument)|Control a Document object in a batch|
|[CSAPage](./objects/CSAPage)|Control a Page in a document|

### Data structure objects

|Object|Description|
|---|---|
|[CSAUserField](./objects/CSAUserField)|User field definition in a job|

### OCR&Text extraction objects

|Object|Description|
|---|---|
|[CSAHOCRParser](./objects/CSAHOCRParser)|Access to OCR data of a CSAPage|
|[CSAPageFullTextBlock](./objects/CSAPageFullTextBlock)|Block of text object in a page|
|[CSAPageFullTextLine](./objects/CSAPageFullTextLine)|Line in a block of text object|


