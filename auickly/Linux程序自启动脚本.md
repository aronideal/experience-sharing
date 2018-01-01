
    cd /etc/init.d/

    vim /etc/init.d/testsrv

```shell
#!/bin/sh
#
# testsrv    testsrv程序的启动脚本

# 如果某某命令未安装，则直接退出
#[ -f testsrv ] || exit 0

testsrv="/sbin/testsrv"
arg0=66

start() {
    echo -n $"Starting testsrv"
    
    $testsrv -a $arg0

    RETVAL=$?
    return $RETVAL
}

stop() {
    if test "x`pidof testsrv`" != x; then
        echo -n $"Stopping testsrv"
        killall testsrv
    fi
    RETVAL=$?
    return $RETVAL
}

status() {
    echo -n $"testsrv status:"
    ps -ef | grep testsrv
}

case "$1" in
        start)
            start
            ;;

        stop)
            stop
            ;;

        restart)
            stop
            start
            ;;
        status)
            status
            ;;

        *)
            echo $"Usage: $0 {start|stop|restart|status}"
            exit 1

esac

exit $RETVAL
```

    chmod +x /etc/init.d/testsrv

    chkconfig testsrv on

    service testsrv restart
