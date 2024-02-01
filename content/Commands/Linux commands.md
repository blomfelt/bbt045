# General Commands
- `ls` - List the names of files and subfolders in the current directory. 
- `cd Y`- Change directory/location to Y. ( `..` = parent directory, one step up, nothing = $HOME)
- `pwd` - Print Working Directory, see where you are
- `cat X`- Print the content of file X
- `less X` - Display the content of file X. Exit using `q`
- `nano X.txt`- edit the text file X.txt using nano.
- `man X`- Display the manual for command X
- `commandX --help` or `commandX -h`- Display the manual for command X (if `man`doesn't work)
- `mkdir X` - Make a new directory named X inside the current directory.
- `rm X` - remove file X (YOU CANNOT UNDO THIS)
- `rm -r X`- remove directory X and all files in it (and subdirectories)
- `mv SOURCE DESTINATION` - move file  SOURCE to DESTINATION. May also be used to rename SOURCE to DESTINATION if no path is used, i.e. no "/" are used. "*The file is moved to the same place but with a new name*"
- `cp X DESTINATION` - copy file X to DESTINATION.
- `touch X`- "Touch" file X (update time accessed). If it does not exist, create it.
- `chmod u+x X` - edit the permissions of file X so that you (u) may execute (x) it.
- `command > X` - write the output from `command` in file X
- `command >> X` - add the output from `command` in the end of file X (append it).
- `command < X` - input file X as the first argument in `command`

# Unix tutorial
- `wc -l X` - print the number of lines in file X
- `curl https://domain.com/filename.txt -O` - download file filename.txt and keep original name
- `gunzip X.gz` - unzip file X.gz
- `tar -xzvf X.tgz` - unpack file X.tgz
- `grep "cat" X` - search in X and print all lines which contain "cat", this would also match both "category" and "scatter" but neither "Category" nor "c at"
- `grep "4932." 2759_members.tsv | cut -f 2 | sort > groups_scerevisiae.txt`
	- `grep` - show the lines that contain "4932." in 2759_members.tsv, 
	- `cut` - keep only the second column of it, 
	- `sort` - sort, and then save the result in the text file.
	- `>` - write the results in a text file
- `sed 'y/ACGT/UGCA/' FILE > FILE_RNA` - substitutes each letter in the first list with the the corresponding one in the second in the file FILE, and writes the result to FILE_RNA
	- may also use the following sed command `'/^>/!y/ACGT/UGCA/'`, which doesn't (`!`) search in lines beginning (`^`) with (`>`)
- `rsync`- transfer files between computers
- `find DIR -name PATTERN` - search for files which match `PATTERN` in the directory `DIR`
- `column` - display tabular files in aligned columns
- `[Ctrl]-R`- reverse history search mode, search for commands you've written 

# Vera server
- `ssh CID@vera1.c3se.chalmers.se`
- `exit` - log out from the server
- `./jupyter_run.sh` - run the file `jupyter_run.sh`, located in the current directory (check with `ls`)
- `squeue -u CID` where CID is your CID. If there is only a list of headers, you have no job running
- `touch X`- "Touch" file X (update time accessed). If it does not exist, create it.
- `cp X ~/DEST` - copy file X to the directory DEST in your home directory (your area on the server)
- An error of `client_loop: send disconnect: Broken pipe` probably means that there was an internet error. Check status with `squeue -u CID`, is it still running? Is the web server still running?
- [[Transfer files from Vera]]