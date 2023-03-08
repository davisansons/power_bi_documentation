# **Clean, Transform, and Load Data in Power BI**
This module covers how to clean and prepare data for analysis, how to
simplify complicated model, change data types, rename objects, and 
pivot data. 

## **Introduction**
When preparing data for reports there may be several possible issues
which make the data unprepared:
* Columns not having the expected data type.
* Columns containing errors.
* Columns containing null values.
* Unique columns containing duplicates.
* Single columns containing all the address information.

Power BI and Power Query offer a powerful environment to clean and
prepare the data. Clean data has the following advantages:
* Measures and columns produce more accurate results.
* Tables are organised and intuitive.
* Duplicates are removed.
* Complicated columns can be split into multiple simpler columns.
* Codes and integers can be made human readable.

## **Shape the Initial Data**
Power Query Editor allows you to transform data. This includes 
actions such as renaming columns or tables, changing data types,
removing columns, and more. 

When working with Power Query Editor, all steps taken are recorded.
Then, every time the query connects to the data source, all the
steps are automatically applied. Power Query only makes changes
to a particular view of data, therefore the changes do not affect
the original data source. 

### **Identify Column Headers and Names**
One step can be to identify the column headers and names within
the data and then ensuring that they are in the right place.

### **Promote Headers**
Power Query Editor assumes that all data belong in table rows. However,
a data source might have a first row that contains columns names. To correct
this inaccuracy you can promote the first table row into column headers.

### **Rename Columns**
You may discover that columns have incorrect header names which contain things
such as spelling errors, or are potentially not human-readable. Power Query
Editor allows you to rename the columns.

### **Remove Columns**
A key part of shaping data is to remove unnecessary columns. Best practice would
recommend that these columns are removed as early as possible.

### **Unpivot Columns**
In certain occasions you may want to unpivot the data, sometimes called
flattening the data, to put similar values in one column. When you unpivot,
you unpack the attribute-value pairs that represent an intersection point
of the new columns and re-orient tem into flattened columns. 

### **Pivot Columns**
Sometimes if the data is flat it can complicate the ability to identify
patterns in the data. Pivoting a column creates a table that contains an
aggregate value for each unique value in that column.

## **Simplify the Data Structure**
When you import data it retains its predefined table and colum names.
You may want to change this to make them more consistent or meaningful
to a user.

### **Rename a Query**
It's good practice to change uncommon or unhelpful query names to
names that are more obvious or that the user is more familiar with. 

### **Replace Values**
You can use Power Query Editor to replace any value with another value
in a selected column. This involves specifying the value to find and
the value you wish to replace it with. 

This feature can also be used to replace null values. 

### **Remove Duplicates**
You can also use the remove duplicates functionality to only keep unique
values in a select column. 

## **Evaluate and Change Column Data Types**
When loading a table, Power BI automatically scans the first 1,000 rows
(default settings) and tries to detect the type of data in the columns.
In certain situations Power BI may detect the incorrect data type.

It is best practice to evaluate the data types in Power Query Editor
before loading data into a Power BI data model. 

### **Implications of Incorrect Data Types**
Incorrect data types will prevent you from creating certain calculations,
deriving hierarchies, or creating proper relationships with other tables.

Having an incorrect data type on a date field will prevent the ability
to create a date hierarchy. However, it is best practice to use a
data table and turn off the auto date/time.

## **Combine Multiple Tables into a Single Table**
Queries can be combined to append or merge different tables together.

### **Append Queries**
When appending queries, you add rows of data to another table or query.
When you merge queries, you add columns from one table or query to another.
To merge two tables, you must have a column that is the key between the
two tables. 

Before combining queries, you can remove extraneous columns that are not
required for the task from the tables. Once this has been done and the tables
have been formatted correctly you can append queries using the **Append Queries**
dropdown in Power Query Editor.

### **Merge Queries**
When you merge queries, you are combining data from multiple tables into one
based on a column that is common between the tables. This process is similar
to a JOIN clause in SQL. You can choose how to join the two tables together:
* **Left Outer** - Displays all rows from the first table and only the matching
rows from the second.
* **Full Outer** - Displays all rows from both tables.
* **Inner** - Displays the matched rows between the two tables. 

## **Profile Data in Power BI**
Profiling data is about studying the nuances of the data: determining anomalies,
examining and developing the underlying data structures, and querying data
statistics. This is important as it allows you to shape and organise data so that
interacting with the data is uncomplicated. 

### **Examine Data Structures**
Before profiling data you should examine the data structure and how it is
organised.

### **Find Data Anomalies and Data Statistics**
Data anomalies are outliers within your data. Determining what the anomalies
are can help identify what a normal distribution of your data looks like and
whether specific data points need to be investigated further. Power Query
determine data anomalies by using the **Column Distribution** feature.

The **Column Quality** feature shows the percentages of data that is valid,
in error, and empty.

**Column Distribution** shows the distribution of data within the column and 
the counts of distinct and unique values. 

**Column Profile** gives a more in-depth overview of the statistics for the
first 1,000 rows of data (default setting). 

**Value Distribution** graph tells you the count for each distinct value in
that specific column. 

**Column Statistics** works on a numeric column and includes how many nulls
and zeroes exist, along with the averages, standard deviation, and how many
odd and even values there are. 

## **Use Advanced Editor to Modify M Code**
Each time data is shaped in Power query, you create a step in the process.
These steps can be created using the GUI, but Power Query uses the M
language behind the scenes. The combined steps can be read by using the
Power Query Advanced Editor. 

Each step will roughly align with one or two lines of M code. M code is
written top-down. Later steps in the process refer to previous steps by the
variable name. You must be careful when reordering these steps as it can
affect dependencies. Generally, the last query step is used as the in final
data set result. 