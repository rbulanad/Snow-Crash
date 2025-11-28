1. level04.pl has SETUID --> we can make it execute the 'getflag' command

2. .pl script uses CGI module (mini web serv) with "param" on localhost:4747, it just echoes whatever is given to "params"

3.  Use a curl http request to send 'x param' to the script, we will try to inject the getflag command in the request using backticks --> backticking 
3. use `curl http://localhost:4747?x='`getflag\`'` --> this will send x = `getflag` to the .pl script which will echo it BUT FIRST the backticks(``) mark it has preprocessable content --> it will replace "x = getflag" with the contents of the command getflag "x = Check flag.Here is ..."
