<h2>Exploit used: Environment variable command injection + Privilege escalation</h2>

1. Executable 'level07' simply `echo` LOGNAME from env.

2. Just modify LOGNAME: `LOGNAME='$(getflag)'`
