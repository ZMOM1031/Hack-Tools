.. _ping:

==========
Ping
==========

ping 是个网络测试命令，用于测试网络的联通性，几乎所有所有操作系统都自带。

Linux
==========

用法
----------

::

    ping [参数] [IP地址或主机名]
    ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]
         [-p pattern] [-s packetsize] [-t ttl] [-I interface]
         [-M pmtudisc-hint] [-m mark] [-S sndbuf]
         [-T tstamp-options] [-Q tos] [hop1 ...] destination

参数
----------

::

    -d     使用Socket的SO_DEBUG功能。
    -f     极限检测。大量且快速地送网络封包给一台机器，看它的回应。
    -n     只输出数值。
    -q     不显示任何传送封包的信息，只显示最后的结果。
    -r     忽略普通的Routing Table，直接将数据包送到远端主机上。通常是查看本机的网络接口是否有问题。
    -R     记录路由过程。
    -v     详细显示指令的执行过程。
    <p>-c  数目：在发送指定数目的包后停止。
    -i     秒数：设定间隔几秒送一个网络封包给一台机器，预设值是一秒送一次。
    -I     网络界面：使用指定的网络界面送出数据包。
    -l     前置载入：设置在送出要求信息之前，先行发出的数据包。
    -p     范本样式：设置填满数据包的范本样式。
    -s     字节数：指定发送的数据字节数，预设值是56，加上8字节的ICMP头，一共是64ICMP数据字节。
    -t     存活数值：设置存活数值TTL的大小。

Windows
==========

用法
----------

::

    ping [选项] [IP地址或主机名]
    ping [-t] [-a] [-n count] [-l size] [-f] [-i TTL] [-v TOS]
                [-r count] [-s count] [[-j host-list] | [-k host-list]]
                [-w timeout] [-R] [-S srcaddr] [-c compartment] [-p]
                [-4] [-6] target_name

选项
----------

::

    -t             Ping 指定的主机，直到停止。
                   若要查看统计信息并继续操作，请键入 Ctrl+Break；
                   若要停止，请键入 Ctrl+C。
    -a             将地址解析为主机名。
    -n count       要发送的回显请求数。
    -l size        发送缓冲区大小。
    -f             在数据包中设置“不分段”标记(仅适用于 IPv4)。
    -i TTL         生存时间。
    -v TOS         服务类型(仅适用于 IPv4。该设置已被弃用，
                   对 IP 标头中的服务类型字段没有任何
                   影响)。
    -r count       记录计数跃点的路由(仅适用于 IPv4)。
    -s count       计数跃点的时间戳(仅适用于 IPv4)。
    -j host-list   与主机列表一起使用的松散源路由(仅适用于 IPv4)。
    -k host-list   与主机列表一起使用的严格源路由(仅适用于 IPv4)。
    -w timeout     等待每次回复的超时时间(毫秒)。
    -R             同样使用路由标头测试反向路由(仅适用于 IPv6)。
                   根据 RFC 5095，已弃用此路由标头。
                   如果使用此标头，某些系统可能丢弃
                   回显请求。
    -S srcaddr     要使用的源地址。
    -c compartment 路由隔离舱标识符。
    -p             Ping Hyper-V 网络虚拟化提供程序地址。
    -4             强制使用 IPv4。
    -6             强制使用 IPv6。
    target_name    IP地址或域名。