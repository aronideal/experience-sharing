# 通过命令检查Java Class编译时使用的JDK版本号

## 用到的命令javap，即Java class文件分解器
    javap -v hello.class | grep major
hello.class替换成需要检查版本的class文件即可

## 执行后得到的结果
    major version: 52  -> 代表JDK 1.8编译
    或
    major version: 51  -> 代表JDK 1.7编译
    或
    major version: 50  -> 代表JDK 1.6编译
    或其它
