# CSAUserField

This object gives access to a ChronoScan job user field.

A field is a label (field name) + a variable value attached to a document.

A job lets user to create a set of user fields for all documents, to set metadata for any of them 
in the Job, like Invoice Number, Date...

## Example
```cs
CSAJob job = client.Job(JobId);
if (job != null)
{
    Console.WriteLine("\t\tJob Name: {0}", job.Name);
    Console.WriteLine("\t\tJob UserFields:");
    var Fields = job.UserFields;
    if (Fields != null)
    {
        foreach (CSAUserField Field in Fields)
        {
            Console.WriteLine("\t\t\tField: {0}[{2}] ({1})", Field.Name, Field.DisplayName, Field.TypeName);
        }
    }
}
```
---
## CSAUserField methods
---
## CSAUserField properties
---
### prop::Name (get,string)
>Field internal name
### prop::DisplayName (get,string)
>Alternative field display name (a showed in the UI)
### prop::TypeName (get,string)
>Field type

| Value				| Description		|
|-------------------|-------------------|
|"DOCTYPE"|Document type|
|"STRING"|The field contains free text|
|"DATE"|Date with dd/mm/yyyy|
|"TIME"|Time hh:mm:ss|
|"DATETIME"|Date&Time|
|"AMOUNT"|An amount up to 6 decimals|
|"NUMBER"|A integer number|
|"DECIMAL"|A number up to 10 decimals|
|"LIST"|A value selected from a list|
|"BOOL"|A true/false value|

