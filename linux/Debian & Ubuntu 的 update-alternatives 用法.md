
## 安装候选项（以python为例）

命令用法：--install <链接> <名称> <路径> <优先级>

    $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1

    $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.5 2

## 查看候选项（以python为例）

    $ update-alternatives --list python

## 切换候选项（以python为例）

    $ sudo update-alternatives --config python

## 测试效果

    $ python --version
