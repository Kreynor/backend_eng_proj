# Back-end Engineer
## Instructions
As a part of the onsite process, we would like to evaluate your coding skills. Please complete the following exercise and
get it back to us 48 hours prior to your visit.

When you come in, be prepared to walk us through your code and answer follow-up questions with a focus on your
assumptions, decisions, and coding process. We will be evaluating you both on the code, as a work product, and your
ability to communicate about your code.

We expect this problem to take at least 2 hours and no more than 8 hours of your time. Please stay within those
bounds.

Although Clover Health uses a primarily Python + PostgreSQL stack, we want to evaluate you in the best light so please
choose technologies and libraries that let you show your best work.

## Problem definition
You have directories containing data files and specification files. The specification files describe the structure of the
data files. Write an application in the language of your choice that reads format definitions from specification files. Use
these definitions to load the data files into a database.

## Problem details
Data files exist in a data/ directory relative to your application and specification files exist in a specs/ directory relative
to your application.

Specification files will have filenames equal to the file type they specify and extension of .csv. So
fileformat1.csv would be the specification for files of type fileformat1.

Data files will have filenames based on their specification file name, followed by an underscore, followed by the drop
date and an extension of .txt. For example, fileformat1_2007-10-15.txt would be a data file to be parsed using
specs/fileformat1.csv, which arrived on 10/15/2007.

Format files will be csv formated with columns "column name", "width", and "datatype".
* "column name" will be the name of that column in the database table
* "width" is the number of characters taken up by the column in the data file
* "datatype" is the SQL data type that should be used to store the value in the database table.

Data files will be flat text files with lines matching single records for the database. Lines are formatted as specified by
their associated specification file.

## Example
This is an example file pair; other files may vary in structure while still fitting the structure of the problem details
(above):
`specs/testformat1.csv:`

```python
"column name",width,datatype
name,10,TEXT
valid,1,BOOLEAN
count,3,INTEGER
```

Here we have a specification that describes 3 columns:
* The first 10 characters labeled "name" of type TEXT
* The next 1 character labeled "valid" of type BOOLEAN ('1' = True, '0' = False)
* The last 3 characters labeled "count" of type INTEGER

`data/testformat1_2015-06-28.txt:`

```python
Foonyor   1  1
Barzane   0-12
Quuxitude 1103
```

Processing this data file results in the following table:

|   | name      | valid   | count |
| 1 | --------- |:-------:| -----:|
| 2 | Foonyor   | TRUE    | 1     |
| 3 | Barzane   | FALSE   | -12   |
| 4 | Quuxitude | TRUE    | 103   |
 
## Expectations
* Database type and connection mechanism is left to your discretion.
* You should include tests that cover, at least, the examples given.
* You should implement the conversions for the data types: TEXT, BOOLEAN, and INTEGER
* You should be able to handle any specification file that matches the problem description (not just the given
example)
* Files can be assumed to use UTF-8 encoding