# PIG


## WHAT IS PIG

## PIG Example

salesTable = LOAD 'myinput/purchases.txt' USING PigStorage('\t') AS (Date:chararray,Time:chararray,Location:chararray,Category:chararray,Amount:float,Payment:chararray);

- This command loads the table into PIG.
- PigStorage is the 
- myinput is your input folder in hadoop


