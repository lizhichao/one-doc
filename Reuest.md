# Reuest 客户端请求的信息
获取 Request 对象
```php
$this->request
```
`Request` 包含以下方法
```php
    // get信息
    public function get($key = null, $default = null)
    
    // post信息
    public function post($key = null, $default = null)

    // 终端下的 $argv信息
    public function arg($i = null, $default = null)

    // response 信息 = get + post
    public function res($key = null, $default = null)

    // cookie信息
    public function cookie($key = null, $default = null)

    // 请求的原生信息 php://input
    public function input()

    // 返回json信息
    public function json()

    // 返回上传的文件信息
    public function file()

    // 返回请求的方法
    public function method()

    // 是否是json格式
    public function isJson()
    public function ip()
    public function server($name = null, $default = null)
    public function userAgent()
    public function uri()
    // request id
    public function id()
```