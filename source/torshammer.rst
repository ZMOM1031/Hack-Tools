.. _torshammer:

=============
Tor's Hammer
=============

Tor's Hammer 是用 Python 写的 DOS 测试工具。它也可以通过 Tor 网络运行进行匿名。
如果你想使用 Tor 运行，需安装TOR并监听于 ``127.0.0.1:9050`` 。
攻击通过单一实例上运行 Apache 和 IIS 最不受保护的 Web 服务器。

* SourceForge：https://sourceforge.net/projects/torshammer/


使用
==========

启动 Tor's Hammer
::

    ./torshammer.py

帮助信息：
::

    /*
     * Tor's Hammer
     * Slow POST DoS Testing Tool
     * Version 1.0 Beta
     * Anon-ymized via Tor
     * We are Anonymous.
     * We are Legion.
     * We do not forgive.
     * We do not forget.
     * Expect us!
     */
    
    ./torshammer.py -t <target> [-r <threads> -p <port> -T -h]
     -t|--target <Hostname|IP>
     -r|--threads <Number of threads> Defaults to 256
     -p|--port <Web Server Port> Defaults to 80
     -T|--tor Enable anonymising through tor on 127.0.0.1:9050
     -h|--help Shows this help
    
    Eg. ./torshammer.py -t 192.168.1.100 -r 256

