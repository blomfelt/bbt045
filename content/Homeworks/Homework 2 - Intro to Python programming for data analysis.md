Source: [homework\_python\_intro](https://bengtssonpalme.github.io/MPBIO-BBT045-2024/python_for_data_analysis/homework_python_intro.html)

See also [[Exercise - Python]] and [[Tutorial - Python]]

> [!important]
> VERY IMPORTANT CHEAT SHEET: [Cheat Sheet - Pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)

# Task 1
Note that you will need to exclude the information in the beginning of the file and the FASTA in the end. The FASTA begin on line 28343 and end on line 180335 (the last line in the file).
![[Exercise - Python#Reading in a GFF file.]]

Filter for certain values in a certain column:
![[Exercise - Python#Working with tabular data Pandas]]

`len(DATAFRAME)` - displays the number of rows in DATAFRAME

# Task 2
## Creating one or more columns from other columns
Source: [Cheat Sheet - Pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)

Creating a new column "area" from the columns "length" and "height" in the dataframe "df":
```python
df = df.assign(area=lambda df: df.length*df.height)
```

## Example of `groupby`:
We have a dataframe `df` where each line contain a name and a time that that person logged into a server. We group it by "name" and store this new dataframe in the variable "df_grouped_name". 
```python
df = pd.DataFrame({
    "name" : ["Steve", "David", "Steve"],
    "time" : [10.38, 11.00, 12.05]})

df_grouped_name = df.groupby('name')

df_grouped_name.describe() 
df_grouped_name.count()
df_grouped_name.mean()
```
We then display a summary for the dataframe (`describe()`). Also shown is the function `count()` which counts the number of values for an object, in this case the number of rows which contain each name (David: 1, Steve: 2). Last is the function `mean()` which calculates the mean for each group.

# Task 3
## Subtask a
Assign the values in gene_IDs to the new column "geneID" in the dataframe "df"
df['geneID'] = gene_IDs

## Subtask b
Search in COLUMN in df for the values in SEARCH_LIST and assign them to "found", then display them.
```python
found = df[df.COLUMN.isin(SEARCH_LIST)]

found # Displays it
```
