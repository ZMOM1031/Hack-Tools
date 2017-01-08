.. _driftnet:

==========
Driftnet
==========

* 网站：
* GitHub：https://github.com/deiv/driftnet

使用
==========

语法： driftnet   [options]   [filter code]

主要参数
==========

-b					捕获到新的图片时发出嘟嘟声

-i  interface		选择监听接口

-f  file			读取一个指定pcap数据包中的图片

-p					不让所监听的接口使用混杂模式

-a					后台模式：将捕获的图片保存到目录中（不会显示在屏幕上）

-m number			指定保存图片数的数目

-d directory		指定保存图片的路径

-x prefix			指定保存图片的前缀名

使用举例
==========

1.实时监听： driftnet -i wlan0

2.读取一个指定pcap数据包中的图片： driftnet -f /home/linger/backup/ap.pcapng -a -d /root/drifnet/