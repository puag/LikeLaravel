Laravel 路由
=====
路由其实在 Laravel 里算是一个重头戏，因为通过路由，Laravel 可以不仅仅走 MVC 的线路，而且其路由的自由度也非常高。在这一部分的路由里，会参杂一些控制器相关的内容，因为我觉得这样的话，对于初学者能更好的使用路由和控制器配合。   
###单一路由
Laravel 的路由定义是在 `app/routes.php` 文件中定义。
####路由基本写法
Laravel 的路由需要指定提交方式，像下面这样：
```php
Route::get('/', function()
{
    return 'Hello World';
});
```
这里的 get 就是提交方式，除了 get 还可以定义为 post，如果 get 和 post 提交方式都有，还可以定义为 any。后面的 '/' 就是写路由的地方，后面会详细介绍。再后面的闭包函数就是路由的调用参数。

路由的调用参数可以是字符串、数组、闭包函数：
```php
Route::get('user', 'UserController@showProfile'); //字符串
Route::get('user', array('before' => 'old', 'uses' => 'UserController@showProfile')); //数组
Route::get('user', function() //闭包函数
{
    return 'Hello World';
});
```
后面跟字符串，那么字符串一般是指控制器以及控制器里的方法，比如上面的 'UserController' 就是指 user 控制器，'@' 是控制器和方法的分隔符，后面的 'showProfile' 就是 user 控制器里的方法了。   
后面跟数组，往往是需要给路由添加过滤，相关元素如下
```php
Route::get('user/name', array('as' => 'xuexi', //定义路由的别名
							'before' => 'auth|old', //定义在进入路由之前需要的过滤，可以用‘|’分割过滤名称进行多重过滤，关于过滤后面讲
							'uses' => 'UserController@showProfile', //定义路由所使用控制器及方法
							function() //定义进入路由后的行为，此闭包函数不与上面的 'uses' 同时使用，当两者都存在的时候，采用 'uses'
							{
								return 'Hello World';
							}
						)
			);
```
后面跟闭包函数，往往可以做到直接处理而不经过控制器，比如404页，闭包函数可以直接返回视图，也可以做其他输出
```php
Route::get('user', function() //闭包函数
{
	echo '测试一下';
	return View::make('hello');
});
```

####路由的

未完待续……

[返回目录] [1]
[上一篇：Laravel 配置] [2]
[下一篇：Laravel 控制器] [3]



[1]: https://github.com/maliang/LikeLaravel "返回目录"
[2]: https://github.com/maliang/LikeLaravel/blob/master/base/config.md "Laravel 配置"
[3]: https://github.com/maliang/LikeLaravel/blob/master/base/controllers.md "Laravel 控制器"

