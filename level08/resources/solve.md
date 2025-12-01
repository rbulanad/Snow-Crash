1. Executable 'level08' prints the contents of a given file to the terminal

2. It obviously does not work with the provided file 'token'.

3. After decompiling, we notice that a simple strstr() check for 'token' within the FILENAME is the only obstacle.

4. To bypass it, create a symbolic link and use the executable with the link.<br>`ln -s ~/token /tmp/link`

5. `./level08 /tmp/link` == quif5eloekouj29ke0vouxean

6. `su flag08` + `getflag`
