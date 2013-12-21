Laravel 配置
=====

### 配置说明
框架下载好了，但是想要很好的使用，可能我们还有一些东西需要知道，这就是配置。和项目有关的配置是在 app/config 文件夹里，但是除了这里还有一些配置可能是我们需要的。作为一个基础教程，我就不一一介绍了，只是选择一些大家配置比较多的地方讲解一下。

### app/config 中的配置说明
在 app/config 文件夹中经常配置的一般有两个文件：`app.php` 和 `database.php` 两个文件，他们一个是配置项目杂项的、一个是配置数据库的。下面我就里面的常用配置做一下解释：   
先是 `app.php` 文件
```php
// app/config/app.php 文件
return array(
	/*
	|--------------------------------------------------------------------------
	| Laravel 的 debug 模块
	|--------------------------------------------------------------------------
	| 当设置为 'true' 的时候为开启状态（下面这种设置是默认设置，为开启状态）
	| 'false' 为关闭状态。开启的时候当程序出现错误会显示错误信息，
	| 而关闭的时候，程序一旦错误，则会跳转到错误页面（一般为404页）
	*/
	'debug' => true,

	/*
	|--------------------------------------------------------------------------
	| 应用地址
	|--------------------------------------------------------------------------
	| 这个地址只有在使用 Artisan 命令的时候才会用到，需要设置为应用的根目录。
	| 额，如果你还是不清楚我在说什么，那就和下面一样设置成空吧。
	*/
	'url' => '',

	/*
	|--------------------------------------------------------------------------
	| 应用的时区
	|--------------------------------------------------------------------------
	| 这个就是时区操作了，一般如果你没有对 PHP 进行设置的话，时区是美国时区，
	| 也就是 'UTC'  ，啊，你是要写面向我天朝网站么？那就设置成 'Asia/Shanghai' 吧。
	*/
	'timezone' => 'Asia/Shanghai',

	/*
	|--------------------------------------------------------------------------
	| 应用的本地化
	|--------------------------------------------------------------------------
	| 简单的说就是多语言设置，默认是 'en' 如果你没有自己写语言包的话那就还是这个值吧。
	| 你可以在 app/lang 文件夹中看到语言包，如果你没有多语言想法的话，那就不用管这个了。
	*/
	'locale' => 'en',

	/*
	|--------------------------------------------------------------------------
	| 应用密钥
	|--------------------------------------------------------------------------
	| 这是在应用 Laravel 自带的加密功能时会用到的密钥，是为了保证加密安全性的。
	| 如果你的文件这里不是一个随机的 32 位字符串的话，你可以用 'php artisan key:generate'
	| 命令生成一个 32 位随机字符串，啊，记住要在你写网页之前做这个事情。
	| 一旦你变更这个字符串，那么用上一个字符串加密过的内容就找不回来了！！
	*/
	'key' => '',
);
```
其实 app.php 后面还有一些内容，但那些基本上不需要你修改。（只有添加第三方包的时候才有需要，我们会到时候再讲）

接下来介绍 `database.php` 文件
```php
// app/config/database.php 文件
return array(
	/*
	|--------------------------------------------------------------------------
	| PDO 类型
	|--------------------------------------------------------------------------
	| 默认情况下 Laravel 的数据库是用 PDO 来操作的，这样能极大化的提高数据库兼容性。
	| 那么默认查询返回的类型是一个对象，也就是如下的默认设置。
	| 如果你需要返回的是一个数组，你可以设置成 'PDO::FETCH_ASSOC'
	*/
	'fetch' => PDO::FETCH_CLASS,

	/*
	|--------------------------------------------------------------------------
	| 默认的数据库连接名
	|--------------------------------------------------------------------------
	| 这里所说的名字是和下面的 'connections' 中的名称对应的，而不是指你用的什么数据库
	| 为了你更好的理解，我在这里换了一个名字
	*/
	'default' => 'meinv',

	/*
	|--------------------------------------------------------------------------
	| 数据库连接名
	|--------------------------------------------------------------------------
	| 这里就是设置各种数据库的配置的，每个数组里的 'driver' 表明了你要用的数据库类型
	| 同一种数据库类型可以设置多种配置，名字区分开就行，就像下面的 'mysql' 和 'meinv'
	| 其他的么，我觉得不需要解释了吧，就是字面意思，我相信你英文的能力（其实是我英文不好）
	*/
	'connections' => array(

		'sqlite' => array(
			'driver'   => 'sqlite',
			'database' => __DIR__.'/../database/production.sqlite',
			'prefix'   => '',
		),

		'mysql' => array(
			'driver'    => 'mysql',
			'host'      => 'localhost',
			'database'  => 'database',
			'username'  => 'root',
			'password'  => '',
			'charset'   => 'utf8',
			'collation' => 'utf8_unicode_ci',
			'prefix'    => '',
		),

		'meinv' => array( //这里就是上面例子里的默认连接数据库名，实际上是 mysql 数据库
			'driver'    => 'mysql',
			'host'      => 'localhost',
			'database'  => 'database',
			'username'  => 'root',
			'password'  => '',
			'charset'   => 'utf8',
			'collation' => 'utf8_unicode_ci',
			'prefix'    => '',
		),

		'pgsql' => array(
			'driver'   => 'pgsql',
			'host'     => 'localhost',
			'database' => 'database',
			'username' => 'root',
			'password' => '',
			'charset'  => 'utf8',
			'prefix'   => '',
			'schema'   => 'public',
		),

		'sqlsrv' => array(
			'driver'   => 'sqlsrv',
			'host'     => 'localhost',
			'database' => 'database',
			'username' => 'root',
			'password' => '',
			'prefix'   => '',
		),

	),
);
```
额～，你懂的，我肯定不会都说完么，对于刚开始的你来说，数据库的设置知道这些就足够了。

