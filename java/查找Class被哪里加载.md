
```java
ProtectionDomain pd = XXXX.class.getProtectionDomain();
CodeSource cs = pd.getCodeSource();
System.out.println(cs.getLocation());
```
