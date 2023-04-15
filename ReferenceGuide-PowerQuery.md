
<h1 id="power-query-m">Reference Guide - Power Query & M language</h1>

This is a reference document with usefull information about Power query and M language.
Written while learning for educational purposes and for quick reference and look-up.

<p align=right>Written by Martin Czerwinski ®CMQ Nordic AB</p>
---

<p id="table-of-content"></p>
<p align=right><a align=right href="https://github.com/CMQNordic/reference-documents#reference-documents">➡️Other reference documents</a></p>  


#### __TABLE OF CONTENT__

  - [__Basics to know__](#basics-to-know) 
    - [Basics of M](#basics-of-m)  
	- [Import data into a query](#import-data-into-a-query-in-m) ◦ [Types in M](#types-values-in-m)
	- [Functions in M](#functions-in-m) ◦ [each &  _](#each-in-m) 
	- [Lists](#lists-in-m) ◦ [Records](#records-in-m) ◦ [Tables](#tables-in-m) ◦ [Accessing values](#accessing-values-in-m)<br> 
    - [Operators and Expressions in M](#operators-in-m)<br>
	- [Step execution order](#step-execution-order-in-m) ◦ [Measuring performance](#measuring-performance-in-m)<br>
	- [Useful native functions](#useful-native-functions-in-m)<br> 
	- [Things to avoid](#things-to-avoid-in-m)<br>
 
 - [__Learn from examples__](#m-syntax-and-main-functionality "[M syntax with some Power Query basics") 
	- [Import of data example](#examples-of-data-import-in-m) - Some M functions that import data
	- [Example: functions](#functions-e) - Example of definition of functions
  	- [Example: lists](#list-syntax-example-in-m) - Example of using list
    - [Example: read values](#accessing-values-in-m) - How to access values

 - [__Native functions__](#m-syntax-and-main-functionality "[M syntax with some Power Query basics") 
	- [Example: import data](#data-sources) - Example of importing data from various data sources
	- [Example: functions](#functions-e) - Example of definition of functions


 - [__Deep dive into some topics__](#m-syntax-and-main-functionality "[M syntax with some Power Query basics") 

 	- [Skip step executions with if/else](#skip-code-execution-in-m) - Changing values and reshaping a table
 	- [Reshaping tables](#reshape-a-table) - Changing values and reshaping a table
 	- [Looping & Iterations](#looping-and-iterations-in-m) - Iterate in M like with _for_-loop.
	- [Change column names dynamically](#change-column-names-dynamically-in-m) - Description
	- [Change column types dynamically](#change-column-types-dynamically-in-m?) - Description
    - [Find first non null elem in a list](#find-first-non-null-elem-in-list-in-m) - Description

---

<br>

### __[Basics to know]()__

<p align=right><a id="why-m-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Why M?]()
---
M is a powerful language behind the scene of **Power Query** that is part of Excel and Power BI. With it you can import, change and restructure big amounts of data. It's hidden behind the graphical interface of Power Query Editor that is designed for "non-programmers". M is very similar to [_F#_](https://en.wikipedia.org/wiki/F_Sharp_(programming_language)), that in turn is used for financial and scientific applications in particular.

Official Power Query [M language specification](https://docs.microsoft.com/en-gb/powerquery-m/power-query-m-language-specification) 

<p align=right><a id="power-query-editor-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Power Query Editor]()
---

Power Query Editor is a graphical script editor and part of [**Excel**](https://support.office.com/en-us/article/getting-started-with-power-query-7104fbee-9e62-4cb9-a02e-5bfb1a6c536a "Getting Started with Power Query in Excel") and [**Power BI**](https://powerbi.microsoft.com/en-us/blog/getting-started-with-power-query-part-i/ "Getting Started with Power Query in Power BI"). It's used for working with M through its graphical interface that present M code as clickable list of steps. It is designed to be used by persons without any coding experience, autogenerating  M code behind the scene, but there is in Power Query Editor an Advanced M Editor (` View -> Advanced Editor`) where M code can be added or modified.

<p align=right><a id="basics-of-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [**Basics of M**]()
---

The first thing you will see in M is an **`let`** **`in`** expressions and probably lots of text lines beginning with short words like `#"Source"` or `#"Changed Types"`. 

Between `let` and `in`, on each line we declare one variable followed by `=` and an expression that perform some action or actions. Each of this lines is in Power query Editor called a step. 

```javascript
let
  firstStep = "Hello",
  #"Second Step" = "World",
  result = firstStep & #"Second Step"
in
  result 
  
// Hello World !!!  
```
Nested **let/in** block
```javascript
let	
	tot = let			
				a = 10,
				b = 10,
			in
				a + b,

	result = "Total is " & Text.From(tot)
in
	Result

// 20
```

> When looking at a query you might think that steps are evaluated in sequential order as they appear in the query. This is NOT the case though. Power Query evaluates steps only when needed for final result and in any order is chooses to be most efficient. This is called in programing world for _lazy evaluation_. If output from a step is not needed to produce the final returned, then such a step may not be evaluated at all.

Understanding what **list**, **record**, **table** are is the first essential things learn. Here come the fundamentals:

```javascript
list = {1, "a", Error, "c"} 
list{1}  // value "c"
list{3}  // ???

record  = [A=1, B="a", C=Error, D=2 )] 
record[B]  // value "anna"
record[D]  // value 2

table = #table({"A", "B", "C", "D"}, {{1, "a", 2, 3}, {2, "b", 3, 4}})
table[A] // list{1,2}
Table.Column(table, "A") // list{1,2}


T[A] ---> list {1,2} (Whaole column. Works with hardcoded name only)
Table.Column(T, "A") ---> list {1,2} (Same as above... but can be called with variable)
  ↓  
+-------+
| A | B | ← Table.ColumnNames(T) ---> list {A, B}  (List of column names)
|---+---|
| 1 | 2 | ← T[B]{0} ---> 2 (Cell value)
| 2 | 4 | ← T{1} ---> record [A=2,B=4]  (Whole row)
+---+---+
```

Remove unwanted rows in a  **table** example
```javascript
	tbl = #table({"N", "A"},{{"m","9"},{"a","2"}}),
	| N | A |
	|---+---|
	| m | 9 |
	| a | 2 |

	// For each row callback with row record is called. 
	// If callback returns false, the row is removed..
	Table.SelectRows(tbl, (_) => [N] ="m")
	| N | A |
	|---+---|
	| m | 9 |
```


**Iterations** like with **for-loop** does exist in M. To simply iterate we usually get help of a list. Note! **each** is simply sugar syntax for **(_) =>**.

```javascript
newList = let
	list = List.Generate(() => 1, each _ <= 5, each _ + 1) 
	// same as list = {1,2,3,4,5}
in 
	List.Accumulate(list, {}, (thisList, i) => List.Combine({thisList, {i+10}}))

// {11, 12, 13, 14, 15}  
```



<p align=right><a id="import-data-into-a-query-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [**Import/export data to/from a query**]()
---

Power Query comes with a build-in intuitive functionality to automatically connect and import data from various sources. You can import data from a table in same document you are in, other excel documents, google sheets, files like PDF or CVS on your hard-drive or connect to web addresses or external databases. More about this can be read [here](https://support.office.com/en-us/article/define-and-use-names-in-formulas-4d0f13ac-53b7-422e-afd2-abd7ff379c64).  

In Excel data importing options can be found in `Data -> Get & Transform data` section.

Example of a basic data import to a query from Excel table/range in current workbook.  

In your excel dworkbook click on a cell or select section containing data that you would like to import into a query.

Then go to `Get Data -> Get & Transform data -> From Table/Range`. 

At current moment Excel need the data to be imported from a _[table](https://support.office.com/en-us/article/overview-of-excel-tables-7ab0bb7d-3a9e-4b56-a3c9-6c94334e492c)_ and if the cell/range you have selected is not recognized by Excel as a table, then Excel will auto-launch wizard to navigate you through converting you selected range to a table Afterward Power Query Editor launches and auto-generates a new query that imports your selected data. 

In this new query data is loaded in first variable usually named `Source`, as a first step. In second step it auto detect column types of the imported columns. This step is usually named `Changed Type`. Sometimes the intelligent guess power query does is not fully correct and it needs your attention to change column-by-column manually. 

Also this `Changed Type` step can be safely removed and you can further work on and modify data in this query according to your needs. 

When done click `Close & Load` button and that load the final result of the query into back into your workbook. Power query will ask where to place the data. It always places the data in worksheets as a table, in a predefined default template style. 

**<a id="examples-of-data-import-in-m">Examples:</a> Some M functions that import data.**

From current worksheet. _Tables_ and _Named Ranges_ from your current workbook.
```javascript
// Import all objects in current Excel workbook to Power Query as a table. Tables, Sheets and Named Ranges defined in workbook will each one reside one row in this table.
TableWithObjects = Excel.CurrentWorkbook()
Source = Excel.CurrentWorkbook(){[Name="tableName"]}[Content]
```

__From local folder.__: List of _Files_ with _Attributes_ in a specific local location.
```javascript
// Import all files from a specific folder and sub-folders.
TableWithFiles = Folder.Files("C:\Users\marti\Favorites")
```

__From Web-page__: HTML presented as _Tables_
```javascript
// Import HTML web page represented as tables
TableWithWabPage = Web.Page(Web.Contents("https://www.timeanddate.com/"))
```

<br><p align=right><a id="types-values-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Types in M]()
---


More detailed description about [here](https://www.poweredsolutions.co/2018/03/12/data-types-data-conversion-ascribed-data-types-power-query-power-bi/). 


||||
---|---|---
type number | 1 or 1,2
type text | "a", "1" or "two words"
type logical | true or false
tape table | i.e. #table({},{})  (empty table)
type list | {1,2}
type record | [A=1, B=2]
type function | (name) => let return = "My name is" & name in return
datetime | 1976-08-21 00:00:00
Type date | 1976-08-21
Type time | 00:00:00

**What does `nullable` mean in Power Query M?**
So what does it mean that a type is nullable and how does it affect us? If you do ever compare `null` value with any other value by a relational operator (<, >, <=, >=) then the result of comparison is not the logical value as you might expect but the null itself. Value compared in if-statement is `null` then error is thrown:<br> `if null < 5 then "A" else "B"` → error.

We can cast a type that usually is not null to a type that can be null. Type number is not nullable by default therefore `if null < 5` fails. If 5 here was defined as `type nullable number` then it would not fail.

When a column is of type nullable number or a input parameter to a function is type nullable number then we implicitly tell that this number can be null and tell Power Query not throwing error it it happens.

> Note! 
`type number` and `type nullable number` are NOT the same! Thefore for example when comparing if a columns type is a number we need to check for both `{{type number},{type nullable number}}` as it can any of thoss, depending on where we imported the data from!


<br><p align=right><a id="each-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [**`Each`**]() & [**`_`**]()
---
Expression __`each`__ is a _function definition_ with one input variable without name nor type. It is simple _the abbreviation_ for __`(_) =>`__. It has not the same functionality nor meaning as "each" in java or C#. In M "conditional functions" are functions returning type logical (true or false). Here word "each" makes sense in this context when working with "conditional functions".

Expression __`__`__ is an _unnamed variable_ in a function. The use of `_`  (that is called a throw-away_ variable) is common across several programming languages, Python included. Whenever a name of the input variable to a function is not necessary to be known (declared), in order to have less to write `_` can be used. Sometimes in obvious cases where the variable name is absolutely necessary, writing out `_` can be skipped if used with `each`.  

For example:
`tSelectedRows = Table.SelectRows(tbl, each [Age] < 25)` 
is same as
`tSelectedRows = Table.SelectRows(tbl, (_) => [Age] < 25)` 

[Table.SelectRows(table, "conditional function")](https://docs.microsoft.com/en-us/powerquery-m/table-selectrows) calls the "conditional function" for each and every row in the table.

__Example:__ <a id="each-e"></a> 
```javascript
let
	list = {1, 2, 3, 4},
	
	// Identical functions
	function1 = (elem) => elem * 100,
	function2 = each _ * 100,

	// Function Transform() calls functionX for every list elem
	result1 = List.Transform(list, function1),
	result2 = List.Transform(list, function2),

	// Prof that each is (_) => 
	result = if (result1 = result2) then "SAME" else "DIFFER"
in
	result

Returns  →   SAME

// Similar as above but as a one-liner
let
	result = List.Transform({1, 2, 3, 4}, each _ * 100)
in
	result

Returns  →  {100, 200, 300, 400}
```

<br><p align=right><a id="lists-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [**Lists**](#)

---

A list can be described as an ordered sequence of values of any type. Each element of a list is assigned an index starting with 0. M supports infinitely large lists. List are easy and fast to iterate (loop) over.

Lists can be empty `{}`. Operators `equal` `=` and `not equal` `<>` make it possible to compare lists. Operator `&` combines lists. 

Read more [here](https://ssbi-blog.de/blog/technical-topics-english/lists-in-power-query-how-when-and-why/).

<a id="list-example-in-m"></a>

```javascript
l = {"a", 24} 
l{0}  // "a"
l{List.Count(l)-1} // 24 (last element)
```

It happens that a list is empty. This may cause error and abort execution of the query. Guard for it like this:

```m
l = {} 
try l{List.Count(l)-1} otherwise "failed here"  // "failed here"
try {}{6} otherwise null // null
```

<a id="list-syntax-example-in-m"></a> 

Some usefull List functions:

```javascript
// Capitalize list elements
List.Transform(l, Text.Proper)

// Combine 2 lists to one list (same as l1 & l2).
List.Combine({l1, l2})

// Convert list elements to text
List.Transform(l, Text.From)
```

### **Some useful List function to keep in mind**

- [**List.Select(list, cb(listItem))**](https://learn.microsoft.com/en-us/powerquery-m/list-select)
Returns SAME list but with filtered items depending on if cb returns true.
- [**List.Accumulate(list, seed, cb(prevRet, listItem))**](https://learn.microsoft.com/en-us/powerquery-m/list-accumulate)
Used to sum a list, or to ADD items to NEW list depending on what callback returns i.e. `if something? then prevRet&{item} else prevRet`. Here prevItem is what the callback returned in previous run. First time prevRet is seed.
- [**List.Transform(list, cb(listitem))**](https://learn.microsoft.com/en-us/powerquery-m/list-transform)
Returns NEW list with same amount of items but modified depending on what callbac returns. Good to change each item. 
- [**List.NonNullCount**](https://learn.microsoft.com/en-us/powerquery-m/list-nonnullcount)
Returns tot number of items thatare not null. If error is in the list, it asserts. 
- [**List.Contains(list, null)**](https://learn.microsoft.com/en-us/powerquery-m/list-contains)
Return true if it found firt value in the list. If an error is found firt, it aserts.

<br><p align=right><a id="records-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [**Records**](#)
---

A record can be described as a set of name=value pairs where name is a text reference (column name) and value is an element of any type (cell value). 

Records can be `[]`. Operators `=` and `<>` make it possible to compare records, while `&` combines records. 
Note, a row of a table is a record. 

Read more here [here](https://ssbi-blog.de/blog/technical-topics-english/records-in-power-query-how-when-and-why/).

<a id="record-example-in-m"></a>

```javascript
R = [A=1, B=2] 
R[B]  //  2

t = Table.FromRecords({R, R})
| A | B |
|-------|
| 1 | 2 |
| 1 | 2 |

Table.ReplaceRows(t, 1, 1, {[A = 3], [B = 4]})
| A | B |
|-------|
| 1 | 2 |
| 3 | 4 |

```

<br><p align=right><a id="tables-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [**Tables**](#)
---
A table can be described as a set of rows and columns building up cells where the values are stored. The very top of each table contains unique column names that must always exist. If column header names are not defined or of some reason unknown (normal scenario when importing data from csv files) then M auto-creates default names like "Column1", "Column2" etc. Power Query mostly works with sets of data represented as tables. Tables are often returned by functions, steps or queries and auto-created when data is imported to Power Query.

Rows of a table are records of values, while columns are list of values. Hold this in mind is when using [power query functions](https://docs.microsoft.com/en-us/powerquery-m/power-query-m-function-reference) as often parameters and iterations of those functions  are _lists_ or _records_.

<a id="record-example-in-m"></a>

```javascript
 T[A] ---> list {1,2} (Whaole column. Works with hardcoded name only)
 Table.Column(T, "A") ---> list {1,2} (Same as above... but can be called with variable)
  ↓  
+-------+
| A | B | ← Table.ColumnNames(T) ---> list {A, B}  (List of column names)
|---+---|
| 1 | 2 | ← T[B]{0} ---> 2 (Cell value)
| 2 | 4 | ← T{1} ---> record [A=2,B=4]  (Whole row)
+---+---+


// Creates table with defined types for its columns.
// Note. On purpose on ofcells contains error.
tbl =#table(type table
			[
				Number=number,
				Date=date,
				#"Column X"=text
			], 
			{
				{1, #date("error"), "Hello"},
				{2, #date(2016,1,1), "World"}  
			}),
	
cell = tbl{1}[Column X], // World
row = tbl{1}, // {2, 2016-01-01, "World" }
column= Table.Column(tbl, "Date"), // { Error, 2016-01-01 }  
```

The header of a column also defines the data type of elements in the column i.e. type `number`, `text`, `date`, `logical` (see [M types](#types-example-in-m)). Type `any`  means that such a column can contain elements with a mix of types.

There are mainly 3 operators that can be used in conjunction with tables: `=`, `<>` and `&`. First two are pretty straight forward, but the third one `&` is worth some extra explanation.

_<a id="record-example-in-m">Example:</a> Combining tables by using `&`_

```javascript
tblA		tblB
| A | B |	| A | B |
|---+---|	|---+---|
| 1 |   |	| 1 | 2 | 

// Combine same headers
tbl = tblA & tblB 
| A | B |
|---+---+
| 1 |   |
| 1 | 2 |

// Order matters
tbl = Table.Combine({tblB, tblA})
| A | B |
|---+---+
| 1 | 2 |
| 1 |   |
```

```javascript
tblA		tblB
| A | B |	| a | b |
|---+---|	|---+---|
| 1 |   |	| 1 | 2 | 

// Combine different headers
tbl = tblA & tblB 
tbl = Table.Combine({tblA, tblB})
| A | B | a | b |
|---+---|---+---|
| 1 |   | 1 | 2 | 
```
 <br><p align=right><a id="columns-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Columns]()
The easiest way to **get a column** from a table is as a list.

```javascript
tbl
      ↓
| A | B |
|-------|
| 1 | 2 |
| 1 | 2 |

columnAsAList = Table.TransformRows(tbl, each [B])  // {2, 2}

```
The easiest way to **replace a column** in a table is ... TODO
```javascript

```

<br><p align=right><a id="columns-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Row]()
The easiest way to **get a row** from a table is as a record.

```javascript
tbl
| A | B |
|-------|
| 1 | 3 |
| 2 | 4 | ←

row = tbl{1} // [A=2, B=4]

```
The easiest way to **replace a row** in a table is ... TODO
```javascript

```
<br><p align=right><a id="columns-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### **Some useful Table function to keep in mind**

- [**Table.FromRecords**({ [A=1,B=2], [B=1,B=2] })](https://docs.microsoft.com/en-us/powerquery-m/Table-FromRecords)<br> Creates a new table from provided list of records and returns this new table. 

- [**Table.ColumnNames**(table)](https://docs.microsoft.com/en-us/powerquery-m/table-columnnames)<br> Returns a list with column names as text.

- [**Table.TransformRows**(table, cb-called-for-each-row(row_as_record))](https://docs.microsoft.com/en-us/powerquery-m/table-transformrows)<br> This useful function returns a list of values returned by a callback. For each row in a table, a callback with current row (in form of record) is called. The value that the callback returns is placed in the list. This can be used i.e.for mappng special column = retuning only a column in a table in form of a list!

- [Table.TransformColumns(tbl, list, )](https://docs.microsoft.com/en-us/powerquery-m/table-transformcolumns)<br>
- [Table.TransformColumnTypes(table, list with <name>,<type> elements. I.e. {"colA,typeA , colB,typeB"})](https://docs.microsoft.com/en-us/powerquery-m/table-transformcolumntypes)<br> This function 
creates new columns the type of one or several columns of the table that provided as first parameter. The result is returned as a NEW modified table. The second parameter is a list of elements with syntax `{"ColName", type X}` - describing what column(s) and what type to change to. Unfortunately most often this column names are __hard-coded__, making the function very sensitive to any future changes in column names. A simple change like "Name"  → "name" in the input data will make this function and whole query fail. There are cases when we can avoid hard-coding column names and this is presented in one of the examples below.

- [Table.TransformColumnTypes(tbl, list)](https://docs.microsoft.com/en-us/powerquery-m/table-transformcolumntypes):<br>  <br><br> [Table.TransformColumns(tbl, list, )](https://docs.microsoft.com/en-us/powerquery-m/table-transformcolumns).<br><br> Many table are constructed in similar way so we explain this in more detail. It takes a table we want to transform as first parameter and returned new transformed table. Second parameter is.

You can read more about records [here](https://ssbi-blog.de/blog/technical-topics-english/tables-in-power-query-how-when-and-why/).

  __Example:__ <a id="accessing-e">Accessing row or single element in a table</a> 
```javascript
// Accessing a row in a table
// TableName[ColumnName] → the result is a list of elements
#table({"A","B"},{{1,"x"},{2,"y"}})[A] → a list {1, 2}
#table({"A","B"},{{1,"x"},{2,"y"}})[B] → a list {"x", "y"}

// Accessing a single cell in a table
// TableName[ColumnName]{RowIndex} → the result is whatever in element
| A | B |
| 1 | 3 |
| 2 | 4 | 
#table({"A","B"},{{1,3},{2,4}}){1}[B] → value 4
```
Example: <a id="dynamically-change-type-e" href="https://community.powerbi.com/t5/Desktop/Power-Query-M-Change-proper-case-for-first-row-of-the-table/td-p/318711">Dynamically change all table column to one typ</a><br>
_When changing type on a column through Power Query UI the auto-generated M code used hard-coded column names. If the column header naming  in the future data imports changes, our query stops working. There exist a more dynamic way of accessing columns._
```javascript
TODO
```

  __Example:__ <a id="accessing-e" href="https://www.thebiccountant.com/2017/01/09/dynamic-bulk-type-transformation-in-power-query-power-bi-and-m/">Capitalizing header texts in a table</a> 

```javascript
// | name | aGe |  <- tblPersons
// | Anna | 22  |
// | Carl | 56  | 

let
	tblPersons = #table({"name", "aGe"}, {{"anna",22},{"carl",56}}),
	result = tblPersons
	TODO
in
	return
```


<br><p align=right><a id="accessing-values-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>


### [**Accessing values**]()
---

Here comes some syntax on how to access parts of lists, records of tables

__TABLES__
```java
T
+-------+
| A | B |
|---+---+
| 1 | 2 |
| 3 | 4 |
+---+---+

T[A] →  a list {1, 3}
T{1} → a record [A=3, B=4]
T[B]{2}→ T{[A=2]}[B] → Table.Column(T, "B"){2} →  a single value 4

//The way T{[A=2]} only possible if values in column A are unique. Otherwise TODO???


Table.ColumnNames(T) → a list of texts {"A", "B"}
Table.ColumnNames(T){1} → a single text "B"

T[X] → error
T[X]? → null
T[A]? →  a list {1, 3}
Table.ColumnNames(T){2} → error
Table.ColumnNames(T){2}? → null ???

Note, when `?` is used after field reference then null is returned in case of "not found". Otherwise error is thrown!

var = "A"
T[var] → error  // referring to column from [] do not support variables
Table.Column(T, var) →  a list {1, 3} // here its fine to use variable

Withing brackets [] variables are not allowed. Here native functions can be used.
```

__RECORDS__
```java
R = [A=1, B=2, C=3]

R[A] → Record.Field(R, "A") → a single value 1
Record.FieldNames(R)  → a list of texts {"A", "B", "C"}
Record.FieldNames(R){0}  → a text "A"

R[X] → error
R[X]? → null 
R[A]? → a single value 1
Record.Field(R, "X")  →  ??? error or null 

var="A"
R[var] → error // referring to column from [] do not support variables
Record.Field(R, var) → a single value 1 // here its fine to use variable
```

__LISTS__
```
L = {1, 2, 3, 4}

L{0} → 1
L{1} → error
L{1}? → null
```

<br><p align=right><a id="operators-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Operators and Expressions in M]()
---

Note in bellow list that meaning of an operator can vary depending on the type of operands. Full list of operators can be found [here](https://docs.microsoft.com/en-us/powerquery-m/operators).

||||
---|---|---
& |	Concatenation | "A" & "BC" → "ABC"<br> {1} & {2,3} → {1,2,3}<br> [a=1] & [b=2] → [a=1, b=2]<br> #date(2020,3,20) & #time(12,30,20) → 20/03/2020 12:30:20
x or y | Cond. OR | _evaluates right operand only if necessary_
x and y | Cond. AND | _evaluates right operand only if necessary_
x <> y | Not equal | →  `true` or `false`
not x | Logical NOT | →  `true` or `false`
x >= y | Greater or equal | →  `true` or `false`
x <= y | Less or equal | →  `true` or `false`
x = y | Equal | →  `true` or `false`
#duration | Duration | #duration(days, hours, minutes, seconds)<br>
#date | Date | #date(year, month, day)<br> #date(2020,3,20) - #duration(10,0,0,0) → 20020/03/10
#time | Time | #time(hour, minute, second)<br> #time(24,0,0) + #duration(0,14,90,0)  → 15:30:00 
1+2 | Sum |  → 3
1+"a" | Error | → We cannot apply operator + to types Number and Text
"a"+"b" | Error | → We cannot apply operator + to types Number and Text
"a"+null | Error | → error

<br>

|__=__| | |
|---|---|---|
|Tables| `tableA = tableA` |  `true` |
|Lists| `listA = listB` | `false` |
|Null| `null = listB` | `???` |
|__<>__| | |
|Tables| `tableA <> tableB` |  `true` |
|Lists| `listA = listB` | `false` |
|Null| `null <> listB` | `???` |
|__&__| | |
|Null| `null & {2,3}` | `null` |
|Strings| `"A" & "BC"` | `"ABC"`|
|Lists| `{1} & {2,3}` | `{1,2,3}` |
|Records| `[a=1] & [b=2,c=3]` |  `[a=1,b=2,c=3]` |
|Tables|` #table({"A"},{{1}}) & #table({"B"},{{2}})` | ` #table({"A","B"},{{1},{2}})` |

<br><p align=right><a id="step-execution-order-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [Step execution order]()
---

__TODO - Write a bit more__
step1 = do something fast
step2 = do something bit time consuming
step3 = do something more time consuming

Result = if step1<>null then step1 else if step2<>null then step2 else  step3
Play around with setting step1/2/3 to null and measuring execution time.

This is a technique to avoid executing steps in vain

```



```
<br><p align=right><a id="measuring-performance-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [Measuring performance]()
---

__TODO - Write something about performance__


```



```

<br><p align=right><a id="useful-native-functions-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [Useful native functions]()
---

__TODO - Add about functions__


```



```


<br><p align=right><a id="things-to-avoid-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [Things to avois]()
---

__TODO - Write more about what to avoid__


```



```


<p align=right><a id="reshape-a-table-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Reshape a table]()
---

Following short examples describe how you reshape a table to different order of columns, different amount of columns with different values, modify ranges of values or how in Power Query just to  modified one single value in a table. Function `Table.TransformRows(table, function)` is very useful. Why? check the code bellow.

_<a id="reshape-example-1-table.transformRows-in-m">Example 1</a>: "Reshaping" to table to exactly same shape_
```
Table T
+-----------------------------+
| ID | First name | Last name |
|-----------------------------+
| 1  |   adam     |  lee      |
+----+------------+-----------+
| 2  |   ewa      |  cox      |
+-----------------------------+
```

```javascript
let
    T = #table({"ID","First name","Last name"},{{1,"adam","lai"},{2,"ewa","lee"}}),
    Result = Table.FromRecords(Table.TransformRows(T,each _))
in
    Result
```
Here the transform function `each _` (second input parameter in in function [Table.TransformRows()](https://docs.microsoft.com/en-us/powerquery-m/table-transformrows)) receives, for every row, current row as a record. Due to _ the very same input records is returned from the function (see section [functions](TODO)). As a result this function __returns a list of records__ as seen bellow.

```
Table.TransformRows() result
+--------+
|  List  |
|--------+
| record |
+--------+
| record |
+--------+
```
This list of records is in turn the input parameter to outer function [Table.FromRecords()](https://docs.microsoft.com/en-us/powerquery-m/table-fromrecords) as this function takes exactly this as input - a list of records. The inner function returns a list of records -> the outer function consumes a list of records. Perfect. In this example exactly same table as the one we stared with is produced.

<br>

_<a id="reshape-example-2-table.transformRows-in-m">Example 2</a>: "Reshaping" the table by combining two columns, capitalizing texts and reordering columns._
```
Table T
+-----------------------------+
| ID | First name | Last name |
|-----------------------------+
| 1  |   adam     |  lee      |
+----+------------+-----------+
| 2  |   ewa      |  cox      |
+-----------------------------+
```
```javascript
let
    T = #table({"ID","First name","Last name"},{{1,"adam","lai"},{2,"ewa","lee"}}),
    fknTransform = each [Name=Text.Proper([First name]) & " " & [Last name], id=[ID]],
    Result = Table.FromRecords(Table.TransformRows(T, fknTransform))
in
    Result
```

```
+---------------+
|   Name   | id |
|---------------+
| Adam lee | 1  |
+----------+----+
| Ewa cox  | 2  |
+---------------+
```
Exactly same technique as in example 1 above with the modification of transform function, second input parameter in in function [Table.TransformRows()](https://docs.microsoft.com/en-us/powerquery-m/table-transformrows) moved to own row for better readability. This function takes in current row record with three items [Id=.., First name=.., Last name=..] and returns a record with two items [Name=.., id=..]. In one go we changed order of columns, combined columns, capitalized elements, changes header names, and this function very well could have been written as a readable one-liner. Powerful.

<br>

_<a id="reshape-example-2-table.transformRows-in-m">Example 3</a>: Change only one single value of a column in Power Query._
```
Table T
+-----------------------------+
| ID | First name | Last name |
|-----------------------------+
| 1  |   adam     |  lee      |  ← i.e- change lee to null
+----+------------+-----------+
| 2  |   ewa      |  lee      |
+-----------------------------+
```
Before starting!<br>
In order to identify one unique cell in a table at least one column with all unique values must exist. In database-world a filed (=column) with all unique values can be set to a [primary key](TODO). Before trying to change a values in a table cell we must know what column contains only unique values. In our example we call such a column a "primary key column".

We assume here that table T in this example has column ID as "primary-key-colum" and every  value in ID column is and will be _unique_ for every row.

_Useful info! When you use the "Remove Duplicates" button in Power Query Editor to remove all duplicate values from a column or columns, which behind the scenes uses the [Table.Distinct()](https://docs.microsoft.com/en-us/powerquery-m/table-distinct) M function, then Power Query behind the scene defines a primary key on a table._

The code used function Table.AddColumn() that work in similar way as Table.TransformRows() as it iterates over each row and provides current row to a callback table. It could be implemented with Table.TransformRows() but as in sfinal part of this example we will transform this to fully dynamic function, then Table.TransformRows() would put a limitation as we need need to know all the field names. TODO is it really tru, can it not be dome with transform?
```javascript
let
    T = #table({"ID","First name","Last name"},{{1,"adam","lai"},{2,"ewa","lee"}}),

    // Values to provide each time in order 
    // to change one value in table Table.
    // Dynamic values. Can be changed for each run!
    NewValue = "CHANGED", 
    Table = T, // Table to change
    PrimKeyColumnName = "ID", // Name of primary key column, with all-unique-values
    PrimKeyValueToChange = 2, // Row to change
    ColumnNameToChange = "Last name", // Column to change

    // Small trick for later. 
    // Rename the column that is defined by PrimKeyColumnName as primary key
    // to a name defined by us, static name, never changing.
    TableBeforeChange = Table.RenameColumns(Table, {PrimKeyColumnName, "PK"}),

    // Save originals for later use, all as lists.
    lOriginalColumns = Table.ColumnNames(TableBeforeChange),
    lOriginalValues = Table.Column(TableBeforeChange, ColumnNameToChange),
    lPrivateKeys = TableBeforeChange[PK],

    // AddColumn() calls each-function for every row,then for desired row we set the new value otherwise old
    // Because field references like [mColName] are never dynamic
    TableAfterChange = Table.AddColumn(
		TableBeforeChange, 
		"TempCol", 
		each if ([PK]=PrimKeyValueToChange) then NewValue else lOriginalValues{List.PositionOf(lPrivateKeys,[PK])}),
    
    // Remove org name, rename tem name to org, restore previous order
    T1 = Table.RemoveColumns(TableAfterChange, ColumnNameToChange),
    T2 = Table.RenameColumns(T1, {"TempCol", ColumnNameToChange}),
    T3 = Table.ReorderColumns(T2, lOriginalColumns),

    Result=T3 
in
    Result
```

Same as above moved out to a fully dynamic function. Save the following function with name `fnChangeValue`.
```javascript
(Table as table, NewValue as any, PrimKeyColumnName as text, PrimKeyValueToChange as any, ColumnNameToChange ) as table =>
let
    // Small trick for later. 
    // Rename the column that is defined by PrimKeyColumnName as primary key
    // to a name defined by us, static name, never changing.
    TableBeforeChange = Table.RenameColumns(Table, {PrimKeyColumnName, "PK"}),

    // Save originals for later use, all as lists.
    lOriginalColumns = Table.ColumnNames(TableBeforeChange),
    lOriginalValues = Table.Column(TableBeforeChange, ColumnNameToChange),
    lPrivateKeys = TableBeforeChange[PK],

    // AddColumn() calls each-function for every row,then for desired row we set the new value otherwise old
    // Because field references like [mColName] are never dynamic
    TableAfterChange = Table.AddColumn(
		TableBeforeChange, 
		"TempCol", 
		each if ([PK]=PrimKeyValueToChange) then NewValue else lOriginalValues{List.PositionOf(lPrivateKeys,[PK])}),
    
    // Remove org name, rename tem name to org, restore previous order
    T1 = Table.RemoveColumns(TableAfterChange, ColumnNameToChange),
    T2 = Table.RenameColumns(T1, {"TempCol", ColumnNameToChange}),
    Result = Table.ReorderColumns(T2, lOriginalColumns)
in  
    Result
```
Calling our function from any query
```javascript
let
    T = #table({"ID","First name","Last name"},{{1,"adam","lai"},{2,"ewa","lee"}}),

	// change the value
    Result = fnChangeValue(T, null, "ID", 1, "Last name")
in
    Result
```
Changing a value in a table, totally dynamically is not a straight forward query to write. Here is a solution that works. There can be some error handling added and a performance tweak. Full solution can be found in our blog TODO [here](TODO).


<p align=right><a id="looping-and-iterations-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>


#### [Looping & Iterations]()
---
Looping and iterations in M work a bit differently. Here we do not have while for for- statements. In M we always loop over a range, and a callback function is usually called for each iteration. This is the standard procedure for most natime List, Record and Table functions.

[List.Accumulate()](https://docs.microsoft.com/en-us/powerquery-m/list-accumulate "Documentation for the function") and its 2nd parameter "seed" is of type "any", meaning that this function is not limited to lists objects, but can handle and  return any structured value like: tables, lists or records. En our example we just add a simple number as list element in callback but this technique can be used to perform more complicated iterative tasks on table or records. Function List.Accumulate is very powerful as iterations on sets of lists is big part of Power Query.

 __Example:__ Iterations in M 
_Just for comparison, in C#, it may looks like this_
```javascript
static List<int> GetList()
{
	// Initial variables
	int NbrOfIterations = 5;
	List<int> Result = new List<int>();

	// Function to call for each iteration, adds item to a list
	void AddToList(List<int> res, int i) { res.Add(i); }

	// Iterate using for loop
	for (int i = 1; i <= NbrOfIterations; i++)
	{
		AddToList(Result, i);
	}

	Console.WriteLine(string.Join("\t", Result));
	return Result;  
}

List `1 2 3 4 5` is returned
```
_Iterate in M over another list using List.Accumulate._
```javascript
// Similar thing in M language, iterating over another list
let
	// Initial variables
	Iterations = {1, 2, 3, 4, 5},

	// Function to call for each iteration, adds item to a list
	AddToList = (res, i) => List.Combine({res, {i}}),

	// Iterate using function Accumulate(list, seed, accumulator(state, current))
	Result = List.Accumulate(Iterations, {}, AddToList)
in 
	Result

	List `1 2 3 4 5` is returned
```

 I think the example above might need some explanation. List.Accumulate is a function that loops through items of a list and calls a provided function for each iteration. Following description of parameters explain how it works. It is a very powerful function - worth understanding! 

 The key here are parameters, specially a bit "special behavior" of parameters in the callback function ("accumulator"):<br> __List.Accumulate( list , seed , accumulator(state, current) )__ 

__list__ - Here we provide a list "iterations" which is {1,2,3,4,5}. Accumulate() calls the callback function (set in 3rd parameter) for each element in this list. As we have in tot 5 elements in the list, then Accumulate() will iterate 5 times meaning function `AddToList` will be called 5 times.

__seed__ - Start value for the very first iteration, the initial "state". As we expect the rest to be a list then we provide empty `list` as input that we later iterations add values to. In first iteration this exact value (empty list) is sent to our callback as "res" (state) parameter. 

__accumulator__ - Our function that that defines what to do for each iteration. It is often called "callback function" as we send it as parameter into another function that later call it. Accumulate() calls it for each iteration. By [definition](https://docs.microsoft.com/en-us/powerquery-m/list-accumulate) it has two required input parameters. First parameter, in documentation, is called "state" and simply is a value return in previous iteration. But for very first iteration there is no previous value. Yes, and here is where the __seed__ value, our start value, comes to use. In our case we provided empty list as initial value so it is provided to callback in first iteration. Second time callback function is called the result from previous run was a list with 1 element, third run it's a list with 2 element, and so on. The second parameter in the callback function, __current__ is simply the current element of the list Accumulate() iterates over. First tie it is element 1, second element 2 an so on.

_Similar thing in M language, using recursiveness_
```javascript
	let 
		// Defining initial variables
		Iterations = 5,

		// Iterate using recursiveness
		Iterate = (i) => if (i > 0) then List.Combine({@Result(i-1), {i}}) else {},

		Result = Iterate(Iterations)
	in
		Result

		List `1 2 3 4 5` is returned
```
In example above we use recursive function. When a function in M calls itself from inside itself then @ parameter must be used when called!

_Finally combining the both M techniques above -auto-create a list to later iterate over with Accumulate() function._
```javascript
	
	// Iterate only by defining number of iterations (here 10000)
	let
		Iterations = (i) => if (i > 0) then List.Combine({@Iterations(i-1), {i}}) else {},

		// Function to call for each iteration, adds item to a list
		AddToList = (res, i) => List.Combine({res, {i}}),

		// Iterate using Accumulate(list, seed, accumulator(state, current)) function
		Result = List.Accumulate(Iterations(10000), {}, AddToList)

	in
		Result

		List `1 2 3 4 5 ... 10000` is returned

```

<p align=right><a id="change-column-names-dynamically-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Change column names dynamically]()
---
There is often problematic whn code is auto-generated by Power Query that hard-coded column names are used in the query. This might work for the data loaded in at the moment, but same second as little as a letter changes in a column nama in source data, or a new column is added, then our query need to regenerated and debugged.

The main problem are always column and referring to those from code!

Here we show how to change column names dynamically without need of knowing number of columns nor their old names.

__TODO__
```
T= Table.RenameColumns(PromotedTable, List.Transform(Table.ColumnNames(PromotedTable), each {_, Text.Proper(Text.Trim(_))}))
```

<p align=right><a id="change-column-types-dynamically-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Change column types dynamically]()
---
There is often problematic whn code is auto-generated by Power Query that hard-coded column names are used in the query. This might work for the data loaded in at the moment, but same second as little as a letter changes in a column nama in source data, or a new column is added, then our query need to regenerated and debugged.

The main problem are always column and referring to those from code!

Here we show how to change column types dynamically without need of knowing number of columns nor their names.
__TODO__
```
T= Table.RenameColumns(PromotedTable, List.Transform(Table.ColumnNames(PromotedTable), each {_, Text.Proper(Text.Trim(_))}))
```

<p align=right><a id="#find-first-non-null-elem-in-list-in-m" align=right href="#table-of-content">↩ Back To Top</a></p>

#### [Find first non null element in a list]()
---
Here is  a simple function that finds first element in a list that is not null.
This kind of function do not exist in native library and can be sometimes handy to have.

```T = {null, null, "A", "B", null},
FirstNonNull= List.Accumulate(T, null, (res,cur)=> if (cur<>null) and (res=null) then cur else res)
```