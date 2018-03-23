
## Class.getResource

```
CLASSPATH
    |- com
        |- A.class
    |- folder1
        |- file1
    |- folder2
        |- file2
```

#### 绝对路径定位

```java
// CLASSPATH 的根路径
A.class.getResource("/")

// A.class 的路径
A.class.getResource("/com/")

// file1 的路径
A.class.getResource("/folder1/file1")

// file2 的路径
A.class.getResource("/folder2/file2")
```

#### 相对路径定位

使用 ‘.’、‘..’ 实现同访问目录一样的相对定位

```java
// 相对于 A.class 的路径查找 CLASSPATH 的根路径
A.class.getResource("..")

// A.class 的路径
A.class.getResource(".")

// 相对于 A.class 的路径查找 file1 的路径
A.class.getResource("../folder1/file1")

// 相对于 A.class 的路径查找 file2 的路径
A.class.getResource("../folder2/file2")
```

## ClassLoader.getResource

与 Class.getResource 不同的是，绝对定位使用 ‘.’，而不是 ‘/’
