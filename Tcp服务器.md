主服务器
```php


'server' => [
    'server_type'   => \One\Swoole\OneServer::SWOOLE_SERVER, // 主服务器类型
    'port'          => 9086,
    'action'        => \App\GlobalData\Server::class, // 主服务器事件回调类
    'mode'          => SWOOLE_BASE,
    'sock_type'     => SWOOLE_SOCK_TCP,
    'ip'            => '127.0.0.1',
    'pack_protocol' => \One\Protocol\Frame::class, // tcp 打包 解包协议
    'set'           => [ // set 相关配置
        'worker_num'          => 1,
        'reactor_num'         => 1,
        'open_length_check'   => 1,
        'package_length_func' => '\One\Protocol\Frame::length',
        'package_body_offset' => \One\Protocol\Frame::HEAD_LEN,
    ]
]




```

添加tcp监听


 ```php

[

    'port' => 8083,
    'pack_protocol' => \One\Protocol\Text::class,
    'action' => \App\Test\MixPro\TcpPort::class,
    'type' => SWOOLE_SOCK_TCP,
    'ip' => '0.0.0.0',
    'set' => [
        'open_http_protocol' => false,
        'open_websocket_protocol' => false
    ]

],

  


```
