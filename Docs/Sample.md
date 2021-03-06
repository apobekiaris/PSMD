# How to use PSMD
You will find a short example from every feature of PSMD here. Feel free to give feedback on the structure of the functions and enjoy PSMD!
Also btw, this Document was generated with PSMD. If you're interessted check out the
[Script that generated this document](../Examples/_Example_SampleDocument.ps1)
## Basics
### New-PSMDDocument
Before you use one of the features of Markdown let me introduce you to the function you'll need to make PSMD work for you.
Surrounding all your PSMD code you will have to have the following piece of code:
```

    $Document = New-PSMDDocument -Name "Sample" -Content {}

```
As an example. This will **not** Work:
```

    Title -Text "Sample Document" -Size h1

```
#### Output as object
If you place your PSMD code **in** the Scriptblock it will Work:
```

    $Document = New-PSMDDocument -Name "Sample" -Content {
        Title -Text "Sample Document" -Size h1
    }

```
So for now you will have the Object of the Document saved in **$Document**
#### Output as .md File
So if you want to export your PSMD code directly in a .md file you can set the parameter '-OutputPath'. The File will then be saved with the name you pass on '-name' and at the folder you pass on '-OutputPath'
```

    $Document = New-PSMDDocument -Name "Sample" -Content {
        Title -Text "Sample Document" -Size h1
    } -OutputPath .\Folder\of\your\choosing

```
## Individual Markdown Features in PSMD
### Titles
You can add titles like this:
```

    Title -Text "Sample Document" -Size h1 

```
### Linebreaks
Normally after every line there is a new line starting. You can however, with PSMD, add more linebreaks or choose to have your value on the same line as the value above.
### Add a linebreak
```

    Paragraph -Text "This is a sample paragraph"
    LineBreak
    LineBreak
    Paragraph -Text "This is a sample paragraph a few lines below." 

```
This will look something like this:
<br/>
<br/>
This is a sample paragraph
<br/>
<br/>
This is a sample paragraph a few lines below.
### Have two sections on one line
```

    Paragraph -Text "This is a sample paragraph."
    Paragraph -Text " And this wil be on the line above." -NoNewLine 

```
This will look something like this:
<br/>
This is a sample paragraph.
<nobr> And this wil be on the line above.</nobr>
### Paragraphs
You can add paragraphes like this:
```

    Paragraph -Text "here you go" 

```
#### Style of Paragraphs
You can add styles to paragraphes like this:
```

    Paragraph -Text "This is bold text" -Style bold
    Paragraph -Text "This is Italic text" -Style Italic
    Paragraph -Text "This is bold and italic text" -Style bold,Italic 

```
The Paragraphes with styles will look something like this:
<br/>
**This is bold text**
<br/>
_This is Italic text_
<br/>
_**This is bold and italic text**_
### BlockQuote
You can add BlockQuotes like this:
```

    BlockQuote -Text "I have a dream" 

```
The Blockquote will look something like this:
> I have a dream
### Links
You can add Links like this:
```

    Link -Text "Google it yourself" -Value "https://Google.com" 

```
The Link will look something like this:
[Google it yourself](https://Google.com)
### Images
You can add Images like this:
```

    Image -Text "Sample image" -ImagePath "Images/Powershell.png" 

```
The image will look something like this:
<br/>
![Sample image](../Images/Powershell.png)
### BulletPoints
You can add BulletPoints like this:
```

    BulletPoint -Text "This is the Base level"
    BulletPoint -Text "This is the first level" -Level 1
    BulletPoint -Text "This is the second level" -Level 2 

```
The BulletPoints will look something like this:
* This is the Base level
   * This is the first level
     * This is the second level
### OrderedListItem
You can add OrderedListItem like this:
```

    OrderedListItem -Text "First of all" -number 1
    OrderedListItem -Text "Second of all" -number 2
    OrderedListItem -Text "And last but not least..." -number 3

```
The OrderedListItem will look something like this:
1. First of all
2. Second of all
3. And last but not least...
### CheckListItem
You can add CheckListItem like this:
```

    CheckListItem -Text "Female"
    CheckListItem -Text "Male" -Status Checked
    CheckListItem -Text "hungry" -Status Unchecked
    CheckListItem -Text "very hungry" -Status Checked

```
The CheckListItem will look something like this:
- [ ] Female
- [X] Male
- [ ] hungry
- [X] very hungry
### CodeBlocks
You can add CodeBlocks like this:
```

    CodeBlock -Code @'
        Function HelloWorld {
            return "HelloWorld"
        } 
    '@


```
The CheckListItem will look something like this:
```

        Function HelloWorld {
            return "HelloWorld"
        } 

```
### Tables
Tables are generated with an object, or an array containing objects, as the input.
<br/>
<br/>
To see how more advanced tables are generated see 
[the Table examples.](../Examples/Example_Table.ps1)
<nobr>To see results of the Tables see  </nobr>
[the Tables themselves.](../Examples/TableResults/)
You can add tables like this:
```

    $hash = @{}
    $hash.surname = "Jones"
    $Hash.SecondName = "Joseph"
    $Hash.FirstName = "Jonas"
    $obj = New-Object psobject -Property $hash
    $doc = New-PSMDDocument -Name "Table_Sample" -Content {
        Table -InputObj $obj
    } -OutputPath .\

```
The Table will look something like this:

 | FirstName | SecondName | surname |
 |----------|-----------|--------|
 | Jonas | Joseph | Jones |

## Sample Document
[Go Checkout the other examples](../Examples/)
