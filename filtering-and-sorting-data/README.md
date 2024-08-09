<h1>
  <span class="headline">Exploratory Data Analysis With Pandas</span>
  <span class="subhead">Filtering and Sorting Data</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to filter and sort data within Pandas DataFrames, using Boolean conditions to create subsets of data and applying sorting methods to organize data based on specific criteria.

| Lesson                     | Duration |
| -------------------------- | -------- |
| Filtering and Sorting Data | 50 min   |

## Filtering on One Condition

Filtering and sorting are important steps that allow us to drill into subsets of our data.

To filter, we use a process called **Boolean filtering**, wherein we first define a Boolean mask and then use it to filter our DataFrame.

> Filtering is how we start to split our data and generate meaningful insights based on the differences in various subsets. While basic exploratory methods are nice, more insights come from splitting, combining, and comparing subsections of data.

## The Boolean Mask

We can create a whole series of `True` and `False` values by using a comparison statement with the column:

```python
df['Column'] == 'ValueDesired'
```

| Index | Value |
| ----- | ----- |
| 1     | False |
| 2     | False |
| 3     | False |
| 4     | False |
| 5     | True  |
| 6     | True  |
| 7     | True  |
| 8     | False |

Once we have a Boolean series, we can then filter the entire data set for only those values with a `True` result:

```python
df[df['Column'] == 'ValueDesired'].tail(3)
```

| Index | Column | ValueDesired |
| ----- | ------ | ------------ |
| Price | 317    | 10.99        |
| Price | 318    | 5.00         |
| Price | 319    | 2.75         |

> Note that we can use other comparisons besides simple equality. Any Boolean result based on a column comparison will work.

## DataFrame Syntax Chaining

When filtering with this syntax, the result is a DataFrame.

This means that we can continue accessing other columns or using methods:

```python
# Access the Price column of all results passing the filter:

df[df['Color'] == 'Purple']['Price']

# Gives numerical summaries based only on results passing the filter:

df[df['Color'] == 'Purple']['Price'].describe()
```

The result of this filtering will be the entire DataFrame, so you can continue on with DataFrame methods after filtering.

## Filtering by Multiple Conditions

Adding more conditions uses the same syntax, even if it looks more complicated:

```python
df[(df['Color'] == 'Silver') & (df['ListPrice'] > 350)]

df[(df['ListPrice'] < 3000) | (df['ZipCode'] == '95404')]
```

The parentheses here are very important! Leaving them out will usually trigger an error.

> You can get even more complex with your conditions, but don’t forget to use parentheses to group conditions together.

## Solo Exercise: 8.3 Boolean Filtering 15 min TKTK

Use Boolean filtering to narrow down the DataFrame in **Section 8.3** of your workbook.

![Image Placeholder](TKTK)

## Sorting

The magic of libraries like **Pandas** is that there’s a method for almost everything. In the case of sorting, we have a `sort_values()` method:

For a Series object, no need to specify column: There's only one!

```python
data_series.sort_values()
```

For a DataFrame, it will sort by index unless given a column name.

```python
data_frame.sort_values(by='column_name', ascending=False)
```

> This is a good opportunity to reiterate the difference between Series and DataFrame objects. Both can be sorted, but with a DataFrame you may need to provide the specific column by which to sort.

## Accessing an Individual Row

Now that we can sort and filter, it’s more likely that we might want to access a single row of data from a DataFrame. We can use the `iloc` property to use indexing syntax, like so:

```python
data_frame.sort_values(by="points_scored").iloc[[0]]
```

Note the two brackets, which mean that the result will be a DataFrame. We could also simply use one bracket to instead return a Series with accessible properties:

```python
data_frame.sort_values(by="points_scored").iloc[0]["player_name"]
```

## Discussion: Key Definitions Recap TKTK

While working with Pandas, it will be important to distinguish between Series and DataFrame objects.

- What are the key properties of each type of object?

- What are their differences and similarities?

## Group Exercise: 8.4 Sorting and Filtering 25 min TKTK

Use sorting and filtering methods to explore the attributes of a data set and answer stakeholder questions.

![Image Placeholder](TKTK)
