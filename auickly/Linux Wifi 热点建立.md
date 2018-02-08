
# 使用 AP-Hotspot 在 Linux 环境建立 Wifi 热点

## 安装 AP-Hotspot （如无法正确执行 add-apt-repository，可手动[下载](https://packages.debian.org)并安装工具包，较繁琐）

    $ sudo add-apt-repository ppa:nilarimogard/webupd8

    $ sudo apt-get update

    $ sudo apt-get install ap-hotspot

## 配置 Wifi 热点信息

    $ sudo ap-hotspot configure

## 启动 AP-Hotspot

    $ sudo ap-hotspot start
