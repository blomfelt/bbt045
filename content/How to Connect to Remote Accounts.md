Open Git Bash

Run: `ssh username@ip-address`

Your username is studentX (where X = the number assigned to you)

If promted about about host authenticity (“*ECDSA key fingerprint is SHA256:… Are you sure you want to continue connecting (yes/no)?*”) write `yes`, then press \[**Enter**]

Enter password (you won’t see any feedback on the screen), then press \[**Enter**]

## To save time
If you want to save time when logging in, you can create an `alias`for the command above. You do this by:
 - Go to your home directory: `cd`
 - Open the file called ".bashrc": `nano .bashrc`. If it doesn't exist, a blank file will be created.
 - Insert the following command, changing CID to your CID:
	 - `alias vera='CID@vera1.c3se.chalmers.se'`
- Save and close the file with Ctrl+O, Enter, Ctrl+X
- Source the file: `source .bashrc`
- Now, you only have to run the command `vera` and the command above will be executed instead!

