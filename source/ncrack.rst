.. _ncrack:

==========
Ncrack
==========

Ncrack 是一个高速的网络认证破解工具。
Ncrack 采用模块化方法，类似的 Nmap 命令行语法和动态引擎，可以根据网络的反馈调整其行为而设计的。
它允许多个主机的快速而可靠的大规模审计。

Ncrack的功能包括一个非常灵活的接口授予网络操作的用户的完全控制，允许非常复杂的暴力破解攻击，
定时模板为便于使用的，类似的Nmap的并有更多的运行时的交互。
支持的协议包括：RDP、SSH、http(s)、SMB、pop3(s)、VNC、FTP、telnet.

* 网站：https://nmap.org/ncrack/
* GitHub：https://github.com/nmap/ncrack

::

    root@kali:~# ncrack -h
    Ncrack 0.4ALPHA ( http://ncrack.org )
    Usage: ncrack [Options] {target and service specification}
    TARGET SPECIFICATION:
      Can pass hostnames, IP addresses, networks, etc.
      Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254
      -iX <inputfilename>: Input from Nmap's -oX XML output format
      -iN <inputfilename>: Input from Nmap's -oN Normal output format
      -iL <inputfilename>: Input from list of hosts/networks
      --exclude <host1[,host2][,host3],...>: Exclude hosts/networks
      --excludefile <exclude_file>: Exclude list from file
    SERVICE SPECIFICATION:
      Can pass target specific services in <service>://target (standard) notation or
      using -p which will be applied to all hosts in non-standard notation.
      Service arguments can be specified to be host-specific, type of service-specific
      (-m) or global (-g). Ex: ssh://10.0.0.10,at=10,cl=30 -m ssh:at=50 -g cd=3000
      Ex2: ncrack -p ssh,ftp:3500,25 10.0.0.10 scanme.nmap.org google.com:80,ssl
      -p <service-list>: services will be applied to all non-standard notation hosts
      -m <service>:<options>: options will be applied to all services of this type
      -g <options>: options will be applied to every service globally
      Misc options:
        ssl: enable SSL over this service
        path <name>: used in modules like HTTP ('=' needs escaping if used)
    TIMING AND PERFORMANCE:
      Options which take <time> are in seconds, unless you append 'ms'
      (miliseconds), 'm' (minutes), or 'h' (hours) to the value (e.g. 30m).
      Service-specific options:
        cl (min connection limit): minimum number of concurrent parallel connections
        CL (max connection limit): maximum number of concurrent parallel connections
        at (authentication tries): authentication attempts per connection
        cd (connection delay): delay <time> between each connection initiation
        cr (connection retries): caps number of service connection attempts
        to (time-out): maximum cracking <time> for service, regardless of success so far
      -T<0-5>: Set timing template (higher is faster)
      --connection-limit <number>: threshold for total concurrent connections
    AUTHENTICATION:
      -U <filename>: username file
      -P <filename>: password file
      --user <username_list>: comma-separated username list
      --pass <password_list>: comma-separated password list
      --passwords-first: Iterate password list for each username. Default is opposite.
    OUTPUT:
      -oN/-oX <file>: Output scan in normal and XML format, respectively, to the given filename.
      -oA <basename>: Output in the two major formats at once
      -v: Increase verbosity level (use twice or more for greater effect)
      -d[level]: Set or increase debugging level (Up to 10 is meaningful)
      --nsock-trace <level>: Set nsock trace level (Valid range: 0 - 10)
      --log-errors: Log errors/warnings to the normal-format output file
      --append-output: Append to rather than clobber specified output files
    MISC:
      --resume <file>: Continue previously saved session
      -f: quit cracking service after one found credential
      -6: Enable IPv6 cracking
      -sL or --list: only list hosts and services
      --datadir <dirname>: Specify custom Ncrack data file location
      -V: Print version number
      -h: Print this help summary page.
    MODULES:
      FTP, SSH, TELNET, HTTP(S), POP3(S), SMB, RDP, VNC
    EXAMPLES:
      ncrack -v --user root localhost:22
      ncrack -v -T5 https://192.168.0.1
      ncrack -v -iX ~/nmap.xml -g CL=5,to=1h
    SEE THE MAN PAGE (http://nmap.org/ncrack/man.html) FOR MORE OPTIONS AND EXAMPLES

