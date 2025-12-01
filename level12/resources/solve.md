<h2>Exploit used: Command injection</h2>

1. 'level12.lua' script listens for request at localhost:4646, it takes 'x' and 'y' parameters but only the 'x' matters

2. The script will always print either '.' or '..', our command injection must include a redirection to be able to see the result.

3. The script uses regex to modify our input by switching lower case to UPPER CASE. To keep our command unmodified we must pass it through a file, the regex will only apply to the file's name.

4. Create a file with an all upper case name `touch /tmp/FILE`, this way the regex won't react.

5. Inside the file: `getflag > /tmp/flag`

6. Pass the file via curl request as 'x': `curl http://localhost:4646?x='$(/*/FILE)'`, using '/*' instead of '/tmp' to once again prevent the regex from reacting and changing it to '/TMP'.

7. `cat /tmp/flag` and there it is. 
