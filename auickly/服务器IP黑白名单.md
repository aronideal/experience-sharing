
屏蔽IP地址

    $ sudo iptables -A INPUT -s x.x.x.x -p TCP -j DROP

屏蔽IP地址段

    $ sudo iptables -A INPUT -s x.x.x.0/255 -p TCP -j DROP

安装ip集工具

    $ sudo yum install ipset

insecureip 是ip集名称。增加 maxelem 属性来增加ip数量。如 maxelem 1000000

    $ sudo ipset create insecureip hash:net

在ip集增加ip

    $ sudo ipset add insecureip 1.1.1.1/32

查看所有ip集

    $ sudo ipset list

ip集可保存到文件中

    $ sudo ipset save insecureip -f /opt/ipset/insecureip.txt

    $ sudo ipset destroy insecureip

    $ sudo ipset restore -f /opt/ipset/insecureip.txt


