<h2>Exploit used: Command injection</h2>

1. The script 'level11.lua' uses `socket.bind("127.0.0.1", 5151)`

2. Do `nc 127.0.0.1 5151`, it prompts to enter a password

3. Looking at the script it seems that no matter the password it is never going to give us the flag.

4. Instead of a password, write `$(getflag) > /tmp/flag`, you can then `cat /tmp/flag` and there it is.
