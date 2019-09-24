# PIG Workshop 1
![](resouces/smith.png) Chase Smith


## WHAT IS PIG
* Pig is an Abstraction over MapReduce.
* Generally used with Hadoop.
* Uses a high-level language known as Pig Latin
* All scripts are internally converted to Map and Reduce tasks
* Pig Engine component converts Pig Latin scripts as inputs and converts them to MapReduce jobs
## Why Use PIG
* Pig Latin can perform MapReduce tasks easily without complex Java code
* Pig Latin is similiar to SQL
* Uses multi-query approach, reduces the length of codes
* Provides many built-in operators to support data operations
*Provides nested data types like tuples, bags, and maps that are missing from MapReduce
## Features of PIG
* Rich set of operators - Provides many operators like join, sort, etc.
* Ease of Programming - Pig Latin is similar to SQL so it's easy if you know SQL
* Optimiation Opportunities - Apache Pig tasks optimize their execution automatically
* Extensibility - With existing operators, users can develop their own functions to read, process, and write data
* UDF's - Pig provides the facility to create User-defined Functions in other programming langues to invoke/embed them in Pig Scripts
* Handles all kinds of data - Apache Pig analyzes all kinds of data and stores the results in HDFS
## PIG vs. HIVE
* Apache Pig uses Pig Latin, Hive uses HiveQL
* Pig Latin is a data flow language, HiveQL is a query processing language
* Pig Latin is a procedural language and fits in a pipeline paradigm, HiveQL is a declarative language
* Apache Pig can handle any form of structured data, Hive is mostly used for structured data
## PIG Example
salesTable = LOAD 'myinput/purchases.txt' USING PigStorage('\t') AS (Date:chararray,Time:chararray,Location:chararray,Category:chararray,Amount:float,Payment:chararray);
- This command loads the table into PIG.
- PigStorage is the 
- myinput is your input folder in hadoop

group_data = GROUP salesTable BY Category;

foreach_data = FOREACH group_data GENERATE CONCAT((chararray)$0,CONCAT(':',(chararray)COUNT($1)));

STORE foreach_data INTO 'pig_output' USING PigStorage('\t');
