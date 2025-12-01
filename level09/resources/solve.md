<h2>Simple Decipher</h2>

1. Executable 'level09' is an **encryption program**, it shuffles a given text by **incrementing every characters by their index**

2. The provided 'token' file contains an encrypted token.

3. Write a program that reverses the simple encryption by **decrementing every characters by their index**<br>
C program example:
#include <stdio.h>
int	main(int argc, char \*\*argv)
{
	int i = -1;
	while (argv[1][++i])
		printf("%c", argv[1][i] - i);
	printf("\n");
	return (0);
}

4. `cd /tmp` and then `gcc yourProgram` otherwise you will get a 'Permission denied'

5. Still within the /tmp directory, `./a.out $(cat ~/token)` == f3iji1ju5yuevaus41q1afiuq

6. `su flag09` + `getflag`
