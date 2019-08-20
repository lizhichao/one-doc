# http控制器

http控制器需要继承`\One\Http\Controller`。  
`\One\Http\Controller`主要提供了如下信息

```php
class HttpController extends Controller
{
    public function index()
    {
        $code = sha1(uuid());
        $this->session()->set('code', $code);
        // 加载模板
        return $this->display('index', ['code' => $code]);
    }
}
```
