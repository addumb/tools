A collection of tools that I think should be in every SysAdmin's ~/bin.

## avg
Spit out the average of a column in a text file
## stddev
Spit out the standard deviation of a column in a text file
## column-bin
bin the columns of a text file (VERY useful for quick summaries of apache HTTP status codes and the like)
### Usage:
     $ cat test.csv	
    	log HTTP status: 200 body_size: 1024
    	log HTTP status: 200 body_size: 1024
    	log HTTP status: 500 body_size: 0
    	log HTTP status: 200 body_size: 10000
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 409 body_size: 10
     $ column-bin -c 4 < test.csv
    	409	1
    	400	3
    	200	3
    	500	1

## column-histogram
Similar to column-bin, but for continuous variables. Bin the column into bins of a fixed size OR bin them into log-based sizes to make either a histogram or a semi-log histogram.
### Usage:
     $ cat test.csv	
    	log HTTP status: 200 body_size: 1024
    	log HTTP status: 200 body_size: 1024
    	log HTTP status: 500 body_size: 0
    	log HTTP status: 200 body_size: 10000
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 400 body_size: 10
    	log HTTP status: 409 body_size: 10
     $ column-histogram -c 6 -b 1000 < test.csv
    	10000	1
    	0	5
    	1000	2
     $ column-histogram -c 6 -L 10 < test.csv
    	10000	1
    	0	1
    	10	4
    	1000	2

