# whistle--跨平台网络抓包调试工具

<p align="center">![whistle](https://raw.githubusercontent.com/avwo/whistle/master/biz/webui/htdocs/img/whistle.png)

### 简介
 whistle是一款跨平台的网络抓包调试工具，基于node开发。支持抓包，重放，替换，修改等方式来调试http(s),WebSocket和普通的Socket(TCP)请求，也可以作为普通的http代理。其功能和常用的fiddler(windows),Charles(Mac)工具功能相同，不过对于开发者更加友好，操作和调试更加方便，还支持node模块的插件。
 
基本功能如下

<p aglin="center">![whistle-list](https://raw.githubusercontent.com/avwo/whistleui/master/assets/whistle.png?v=1)

### 安装启动

官方推荐使用最新的`LTS`版本node。
node环境配置成功后开始安装whistle，非root用户加`sudo`

```js
npm install -g whistle
```
安装完成后，执行命令`whistle help`或者`w2 help`可以查看whistle的帮助信息，有输出则证明已安装成功


```
$ w2 help
Usage: whistle <command> [options]

Commands:

	run       Start a front service
	start     Start a background service
	stop      Stop current background service
	restart   Restart current background service
	help      Display help information
	
Options:

	-h, --help                                      output usage information
	-D, --baseDir [baseDir]                         the base dir of config data
	-A, --ATS                                       generate Root CA for iOS ATS (Node >= 6 is required)
	-z, --certDir [directory]                       custom certificate path
	-l, --localUIHost [hostname]                    local ui host (local.whistlejs.com by default)
	-n, --username [username]                       the username of whistle
	-w, --password [password]                       the password of whistle
	-N, --guestName [username]                      the guest name
	-W, --guestPassword [password]                  the guest password
	-s, --sockets [number]                          max sockets (60 by default)
	-S, --storage [newStorageDir]                   the new local storage directory
	-C, --copy [storageDir]                         copy storageDir to newStorageDir
	-c, --dnsCache [time]                           the cache time of DNS (30000ms by default)
	-H, --host [host]                               whistle listening host(:: or 0.0.0.0 by default)
	-p, --port [port]                               whistle listening port (8899 by default)
	-P, --uiport [uiport]                           whistle ui port (8900 by default)
	-m, --middlewares [script path or module name]  express middlewares path (as: xx,yy/zz.js)
	-M, --mode [mode]                               the whistle mode (as: pureProxy|debug|multiEnv)
	-u, --uipath [script path]                      web ui plugin path
	-t, --timeout [ms]                              request timeout (66000 ms by default)
	-e, --extra [extraData]                         extra data for plugin
	-f, --secureFilter [secureFilter]               the script path of secure filter
	-R, --reqCacheSize [reqCacheSize]               the cache size of request data (512 by default)
	-F, --frameCacheSize [frameCacheSize]           the cache size of socket frames (512 by default)
	-V, --version                                   output the version number
```

**启动whistle**
新版本的whistle支持三种等价命令`whistle`,`w2`,`wproxy`

```
w2 start
```

**重启whistle**

```
w2 stop
```

**停止whistle**

```
w2 stop
```
**启动调试模式**（启动了一个前台服务）

```
w2 run
```

### 设置代理

代理服务器，如果在本地则为`127.0.0.1`，如果部署在远程服务器或者虚拟机上，就改成对应IP即可。
默认端口为8899，如果端口被占用，要修改端口号，可以通过 `-p`来指定新的端口号

**代理方式**
1. 直接配置系统代理
* Windows
* Mac
2. 安装浏览器插件

### 功能

#### websocket
#### 设置代理
#### 反向代理
#### 移动端调试
#### 插件扩展
#### 抓包重放
#### 修改请求
#### 修改相应
#### socket






