# CSAHOCRParser

This object gives access to a ChronoScan HOCR file.

## Example
```cs
	CSAHOCRParser parser = new CSAHOCRParser();
	if (parser.LoadFromFile(Page.OCRFile) == 1) {
		Console.WriteLine("Page contains {0} words.",parser.WordCount);
	}
```
---
## CSAHOCRParser methods
---
### method::LoadFromFile
>Load a HOCR file from disk
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
|FileName||
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|

---
## CSAHOCRParser properties
---
### prop::WordCount (get,string)
>Number of words
### prop::SourceType (get,string)
>Get the source type of the file (OCR engine, PDF text, merged text...)
