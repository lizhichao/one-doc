
#  one 

     One - 一个极简高性能php框架，支持[swoole | php-fpm]环境

每一个功能都足够的简单、灵活、高效。 让你在fpm下也能在`1ms`内响应请求。不需要改一行代码就可以在`swoole`和`php-fpm`之间来回切换，甚至可以共存。


## 特点：
- RESTful路由
- 中间件
- WS/TCP……任意协议路由
- ORM模型
- SQL日志模板
- MYSQL连接池
- REDIS连接池
- HTTP/TCP/WEBOSCKET/UDP服务器
- 缓存
- 进程间内存共享
- RPC(http,tcp,udp)
- 日志
- TraceId调用链跟踪
- Actor (Actor之间 可跨进程，跨机器通讯）

## apache/php-fpm 运行
框架支持在 `apache/php-fpm` 下运行。  
  
> 在`apache/php-fpm` 下运行不支持的功能
- HTTP/TCP/WEBOSCKET/UDP服务器
- 进程间内存共享
- RPC(http,tcp,udp)
- 各种连接池自动退化为单例模式

## one框架交流群
QQ： 731475644
