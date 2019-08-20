## 配置服务
```php
// http 协议 rpc服务
[
    'port'   => 8082,
    'action' => \App\Server\RpcHttpPort::class,
    'type'   => SWOOLE_SOCK_TCP,
    'ip'     => '0.0.0.0',
    'set'    => [
        'open_http_protocol'      => true,
        'open_websocket_protocol' => false
    ]
],
// tpc 协议 rpc服务
[
    'port'          => 8083,
    'action'        => \App\Server\RpcTcpPort::class,
    'type'          => SWOOLE_SOCK_TCP,
    'pack_protocol' => \One\Protocol\Frame::class, // tcp 打包 解包协议
    'ip'            => '0.0.0.0',
    'set'           => [
        'open_http_protocol'      => false,
        'open_websocket_protocol' => false,
        'open_length_check'       => 1,
        'package_length_func'     => '\One\Protocol\Frame::length',
        'package_body_offset'     => \One\Protocol\Frame::HEAD_LEN,
    ]
]
```

## 添加服务

```php

// 添加Abc到rpc服务
RpcServer::add(Abc::class);

// 如果你不希望把Abc下的所有方法都添加到rpc服务，也可以指定添加。
// 未指定的方法客户端无法调用.
//RpcServer::add(Abc::class,'add');

// 分组添加
//RpcServer::group([
//    // 中间件 在这里可以做 权限验证 数据加解密 等等
//    'middle' => [
//        TestMiddle::class . '@aa'
//    ],
//    // 缓存 如果设置了 当以同样的参数调用时 会返回缓存信息 不会真正调用 单位:秒
//    'cache'  => 10
//], function () {
//    RpcServer::add(Abc::class);
//    RpcServer::add(User::class);
//});

```


### 客户端调用
```php
// 映射类 one框架会自送生成 访问http服务 http://127.0.0.1:8082/ 下载
class ClientAbc extends RpcClientHttp {

    // rpc服务器地址 
    protected $_rpc_server = 'http://127.0.0.1:8082/';

    // 远程的类 不设置 默认为当前类名
    protected $_remote_class_name = 'Abc';
}

$abc = new ClientAbc(5);
// $res === 10
$res = $abc->add(2,3);
// 链式调用 $res === 105
$res = $abc->setA(100)->add(2,3);

```

如果是tcp请继承 RpcClientTcp
代码地址 [RpcClientTcp ](https://github.com/lizhichao/one/blob/master/src/Swoole/RpcClientTcp.php)， [RpcClientHttp](https://github.com/lizhichao/one/blob/master/src/Swoole/RpcClientHttp.php)

如果在one框架内tcp调用 请继承 [RpcTcp](https://github.com/lizhichao/one-app/blob/master/App/Client/RpcTcp.php)支持协程



