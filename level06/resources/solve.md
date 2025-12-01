<h2>Exploit used: Command injection</h2>

1.	PHP script that uses preg_replace in a peculiar way

2.	Script contains 2 functions 'y' and 'x'.
	'x' uses the exploitable `/e` modifier from preg_replace --> `/e` modifier treats the **replacement string as PHP code and executes it.**

3.	To properly exploit this:
<br>-	create a file containing the pattern searched by 'x' which is [x toBeReplaced] and try to inject `getflag` as 'toBeReplaced'
<br>-	simply writing **\`getflag\` will not work** because `y( )` function encases 'toBeReplaced' with double quotes (") effectively making our **command substition injection a simple string**, using `${}` allows us to embed a variable in a string, making our injection effective again. 
<br>-	**[x ${\`getflag\`}]** will give us the flag

5.	Run the executable with the created file
