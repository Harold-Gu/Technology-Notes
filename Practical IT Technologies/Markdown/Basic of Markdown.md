# Basic of Markdown

Markdown is a lightweight markup language designed to enable users to write and edit documents using simple text formatting, while maintaining certain formatting capabilities. By employing Markdown syntax, users can quickly convert plain text into formatted documents, such as headings, lists, links, images, etc. The Markdown syntax is simple and intuitive, making it easy to learn and use. It has gradually become a common format for writing documents on various platforms, and even allows for the rapid conversion of Markdown documents to formats like PDF and Word.

## Grammar of Markdown

### Paragraphs and line breaks

* Line break effect: Add two consecutive spaces at the end of the previous line, then start a new line.
* Paragraph change effect: Continuously switch to two new lines.

### Bold and italic

* To make the text bold, all we need to do is add two asterisks on both sides of the text that needs to be bolded.
* Or you can use two underscores, and the effect will be the same.
* It is similar to bolding. We just need to add an asterisk (*) on both sides of the text that requires italicization.
* It is also possible to use an underscore (_) instead, and the effect will be the same.
* If you need to use both bold and italic simultaneously, you can simply use three consecutive asterisks (*) or an underscore (_) instead.
* If we merely want to use these special symbols (including the ones we will encounter later) in the document, we can use escape characters. Otherwise, some editors may encounter formatting issues. All you need to do is add a backslash (\) at the beginning.

### Strikethrough and underline

* To add a strikethrough to the text, all we need to do is to add two ~ waves on both sides of the text that requires the strikethrough.

* Underlines in the native Markdown syntax do not have corresponding symbols. We can only achieve this by using HTML code. Markdown supports embedding HTML tags in the text, including their styles.

  * ```html
    <u>Here is the underline</u>
    ```

### split line

* Just use three or more consecutive asterisks on a separate line.
* It can also be achieved by using underlines.

### title

* In many cases, we need a title to represent the core content of the current text so that readers can understand it. In Markdown, multiple sizes of titles can be created, just like in Word documents, and it's very simple. We only need to use the "#" symbol to create the title.
* The titles are divided into various levels. Different levels represent titles at different levels. We can use consecutive addition of multiple # symbols to indicate multiple titles of different levels. However, the maximum number of levels supported is six.

```markdown
# This is a first-level heading
## This is a second-level heading
### This is a third-level heading
#### This is a fourth-level heading
##### This is a fifth-level heading
###### This is a sixth-level heading (up to six levels)
```

### List and checkboxes

Lists play a very important role in our daily life. For instance, our daily plans, work tasks, shopping lists, etc., all require the use of lists to present them. This often makes them clearer and more intuitive. In Markdown, it is also very easy to create lists.

* To create an unordered list, all we need to do is use an asterisk (*) as the prefix, and remember to add a space.

* Apart from the asterisk, we can also use the plus sign + or the minus sign - instead, and the effect will be exactly the same. Note that in a list, these three symbols can only be uniformly used in the same way and cannot be mixed. If there is a mixed use, it will be regarded as a new list under the previous list. For example, the following is considered to be three lists.

* To create an ordered list with numbers, we can use the numbers 123 to represent them. First, input the numbers and then add a period as the prefix, and remember to add a space.

* In a list, line breaks also need to be handled in the same way as in regular text. If you simply make a line break without any content, it will be regarded as a blank space.

* If you add two spaces at the end and then start a new line, it will be regarded as a line break within the list item.

* Only two consecutive line breaks can break away from the list and start a new paragraph.

* The list supports multiple levels of nesting. We can create a secondary list under a primary list. To indicate a secondary list, we can add two or four spaces (or a TAB indentation) before it, indicating that this list is a child of the previous list.

* We can also convert the list into a checkbox format to represent the completion status of our tasks. All we need to do is add a square bracket.

  * ```markdown
    * [ ] This is an unfinished task
    * [x] This is a completed task
    ```

  * Fill in the blank spaces within the square brackets to indicate "not completed", and fill in an uppercase or lowercase "x" to indicate "completed".

   

### code block

