主服务器
```php

    'server' => [
        'server_type' => \One\Swoole\OneServer::SWOOLE_WEBSOCKET_SERVER,
        'port' => 8082,
        'action' => \App\Test\MixPro\Ws::class,
        'mode' => SWOOLE_PROCESS,
        'sock_type' => SWOOLE_SOCK_TCP,
        'ip' => '0.0.0.0',
        'set' => [
            'worker_num' => 5
        ]

    ]


```


  


```
