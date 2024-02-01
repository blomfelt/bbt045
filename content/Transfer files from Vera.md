To transfer a file from the cluster to the directory where you are currently (on your own computer), use the following command, replacing CID (2 times), PATH, and FILENAME.ipynb  to the relevant values:
```bash
rsync -avn CID@vera1.c3se.chalmers.se:/cephyr/users/CID/Vera/PATH/FILENAME.ipynb .
```
The flag "n" makes it not actually transfer any files (even though it says so), and is to make sure that you actually are about to copy the right file. Remove this character to actually transfer the files.

If this doesn't  work, try:
```bash
scp CID@vera1.c3se.chalmers.se:/cephyr/users/CID/Vera/PATH/FILENAME.ipynb .
```