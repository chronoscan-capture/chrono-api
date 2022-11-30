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

## Example 4: Creating a batch, process and export
```cs
CSAClient client = new CSAClient();

if (client.CreateClient("ChronoScan.MYCONFIGNAME", "admin", "12345") == 1)
{
	Console.WriteLine("System information:");
	Console.WriteLine("\tCS Is Enterprise: {0}", client.Enterprise);
	Console.WriteLine("\tCS Version: {0}", client.Version);
	Console.WriteLine("\tCS Directory: {0}", client.Directory);

	var JobId = "AP1@77EBE544-4703-4681-93F7-60AB7A8E2A8E";
	var BatchName = "NEW_BATCH_NAME_%job_batch_counter%";

	Console.WriteLine("Loading job Id: " + JobId);

	CSAJob job = client.Job(JobId);
	if (job != null)
	{
		Console.WriteLine("\t\tJob Name: {0}", job.Name);
		Console.WriteLine("\t\tJob Id: {0}", job.Id);
		Console.WriteLine("\t\tJob WorkDir: {0}", job.WorkDir);
		Console.WriteLine("\t\tJob Description: {0}", job.Description);
		Console.WriteLine("\t\tJob chrono_version: {0}", job.chrono_version);
		Console.WriteLine("\t\tJob Base batch_name: {0}", job.batch_name);
		Console.WriteLine("\t\tJob task_OnProcessing_cfg: {0}", job.task_OnProcessing_cfg);

		Console.WriteLine("\t\tCreating BATCH: " + BatchName);

		CSABatch Batch = job.CreateBatch(BatchName);
		if (Batch == null)
		{
		Console.WriteLine("\t\t\tBatch loading ERROR: " + client.LastError);
		if (client.LastError == "batch_already_exist")
		{
		    Console.WriteLine("Do you want to delete the batch? Push 'y' to delete it");
		    var key = Console.ReadKey();
		    if (key.KeyChar == 'y')
		    {
			CSABatch BatchDel = job.LoadBatch(BatchName);
			if (BatchDel != null)
			{
			    if (BatchDel.Delete() == 1)
				Console.WriteLine("\t\t\tBatch deleted");
			    else
				Console.WriteLine("Error {0}", client.LastError);
			    BatchDel.FreeItem();
			}
			else
			    Console.WriteLine("Error {0}", client.LastError);
		    }
		}
		Batch = job.CreateBatch(BatchName);
	}

	if (Batch != null)
	{
		Console.WriteLine("\t\t\tBatch Created!!");
		Console.WriteLine("\t\t\tBatch Name: {0} ({1} document(s))", Batch.Name, Batch.DocumentsCount);
		if (client.Enterprise)	
			Console.WriteLine("\t\t\tEntBatchStatus: {0}", Batch.EntBatchStatus);
		Batch.SplitManual = 1;
		Batch.SplitOnEachFile = 1;
		Console.WriteLine("\t\t\tAdding sample FILE 1 to the Batch----------------------------------------------->");
		Batch.AddFileToBatch("c:\temp\file1.pdf");
		Console.WriteLine("\t\t\tAdding sample FILE 2 to the Batch----------------------------------------------->");
		Batch.AddFileToBatch("c:\temp\file2.pdf");

		Console.WriteLine("\t\t\tListing document data:");
		for (int x = 0; x < Batch.DocumentsCount; x++)
		{
		    Console.WriteLine("\t\t\tDocument {0}:", x);
		    CSADocument Doc = Batch.GetDocument(x);
		    if (Doc != null)
		    {
			Console.WriteLine("\t\t\t\tGuid: {0}", Doc.Guid);
			Console.WriteLine("\t\t\t\tPages: {0}", Doc.PageCount);
			Console.WriteLine("\t\t\t\tSrcDoc: {0}", Doc.GetFieldValue("SrcDoc"));

			Doc.ProcessDocument("");//empty will execute the job configured actions
			//Doc.ProcessDocument("OCR;FULLTEXT;");

			if (Doc.ValState == "OK")
			    Console.WriteLine("\t\t\t\tDocument VALIDATED");
			else
			    Console.WriteLine("\t\t\t\tDocument with ERRORS: " + Doc.ValStateInfo);
		    }
		}

		Console.WriteLine("Do you want to export the batch? Push 'y' to export it");
		var key = Console.ReadKey();
		if (key.KeyChar == 'y')
		{
		    Batch.ExportBatch();
		}

		Batch.Close();
		Batch.FreeItem();
		}

		job.FreeItem();
	}
}
else
{
	Console.WriteLine("Error {0}", client.LastError);
}
client.FreeItem();
```
---


