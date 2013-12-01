Laravel 安装指南
=====
### Git 介绍
之所以要说 Git，就是因为 Composre 有时需要用到 Git，还是安装上比较好，Composer 暂且不表，先来了解一下 Git 吧（已经安装的童鞋跳过这里，直接看 [Composer介绍] [7]）

Git 是一个快速、可扩展的分布式版本控制系统。好，介绍就到这里，详细的可以到 [Git 官网] [8] 去了解更多，我们主要讲一下它的安装。这里只以 Ubuntu 和 Windowns 为例，其他你们应该可以推理出来吧？
#### Ubuntu Git 安装
打开终端输入以下命令
```terminal
sudo apt-get install git-core
```
好了，现在我们的 Git 就装好了。

#### Windowns Git 安装
下载 Windowns 下的 Git 安装包：[官网下载页面] [9] 或者点击 [下载安装文件] [10]，进行安装。  
安装过程中其他不用管，只是到了下面这幅界面的时候，记得选择第二项，此项会将 Git 添加到 Windows 的环境变量，并且有专门的执行文件，可以解决因 Git 添加到环境变量而产生的冲突。**总之一句话，选第二个就对了**  
![Git 安装界面] [11]  
这样 Windowns 下的 Git 就安装好了。下面介绍 Composer。

### Composer 介绍
很多童鞋很奇怪，为什么要讲 Composer ？

恩，因为我们这里介绍的是 Laravel4，早在 Laravel3 的时候还是不用的 Composer 的。那么 Composer 是神马呢？简单的说 Composer 就是一个 PHP 的组件包的依赖管理器。早年间 PHP 其实是有自己的包管理器的，叫 PEAR。PEAR 就介绍到这里，你只要知道这是一个狗屎一般的管理器就行了。在 Node 的 npm 和 Ruby 的 bundler 都如火如荼的时候，连 Python 都有了好基友 easy_iinstall 和 pip，PHP也坐不住了，几个非官方的小伙伴一咬牙一跺脚，于是就有了 Composer。Composer 已经得到越来越多的 PHP 框架支持，基本就是你的 PHP 框架如果不支持 Composer，你都不好意思和同行打招呼。

Composer解决的问题是：

1. 你有一个依赖N多库的项目。
2. 这些库中一些又依赖于其他的库。
3. 你声明你所依赖的库。
4. Composer找出哪些包的哪个版本将会被安装，然后安装它们（也就是把它们下载到你的项目中）。

下面就是小白使用流程，更多关于 Composer 的内容，请到 [Composer官网] [3]

首先是安装，这里只介绍 Ubuntu 和 Windows 的安装，其他你们应该可以推理出来吧？

#### Ubuntu Composer 安装
1、下载并执行 Installer，要注意的是，如果沒有在 php 前面加上 sudo 的话，有可能出现错误信息。
```terminal
sudo curl -sS https://getcomposer.org/installer | sudo php -d detect_unicode=Off
```

2、切换到全局安装文件夹
```terminal
sudo mv composer.phar /usr/local/bin/composer
```

3、更改文件权限：上面的命令完成后，会下载好一个名为 composer.phar 的文件，而这个文件就是 Composer 的本体了，不过要更改一下它的权限。
```terminal
sudo chmod a+x composer.phar
```

4、更新：完成上面的步骤后，Composer 就装好了，过一段时间 Composer 自身升级版本，执行下面的命令就行（一般在你更新包的时候如果 Composer 有新版本，会提醒你需要升级）。
```terminal
sudo composer self-update
```

#### Windowns Composer 安装
1、下载 Windowns 下的 Composer 安装包：[官网下载页面] [4] 或者点击 [下载安装文件] [5]，进行安装。  
2、然后，就没然后了，你已经装好了。Composer 自身需要升级版本的时候你只需要在命令行（运行：cmd）输入
```terminal
composer self-update
```
Composer 装好后，我们就开始装 Laravel 吧！

### Laravel 安装
#### 最低要求（注意 PHP 版本）
1. PHP最低版本： 5.3.7
2. MCrypt PHP扩展

