# PIG Workshop 1
![](resources/smith.png) ![](resources/LinkedIn.jpg) <img src="resources/ProfilePicture.png" width="20%"> <img src="resources/hart_profile.png" width="20%"><br/>
&emsp;&emsp;&emsp; Chase Smith &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Kaleb Odle &emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Jacob Taylor &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Kevin Hart

![](resources/Apache_Pig_Logo.png)
## WHAT IS PIG
* Pig is an Abstraction over MapReduce.
* Created by Yahoo researchers as an easier alternative for MapReduce than Java
* Generally used with Hadoop.
* Uses a high-level language known as Pig Latin
* All scripts are internally converted to Map and Reduce tasks
* Pig Engine component converts Pig Latin scripts as inputs and converts them to MapReduce jobs

## Why Use PIG
* Pig Latin can perform MapReduce tasks easily without complex Java code
* Pig Latin is similiar to SQL, but is a scripting language instead of a query language
* Uses multi-query approach, reduces the length of codes
    * *Fun Fact: 10 lines of Pig Latin can be the equivalent of 200 lines of another language for MapReduce*
* Provides many built-in operators to support data operations
* Provides nested data types like tuples, bags, and maps that are missing from MapReduce

## Features of PIG
* Rich set of operators - Provides many operators like join, sort, etc.
* Ease of Programming - Pig Latin uses similar "query-speak" as SQL so SQL knowledge helps Pig Latin readability
* Optimization Opportunities - Apache Pig tasks optimize their execution automatically
* Extensibility - With existing operators, users can develop their own functions to read, process, and write data
* UDF's - Pig provides the facility to create User-defined Functions in other programming langues to invoke/embed them in Pig Scripts
* Handles all kinds of data - Apache Pig analyzes all kinds of data and stores the results in HDFS

## PIG vs. HIVE
* Apache Pig uses Pig Latin, Hive uses HiveQL
* Pig Latin is a data flow language, HiveQL is a query processing language
* Pig Latin is a procedural language and fits in a pipeline paradigm, HiveQL is a declarative language
* Apache Pig can handle any form of data (structured, semi-structured, and unstructured), Hive is mostly used for structured data

## PIG Example

1. Make small purchases.txt

    - `cd udacity_training/data`
    - `head -50 purchases.txt > test.txt`
    - `hadoop fs -put test.txt myinput`

2. Open Pig

    - `pig -x mapreduce`
 
3. Load data into a variable called salesTable (IGNORE warnings)

    - `salesTable = LOAD 'myinput/test.txt' USING PigStorage('\t') AS (Date:chararray,Time:chararray,Location:chararray,Category:chararray,Amount:float,Payment:chararray);`

4. Group our data by columns

    - `group_data = GROUP salesTable BY Category;`

5. Reduce the data

    - `foreach_data = FOREACH group_data GENERATE CONCAT((chararray)$0,CONCAT(':',(chararray)COUNT($1)));`

6. Put our foreach_data into mapreduce

    - `STORE foreach_data INTO 'pig_output' USING PigStorage('\t');`
