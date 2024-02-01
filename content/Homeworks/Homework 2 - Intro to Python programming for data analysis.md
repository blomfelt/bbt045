Source: [homework\_python\_intro](https://bengtssonpalme.github.io/MPBIO-BBT045-2024/python_for_data_analysis/homework_python_intro.html)

See also [[Exercise - Python]] and [[Tutorial - Python]]

> [!important]
> VERY IMPORTANT CHEAT SHEET: [Cheat Sheet - Pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)


> [!info] 
> If you get an error saying "*'Series' object has no attribute ...*" try adding ".str" before the function you just applied.


# Task 1
Note that you will need to exclude the information in the beginning of the file and the FASTA in the end. The FASTA begin on line 28343 and end on line 180335 (the last line in the file).
![[Exercise - Python#Reading in a GFF file.]]

Filter for certain values in a certain column:
![[Exercise - Python#Working with tabular data Pandas]]

`len(DATAFRAME)` - displays the number of rows in DATAFRAME

# Task 2
To find all rows in the dataframe "df" which contain "eggs" in the column "name"
```python
genes = df.loc[df.name == "eggs"]
```

## Creating one or more columns from other columns
Source: [Cheat Sheet - Pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)

Creating a new column "area" from the columns "length" and "height" in the dataframe "df":
```python
df = df.assign(area=lambda df: df.length*df.height)
```

## Example of `groupby`:
We have a dataframe "df" where each line contain a name and a time that that person logged into a server. We group it by "name" and store this new dataframe in the variable "df_grouped_name". 
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
```python
df['geneID'] = gene_IDs
```

## Subtask b
Search in COLUMN in df for the values in SEARCH_LIST and assign them to "found", then display them.
```python
found = df[df.COLUMN.isin(SEARCH_LIST)]

found # Displays it
```

# Task 4
To find the ten largest values in the column "height" in the dataframe df:
```python
df.nlargest(10, 'height')
```

# Task 5
## Subtask a
To apply the function `function` to all values in COLUMN in the dataframe "df" and store it in "names":
```python
names = df.COLUMN.apply(function)
```

## Subtask b
Splitting each line in a dataframe may be done to find the number of occurances of a specific string in that
```python
# Split 
# Search for a word, count the number of items in each row
rare_occurances = df.sequence.str.split("word").str.len()-1
# Remove one since if no matches = unsplit = 1 string
```

# Task 6
- Create a dataframe from a fasta file (task 5)
- Extract chromosome name (or maybe "chromosome=..."?) from gene_info using a modified version of "extract_gene_id_from_names"?
- Optional: remove the trailing "]" with "*.str.removesuffix("]")*
- Use `df.loc[df.COL.idxmax(),:]` to extract the row with the highest number in COL

![[Transfer files from Vera]]