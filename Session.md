# session 对象
```php
    // 设置
    $this->session()->set('a',123);
    
    // 获取
    $this->session()->get('a');
    
    // 删除
    $this->session()->del('a');

   // 删除当前会话所有
    $this->session()->del();
    
    // 获取所有的
    $this->session()->get();
    
    // 获取session id
    $this->session()->getId();
```