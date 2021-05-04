# Markdown Cheatsheet

### Resources

https://dillinger.io/ - Online Markdown Editor

https://www.markdowntutorial.com/ - Markdown Tutorial

https://www.markdownguide.org/cheat-sheet/ - Basic Cheatsheet

https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet - Another Cheatsheet

### Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support th
se elements.
|Element|Markdown Syntax|
|---|---|
|Heading|`# H1`<br>`## H2`<br>`### H3`|
|Bold|`**bold text**`|
|Italic|`*italicized text*`|
|Blockquote|`> blockquote`|
|Ordered List|`1. First item`<br>`2. Second item`<br>`3. Third item`|
|Unordered List|`- First item`<br>`- Second item`<br>`- Third item`|
|In-line Code|&grave; code &grave;|
|Embedded Code Snippet|&grave;&grave;&grave; [lang]<br>code<br>&grave;&grave;&grave;<br>*Note* - You can specify the language [lang] and markdown will automatically highlight keywords for readability.|
|Horizontal Rule|`---`|
|Link|`[title](https://www.example.com)`|
|Image|`![alt text](image.jpg)`|

### Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

|Element|Markdown Syntax|
|---|---|
|Table| `| Syntax | Description |`<br>`| -------- | -------- |`<br>`| Header | Title |`<br>`|Paragraph|Text|`<br>*Notes* - There must be at least 3 dashes in the second row.<br> - Colons can be used to align columns (:--- = left aligned, :---: = centre-aligned, ---: = right-aligned).|
|Fenced Code Block|&grave;<br>`{`<br>`"firstName": "John",`<br>`"lastName": "Smith",`<br>`"age": 25`<br>`}`<br>&grave;|
|Footnote|Here's a sentence with a footnote.`[^1]`<br>`[^1]: This is the footnote.`|
|Heading ID|### My Great Heading {#custom-id}|
|Definition List|term<br>: definition|
|Strikethrough|`~~The world is flat.~~`|
|Task List|	`- [x] Write the press release`<br>`- [ ] Update the website`<br>`- [ ] Contact the media`|
