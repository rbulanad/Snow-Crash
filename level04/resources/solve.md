1. level04.pl has SETUID --> we can make it execute the 'getflag' command

2. .pl script uses CGI module (mini web serv) with "param" on localhost:4747, it just echoes whatever is given to "params"

3.  Use a curl http request to send 'x param' to the script, we will try to inject the getflag command by using command substition syntax: $(...) or backticks (`).

4. Do `curl http://localhost:4747?x=$(getflag)` --> 'getflag' will be substituted by its output (Check flag. Here is your [....] ), it does not work we must force the substition to happen within the script's scope to take advantage of the SETUID.

5. Surround the getflag injection with single quotes to prevent our shell to do the command substition, it will simply pass '$(getflag)' as a string thanks to the single quotes. The script will receive the $() intact and proceed to do the command substition by invoking its own shell subprocess (with SETUID privileges), effectively echoing the result of getflag.

6. Full curl request: `curl http://localhost:4747?x='$(getflag)'`
