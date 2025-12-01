<h2>🕵Packet Spy</h2>

1. `scp -P 4242 level02@IP_of_VM:/path/to/file/VM /target/path/HOST` to transfer the .pcap file to host

2. Read .pcap file with wireshark / app.packetsafari.com

3. Follow TCP stream --> can see communications (such as keyboard inputs)

4. Go to "Password:" request line. Check inputs for password --> '.' == non printable characters --> switch to HEX view to see character code

5. translate HEX codes to ASCII equivalent to see keyboard inputs

6. `su flag02` + password == ft_waNDReL0L

7. getflag
