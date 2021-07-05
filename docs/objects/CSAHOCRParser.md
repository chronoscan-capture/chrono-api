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
|FileName|Full path to source hocr file (usually an .html file)|
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
### prop::Words (get,array of CSAHOCRWord)
>Get all the words contained in the HOCR as a CSAHOCRWord objects array
