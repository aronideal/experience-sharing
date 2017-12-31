
屏蔽IP地址

    $ sudo iptables -A INPUT -s x.x.x.x -p TCP -j DROP

屏蔽IP地址段

    $ sudo iptables -A INPUT -s x.x.x.0/255 -p TCP -j DROP
