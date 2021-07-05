# CSABarcode

Barcode data in a CSADocument

## Example
```cs
var Barcodes = document.Barcodes;
if (Barcodes != null)
{
    foreach (CSABarcode Barcode in Barcodes)
    {
        Console.WriteLine("\t\t\tBarcode: page:{0}[{1}({2})]", Barcode.Page, Barcode.Value, Barcode.Type);
    }
}
```
---
## CSABarcode properties
---
### prop::Value (get,string)
>Value of the barcode
### prop::Page (get,string)
>Page where the barcode was read
### prop::Type
>Barcode type
### prop::RectPx (get,string)
>Rect in pixels in string format (left,top,right,bottom)