主服务器
```php

    'server' => [
        'server_type' => \One\Swoole\OneServer::SWOOLE_HTTP_SERVER,
        'port'        => 8081,
        'action'      => \App\Server\AppHttpServer::class,
        'mode'        => SWOOLE_PROCESS,
        'sock_type'   => SWOOLE_SOCK_TCP,
        'ip'          => '0.0.0.0',
        'set'         => [
//            'worker_num' => 10
        ],
    ]


```

添加http监听


 ```php

[
    'port' => 8081,
    'action' => \App\Server\AppHttpPort::class,
    'type' => SWOOLE_SOCK_TCP,
    'ip' => '0.0.0.0',
    'set' => [
        'open_http_protocol' => true,
        'open_websocket_protocol' => false
    ]
],

  


```
