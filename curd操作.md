# 模型操作

通过模型操作数据库，在swoole下自动切换为连接池。在fpm下自动为单列。

插入一条数据

```php

$id  = User::insert([
    'name'  => $key,
    'email' => 'name@aa.com',
]);

```

迭代用户所有的数据
```
$rs = User::chunk();
foreach($rs as $user){
    
}
```

迭代和关系组合使用
```
User::where('id', '>', 100)
->where('status', '>', 1)
->with('category')
->with('article', [
    function ($q) {
        $q->with('tags.tag')->with('commmit.user');
    }
])
->chunk();
```


插入多条数据

```php

$ar = [];
for ($i = 0; $i < 100; $i++) {
    $ar[] = [
        'name'  => 'name' . $i,
        'email' => 'name' . $i . '@aa.com',
        'age'   => rand(10, 70)
    ];
}
User::insert($ar, true);

```

更新数据

```php

// 先查询后更新 累加
$one = User::find(10);
$row = $one->update(['name' => 'name3s', 'age' => ['age+1']]); // 条件是主键
echo $row . PHP_EOL; // 影响行数
//update users set name='name3s',age=age+1 where id='10'

// 批量更新
$row = User::whereIn('id', [6, 7, 8])->update(['email' => 1423]);
echo $row . PHP_EOL;
// update users set email='123' where id in ('6','7','8')

// 查询出来的对象可以直接调用update
$arr = User::where('id', '>', '20')->orderBy('id asc')->limit(3)->findAll();
foreach ($arr as $v) {
    $v->update(['age' => 19]); // 条件是主键
}


```

删除

```php

$row = User::whereIn('id', [61, 71, 81])->delete();
echo $row . PHP_EOL;// 影响行数
$one = User::find(66);
$row = $one->delete();  // 条件是主键
echo $row . PHP_EOL;


```


查询

```php

// with 可无限级数关联下去

$arr = User::with('articles.article_tags.tag')->limit(10)->findAll()->toArray();

```

关联查询

```php
// select * from users left join articles on users.id=articles.user_id where users.id>1
$arr = User::where('users.id', '>', '1')->leftJoin('articles', 'users.id', 'articles.user_id')->findAll()->toArray();

// select * from users left join articles on users.id=articles.user_id and articles.read_count>2 where users.id>1
$arr = User::where('users.id', '>', '1')->leftJoin('articles', function (Join $q) {
    $q->on('users.id', 'articles.user_id')->where('articles.read_count', '>', 2);
})->findAll()->toArray();

```