###配置开发环境
有时候我们需要指定开发环境是“本地”（本地环境一般是指我们自己电脑上的虚拟服务器，并没有发布到网上）还是“生产”（生产环境一般是指线上环境，就是在正式的服务器上），亦或是还有其他环境（有些开发公司还会分测试环境等等），以方便做一个配置上的改变，比如“本地”环境的话就可以打开 debug 等等，而“生产”环境就不能打开 debug，否则会让人知道我们服务器的一些信息，这可是秘密，会造成不安全的。那下面就介绍一下 Laravel 中的环境配置。

环境配置在 `bootstrap/start.php` 中，我们打开这个文件，在里面找到下面这段代码
```php
$env = $app->detectEnvironment(array(

	'local' => array('your-machine-name'),

));
```
这里的 'your-machine-name' 是指你电脑的 hostname（啥是 hostname？好吧，我也查了好久，就是你的服务器名）。有童鞋问了：怎么知道我电脑的 hostname 呢？   
Windows 中打开 cmd 输入
```
ipconfig /all
```
下面“主机名”就是 hostname，

Ubuntu 中打开终端输入
```
hostname
```
显示的就是 hostname   
比如我的电脑的 hostname 是 admin，那么就是这样的
```php
$env = $app->detectEnvironment(array(

	'local' => array('admin'),

));
```
这样的话在我的电脑中的时候，用的就是 'local' 中的配置。

那前面的 'local' 是什么呢？是表示 app/config 中的文件夹名。当 hostname 符合你的设置的时候，Laravel 会在你的 app/config 文件夹里寻找 local 文件夹，并启用里面文件的设置，如果需要的设置 local 文件夹里没有的话就会启用 app/config 里的设置。听起来有些绕是不是？看下面，我们的 app/config 中一般是这样的
```files
config
  |-- packages
  |-- testing
  |-- app.php
  |-- auth.php
  |-- cache.php
  |-- compile.php
  |-- database.php
  |-- mail.php
  |-- queue.php
  |-- remote.php
  |-- session.php
  |-- view.php
  |-- workbench.php
```
这时候我们的环境设置起不了任何作用，配置用的就是现在这些文件的设置。下面我们在里面建一个名叫 local 的文件夹，并将 `app.php` 和 `database.php` 两个文件拷贝进去。于是文件结构变成了这样：
```files
config
  |-- local
        |-- app.php
        |-- database.php
  |-- packages
  |-- testing
  |-- app.php
  |-- auth.php
  |-- cache.php
  |-- compile.php
  |-- database.php
  |-- mail.php
  |-- queue.php
  |-- remote.php
  |-- session.php
  |-- view.php
  |-- workbench.php
```
结合上面我的环境设置，当我在我的电脑看的时候，`app.php` 和 `database.php` 启用的是 local 文件夹中的，其他配置用的还是原来的，我本地需要什么配置和线上的有不同的时候，就将那个配置文件拷贝到 local 文件夹里，然后配置就行了。

'local' 这个名字不是必须的，我们可以任意起，而且可以不止一个，比如像下面这样
```php
$env = $app->detectEnvironment(array(

	'shenma' => array('admin'),
	'fuyun' => array('work','ayaya.group'),

));
```
好了，配置就介绍到这里，更多的配置内容，我会在高级教程里继续介绍：）


[返回目录] [1]
[上一篇：Laravel 安装] [2]
[下一篇：Laravel 路由] [3]



[1]: https://github.com/maliang/LikeLaravel "返回目录"
[2]: https://github.com/maliang/LikeLaravel/blob/master/base/install.md "Laravel 安装"
[3]: https://github.com/maliang/LikeLaravel/blob/master/base/routes.md "Laravel 路由"

