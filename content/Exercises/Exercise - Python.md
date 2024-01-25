See also [[Tutorial - Python]] and [[Homework 2 - Intro to Python programming for data analysis]]

# Jupyter
- `%%script false --no-raise-error` - inserted first in a cell. The cell will not execute by default.
- `help(command)` or `command?` - open the help page for `command`

As a general rule, it is a good idea to load all required modules at the beginning of a script, and to group them together.

# Python
See [Reference Sheet: Python Data Types](https://www.w3schools.com/python/python_datatypes.asp)

*Note that indexing in Python starts with 0, and index values should be contained in \[brackets].*

## Data types:
- str = string = text
- int = integer = number without decimals
- float = number with decimals

## Data structures:
- list - a comma separated list of objects in brackets: `\["test", "list"]`
- tuple - a comma separated list of objects in parenthesis: `("test", "tuple")`. The contents of a tuple cannot be changed.
- set - similiar to a tuple. Unordered. Contents cannot be changed but items may be added or removed from the list. Comma separated in braces: `{"test", "set"}`
- dictionary - series of key:value pairs. To store information with a reference. `testdict["key"]`

### Iterating over data structures
If and elif
```python
k = random.randint(-10, 10) # return a random integer between -10 and 10

if k > 0:
    # see if the value of k is >0
    print("The value of k is positive.")
elif k < 0:
    # see if the value of k is <0
    print("The value of k is negative.")
else: 
    # if neither the primary nor secondary conditions are fulfilled
    # i.e., if k==0
    print("The value of k is 0.")
```

Looping over a list
```python
ras_list = ["A0A010QKF9", "A0A010QSB8"]

for ras_prot in ras_list: 
    # loop over the elements of ras_list
    if ras_prot.endswith("8"): 
        # find a RAS protein accession ending with the number 8
        # and print the results
        print("The RAS protein accesion number " + ras_prot + " ends with the number 8.")

```

Looping over dictionary
```python
bacteria_dict = {"Gardnerella vaginalis": "Actinobacteria",
                "Lactobacillus crispatus": "Firmicutes"}
# loop over the dictionary to find which species are Firmicutes
for key, value in bacteria_dict.items():
	doSomething()
```

## Working with tabular data: Pandas
Reading a file:
```python
pd.read_csv("iris.csv", sep=',', header=0)
# comma separated, header on the first line (line 0)
```

Filter the dataframe to only the rows which have sepal lengths greater than or equal to 5:
```python
iris_df.loc[iris_df['Sepal_Length'] >= 5]
```

To select a column of a Pandas dataframe, use the syntax `DATAFRAME[COLUMN_NAME]`

To select multiple columns of a Pandas dataframe, use the syntax `DATAFRAME[[COLUMN_NAME_1, COLUMN_NAME_2]]`

Group the data according to the type of iris and get the means of each type of data for that iris type: `iris_df.groupby(['Class']).mean()`
