Source: [Homework 1: Basic Unix operations for bioinformatics | BBT045: Applied Bioinformatics](https://bengtssonpalme.github.io/MPBIO-BBT045-2024/homework1)

See also [[Exercise - Basic Unix]]

# Test you results
- Log in to the server (`ssh CID@vera1.c3se.chalmers.se`)
- Move (`cd`) into the directory where you want to create the file with your answers, I put mine in a directory called BBT045.
- `touch hw1.txt` to create an empty text file (`.txt`) with the name `hw1`.
- `nano hw1.txt` - write down your answers, one answer per line and with two significant digits in the case of fractions.
- Save the file and close it with Ctrl+O, Enter, Ctrl+X
- Move to the directory called `test`in the common area: `cd /cephyr/NOBACKUP/groups/bbt045_2024/test`
- Run: `/cephyr/NOBACKUP/groups/bbt045_2024/test/test_unix.sh ~/BBT045/hw1.txt` 

The first five lines tell you if you have the right answers or not. I got some errors, but those seem to happen when creating a log for the teachers and not affect us.