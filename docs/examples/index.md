# Examples

This page contain an index of available examples.

## Example 1: Creating a ChronoScan Client.
```cs
CSAClient client = new CSAClient();

if (client.CreateClient("ChronoScan.CHRONOSCAN_DOCS", "", "") == 1)
{
	Console.WriteLine("Connected!!");
}
else
{
	Console.WriteLine("Error: " + client.LastError);
}
```
## Example 2: Listing documents in a batch.
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
## Example 3: Accesing OCR and rendered data
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


