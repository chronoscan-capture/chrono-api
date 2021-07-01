# CSAPage

This object gives access to a ChronoScan page object.

A ChronoScan page contains a page and his data (fields, image, OCR layers).

## Example
```cs
CSADocument Doc = Batch.GetDocument(x);
if (Doc != null)
{
	var Pages = Doc.Pages;
	if (Pages != null)
	{
		foreach (CSAPage Page in Pages)
        {
			Console.WriteLine("Page image file: {0}",Page.ImageFile);
			Console.WriteLine("Page HOCR file: {0}",Page.OCRFile);
		}
	}
}
```
---
## CSAPage methods
---
### method::
#### Parameters
| Name				| Description		|
|-------------------|-------------------|
#### Return value
| Value				| Description		|
|-------------------|-------------------|
|number|1 = ok, 0 = error|

---
## CSAPage properties
---
### prop::ImageFile (get,string)
>Path to source image file (original or rendered if PDF files).
### prop::OCRFile (get,string)
>Path to source OCR file.
### prop::ThumbLRFile (get,string)
>Path to a thumbnail of 512px wide of source image file (original or rendered if PDF files).
### prop::ThumbHRFile (get,bool)
>Path to a thumbnail of 256px wide of source image file (original or rendered if PDF files).
### prop::TextBlocks (get,array of [CSAPageFullTextBlock](./objects/CSAPageFullTextBlock/index))
>An array of full text TextBlocks in the page