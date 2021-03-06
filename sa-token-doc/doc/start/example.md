# 示例

---

> - 本篇将带你从零开始集成sa-token，从而让你快速熟悉sa-token的使用姿势
> - 以maven + springboot为例

## springboot环境

#### 1、创建项目
在IDE中新建一个Springboot项目，例如：`sa-token-demo-springboot`（不会的同学请自行百度或者参考github示例）

#### 2、设置jar包依赖
- 在 `pom.xml` 中添加依赖：

``` xml 
<!-- sa-token 权限认证, 在线文档：http://sa-token.dev33.cn/ -->
<dependency>
	<groupId>cn.dev33</groupId>
	<artifactId>sa-token</artifactId>
	<version>1.4.0</version>
</dependency>
```

#### 3、配置文件
- 你可以零配置启动项目
- 但同时你也可以在`application.yml`中增加如下配置，定制性使用框架：

``` java
spring: 
    # sa-token配置
    sa-token: 
        # token名称（同时也是cookie名称）
        token-name: satoken
        # token有效期，单位s 默认30天
        timeout: 2592000
        # 在多人登录同一账号时，是否共享会话（为true时共用一个，为false时新登录挤掉旧登录）
        is-share: true
        # 是否在cookie读取不到token时，继续从请求header里继续尝试读取 
        is-read-head: true
        #  是否在header读取不到token时，继续从请求题参数里继续尝试读取 
        is-read-body: true
        # 是否在初始化配置时打印版本字符画
        is-v: true
```

> - 如果你习惯于 `application.properties` 类型的配置文件，那也很好办: 
> - 百度： [springboot properties与yml 配置文件的区别](https://www.baidu.com/s?ie=UTF-8&wd=springboot%20properties%E4%B8%8Eyml%20%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E7%9A%84%E5%8C%BA%E5%88%AB)

#### 4、创建主类
在项目中新建包 `com.pj` ，在此包内新建主类 `SaTokenDemoApplication.java`，输入以下代码：

``` java
@SaTokenSetup // 标注启动 sa-token
@SpringBootApplication
public class SaTokenDemoApplication {
	public static void main(String[] args) throws JsonProcessingException {
		SpringApplication.run(SaTokenDemoApplication.class, args); // run-->
		System.out.println("启动成功：sa-token配置如下：" + SaTokenManager.getConfig());
	}
}
```

#### 5、运行
运行代码，当你从控制台看到类似下面的内容时，就代表框架已经成功集成了

![运行结果](https://color-test.oss-cn-qingdao.aliyuncs.com/sa-token/app-run.jpg)


## 普通spring环境
- 普通spring环境与springboot环境大体无异，只不过需要在项目根目录手动创建配置文件`sa-token.properties`来完成配置


## 详细了解
通过这个示例，你已经对sa-token有了初步的了解，那么现在开始详细了解一下它都有哪些[能力](/use/login-auth)吧







