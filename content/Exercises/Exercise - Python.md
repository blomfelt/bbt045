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

# Working with tabular data: Pandas
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

Overall, the way you handle tabular data with pandas seem similar to the way you handle them in R.

# Lambda functions
Lambda functions are functions which only exist for one line, and enable you to manipulate data in ways which are not supported by Python's built-in functionality. They have the form `lambda ARGUMENTS: EXPRESSION`, and are often seen in StackOverflow answers, so it can be good to be able to read them even though you are not expected to be able to write them.

# Reading FASTA files
Using the Biopython package may be a useful tool. It is imported with `import Bio.MODULE`. See also the [Biopython Tutorial & Cookbook](https://biopython.org/DIST/docs/tutorial/Tutorial.pdf).

> [!NOTE]- Creating a dictionary using Biopython
> 
> ```python
> # first set necessary variables
> url = ("http://sgd-archive.yeastgenome.org/sequence/S288C_reference/orf_dna/orf_genomic_all.fasta.gz")
> filename = "orf_trans.fasta.gz"
> 
> # download file
> urlretrieve(url, filename)
> 
> # open the FASTA file & extract the data
> 
> # we need to start by decompressing the gzipped file because Biopython does not play well with gzipped files
> # ref: https://github.com/biopython/biopython/issues/1686
> # we can do this with the gzip module
> # ref: https://stackoverflow.com/questions/31028815/how-to-unzip-gz-file-using-python
> with gzip.open(filename, 'rt') as f_in:
>     # open the gzipped file for reading
>     # create the output filename based on the input filename
>     new_file = filename.removesuffix('.gz')
>     with open(new_file, 'wt') as f_out:
>         # now open the new file for writing
>         # and write out the contents
>         shutil.copyfileobj(f_in, f_out)
> 
> # now create a dictionary 
> # ref: https://stackoverflow.com/questions/29333077/reading-a-fasta-file-format-into-python-dictionary
> yeast_seq_dict = {rec.id : rec.seq for rec in SeqIO.parse(new_file, "fasta")}
> ```
> 
> 

> [!NOTE]- Creating your own sequence dictionary
> 
> ```python
> 
> # create an empty dictionary to fill with sequence information
> seq_dict = {}
> 
> # iterate over the gzipped file's contents to extract information
> with gzip.open(filename, "rt") as handle:
>     # open the .gzip file for reading
>     # create an empty list for the sequence information
>     seq_list = []
>     for line in handle: 
>         # iterate through the file line by line
>         if line.startswith(">"): 
>             # identify the sequence header lines
>             # first add the previous header & sequence to the dictionary
>             if seq_list:
>                 # if list block contains sequence portions
>                 # concatenate the list into a single sequence
>                 seq_dict[header] = ''.join(seq_list)
>                 # empty the list
>                 seq_list = []
>             header_full = line.strip()[1:]
>             # remove the ">" character with [1:] and the end-line character with .strip()
>             header = header_full.split()[0]
>             # save only the sequence identifier to be the new header
>         else: 
>             # for the sequence lines
>             seq_list.append(line.strip())
>     if seq_list:
>         # for the last sequence line
>         # need to add the dictionary contents outside the main loop
>         seq_dict[header] = ''.join(seq_list)
> 
> # reference for working with multi-line fastas
> # https://stackoverflow.com/questions/50856538/how-to-convert-multiline-fasta-files-to-singleline-fasta-files-without-biopython
> ```

Biopython's greatest advantage over base Python is the ability to perform operations that would be programmatically more complex (and would likely take longer both in terms of the amount of time required to generate the code, and in terms of the number of lines of code) in a quick and straightforward manner.

For example, in the notebook you can see how to use Biopython to generate the reverse complements of the yeast ORFs (`seq.complement()`); and to translate the original ORF sequences (`seq.translate()`).

# Reading in a GFF file.
It's structured as a (\[Tab] delimited) table, meaning we can read it directly into a Pandas dataframe.

> [!NOTE]- Reading in a .gff file
> 
> ```python
> # set necessary variables
> gff_url = ("ftp://ftp.ncbi.nlm.nih.gov/genomes/archive/old_genbank/Bacteria/Halobacterium_sp_uid217/AE004437.gff")
> gff_filename = "AE004437.gff"
> 
> # download file
> urlretrieve(gff_url, gff_filename)
> 
> 
> # gff files don't contain column names, so we have to manually provide those
> col_names = ["sequence_id", "source", "feature", "start", "end", "score", "strand", "phase", "attributes"]
> 
> # read the GFF file into a Pandas dataframe
> AE004437_df = pd.read_csv(gff_filename, sep = '\t', names = col_names, skiprows = 5, skipfooter = 1, engine = 'python')
> # gff files are tab-separated, so need to specify sep='\t' because read_csv will assume sep=',' by default
> # the names = colnames argument allows us to set the column names on import
> # skiprows here skips the first n rows of the dataframe on import
> # skipfooter skips the last n lines of the file; the last line of the GFF file contains only hashtags ("#")
> # engine = 'python' prevents skipfooter from raising an error
> ```
