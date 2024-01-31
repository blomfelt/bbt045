Source: [Homework 1: Basic Unix operations for bioinformatics | BBT045: Applied Bioinformatics](https://bengtssonpalme.github.io/MPBIO-BBT045-2024/homework1)

See also [[Exercise - Basic Unix]]

## Useful commands
Everything from [[Exercise - Basic Unix]] but especially:
- `mv OLD NEW` - rename OLD to NEW
- `less X` - view content of X
- `grep "cat" X` - search in X and print all lines which contain "cat", this would also match both "category" and "scatter" but neither "Category" nor "c at"
	- `grep "^X\t" FILE | grep -c "PATTERN"` - Search for line which begin (^) with an X and then a tab (\\t) in the file FILE, and then count (-c) how many of these contain the REGEX-pattern PATTERN. 
	- `grep -v "PATTERN" FILE` - Search for lines in FILE which do NOT (-v) contain PATTERN 
- `tr -d 'A'` - Delete (-d) all "A" from the input (usually piped in: | )
- `sed 's/[^AB]//g'` - Substitute (s) everything (g) that is neither A nor B with nothing ""
- `wc -m` - Count the number of characters in the input.
- `cut -d "_" -f 1` - Cut every line at the "\_"-sign and keep the first column of it (-f 1)
- `X > file.txt` - write the output from X into the file file.txt
- `comm -12 A.txt B.txt`- compare the files A.txt and B.txt and print only the third column (-1 and -2, combined into -12) which contain the common lines between them. NOTE: The lines must be sorted! Use `sort`
- `sort` - sorts the lines. *Hint: pipe in your unsorted lines and pipe the sorted lines into `comm`*


> [!TIP] Tip
> Do not complicate your REGEX-patterns too much in the beginning, maybe you are able to accomplish your goal with two or more different searches? Example: first search for lines which begin with A, pipe ( | ) this output into another grep which searches for the word "eggs".


# Test your results
- Log in to the server (`ssh CID@vera1.c3se.chalmers.se`)
- Move (`cd`) into the directory where you want to create the file with your answers, I put mine in a directory called BBT045.
- `touch hw1.txt` to create an empty text file (`.txt`) with the name `hw1`.
- `nano hw1.txt` - write down your answers, one answer per line and with two significant digits in the case of fractions.
- Save the file and close it with Ctrl+O, Enter, Ctrl+X
- Move to the directory called `test`in the common area: `cd /cephyr/NOBACKUP/groups/bbt045_2024/test`
- Run: `/cephyr/NOBACKUP/groups/bbt045_2024/test/test_unix.sh ~/BBT045/hw1.txt` 

The first five lines tell you if you have the right answers or not. I got some errors, but those seem to happen when creating a log for the teachers and not affect us.


Hejsan lite meningar
# Titel
## Subtitel
### LIte mindre titel igen

`kod`
```python
Lite kod här 
print(2)
if X = 3
	print("hej")
else
```

[[index]]

