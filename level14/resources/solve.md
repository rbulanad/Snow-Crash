1.	Use (gdb) on /bin/getflag: `gdb /bin/getflag`
2.	Breakpoint on main: `b *main` and `run`
3.	We identify a pattern: <ft_des> + <fputs> pattern<br>
Each occurrence of the pattern is a flag for a level
4.	Jump to the last occurrence of that pattern: `jump *0x08048de5`
5.	Token displays