**注意：请保证你的 PHP 已经打开 openssl，如果不知道是否打开，请到 php.ini 中查看`extension=php_openssl.dll`，并将其前面的`;`去掉。也就是`;extension=php_openssl.dll`改成`extension=php_openssl.dll`**

上面我们已经安装好了 Composer，然后我们打开终端（Win 开打cmd），进入到 PHP 环境目录，运行命令
```terminal
composer create-project laravel/laravel your-project-name
```
面对这一串命令不要害怕，你只要修改`your-project-name`就行了，它代表你要安装 Laravel 的文件名。比如我有个项目叫 onepiece，那么上面的命令就是
```terminal
composer create-project laravel/laravel onepiece
```
运行这句代码后，Composer 就开始下载需要的文件了，等运行结束，你会在你的 PHP 环境目录里看到 onepiece 这个文件夹，这就安装好了。

#### 另一种安装方式
有的小盆友说了，大哥，我不是这么弄的，我从 [Laravel 官方的 github 库里] [12] 直接下载的 master 压缩包，肿么不能用啊？

是的，直接下载的 master 压缩包解压后只是 Laravel 的包装文件（暂且这样叫吧），是不能直接运行的，缺少核心文件，这时候我们需要先进入到这个文件夹里。比如我们的文件都拷贝到了 luffy（这是我们自己手动创建的文件夹）这个文件夹里了，那么目绿结构应该是这样的：
```fiels
luffy
  |-- app
  |-- bootstrap
  |-- public
  |-- .gitattributes
  |-- .gitignore
  |-- artisan
  |-- composer.json
  |-- CONTRIBUTING.md
  |-- phpunit.xml
  |-- readme.md
  |-- server.php
```
好，现在我们从 终端（Windowns是cmd）进入到 luffy 这个文件夹，然后运行
```terminal
composer install
```
然后你会看到画面卡顿了，这是正常的，一般会等待一会儿（要看你的联网速度了，是外网的速度），再然后就看到开始下载，很激动有木有？等吧，等啊……等啊……等到界面再次停到你的文件夹路径——在这个例子里就是 luffy ——下面，那就是安装好了。

#### 懒人包
好吧，以上步骤你受到了各种阻力，不能翻墙有木有？虚拟主机不能终端有木有？各种没看懂有木有？

别急，这里给你提供了一个懒人包，是已经将核心文件通过 composer 下载好的压缩包，简单说就是下载后就可以直接用的包（鲜花，掌声，美女……什么？没有美女？T_T……）。

下载地址：  
[完整包 Github 地址] [13]  
[直接下载完整包zip] [14]  
#### 浏览
现在 Laravel 就安装好了，我们可以在浏览器输入
```browser
http://127.0.0.1/项目文件夹名/public
```
这里的 **项目文件夹名** 就是我们上面说的 onepiece 、luffy 这种。  
看到如下画面就是安装成功了
![安装成功！] [6]


[返回目录] [1]  
[下一篇：Laravel 配置] [2]  



[1]: https://github.com/maliang/LikeLaravel "返回目录"
[2]: https://github.com/maliang/LikeLaravel/blob/master/base/config.md "Laravel 配置"
[3]: http://getcomposer.org/ "Composer官网"
[4]: http://getcomposer.org/download/ "Composer 官网下载页面"
[5]: http://getcomposer.org/Composer-Setup.exe "Composer 安装程序"
[6]: succeed.png "安装成功！"
[7]: #composer-%E4%BB%8B%E7%BB%8D "跳到 Composer 介绍"
[8]: http://git-scm.com/ "Git 官网"
[9]: http://git-scm.com/download "Git 官网下载页面"
[10]: http://git-scm.com/download/win "Git 安装程序"
[11]: git.png "Git 安装界面"
[12]: https://github.com/laravel/laravel "Laravel 官方的 github 库里"
[13]: https://github.com/maliang/complete-laravel4 "完整包 Github 地址"
[14]: https://github.com/maliang/complete-laravel4/archive/master.zip "直接下载完整包zip"
