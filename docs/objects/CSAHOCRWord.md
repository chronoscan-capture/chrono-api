# CSAHOCRWord

A word text and extra information inside a CSAHOCRParser.

## Example
```cs
var words = OCR.Words;
foreach (CSAHOCRWord word in words)
{
    Console.WriteLine("{0}({1})", word.value, word.Confidence );
}
```
---
## CSAHOCRWord properties
---
### prop::Value (get,string)
>Text of the word
### prop::Left (get,int)
>Left coordinate of the work in px
### prop::Top (get,int)
>Top coordinate of the work in px
### prop::Right (get,int)
>Right coordinate of the work in px
### prop::Bottom (get,int)
>Bottom coordinate of the work in px

### prop::Confidence (get,int)
>Confidence, 0 to 100 (max confidence)
### prop::Merged (get,int)
>Word was added from the OCR to the original PDF text layer.
### prop::Horientation (get,int)
>Text orientation:
- 0 = NORMAL TEXT
- 1 = R_LEFTTEXT
- 2 = R_RIGHTTEXT
