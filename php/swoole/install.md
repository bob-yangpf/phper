# 安装Swoole

swoole 可以通过 `pecl install swoole` 来直接安装,`pecl `库一般会晚于github上的版本.所以,下面主要使用编译release版本安装

> 编译的有另外一个好处就是可以指定版本

## 安装准备

安装前必须保证系统已经安装了下列软件

- `php-7.1` 或更高版本
- `gcc-4.8` 或更高版本
- `make`
- `autoconf`

## 下载源码

国内可以到[码云仓库](https://gitee.com/swoole/swoole/releases)下载 或者直接在[Github](https://github.com/swoole/swoole-src/releases)上下载

选择版本后下载

```
wget https://gitee.com/swoole/swoole/repository/archive/v4.5.2?format=tar.gz -O swoolev4.5.2.tar.gz
tar -zxvf swoolev4.5.2.tar.gz
```

## 编译安装

```
cd swoole
./configure -with-php-config=/www/server/php/73/bin/php-config --enable-openssl --enable-http2
make -j4 && make install
```

> make -jx 这个表示多核CPU下使用多核 单核就不用加了直接`make`
>
> php-config 路径你按照自己的路径配置
>
> 后面的enable参数可以参考[swoole编译选项]([https://wiki.swoole.com/#/environment?id=%e7%bc%96%e8%af%91%e9%80%89%e9%a1%b9](https://wiki.swoole.com/#/environment?id=编译选项))

当看如下生成时候就表示成功了

> Installing shared extensions:     /www/server/php/73/lib/php/extensions/no-debug-non-zts-20180731/
> Installing header files:          /www/server/php/73/include/php/

## 增加PHP配置

不知道配置文件在哪里可以使用 `php --ini`

```
vim /www/server/php/73/etc/php.ini
extension=swoole
```

> 如果编译没有指定php-config情况下,要使用绝对路径

有其他配置也可以一起加进来,比如 [hyperf](https://github.com/hyperf/hyperf) 要求关闭短名

```
swoole.use_shortname = off
```

## 查看swoole信息

使用`php --ri swoole`就可以查看`swoole`的版本和配置信息了

> swoole
>
> Swoole => enabled
> Author => Swoole Team <team@swoole.com>
> Version => 4.5.2
> Built => Jun 29 2020 17:46:18
> coroutine => enabled
> epoll => enabled
> eventfd => enabled
> signalfd => enabled
> cpu_affinity => enabled
> spinlock => enabled
> rwlock => enabled
> openssl => OpenSSL 1.0.2k-fips  26 Jan 2017
> http2 => enabled
> pcre => enabled
> zlib => 1.2.7
> mutex_timedlock => enabled
> pthread_barrier => enabled
> futex => enabled
> async_redis => enabled
>
> Directive => Local Value => Master Value
> swoole.enable_coroutine => On => On
> swoole.enable_library => On => On
> swoole.enable_preemptive_scheduler => Off => Off
> swoole.display_errors => On => On
> swoole.use_shortname => Off => Off
> swoole.unixsock_buffer_size => 8388608 => 8388608

## 引用

[swoole官方文档](https://wiki.swoole.com/#/environment)