# whistle--跨平台网络抓包调试工具

![whistle](http://7xiqdg.com1.z0.glb.clouddn.com/15259362357029.png)


[TOC]

## 简介
 [whistle](https://github.com/avwo/whistle)是一款跨平台的网络抓包调试工具，基于node开发。支持抓包，重放，替换，修改等方式来调试http(s),WebSocket请求，也可以作为普通的http代理。其功能和常用的fiddler(windows),Charles(Mac)工具功能相同，不过对于开发者更加友好，操作和调试更加方便，还支持node模块的插件。
 

## 快速上手

### 安装
```js
npm install -g whistle // 全局安装whistle
```
### 启动
```js
w2 start  //启动whistle
```
### 配置代理 (推荐使用浏览器插件)
```
127.0.0.1:8899
```
### 配置规则
浏览器访问[http://local.whistlejs.com](http://local.whistlejs.com) 打开whistle界面，在rule里面配置:

```js
jd.com  127.0.0.1
taobao.com  127.0.0.1
tmall.com 127.0.0.1
```
OK，就是这么简单

## 安装使用
首先需要安装好node,官方推荐使用最新的LTS版本node

### 安装whistle
node环境配置成功后开始安装whistle，非root用户加sudo

```js
npm install -g whistle
```

安装完成后，执行命令`whistle help`或者`w2 help`可以查看whistle的帮助信息，有输出则证明已安装成功

```js
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

### 启动whistle

新版本的whistle支持三种等价命令`whistle`,`w2`,`wproxy`

启动whistle

```js
w2 start
```
重启whistle

```js
w2 stop
```
停止whistle

```js
w2 stop
```
启动调试模式（启动了一个前台服务,主要用于查看whistle的异常及插件开发）

```
w2 run
```

### 配置代理

代理服务器，如果在本地则为`127.0.0.1`，如果部署在远程服务器或者虚拟机上，就改成对应IP即可。
默认端口为8899，如果端口被占用，要修改端口号，可以通过 `-p`来指定新的端口号

**代理方式**

1. 直接配置系统代理
    * [Windows](http://jingyan.baidu.com/article/0aa22375866c8988cc0d648c.html)
    * [Mac](http://jingyan.baidu.com/article/a378c960849144b3282830dc.html)
2. 安装浏览器代理插件，推荐方式
    * Chrome插件：[SwitchyOmega](https://chrome.google.com/webstore/detail/padekgcemlokbadohgkifijomclgjgif)
    * Firefox插件： [ProxySelector](https://addons.mozilla.org/zh-cn/firefox/addon/proxy-selector/)
3. 移动端需要配置当前WIFI的代理


## 如何使用

通过`w2 start`启动后，访问http://local.whistlejs.com 即可打开whistle界面。
![图片](http://7xiqdg.com1.z0.glb.clouddn.com/15204233854650.jpg)

所有通过whistle的篡改操作，都可以用过下面的配置方式实现


```
pattern operatorURL
```
pattern为匹配请求URL，支持域名，路径，正则，通配符等多种方式

operatorURI为对应的操作，由协议和值组成（operatorURL = opProtocol://opValue）
支持的协议类型：[协议列表](http://wproxy.org/whistle/rules/)

PS; {value} 则对应工具栏Values下的文件


两边结合一下：

```
# 域名匹配IP
 www.example.com  127.0.0.1
 # 带端口的域名匹配
 www.example.com:6666  127.0.0.1
 # 带协议的域名，支持：http、https、ws、wss、tunnel
 http://www.example.com  127.0.0.1

 # 路径匹配，同样支持带协议、端口
 www.example.com/test  http://127.0.0.1:9090
 https:/www.exapmle.com/test http://127.0.0.1:9090
 https:/www.exapmle.com:6666/test  http://127.0.0.1:9090

 # 正则匹配
 /^https?://www\.example\.com\/test/(.*)/ referer://http://www.test.com/$1

 # 通配符匹配
 ^www.example.com/test/*** referer://http://www.test.com/$1

```

## 功能详解
whistle功能概括：
![](http://7xiqdg.com1.z0.glb.clouddn.com/15259409497970.png)



#### 代理设置

##### 设置http代理

```
pattern proxy://ip:port
# 加用户名密码
pattern proxy://username:password@ip:port
www.jd.com proxy://test:123@127.0.0.1:8888
```
#####设置socks代理

```
pattern socks://ip:port
# 加用户名密码
pattern socks://username:password@ip:port

www.jd.com socks://test:123@127.0.0.1:8888
```

#####设置pac代理

```
pattern pac://filepath

/./ pac://https://raw.githubusercontent.com/imweb/node-pac/master/test/scripts/normal.pac
```

#####设置反向代理
区别于正向代理，具体可参考 [正向代理与反向代理](https://www.cnblogs.com/Anker/p/6056540.html)
whistle作为反向代理只支持http访问，启动whistle时设置监听的端口为6060:

```
w2 start -p 6060
#或
w2 restart -p 6060
```

非root用户需要加`sudo w2 start -p 6060`。 ​ 根据域名、或路径、或正则表达式配置带端口的host：

```
localhost:6060/aa host://10.8.43.82:8080
localhost:6060/bb host://10.8.43.82:8081
```
这样访问localhost:6060的请求会自动转到8080或8181端口，实现无端口访问。 PS：如果要用IP访问，可以采用 http://127.0.0.1/-/xxx 或 http://127.0.0.1/_/xxx，whistle会自动转成 http://127.0.0.1/xxx

#### 移动端调试
移动端调试的时候需要在同一个局域网内，涉及到https的连接需要开启https拦截。

##### 开启https拦截

如果要拦截https和websockets请求，必须安装根证书和开启https拦截。

![下载根证书](http://7xiqdg.com1.z0.glb.clouddn.com/15234431596108.gif)

在工具栏=>https 下载 RootCA, 并勾选 `intercept HTTPS CONNECTs` 选项

##### 安装CA证书

具体参见：[安装根证书](http://wproxy.org/whistle/webui/https.html)

##### 设置手机代理

设置 => 无线局域网 => 找到对应局域网点击感叹号 => HTTP代理 配置代理 => 选择手动 => 填写whistle服务的IP和端口号

PS: 如果配置完代理，手机无法访问，可能是whistle所在的电脑防火墙限制了远程访问whistle的端口，关闭防火墙或者设置白名单： http://jingyan.baidu.com/article/870c6fc317cae7b03ee4be48.html

##### 访问界面

whistle集成了weinre的功能，只需要简单配置`pattern weinre://id`即可使用。

![weinre in whistle](http://7xiqdg.com1.z0.glb.clouddn.com/15234306853141.gif)

然后点击工具栏的weinre，选择对应的ID打开weinre界面

##### 移动调试

相对于PC调试，移动端调试会常遇到以下问题
1. 无法通过console输出错误，也无法看到页面的js报错
2. 无法查看和修改页面的DOM和样式
3. 无法debug

######1.来捕获页面的错误和log

whistle可以通过类似console的log平台，来捕获页面的错误和log

```
www.jd.com log://
# 如果你想同时注入js脚本，可以用下面一种方式
# 在mac或linux中
www.jd.com log:////Users/willhu/work/whistle-test/log-test.js
# 在windows中
www.jd.com log://D:\xxx\test.js
# 直接从whistle的Values配置的key-value里面获取脚本
www.jd.com log://{log-test.js}
```

![log-test](http://7xiqdg.com1.z0.glb.clouddn.com/15239363346151.jpg)

######2.查看、修改页面的DOM和样式

集成了weinre的功能，用户只需通过简单配置(pattern weinre://id)即可使用即可通过在pc上通过weinre修改网页的DOM结构及其样式,这里的ID只是一个分类，避免一个weinre调试页面出现太多链接


```
m.jd.com weinre://test-weinre
```
![test-weinre](http://7xiqdg.com1.z0.glb.clouddn.com/15239373901685.jpg)


######3. 暂不支持debug功能,可以通过log来替代

推荐腾讯的vConsole插件

```
m.jd.com js:///Users/willhu/work/whistle-test/vconsole.min.js
```
vConsole: https://github.com/Tencent/vConsole

demo: [vConsole](http://wechatfe.github.io/vconsole/demo.html)


#### 文件导入导出

在network中右键点击请求列表，可以将请求的数据导出到txt.saz文件，也可导入txt.saz.har文件。

#### 抓包重放

##### 查看请求响应数据

在network中可以看到每条请求的详细情况。

![network](http://7xiqdg.com1.z0.glb.clouddn.com/15239485540063.jpg)

##### 重放请求

打开network ==> 选中请求 ==> 右键选择replay

![replay-w433](http://7xiqdg.com1.z0.glb.clouddn.com/15239478785805.jpg)

*重构请求*

可以自定义请求的URL、请求方法、请求头，请求内容
![Composer](http://7xiqdg.com1.z0.glb.clouddn.com/15239497324966.gif)


##### 请求和响应修改

######修改请求URL或者参数

设置静态规则列表

```
pattern reqScript://filepath
www.jd.com reqScript:///Users/willhu/work/whistle-test/rulelist.txt
```
rulelist.txt如果文件的第一行为规则的注释，即`#`开头则任务filepath指定的是规则列表，会加载该列表，并进行二次匹配获取规则

```
# rules
pattern1 operatorURI1
pattern2 operatorURI2
patternN operatorURIN
```

通过脚本设置规则列表

```
www.jd.com reqScript://{rulelist.js}
```

######设置服务器IP(host)
支持两种配置方式，这样就不用查找本机的host文件了

```
ip pattern
或者
pattern host://ip
```
例子

```
# 传统hosts配置
127.0.0.1 www.example.com # 等价于： www.example.com  127.0.0.1
127.0.0.1 a.example.com b.example.com c.example.com

# 支持带端口
127.0.0.1:8080 www.example.com # 等价于： www.example.com  127.0.0.1：8080
127.0.0.1:8080 a.example.com b.example.com c.example.com

# 支持通过域名获取host，类似DNS的cname
host://www.qq.com:8080 www.example.com # 等价于： www.example.com  host://www.qq.com:8080
host://www.qq.com:8080 a.example.com b.example.com c.example.com

# 支持通过正则表达式匹配
127.0.0.1:8080 /example\.com/i # 等价于： /example\.com/i  127.0.0.1：8080
127.0.0.1:8080 /example\.com/ /test\.com/

# 支持路径匹配
127.0.0.1:8080 example.com/test # 等价于： example.com/test 127.0.0.1：8080
127.0.0.1:8080 http://example.com:5555/index.html www.example.com:6666 https://www.test.com/test

# 支持精确匹配
127.0.0.1:8080 $example.com/test # 等价于： $example.com/test 127.0.0.1：8080
127.0.0.1:8080 $http://example.com:5555/index.html $www.example.com:6666 $https://www.test.com/test
```
######替换请求

```
https://jd.com https://baidu.com/
```

######修改请求方法
配置方式如下：

```
pattern method://newMethod
jd.com method://post
```

######修改请求头
修改请求头，配置方式：

```
pattern reqHeaders://filepath
jd.com reqHeaders://{reqHeaders.json}
```
######修改请求内容

把指定的内容替换请求内容(GET等请求没有内容没有替换一说)，配置方式

```
pattern reqBody://filepath
www.jd.com method://post reqBody://{test-reqBody.html}
```
######注入或替换内容
把指定的内容添加到请求内容前面(GET等请求没有内容无法添加)，配置方式：

```
pattern reqPrepend://filepath
```
######限速或者延迟请求
延迟请求

```
pattern reqDelay://timeMS
www.jd.com reqDelay://3000
```
设置速度

```
pattern reqSpeed://kbs
www.jd.com reqSpeed://3
```

######修改相应状态码
设置响应状态码(状态码范围100~999)，请求会直接根据设置的状态码返回，不会请求到线上，配置方式：

```
pattern statusCode://code
jd.com statusCode://404
```
######修改响应头

方式同请求头

######修改响应内容

把指定的内容替换响应内容(304等响应没有内容无法替换)，配置方式：

```
pattern resBody://filepath
st.360buyimg.com/m/css/2014/layout/layout2015.css resBody://{myAppend.css}
```

######注入或者替换内容
把指定的内容追加到响应内容后面(304等响应没有内容无法追加)，配置方式：

```
pattern resAppend://filepath
st.360buyimg.com/m/css/2014/layout/layout2015.css resAppend://{myAppend.css}
```

#####限制速度或延迟响应
延迟响应

```
pattern resDelay://timeMS
www.jd.com resDelay://3000
```
设置速度

```
pattern resSpeed://kbs
www.jd.com resSpeed://3
```

#### 插件扩展

有些很少用的功能，及一些跟业务相关的功能，考虑到会导致安装过程比较长或者占用内存空间或者适应范围比较小，whistle没有把这些功能加进去，但提供了插件的方式扩展这些功能。whistle本身就是一个Node模块，只需要按照whistle.xxx的形式命名即可。

编写whistle插件：[如何编写插件](http://wproxy.org/whistle/plugins.html)

官方提供的插件列表：[官方插件列表](https://github.com/whistle-plugins)

#### socket和websocket

[利用whistle调试socket和webscoket](http://imweb.io/topic/5a11b1b8ef79bc941c30d91a)


测试用的文件：[whistle-test-files](whistle-test)

测试用的rules: [rules](rules_20180516162810433.txt)

