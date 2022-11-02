# DataAggregation
![Data Aggregation](https://github.com/miielab/DataAggregation/workflows/Data%20Aggregation/badge.svg)

## Description
This script combines data in customizable ways based on a metadata CSV file provided by the user. 

Let's say that we have a collection of books and we want to aggregate the txt files based on their narration_style or any other columns. The CSV file may look something like this:
```
path,narration_style,protagonist_gender
data/book1.txt,1,female
data/book2.txt,1,male
data/book3.txt,1,female
data/book4.txt,0,female
data/book5.txt,0,male
```

Instead of performing an analysis on each book individually to answer our research questions, we can aggregate these books into larger collections which will give us more accurate, representative results. This script will do the aggregation for us based on how we would like your data grouped.

You have to add some groups you want to combine the data in the yaml file in order for this code to work.
