
查看当前ip规则（加上n属性，以ip形式显示）

    $ sudo iptables -L

屏蔽IP地址（-A表示追加、-D表示删除；INPUT请求入；-j： DROP拒绝、ACCEPT接受）

    $ sudo iptables -A INPUT -s x.x.x.x -p TCP -j DROP

屏蔽IP地址段（-A表示追加、-D表示删除；INPUT请求入；-j： DROP拒绝、ACCEPT接受）

    $ sudo iptables -A INPUT -s x.x.x.0/255 -p TCP -j DROP

开放指定的端口（-A表示追加、-D表示删除；INPUT请求入；--dport表示目标端口（服务器端口）、--sport表示源端口（客户端端口）；-j： DROP拒绝、ACCEPT接受）

    $ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

禁止指定的端口（-A表示追加、-D表示删除；INPUT请求入；--dport表示目标端口（服务器端口）、--sport表示源端口（客户端端口）；-j： DROP拒绝、ACCEPT接受）

    $ sudo iptables -A INPUT -p tcp --dport 80 -j DROP

举例（INPUT 规则一定要先 ACCEPT，然后再 DROP）：

    $ sudo iptables -F

    $ sudo iptables -A INPUT -s x.x.x.x -p TCP --dport 22 -j ACCEPT

    $ sudo iptables -A INPUT -p TCP --dport 80 -j ACCEPT

    $ sudo iptables -A INPUT -p TCP --dport 8081 -j ACCEPT
    
    # 使用这句则可以ping出去 $ sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

    $ sudo iptables -A INPUT -j DROP

    $ sudo iptables -nL

    $ sudo service iptables save

保存后，请检查 /etc/sysconfig/iptables
