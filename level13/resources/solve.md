<h2>🛠New tool: GDB</h2>

1. After decompiling the executable we notice only one `if()` condition stops us from getting the token, unfortunately the `if()` condition checks UID and we can not change that.
2. Use GDB on the executable: `gdb level13`
3. `disas main` and find the `cmp` line, that is the `if()` condition, the line right after (`je`) shows where the assembly program jumps if the condition is respected.
4.	set a breakpoint on main: `b *main` and run the program: `run`
5.	We can now jump to the 'inside' of the `if()`, which starts at line <+63>: `jump *0x080485cb`
6.	token displays
