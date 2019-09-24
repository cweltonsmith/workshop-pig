# PIG


## WHAT IS PIG

## Why Use PIG

## PIG vs. HIVE

## PIG Example

salesTable = LOAD 'myinput/purchases.txt' USING PigStorage('\t') AS (Date:chararray,Time:chararray,Location:chararray,Category:chararray,Amount:float,Payment:chararray);

- This command loads the table into PIG.
- PigStorage is the 
- myinput is your input folder in hadoop

group_data = GROUP salesTable BY Category:



foreach_data = FOREACH group_data GENERATE CONCAT((chararray)$0,CONCAT(':',(chararray)COUNT($1)));


STORE foreach_data INTO 'pig_output' USING PigStorage('\t');

