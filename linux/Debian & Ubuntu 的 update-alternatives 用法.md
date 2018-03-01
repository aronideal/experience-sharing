
## 安装候选项（以python为例）

命令用法：--install <链接> <名称> <路径> <优先级>

    $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1

    $ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.5 2

## 移除候选项（以python为例）

* 移除候选项条目

命令用法：--remove <名称> <路径>

    $ sudo update-alternatives --remove python /usr/bin/python2.7 1

    $ sudo update-alternatives --remove python /usr/bin/python3.5 1

* 移除候选项所有条目

命令用法：--remove-all <名称>

    $ sudo update-alternatives --remove-all python

## 查看候选项（以python为例）

    $ update-alternatives --list python

## 切换候选项（以python为例）

    $ sudo update-alternatives --config python

## 测试效果

    $ python --version
