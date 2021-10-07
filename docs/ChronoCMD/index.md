# ChronoCMD - Command line inferface for ChronoScan/ChronoTXT

ChronoCMD is an exe file that allows to automate common tasks on ChronoScan/ChronoTXT through command line commands.


## ChronoScan connection&configuration:

| Command   		        | Description		|
|---------------------------|-------------------|
|-list_configs              |Show available configurations|
|-cfg              |Connect to an specific Chronocan configuration (optional, if not specified ChronoCMD will connect to default configuration)|
|-usr              |Enterprise user|
|-pwd              |Enterprise user password|
|-list_jobs        |List available job id's|
|-job              | Set working job for ChronoCMD session|
|-list_batches     | List batches of current job|
|-batch            | Set working batch name for ChronoCMD session|


### List configurations

```cs
Command:
ChronoCMD.exe -list_Configs
Output:
ChronoScan                      <--- (default configuration)
ChronoScan.MyTestConfig         <--- (custom configuration)
```

### Connect to an enterprise configuration and list Jobs

```cs
Command:
ChronoCMD.exe -cfg:"ChronoScan.MyTestConfig" -usr:"Admin" -pwd:"mypassword" -list_jobs
Output:
Configuration: ChronoScan.MyTestConfig
aaa@DC9FF26E-2744-447F-BE08-A4D47C292641
AP1@77EBE544-4703-4681-93F7-60AB7A8E2A8E
...
```

### Connect to default configuration and list Job batches

```cs
Command:
ChronoCMD.exe -job:"AP1@77EBE544-4703-4681-93F7-60AB7A8E2A8E" -list_batches
Output:
Configuration: << Default >>
Batchname_00001
Batchname_00002
Batchname_00003
...
```

## Batch operations:

| Command   		        | Description		|
|---------------------------|-------------------|
|**-create_batch**|Create a new batch (needs working batch name)|
||if batch name is "%guid%" a new guid will be generated (ex: -batch:\"%guid%\")|
| |**-overwrite** - Allows to overwrite if the batch already exists|
|**-add_files**|Add files on the path to current batch (ex: -add_files:\"c:\\temp\\*.pdf\")|
||**-recurse** : Add files will find on subdirectories|
||**-pages** : Allows to specify with pages to import from each file (ex: -pages:\"1-2\" or -pages:\"2-\"|
||**-excludeifprocextension** : Exclude if a file with same name and expecified extesion exists (ex: -excludeifprocextension:\".1.0.2.65.xml\")|
|**-delete_batch**| Delete a batch (needs working batch name)|
|**-process_batch**|Process batch, specific process can be indicated (ex: -process_batch:\"LANG_DETECT;OCR;FIELDREAD;\"|
|**-export_batch**|Execute batch export configuration|
|**-delete_after_export**|Delete batch after exporting|


## Batch operations:
| Command   		        | Description		|
|---------------------------|-------------------|
|**-tX_list_configs**| Show available db configurations|
|**-tX_db**| Set ChronoTxt database connection (ex: -tX_db:\"mydbconnection\")|
|**-tX_jobs**| List ChronoTxt Jobs (needs a -tX_db connection first)|
|**-tX_load_batch**| Load a batch by name or id (needs -tx_db & -tx_jobId)|
|**-tX_reprocess**| Reprocess loaded batch|


## API operations:

API operations allows to process files without creating ChronoScan batches.

| Command   		        | Description		|
|---------------------------|-------------------|
|**-api_sel_files**          | files selector path (ex: -api_sel_files:\"c:\\temp\\*.pdf\"|
||**-recurse** : Recurse on children directories|
||**-pages** : Execute only on specified page ranges ex: -pages:\"1-2\"|
||**-rebuild** :Delete previous results|
||**-excludeifprocextension**  : Exclude if a file with same name and expecified extesion exists (ex: -excludeifprocextension:\".1.0.2.65.xml\")|
|**-api_preprocess_files**| process sel_files|
|**-api_delete_proc**| delete selected files process containers|
|**-api_OCR**                | Build OCR using standard engine|
|**-api_OCRTESS**            | Build OCR using tesseract engine|
|**-api_OCRADV**             | Build OCR using advanced engine|
|**-api_MERGEPDFOCRADV**     | Merge OCR (by default OCR.ADV) with native PDF text|
|**-api_MERGEPDFOCRADV_set_active**   | Set merged Text as active text|
|**-api_MERGE**              | Merge OCR (api_Merge:\"STORAGE.A;STORAGE.B;STORAGE.DEST\"|
|**-api_MERGE_set_active**| Set merged Text as active image|
|**-api_MERGE_compareocr**| Execute in OCR compare merge mode|
|**-api_SOPA**| Execute SOPA layout on active item|
|**-api_SORTHOCR**| Force Resort an hocr file (ex: -api_SORTHOCR:\"c:\\temp\\inputfile.html\"|
||        if not file sent will use api_sel_files selection|

## Testing & Debug utilities:
| Command   		        | Description		|
|---------------------------|-------------------|
|**-ctd_Compare**| Compare xml files using a json configuration file -ctd_Compare:\"c:\\mytest.json\", this command allows to create automated tests for version or configuration changes. [LINK TO TUTORIAL]|