# RESTful路由

```php
Router::get('/', \App\Controllers\IndexController::class . '@index');
Router::post('/',  \App\Controllers\IndexController::class . '@' . 'post');
Router::put('/',  \App\Controllers\IndexController::class . '@' . 'put');
Router::delete('/',  \App\Controllers\IndexController::class . '@' . 'delete');
Router::patch('/',  \App\Controllers\IndexController::class . '@' . 'patch');
Router::head('/',  \App\Controllers\IndexController::class . '@' . 'head');
Router::options('/',  \App\Controllers\IndexController::class . '@' . 'options');
```
或者直接用
```php
Router::controller('/', \App\Controllers\IndexController::class);
```
要求`\App\Controllers\IndexController`中包含 `getAction`、`postAction`、`putAction`、`deleteAction`、`patchAction`、`headAction`、`optionsAction` 方法。

除上面方法外你可通过`set`自定义任意方法
> Router::set(请求方法,请求路径,绑定执行的方法);
```php
 Router::set('xxx','/a','TestController@abc');
```
列入增加`ws`方法，设置为websocket路由。
```php
Router::set('ws','/a','TestController@abc');
```