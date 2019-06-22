## 系统简介
  个人开发的一套管理系统，主要是为了学习相关技术，并用新技术应用到项目中实战。
  
## 技术框架
 * 后端：Spring boot 2.0.1、Spring Security、Oauth2、Hibernate、JPA、Redis、Freemarker。  
 * 前端：jQuery、FancyTree。
 
## 功能介绍
  系统管理功能：如用户管理、角色管理、菜单管理、组织管理、数据字典。
  redis博客：博客中心。 
  
### 模块介绍
* psys-auth-server oauth2实现的单点登录服务器
* psys-common 存放不用额外导入pom的通用工具类
* psys-eureka-server 服务注册与发现的服务器
* psys-redis redis 通用redis的jar    
* psys-sec-server sec即系统管理模块的服务
* psys-sys-web-server ui-web服务，首页加载js资源比较多，可能有点慢，没有商业化，将就着用吧，有空再考虑优化等
  
### 注意事项

#### oauth2客户端认证不成功

oauth2使用时,下列配置项需要配置,否则oauth2会认证不成功。```server.servlet.context-path: /eureka-server```

#### eureka-server部署到不同服务器时,节点找不到eureka服务器情况
节点需要找到注册服务器的主机,可以手动改下host文件,配置eureka服务器的服务器名指向其ip地址  
示例: eureka-server注册服务器web服务器地址为: http://域名或ip:18080/eureka-server  
进去可以看到 jdu4e00u53f7:sec-server:18081,其中jdu4e00u53f7是注册服务器的服务器名称,修改下hosts文件即可.如:```IP jdu4exxxx```

### 部署流程
* 导入sql.即执行psys_oauth2_db.sql和psys_sec_db.sql文件，sql脚本见source/sql目录
* 启动enreka-server
* 启动auth-server，注意修改配置文件里的mysql和redis连接参数
* 启动sec-server，注意修改配置文件里的mysql和redis连接参数
* 启动sys-web-server

### 启动成功后页面
* [eureka](http://localhost:18080/eureka-server/)
* [登录页面，账号密码为admin/admin)](http://localhost:18090/auth-server/login)
* [首页](http://localhost:18091/sys-web-server/index)

### 参考
[markdown文件的基本常用编写语法](https://www.cnblogs.com/liugang-vip/p/6337580.html) 



