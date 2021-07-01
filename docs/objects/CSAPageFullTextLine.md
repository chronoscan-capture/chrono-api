# CSAPageFullTextLine

Line in a text block object

## Example
```cs
var TextBlocks = page.TextBlocks;
if (TextBlocks != null)
{
    foreach (CSAPageFullTextBlock TextBlock in TextBlocks)
    {
        Console.WriteLine("\t\t\tText: {0}[{1}]", TextBlock.Value, TextBlock.RectPx);

		var TextLines = TextBlock.TextBlocks;
		if (TextBlocks != null)
		{
			foreach (CSAPageFullTextLine TextLine in TextLines)
			{
				Console.WriteLine("\t\t\t\tLine: {0}[{1}]", TextLine.Value, TextLine.RectPx);
			}
		}
    }
}
```
---
## CSAPageFullTextLine properties
---
### prop::Value (get,string)
>Value of the text block
### prop::RectPx (get,string)
>Rect in pixels in string format (left,top,right,bottom)
