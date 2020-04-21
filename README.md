
 1.访问jsp页面时，报404
 
 查看application.properties中spring.mvc.view.prefix=/WEB-INF/views/jsp/；spring.mvc.view.suffix=.jsp 路径是否配置正确
 在控制层的模块或在父类模块的pom.xml加上这几个依赖
 <dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <!--<scope>provided</scope>-->
</dependency>
<!-- JSTL (JSP standard Tag Library) JSP 标准标签库 -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
</dependency>
 
 2.控制台输出：o.s.w.s.r.ResourceHttpRequestHandler : Path with "WEB-INF" or "META-INF": [WEB-INF/views/jsp/index.jsp]
 
 在控制层的模块或在父类模块的pom.xml加上这几个依赖
 <dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
    <scope>provided</scope>
</dependency>

3.错误提示：There was an unexpected error (type=Not Found, status=404). /kind/WEB-INF/views/jsp/index.jsp

在写jsp页面的那个模块加个插件
<build>
        <resources>
            <resource>
                <directory>src/main/webapp</directory>
                <targetPath>META-INF/resources</targetPath>
                <includes>
                    <include>**/**</include>
                </includes>
            </resource>
        </resources>
    </build>
