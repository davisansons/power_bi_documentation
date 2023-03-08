# **Get Data in Power BI**
This module covers how to retrieve data from a wide variety of sources and how to
improve performance while retrieving data. 

## **Introduction**
To create reports you must first extract data from various sources. Power Query
can then be used to help you clean data such as renaming columns, replacing values,
removing errors, and combining query results. Once the dataset is created it can be
published to Power BI Service. From there, other people can use that dataset to
build their own reports. 

## **Get Data From Files**
A frequent format used is a flat file. A flat file has only one data table and every
row of data is in the same structure. The file doesn't contain hierarchies. Some files
include .csv and .txt files.

The first step in this scenario would be to determine the location of the file being
used. It could be in the following locations:
* **Local** - You can import local files into Power BI. The file isn't moved into Power BI,
and a link doesn't remain to it. Instead, a new dataset is created in Power BI, and data 
from the Excel file is loaded into it. This means any changes made to the original file 
in Excel will not be reflected in the Power BI dataset. 
* **OneDrive for Business** - You can pull files from OneDrive. This method is effective
in keeping an Excel file and your dataset, reports, and dashboards in Power BI
synchronised. Power BI connect regularly to the file, this means any changes found are
automatically updated. 
* **SharePoint** - Saving files in SharePoint is similar to OneDrive. The main difference
is how you connect. You can either specify a URL or connect to the root folder.

### **Get Data From RDBMS**
Power BI can connect directly to the database instead of using exported flat files. 
These databases can be on the cloud or on-premise. 

The two options for connecting are **Import** and **DirectQuery**.

You can also write SQL queries to select a subset of data. However, this is not best
practice, instead you should create a view. A view is an object in a relational 
database, similar to a table. When Power BI uses a view, it applies query folding.

### **Get Data From a NoSQL Database**
A NoSQL database is a flexible type of database that does not use tables to store data.

### **Import a JSON File**
JSON type records must be extracted and normalised before you can report on them. 
In Power Query, select the Expander button which will display the context menu
with a list of fields. Select the fields that need to be loaded. 

## **Select a Storage Mode**
The most common way to use data is to import it into a Power BI dataset. This means
the data is stored in the Power BI file and gets published along with the Power BI
report. This makes it easier to interact directly with your data. 

In certain cases import may not be possible due to security requirements or if the
dataset is simply too large and causes performance bottlenecks. Power BI solves
this by using DirectQuery storage mode, this mode queries the data directly from
the source and does not import a copy into Power BI. This is also helpful as it
ensures the most recent view of the data. 

Another mode is Dual (Composite Mode) which allows some data to be directly
imported and other data to be queried. 

### **Get Data From Azure Analysis Services**
Azure Analysis Services is a fully managed platform as a service (PaaS) that
provides enterprise-grade data models in the cloud. You can use modeling
features to combine data from multiple data sources, define metrics, and
secure your data in a single, trusted tabular semantic data model. 

## **Fix Performance Issues**
Occasionally performance issues need to be addressed. Power BI provides
the Performance Analyzer tool to help fix problems and streamline the process.

## **Optimise Performance in Power Query**
Power Query takes advantage of good performance at the data source through
a technique called query folding.

### **Query Folding**
Query Folding can help increase the performance of reports. Query Folding is the
process by which the transformations and edits made in Power Query Editor are
simultaneously tracked as native queries. The reason for implementing this process
is to ensure that these transformations can take place in the original data source
server and don't overwhelm Power BI computing resources. 

The benefits to query folding include:
* **More efficiency in data refreshes and incremental refreshes**. When you import
data tables by using query folding, Power BI is better able to allocate resources
and refresh the data faster because Power BI doesn't have to run through each
transformation locally. 
* **Automatic compatibility with DirectQuery and Dual storage modes**. All
DirectQuery and Dual storage mode data sources must have the back-end server
processing abilities to create a direct connection. 

### **Query Diagnostics**
Another tool to study performance is query diagnostics. This determines what
bottlenecks may exist while loading and transforming data, refreshing your data
in Power Query, running SQL statements in Query Editor, and so on. 

### **Other Techniques to Optimise Performance**
Other ways to optimise performance include:
* **Process as much data as possible in the original data source**.
* **Use native SQL queries**. 
* **Separate data and time**. 

## **Resolve Data Import Errors**
While importing data you may encounter errors resulting from factors such as:

### **Query Timeout Expired**
Relational source systems often have many people using the same data concurrently.
Some systems and administrators seek to limit a user from monopolising resources by
setting a query timeout 

### **Power BI Query Error: Timeout Expired**
This error indicates that too much data is being pulled according to your organisation's
policies. You can resolve the error by pulling fewer columns or rows from a single
table.

If you need the rows, columns, and complexity, take small chunks of data and then
bringing them back together by using Power Query.

### **We Couldn't Find any Data Formatted as a Table**
This error is self-explanatory. Power BI expects to find data formatted as a table
from Excel. A possible resolution is to open the Excel file and format the data you
wish to pull in as a table with headers.

### **Couldn't Find File**
Usually, this error is caused by the file moving locations or the permissions to the
changing. If the cause is the former then you need to find the file and change the
source settings.

### **Data Type Errors**
Sometimes, when importing data, the columns appear blank. This happens because of an
error in interpreting the data type. By specifying the correct type at the data source,
you eliminate many of these common data source errors.