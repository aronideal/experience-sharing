
<<Maven命令使用之-列举依赖关系 >>

定位到 pom.xml 所在的目录里：
cmd> mvn dependency:tree

拓展：
编译后的war包里包含重复的工具包（即maven引用的与tomcat lib里的重复，且版本不一致）。
为避免日后出现版本不一致导致迁移或其它问题，开发人员需要统一使用tomcat lib里的servlet jar和jsp jar。

如下方式，使用这两个包：
第1步，删除所有版本的依赖：javax.servlet: javax.servlet-api | javax.servlet: servlet-api | javax.servlet.jsp: jsp-api
（1）查看依赖，找到所有版本的（javax.servlet-api、servlet-api 、jsp-api）
        mvn dependency:tree
（2）忽略掉这些包
    
            javax.servlet
            javax.servlet-api
    
        
            javax.servlet
            servlet-api
    
        
            javax.servlet.jsp
            jsp-api
    

第2步，添加两个maven打包必须用到的包。增加scope作用域，使编译期间有效）。
        
            javax.servlet
        jsp-api
        2.0
        provided
        
        
            javax.servlet
        servlet-api
        3.0-alpha-1
        provided