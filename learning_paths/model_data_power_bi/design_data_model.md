# **Design a Data Model in Power BI**
A star schema is one of the most simple ways to simplify a data model.
This module will cover how to choose the correct data granularity and how
to improve the performance of models.

## **Introduction**
Creating a good data model is one of the most important tasks. A good data
model offers the following benefits:
* Data exploration is faster.
* Aggregations are simpler to build.
* Reports are more accurate.
* Writing reports takes less time.
* Reports are easier to maintain in the future.

Generally a smaller data model is better as it will perform faster and will
be simpler to use. However what can be considered a small model is subjective.
To summarise you should aim for simplicity when designing your data models.

Relationships are defined between tables through primary and foreign keys.
Primary keys are columns that identify each unique, non-null data row.
Relationships between tables are formed when you have primary and foreign keys
in common between different tables. 

### **Star Schemas**
You can design a star schema to simplify your data. In a star schema, each
table within your dataset is defined as dimension or a fact table. 

**Fact tables** contain observational or event data values. With fact tables,
it is common to see columns that are filled with numbers and dates. These
numbers can be units of measurement, such as sales amount, or they can be keys,
such as customer ID.

**Dimension tables** contain the details about the data in fact tables.
These tables are connected to the fact table through key columns. Dimension
tables are used to filter and group the data in fact tables. 

Fact tables are usually much larger than dimension tables because numerous
events occur in fact tables. 

## **Work with Tables**
A simple table structure will:
* Be simple to navigate because of column and table properties that are specific and
user-friendly.
* Have merged or appended tables to simplify the tables within your data structure.
* Have good-quality relationships between tables that make sense.

### **Configure Data Model and Build Relationships Between Tables**
In the model tab you can create, edit, and delete relationships between tables and
autodetect relationships that already exist. Relationships can be active or inactive.
Only one active relationship can exist between tables.

### **Configure Table and Column Properties**
The model view provide options within the column properties that can be updated
or viewed. 

Under the **General** tab, you can:
* Edit the name and description of the column.
* Add synonyms that can be used to identify the column when you are using the
Q&A feature.
* Add a column into a folder to further organise the table structure.
* Hide or show the column.

Under the **Formatting** tab, you can:
* Change the data type.
* Format the date.

Under the **Advanced** tab, you can:
* Sort by a specific column.
* Assign a specific category to the data.
* Summarize the data.
* Determine if the column or table contains null values.

## **Create a Date Table**
A common business requirement is to make calculations based on date and time. For this
reason it is crucial that time-oriented values are formatted correctly. 

You can create a common date table that can be used by multiple tables.

## **Create a Common Date Table**
There are three ways to build a common date table:

### **Source Data**
In some cases, source databases and data warehouses already have their own date tables.
It is recommended to use a source date table as it is likely shared with other tools
that you may be using in addition to Power BI.

### **DAX**
You can use the CALENDARAUTO() or CALENDAR() function to build a common date table.
The CALENDAR() function returns a contiguous range of dates based on a start and end date
that are entered as arguments in the function. 

Alternatively, the CALENDARAUTO() function returns a contiguous, complete range of dates
that are automatically determined from your dataset. The starting date is chosen as the
earliest starting date in your dataset and the latest date is used as the ending date.

### **Power Query**
You can use the M language to define a common date table using the following calculation:
```
= List.Dates(#date(2011,05,31), 365*10, duration(1,0,0,0))
```

You start by providing the earliest start date in your data, then you specify how many
years of dates you want in the future. This approach ensures that as new data flows in,
there is no need to re-create this table.

### **Mark as the Official Date Table**
Date tables need to be marked using the **Mark as date table** button. By marking the table
as a date table, Power BI performs validation to ensure that the data contains zero null values,
is unique, and contains continuous date values over a period. 

## **Work with Dimensions**
When building a star schema, you will have dimension and fact tables. 

You can use hierarchies as one source to help you find detail in dimension tables. These
hierarchies form through natural segments in your data. 

### **Hierarchies**
Power BI automatically enters values of the date type as a hierarchy. To create a
hierarchy for other columns, go to the **Fields** pane and right-click the column
that you want to apply a hierarchy for and select **New hierarchy**. You can then
drag and drop the relevant columns into the new hierarchy.

### **Role-playing Dimensions**
A single dimension can sometimes be referenced multiple times in a fact table, with each
reference linking to a logically distinct role for the dimension. These separate dimension
views are called roles. 

## **Defined Data Granularity**
Data granularity is the detail that is represented within your data, meaning the more
granularity you have, the greater the level of detail in your data.

## **Work with Relationships and Cardinality**
Power BI has the concept of directionality to a relationship. This directionality
plays an important role in filtering data between multiple tables. Power BI attempts
to autodetect relationships, it is important to ensure these relationships accurately
reflect those that exist in the data.

### **Relationships**
The following are different types of relationships:

Many-to-one or one-to-many relationships:
* Describes a relationship in which you have many instances of a value in one column that
are related to only one unique corresponding instance in another column. 
* Describes the directionality between fact and dimension tables.
* Is the most common type of directionality and is the Power BI default when
automatically creating relationships.

One-to-one relationships:
* Describes a relationship in which only one instance of a value is common between two tables.
* Requires unique values in both tables.
* Is not recommended because this relationship stores redundant information and suggests the
model isn ot designed correctly. It is better practice to combine the tables.

Many-to-many relationships:
* Describes a relationship where many values are in common between two tables. 
* Does not require unique values in either table in a relationship.
* Is not recommended; a lack of unique values introduces ambiguity and your users might not
know which column of values is referring to what. 

### **Cross-filter Direction**
Data can be filtered on one or both sides of a relationship.

With a **single cross-filter direction**:
* Only one tale in a relationship can be used to filter the data. For example, Table 1 can be
filtered by Table 2, but Table 2 cannot be filtered by Table 1.
* For a one-to-many relationship, the cross-filter direction will be from the "one" side, meaning
that the filtering will occur in the table that has many values. 

With **bi-directional cross-filtering**:
* One table in a relationship can be used to filter the other. For instance, a dimension table
can be filtered through the fact table, and the fact tables can be filtered through the dimension
table. 
* You might have lower performance when using bi-directional cross-filtering with
many-to-many relationships. 

### **Cardinality and Cross-filter Direction**
For one-to-one relationships, the only option that is available is bi-directional cross-filtering.
Data can be filters on either side of the relationship.

For many-to-many relationships, you can choose to filter in a single direction or in both
directions. 

## **Resolve Modeling Challenges**
When creating relationships, a common 