# CSAPageFullTextBlock

Full text block in a CSAPage

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
## CSAPageFullTextBlock properties
---
### prop::Value (get,string)
>Value of the text block
### prop::RectPx (get,string)
>Rect in pixels in string format (left,top,right,bottom)
### prop::TextLines (get,array of [CSAPageFullTextLine](./objects/CSAPageFullTextLine))
>Array of [CSAPageFullTextLine](./objects/CSAPageFullTextLine) objects
