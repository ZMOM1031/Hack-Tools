.. _nosqlmap:

==========
NoSQLMap
==========

NoSQLMap 是一款开源 Python 工具，可以帮助安全测试人员自动化对 NoSQL 数据库进行攻击测试。
目前这款工具的漏洞利用程序围绕 MongoDB，但是以后会支持更多的 NoSQL 数据库，如：CouchDB、Redis、Cassandra。

* 网站：http://www.nosqlmap.net/
* GitHub：https://github.com/tcstool/NoSQLMap

安装
==========

要求
---------

在一个基于 Debian 或 Red Hat 系统，``setup`` 脚本可能会以 ``root`` 身份来自动安装 NoSqlMap 的依赖

根据使用的功能有所不同：

* Metasploit Framework
* Python 和 PyMongo
* httplib2
* urllib
* 一个本地默认MongoDB实例对数据库进行复制。点击 `这里 <mongodb_install>`_ 查看安装说明。

编译安装
-------------

::

    git clone https://github.com/tcstool/NoSQLMap.git
    cd NoSQLMap
    python setup.py install

用法
==========

启动 NoSQLMap
::

    ./nosqlmap.py

当打开 NoSQLMap 时你会看到主菜单：
::

    1-Set options (do this first)		// 1-设置选项（第一步操作）
    2-NoSQL DB Access Attacks		// 2-NoSQL DB 访问攻击
    3-NoSQL Web App attacks		// 3-NoSQL Web应用攻击
    4-Scan for Anonymous MongoDB Access		// 4-扫描匿名 MongoDB 访问
    x-Exit		// x-退出

菜单说明
----------

::

    1.设置目标 host/host/IP 目标 Web 服务器 如：(www.google.com) 或者任何你想要攻击的 MongoDB 服务器。
    2.设置 Web 应用 port-TCP 如果一个 Web 应用成为目标，为 Web 应用设置 TCP 端口。
    3.设置 URI 路径，部分 URI 包含页面名称及任何非主机名称的参数 如：(/app/acct.php?acctid=102)。
    4.设置 HTTP 请求方法 (GET/POST) 设置请求方法为 GET 或 POST ；现在只能使用 GET 方法但是后续会增加 POST 方法。
    5.设置我的本地 Mongo/Shell IP-Set 如果直接攻击一个 MongoDB 实例，设置这个选项到目标 Mongo 安装的IP来复制受害者服务器或打开 Meterpreter Shell。
    6.设置 Shell 监听端口，如果开放 Meterpreter Shell 就会指定端口。
    7.加载选项 file-Load 加载之前保存的 1-6 中的设置。
    8.加载选项 从 Burp 保存的 (request-Parse) 请求中加载 Burp Suite 的请求，并填充 Web 应用选项。、
    9.保存选项设置 file-Save 保存 1-6 中的设置以便未来使用。
    x.返回主菜单 meun-Use 使用这个选项开始攻击。

演示视频
----------

MongoDB 中的 SqlMap 管理攻击演示

|youtube|

.. _mongodb_install: http://docs.mongodb.org/manual/installation/

.. |youtube| raw:: html

   <iframe src="https://www.youtube.com/embed/xSFi-jxOBwM" frameborder="0" allowfullscreen></iframe>