* To create a code block, simply add four spaces at the beginning of this line. Remember to separate the code block from the other text on the previous line.
* However, this is very inconvenient. Not only do you need to leave four spaces, but you also have to specifically leave one line of space. I suggest that all of you use the following method to create code blocks, which is much simpler. We can also use three consecutive ` symbols to add code blocks. Remember to add them both at the beginning and the end to encompass them.

### quote

* When we quote the content from others' articles, we often need to make special markings for this part. However, Markdown provides us with a more convenient text citation block. We just need to add the greater than symbol (>) at the beginning to indicate that the following text is the quoted text.
* The referenced text will be wrapped in a special block, similar to a code block. The important thing is to convey the meaning accurately. 
* In a quotation block, line breaks are also treated the same way as in regular text. If you simply make a line break without any additional content, it will be regarded as a space.
* If you add two spaces at the end and then start a new line, it will be regarded as a line break within the quotation block.
* Only two consecutive line breaks can break away from the quotation block and start a new paragraph.
* For the citation of multi-line content, we recommend adding a ">" symbol before each line. The effect will be exactly the same as above, and it will also look more intuitive.
* Within the quotation block, we can also nest other Markdown content, such as lists or code blocks.
* References can also be nested within each other, even to multiple levels, simply by continuously adding the > symbol prefix.

### Links and images

* We can insert hyperlinks in Markdown documents just like in Word. All you need to do is use the combination of [] and (). The specific syntax format is as follows:

  * ```markdown
    [Link Text](Link Address)
    ```

* In this way, the specified text will be presented in the document in the form of hyperlinks, allowing users to directly click and jump to it, which is very convenient. 

* Sometimes, there may be many links in our documents, and even some duplicates. In such cases, writing them one by one is quite time-consuming, and the numerous links scattered throughout the source code make it look rather messy. We can utilize variables to optimize this situation. The values of the variables can be determined at the end of the article.

  * ```markdown
    [Link Text] [Variable] 
    [Variable]: https://www.baidu.com
    ```

* Inserting an image is very simple, similar to linking.

  * ```markdown
    ! [Description of the picture] (Picture URL "Picture Name (optional)")
    ```

### footnote

* In Word, we often use footnotes. Especially in academic papers, we frequently mark a number (such as 123) above the right corner of a certain word to indicate that there is an annotation for that word at the bottom of the document. If you don't understand, you can go to the footer to view the content of the annotation.

  * ```markdown
    Lady, if you meet a PHP[^1] programmer, just get married. 
    [^1]: The best language in the world.
    ```

* Lady, if you meet a PHP[^1] programmer, just get married. 

  [^1]: The best language in the world.

### form

* In Markdown, it is also possible to create a table, which makes the presentation of data more neat and orderly. 

* However, this grammar might be a little bit complicated. First, let's take a look at the structure of a table. A table consists of a header row at the top and a body. The header row is the topmost row and is used to indicate the data type of the current column, such as age, gender, etc. The body is each row of data. Let's see how to write it in Markdown.

* ```markdown
  | Name | Age | Gender |
  | --- | --- | --- |
  ```

* The top row is the header, which needs to be separated by | on both sides to indicate that this is a table. Additionally, a divider line needs to be added below, using - as the symbol. One or more lines can be used, and it is recommended to be the same width as the table for a more appealing appearance. Thus, it can be successfully displayed as a table

* At the same time, Markdown's table supports alignment adjustment of the content. All you need to do is use a colon to adjust the divider line.

* ```markdown
  | Name | Age | Gender |
  | :--- | :---: | ---: |
  ```

* :--- for left alignment
  ---: for right alignment
  :--- : for center alignment

### HTML label

* After learning the most basic grammar, some friends might feel that the degree of customization is not sufficient. For example, they may not be able to change the font color or customize the size of the images. We can also use some supported HTML tags in Markdown text to make the document content more personalized. 
* For example, we can embed an <img> tag and write the corresponding inline CSS style to enable the image size to be customized.
* Also, the line breaks, divider lines, underlines, etc. that we used earlier can all be achieved using the tags provided by HTML.
* However, if the Markdown syntax already supports the corresponding functionality, we should still prefer to use the native Markdown syntax to avoid reducing readability.



### Other Extended Grammar

* In addition to the grammar we have learned above, there are some extended grammars that can be used (some editors do not support them, while Typora needs to be set up in the settings to support them) 
* First, there is text highlighting, which is achieved by using two equal signs to enclose it.

```markdown
==The highlighted part==
```

* At this point, the text will be highlighted. The exact way of highlighting may vary depending on the different editors, and the effect may also differ. 
* The superscripts and subscripts of the text can be achieved by using a single "^" for superscripts and "~" for subscripts.

```markdown
I am the text ^ I am the superscript ^ 
I am the text~ I am the subscript~
```

### Mathematical formula grammar

* In addition to the basic document format Markdown which it can support, it can also write mathematical formulas, presenting them in a more intuitive and standardized way. Science students will definitely love it. 
* Users of Typora need to enable inline formula support in the settings.

#### Formula block

* Mathematical formulas need to be written as well. We should also write them within specific blocks. The formula blocks are denoted by the dollar sign $. Multi-line formulas use two consecutive dollar signs: 

```
$$
I am the formula. 
$$
```

* If you only want to write within a line, a single dollar sign is sufficient to enclose a line of content: 

```
The formula is: $ x = 17 + y $ 
```

* The content displayed in the formula block will automatically be formatted in the standard academic formula style, and the font is also very standard. I highly recommend that all of you use Markdown to write mathematical formulas.

#### Special mathematical symbols

* In the formula block, most mathematical symbols can be directly input using the keyboard. However, there are still some symbols that cannot be directly entered via the keyboard, such as the multiplication sign, division sign, square root symbol, etc. We need to use some special codes to replace them.

|         code         |      symbol       |            describe             |
| :------------------: | :---------------: | :-----------------------------: |
|        \not=         |         ≠         |           unequal to            |
|       \approx        |         ≈         |           approximate           |
|        \times        |         ×         |          multiple sign          |
|         \div         |         ÷         |        sign of division         |
|         \leq         |         ≤         |      less than or equal to      |
|         \geq         |         ≥         |    be equal or greater than     |
|         \pm          |         ±         |         Plus-minus sign         |
|         \sum         |         ∑         | Summation symbol (accumulation) |
|        \prod         |         ∏         |         multiplicative          |
|       \coprod        |         ∐         |            Exhausted            |
| \overline{a + b + c} | a+b+c‾*a*+*b*+*c* |          average value          |

|   code   | symbol |  code  | symbol |
| :------: | :----: | :----: | :----: |
|  \alpha  |  *α*   | \beta  |  *β*   |
|  \gamma  |  *γ*   | \delta |  *δ*   |
| \epsilon |  *ϵ*   |  \eta  |  *η*   |
|  \theta  |  *θ*   |  \pi   |  *π*   |
|  \omega  |  *ω*   |  \rho  |  *ρ*   |
|  \sigma  |  *σ*   |  \mu   |  *μ*   |

| code  | symbol | describe  |
| :---: | :----: | :-------: |
| \sin  |  sin⁡   |   sine    |
| \cos  |  cos⁡   |  cosine   |
| \tan  |  tan⁡   |  tangent  |
| \cot  |  cot⁡   | cotangent |
| \sec  |  sec⁡   |  secant   |
| \csc  |  csc⁡   | cosecant  |
| \circ |   ∘∘   |  degree   |

|  code   | symbol |       describe       |
| :-----: | :----: | :------------------: |
| \infty  |   ∞    |       infinity       |
|  \int   |   ∫    |  definite integral   |
|  \iint  |   ∬    |   Double integral    |
| \iiint  |   ∭    |   triple integral    |
|  \oint  |   ∮    | curvilinear integral |
| x\prime |  *x*′  |      derivation      |
|  \lim   |  lim   |      limitation      |

|   code    | symbol |     describe     |
| :-------: | :----: | :--------------: |
| \emptyset |   ∅    |    empty set     |
|    \in    |   ∈    |    belong to     |
|  \notin   |   ∉    |  not belong to   |
|  \supset  |   ⊃    | properly include |
| \supseteq |   ⊇    |     include      |
|  \bigcap  |   ⋂    |   intersection   |
|  \bigcup  |   ⋃    |    union set     |

| code | symbol |               describe                |
| :--: | :----: | :-----------------------------------: |
| \log |  log⁡   |         logarithmic function          |
| \ln  |   ln   |   Logarithmic function with base e    |
| \lg  |   lg⁡   | The logarithmic function with base 10 |

#### Score

* The score is represented by \farc, and the specific format is as follows: 

  ```
  $\frac{\text{numerator}}{\text{denominator}}$ 
  ```

#### Square root

* The square root is represented by \sqrt. The specific format is as follows: 

  ```
  $\sqrt{4}$
  ```

* If you need to modify the value above the square root symbol, you can add square brackets: 

   ```
  $\sqrt[3]{8}$
   ```

#### Superscripts and Subscripts

* The superscripts and subscripts in the formula block are different from those in Markdown and have different syntax. The symbol ^ represents superscript, and _ represents subscript

  ```
  $ subscript x $
  $ superscript x $
  $ subscript x superscript x $
  ```

* If the content of the superscript or subscript is more than one character, it needs to be enclosed in {} brackets. If there is a situation where only one character takes effect, consider using curly braces to enclose all the content

  ```
  $ x_{subscript} $
  $ x^{superscript} $
  $ x^{superscript}_{subscript} $
  ```

#### Integration and limits

* Integration is very simple. Just use the superscript and subscript to specify the range, and the subsequent content can be written directly below, and it will be automatically centered

  ```
  $ \int_1^2xdx $
  ```

* Just like in the case of limits, the same notation can be used for products as well: 

  ```
  $ \lim_{n\rightarrow+\infty}\frac{1}{n + 1} $
  ```

#### Other symbols

* Vector symbols: 

  ```
  $ \vec{a} $
  ```

* Ellipsis: 

  ```
  $ \cdots $  Centered ellipsis
  $ \ldots $  Ellipsis at the bottom
  ```

* Dot notation: 

  ```
  $ \cdot $
  ```

* Accumulation: 

  ```
  $ \sum_1^n $
  ```

  

  