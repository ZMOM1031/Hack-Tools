.. _dig:

==========
Dig
==========

dig (Domain Information Groper) 是个常用的域名查询工具。dig 的功能比 :ref:`nslookup <nslookup>` 更强大。

用法
==========

dig 基本的用法
::

    dig www.exmaple.com

::

    ; <<>> DiG 9.8.4-rpz2+rl005.12-P1 <<>> www.exmaple.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63806
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 7
    
    ;; QUESTION SECTION:
    ;www.exmaple.com.               IN      A
    
    ;; ANSWER SECTION:
    www.exmaple.com.        86400   IN      A       85.119.83.248    // 主机名对应的 IP 地址
    
    ;; AUTHORITY SECTION:
    exmaple.com.            86365   IN      NS      a.authns.bitfolk.co.uk.
    exmaple.com.            86365   IN      NS      c.authns.bitfolk.com.
    exmaple.com.            86365   IN      NS      b.authns.bitfolk.com.
    exmaple.com.            86365   IN      NS      numpty.absolutelyplastered.com.
    
    ;; ADDITIONAL SECTION:
    a.authns.bitfolk.co.uk. 172800  IN      A       85.119.80.222
    a.authns.bitfolk.co.uk. 172800  IN      AAAA    2001:ba8:1f1:f019::53
    b.authns.bitfolk.com.   172764  IN      A       174.136.109.67
    b.authns.bitfolk.com.   172764  IN      AAAA    2607:f2f8:a104::53
    c.authns.bitfolk.com.   172764  IN      A       173.255.227.192
    c.authns.bitfolk.com.   172764  IN      AAAA    2600:3c03::31:2053
    numpty.absolutelyplastered.com. 172764 IN A     85.119.82.19
    
    ;; Query time: 255 msec
    ;; SERVER: 192.168.1.1#53(192.168.1.1)
    ;; WHEN: Mon Feb 22 21:27:01 2016
    ;; MSG SIZE  rcvd: 321
