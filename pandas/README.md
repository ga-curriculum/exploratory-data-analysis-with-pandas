<h1>
  <span class="headline">Exploratory Data Analysis With Pandas</span>
  <span class="subhead">Pandas</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to utilize the Pandas library to perform exploratory data analysis (EDA), including inspecting data types, calculating summary statistics, identifying missing data, and manipulating DataFrames for deeper insights into datasets.

| Lesson | Duration |
| ------ | -------- |
| Pandas | 45 min   |

# What Is Pandas?

**Pandas** is the most prominent Python library for **exploratory data analysis (EDA)**. We use Pandas to investigate, wrangle, and clean our data.

Pandas is a versatile toolbox that can be used for all of our data exploration needs. (Think Excel or Google Sheets, but much faster and with way more flexibility!)

![Image Placeholder](TKTK)

## Exploratory Data Analysis: Definition

In a nutshell, exploratory data analysis (EDA) means **"getting to know" a data set**. This can include:

- **Checking data types** to make sure data is stored properly.
- **Calculating summaries for columns**, like the average, minimum, or maximum.
- Evaluating your data set for **missing data**.
- Identifying potential **trends or outliers**.
- **Basic visualization** of your data.

![Image Placeholder](TKTK)

> 🍎 It's common to reach a later point in the Data Analytics Workflow only to realize that unclean data or a particular feature could have been engineered earlier in the process. Exploring the data first makes working with it later much more reliable. Hypothesis-driven EDA is essential for effective EDA, otherwise, we would be endlessly mining our data for answers.

## Exploratory Data Analysis Best Practices

At the very least, as part of EDA, you should determine:

- **The number of rows** in the data set.

  - What does each row represent? Is each row a person, an observation, a time point?

- **The number of columns** in the data set.
  - What does each column represent? How was that data collected? Try using a data dictionary — it can often directly answer these questions for you!

![Image Placeholder](TKTK)

## From Questions to Hypotheses

**Start by asking yourself…**

- What **fields can I COMBINE** to find interesting insights?
- What **ACTIONS can someone take** as a result of my charts and analyses?

![Image Placeholder](TKTK)

> 🍎 One of the most challenging parts of data analytics can be turning business questions into analyses, or even forming your own questions when the request you receive is vague. You can start by asking these two questions. Answering them will also help you figure out what to do with your projects.

## Reading a Data Set

Pandas makes it easy to import a data set using a method for reading `.csv` files.

```python
import pandas as pd

data_frame = pd.read_csv(file_address, sep=delimiter_character)
```

> **Note:** Not all `.csv` files use commas! `sep` defines the character used to separate values.

## Series vs. DataFrames

Pandas relies on two key objects, each with their own methods and properties:

| Object Type   | Details                                                                                                               | Example                                                                 |
| ------------- | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **Series**    | accessed using single square brackets, is an attribute of the larger DataFrame object and can only access one column. | `data_frame['column_name']`                                             |
| **DataFrame** | accessed using double square brackets, treats the output as its own smaller table and can include multiple columns.   | `data_frame[['column_name']]`<br>`data_frame[['column_a', 'column_b']]` |

When looking at documentation, be clear whether you're looking at a Series or a DataFrame and always be sure of which one you're working with at any particular point in code.

## Accessing and Modifying the Index

Much like lists, DataFrame rows also have an **_index_** to keep track of them.

> While the default index starts at zero (remember that Python starts counting at zero!), there may already be a column in the data itself that we’d prefer to use as the index.

```python
data_frame.index

data_frame.set_index(column_name, inplace=True)
```

- Make special note of the `inplace` keyword argument that will recur throughout Pandas.
- Do we want to actually modify the original data set (`inplace=True`) or simply create a new copy to store in a variable (the default, `False`)? We will cover this later in the lesson.

## Columns and Data Types

One of the first things we want to learn about a new table is what columns and data types we’ll be working with in that table.

```python
data_frame.columns # Prints all the column names.

data_frame.dtypes # Prints all the data types, but is hard to read!
```

Easy-to-read DataFrame of the data types:

```python
pd.DataFrame(data_frame.dtypes, columns=['DataType'])
```

## Discussion: Why Investigate Data Types? TKTK

Why would we be interested in the data types as one of our first questions?

What operations might we perform in response to the data types we see?

<details>
<summary>✅ Click to see the answer: </summary>
<hr>

Data types can interfere with calculations and operations, thus, we may have to use type casting to convert column types when working with them in terms of comparisons, calculations, and so on.

</details>

## Renaming Columns

We can use the `.rename()` method to provide a dictionary of replacement names:

```python
df.rename(columns={'OldName': 'NewName'}, inplace=True).head(3)
```

- The `inplace` option determines whether we’re creating a new DataFrame or modifying the original directly. `inplace=True` means we are overwriting the original!

> 🍎 When introducing new topics, it can be needlessly complex to throw out multiple options for accomplishing a single task, so, for now, we will recommending just one specific way of renaming columns. There are other ways you can explore on your own.

## Common Column Operations

| **Method**                   | **What This Method Does**                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `.describe()`                | Provides summary attributes, including maximum, minimum, mean, and the 25%, 50%, and 75% quartile values (for numeric columns) or most frequent value (for categorical columns). |
| `.value_counts()`            | Counts the number of occurrences of each value in the column.                                                                                                                    |
| `.unique()`<br> `.nunique()` | Provides a list of unique values or the number of unique values.                                                                                                                 |

<br>

Note that you must grab the column to use these methods, i.e., `df['Color'].value_counts()`.

## Guided Walk-Through: 8.1 Exploring the Superstore Data 15 min TKTK

We’ll use the Superstore data set to practice exploring data with Pandas. We will be looking at a single table from this database — the “Orders” table — to explore its properties.

![Image Placeholder](TKTK)

In this exercise we will:

- Run through each of the cells and discuss the patterns one follows when encountering a data set for the first time.
- Demonstrate how to read Pandas docs when choosing the appropriate methods

## Partner Exercise: 8.2 Explore Another Table 20 min TKTK

Answer the questions in **Section 8.2** by using the column operations methods. You may want to start with some of the same exploratory methods we just used.

![Image Placeholder](TKTK)
