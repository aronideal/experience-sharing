
```java
ProtectionDomain pd = OSSApi.class.getProtectionDomain();
CodeSource cs = pd.getCodeSource();
System.out.println(cs.getLocation());
```
