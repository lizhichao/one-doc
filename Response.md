# Response 相应信息给客户端的对象
通过 Response 可获取 Reuest 对象
```php
$this->response->getHttpRequest() === $this->request
```
其他常用方法

```php
    // 设置头部信息
    $this->response->header();

    // 设置cookies 参数方法 同 setcookie 一直
    $this->response->cookie();

    // session 对象
    $this->response->session() === $this->session()
    
   // 直接输出信息 推荐直接在控制器 return 信息;
   $this->response->write('hello');
```