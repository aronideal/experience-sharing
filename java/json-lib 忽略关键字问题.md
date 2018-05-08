
## 问题：当 Java -> JSON 时，存在以下关键字，如class。获得的 JSONObject中相应字段被忽略。

    "class", "declaringClass", "metaClass"

以下是 json-lib 的源码部分，关键字项被忽略。详见 《JsonConfig.java》

```java
private static final String[] DEFAULT_EXCLUDES = new String[] { "class", "declaringClass", "metaClass" };

if( !ignoreDefaultExcludes ) {
    for( int i = 0; i < DEFAULT_EXCLUDES.length; i++ ) {
        if( !exclusions.contains( DEFAULT_EXCLUDES[i] ) ) {
            exclusions.add( DEFAULT_EXCLUDES[i] );
        }
    }
}
```

## 解决办法：通过使用 JsonConfig 设置忽略默认的排除即可

```java
JsonConfig config = new JsonConfig();
config.setIgnoreDefaultExcludes(true);
JSONObject jo = JSONObject.fromObject(data, config);
```
