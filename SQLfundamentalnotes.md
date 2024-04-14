# SQL Fundamentals

## SELECT
_Selection of columns_

`SELECT * FROM tbl;`
|**Col 1** |**...**|**Col n**|
|----------|----------|----------|
| xx    | ...    | xx    |
| xx    | ...    | xx    |

`SELECT col1, col2 FROM tbl;`
|**Col 1** |**Col 2**|
|----------|----------|
| xx    | xx    |
| xx    | xx    |


## SELECT DISTINCT

`SELECT DISTINCT first_name FROM tbl;`
|**First Name** |
|----------|
| Anne    |
| Sally    |

`SELECT DISTINCT first_name, last_name FROM tbl;`
|**First Name** |**Last Name**|
|----------|----------|
| Anne    | Carter    |
| Anne    | Peterson    |
| Sally    | Green    |


## COUNT
_This counts the total number of rows in the query result._

`SELECT COUNT(DISTINCT first_name, last_name) FROM tbl;`
|**Count** |
|----------|
| 3    |



## SELECT WHERE
_Filtering of rows using the following operators:_
|**Operator** |**Description**|
|:----------:|:----------:|
| =    | Equal    |
| >    | Greater Than    |
| <    | Less Than    |
| >=    | Greater Than or Equal to    |
| <=    | Less Than or Equal to    |
| <> or != | Not Equal to    |


`SELECT * from tbl 
WHERE col1 > 4;`
|**Col 1** |**...**|**Col n**|
|----------|----------|----------|
| 5    | ...    | xx    |
| 7    | ...    | xx    |

`SELECT * from tbl 
WHERE col1 = 4 OR col2 = 'a';`
|**Col 1** |**Col 2**|**...**|**Col n**|
|----------|----------|----------|----------|
| 5    | a | ...    | xx    |
| 4    | b | ...    | xx    |



