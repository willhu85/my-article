# 如何使用package.json文件

*最近在整理之前写的模块的时候，发现很多模块的package.json写的并不是那么规范，所以查阅了一些资料，了解了一下关于如何使用package.json，列出来供大家参考*

*本文参考了篇文章*
* https://docs.npmjs.com/files/package.json#dependencies
* http://www.cnblogs.com/tzyy/p/5193811.html
* http://javascript.ruanyifeng.com/nodejs/packagejson.html

#### 属性列表

### 概述
这篇文档告诉了你package.json里面，包含了那些字段。这个文件必须是个json文件，而不仅是一个js对象。文档中很多属性和设置可以通过[npm-config](https://docs.npmjs.com/misc/config)来生成。

### name（必填字段）
package.json中有两个字段是必填字段。name字段和version字段。缺少这两个字段则无法安装npm模块。每个npm模块也是依赖这两个字段作为唯一标识。如果你的npm模块有所修改，那么对应的version字段也应该有所改变。

name字段就是你的npm模块的名称。

name字段需要符合以下规则：

* name必须<= 214 个字节，包括模块的前缀
* 不得以“\_” 或者 “\.” 作为name的开头
* 不能有大写字符
* 因为name字段会成为URL的一部分，或是命令行的一个实参，也有可能是个文件夹的名字，所以不能包含no-URL-safe(URL非法)字符。

一些建议：
* 不要用和node核心模块一样的名称
* 不要把“js”和”node”字段包含在name中。因为你实际在编写json文件，而包含这些字段会被认为是个js文件而非npm模块，如果你需要指定某些引擎的话，可以在“engines”字段中填写。
* name会被写在require()的参数中，所以name最好简短且明确。
* 创建一个name的时候，最好去[https://www.npmjs.com/](https://www.npmjs.com/)查查名称是否被占用。

name可以有一些前缀如 例如 @myorg/mypackage.可以在[npm-scope](https://docs.npmjs.com/misc/scope)的中查看详情。

### version（必填字段）

package.json中有两个字段是必填字段。name字段和version字段。缺少这两个字段则无法安装npm模块。每个npm模块也是依赖这两个字段作为唯一标识。如果你的npm模块有所修改，那么对应的version字段也应该有所改变。

version字段必须可以被node-semver这个模块解析，是个和npm捆绑在一起的包。

这里有关于版本号形式的含义[nodejs中每个版本形式的含义](https://segmentfault.com/a/1190000007787025)

### description

一段字符串，用来描述这个npm模块的作用，通过npm search的时候回用到。

### keywords

一个由字符串组成的数组，也有助于别人通过npm search的时候快速找到你的包。

### homepage

这个项目的主页URL。 注意：这里和url属性不是一个东西，如果你填了url属性，npm的注册工具会认为你把项目发布到别的地方了，就不会去npm官方仓库去找。

### bugs

包含你的项目的issue和email地址，如果别人在使用你的包的时候遇到了问题，可以通过这里找到你并提交问题。

它的格式如下：


    {     
      "url" : "https://github.com/owner/project/issues",    
      "email" : "project@hostname.com"    
    }




url和email你可以选填其中一个或者两个，如果只填一个，可以直接写成字符串，而不是一个对象。

如果提供了url, 使用npm bugs命令的时候会用到。

### license

给你的模块定一个协议，让大家知道这个模块的使用权限。例如：遵循BSD-2-Clause or MIT协议。添加一个SPDX许可如下：

```

{ "license" : "BSD-3-Clause" }

```
这里查看[SPDX协议完整列表](https://spdx.org/licenses/)。理想情况下，你应该选一个[OSI](https://opensource.org/licenses/alphabetical)许可（开源许可）。

如果你的模块遵循多种许可，可以使用[SPDX协议2.0的语法](https://npmjs.com/package/spdx)，如下：

```

{ "license" : "(ISC OR GPL-3.0)" }

```
如果你使用的是许可证还没有分配一个SPDX标识符,或者如果您使用的是一个定制的许可证,使用这样的字符串值:

```

{ "license" : "SEE LICENSE IN <filename>" }
```

然后在模块的顶部include 这个<filename>的文件。

一些旧的模块使用许可对象或一个“许可证”属性,其中包含许可对象数组:

```
// Not valid metadata
{ "license" :
  { "type" : "ISC"
  , "url" : "http://opensource.org/licenses/ISC"
  }
}
// Not valid metadata
{ "licenses" :
  [
    { "type": "MIT"
    , "url": "http://www.opensource.org/licenses/mit-license.php"
    }
  , { "type": "Apache-2.0"
    , "url": "http://opensource.org/licenses/apache2.0.php"
    }
  ]
}
```

上面的样式现在已经弃用。现在使用SPDX表达式,是这样的:

```
{ "license": "ISC" }
{ "license": "(MIT OR Apache-2.0)" }
```

最后,如果你不希望别人在任何条件下有任何使用你的包的权限，你可以这样:

```
{ "license": "UNLICENSED"}
```
也考虑设置"private": true,来防止模块的意外发布

### people fields: author, contributors

用户相关的属性：author是一个作者，contributors是一个包含一堆作者的数组。每个person有一些描述的字段，如下：

```
{ "name" : "Barney Rubble"
, "email" : "b@rubble.com"
, "url" : "http://barnyrubble.tumblr.com/"
}
```
也可以用下面的格式简写，npm会自动解析:

```
"Barney Rubble <b@rubble.com> (http://barnyrubble.tumblr.com/)"
```

email和url属性实际上都是可以省略的。描述用户信息的还有一个"maintainers"（维护者）属性。

### files

file字段是一个包含在你项目里的文件的数组，里面的内容是文件名或者文件夹名。如果是文件夹，那么里面的文件也会被包含进来,除非你设置了ignore规则。
你也可以在模块根目录下创建一个".npmignore"文件（windows下无法直接创建以"."开头的文件，使用linux命令行工具创建如git bash），写在这个文件里边的文件即便被写在files属性里边也会被排除在外，这个文件的写法".gitignore"类似。

以下文件始终包含在内，无论是否设置：

* package.json
* README (and its variants)
* CHANGELOG (and its variants)
* LICENSE / LICENCE

相反，以下文件通常会被忽略：

* .git
* CVS
* .svn
* .hg
* .lock-wscript
* .wafpickle-N
* *.swp
* .DS_Store
* ._*
* npm-debug.log

### main

main字段规定了程序的主入口文件。如果你的模块命名为foo,用户安装后，就会通过require("foo")来引用该模块，返回的内容就是你的模块的 module.exports指向的对象。

这是一个相对于你的模块文件夹的模块ID，对于大多数的模块，有个主脚本就足够了。

### bin

很多模块有一个或多个可执行文件需要配置到PATH路径下。npm就是通过这个特性安装，使得npm可执行。

要用这个功能，给package.json中的bin字段一个命令名到文件位置的map。初始化的时候npm会将他链接到prefix/bin（全局初始化）或者./node_modules/.bin/（本地初始化）。

例如：一个myapp模块可能是这样：

```
{ "bin" : { "myapp" : "./cli.js" } }
```
所以，当你安装myapp，npm会从cli.js文件创建一个到/usr/local/bin/myapp路径下。

如果你只有一个可执行文件，并且名字和包名一样。那么你可以只用一个字符串，比如：

```
{ "name": "my-program"
, "version": "1.2.5"
, "bin": "./path/to/program" }
```

和下面是一样的效果：

```{ "name": "my-program"
, "version": "1.2.5"
, "bin" : { "my-program" : "./path/to/program" } }
```

### man

用来给Linux下的man命令查找文档地址，是个单一文件或者文件数组。 如果是单一文件，安装完成后，他就是man + <pkgname>的结果，和此文件名无关，例如：

```
{ "name" : "foo"
, "version" : "1.2.3"
, "description" : "A packaged foo fooer for fooing foos"
, "main" : "foo.js"
, "man" : "./man/doc.1"
}
```
通过man foo命令会得到 ./man/doc.1 文件的内容。
如果man文件名称不是以模块名称开头的，安装的时候会给加上模块名称前缀。因此，下面这段配置：

```
{ "name" : "foo"
, "version" : "1.2.3"
, "description" : "A packaged foo fooer for fooing foos"
, "main" : "foo.js"
, "man" : [ "./man/foo.1", "./man/bar.1" ]
```
会创建一些文件来作为man foo和man foo-bar命令的结果。
man文件必须以数字结尾，或者如果被压缩了，以.gz结尾。数字表示文件将被安装到man的哪个部分。

```
{ "name" : "foo"
, "version" : "1.2.3"
, "description" : "A packaged foo fooer for fooing foos"
, "main" : "foo.js"
, "man" : [ "./man/foo.1", "./man/foo.2" ]
}
```

会创建 man foo 和 man 2 foo 两条命令。

### directories

CommonJs通过directories来制定一些方法来描述模块的结构，看看npm的package.json文件[npm's package.json](https://registry.npmjs.org/npm/latest) ，会看到有directories标示出doc, lib, and man。

目前这个配置没有任何作用，将来可能会整出一些花样来。

#### directories.lib
告诉用户模块中lib目录在哪，这个配置目前没有任何作用，但是对使用模块的人来说是一个很有用的信息。

#### directories.bin
如果你在这里指定了bin目录，这个配置下面的文件会被加入到bin路径下，如果你已经在package.json中配置了bin目录，那么这里的配置将不起任何作用。

#### directories.man
指定一个目录，目录里边都是man文件，这是一种配置man文件的语法糖。

#### directories.doc
在这个目录里边放一些markdown文件，可能最终有一天它们会被友好的展现出来（应该是在npm的网站上）

#### directories.example
放一些示例脚本，或许某一天会有用 - -！

### repository

指定你的代码存放的地方。这个对希望贡献的人有帮助。如果git仓库在github上，那么npm docs命令能找到你。

如下：

```
"repository" :
  { "type" : "git"
  , "url" : "https://github.com/npm/npm.git"
  }
"repository" :
  { "type" : "svn"
  , "url" : "https://v8.googlecode.com/svn/trunk/"
  }
```

URL应该是公开的（即便是只读的）能直接被未经过修改的版本控制程序处理的url。不应该是一个html的项目页面。因为它是给计算机看的。

若你的模块放在GitHub, GitHub gist, Bitbucket, or GitLab的仓库里，npm install的时候可以使用缩写标记来完成：

```
"repository": "npm/npm"
"repository": "gist:11081aaa281"
"repository": "bitbucket:example/repo"
"repository": "gitlab:another/repo"
```

### scripts

scripts属性是一个对象，里边指定了项目的生命周期个各个环节需要执行的命令。key是生命周期中的事件，value是要执行的命令。
具体的内容有 install start stop 等，详见[npm-scripts](https://docs.npmjs.com/misc/scripts).

### config

用来设置一些项目不怎么变化，跨版本的项目配置，例如port等。
用法如下：

```
{ "name" : "foo"
, "config" : { "port" : "8080" } }
```
然后有一个start命令引用npm_package_config_port环境变量，用户也可以用如下方式改写：```npm config set foo:port 8001```


See [npm-config](https://docs.npmjs.com/misc/config) and [npm-scripts](https://docs.npmjs.com/misc/config) for more on package configs.

### dependencies

dependencies属性是一个对象，配置模块依赖的模块列表，key是模块名称，value是版本范围，版本范围是一个字符，可以被一个或多个空格分割。

dependencies也可以被指定为一个git地址或者一个压缩包地址。

*不要把测试工具或transpilers写到dependencies中。* 对比下面的devDependencies。

下面是一些写法，详见https://docs.npmjs.com/misc/semver

* version 精确匹配版本
* \>version 必须大于某个版本
* \>=version 大于等于
* <version 小于
* <=versionversion 小于
* ~version "约等于"，具体规则详见semver文档
* ^version "兼容版本"具体规则详见semver文档
* 1.2.x 仅一点二点几的版本
* \http://... 见下面url作为denpendencies的说明
* \*任何版本
* "" 空字符，和*相同
* version1 - version2 相当于 >=version1 <=version2.
* range1 || range2 范围1和范围2满足任意一个都行
* git... 见下面git url作为denpendencies的说明
* user/repo See 见下面GitHub仓库的说明
* tag 发布的一个特殊的标签，见npm-tag的文档 https://docs.npmjs.com/getting-started/using-tags
*  path/path/path 见下面本地模块的说明

下面的写法都是可行的：

```
{ "dependencies" :
  { "foo" : "1.0.0 - 2.9999.9999"
  , "bar" : ">=1.0.2 <2.1.2"
  , "baz" : ">1.0.2 <=2.3.4"
  , "boo" : "2.0.1"
  , "qux" : "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0"
  , "asd" : "http://asdf.com/asdf.tar.gz"
  , "til" : "~1.2"
  , "elf" : "~1.2.3"
  , "two" : "2.x"
  , "thr" : "3.3.x"
  , "lat" : "latest"
  , "dyl" : "file:../dyl"
  }
}
```

#### URLs依赖

在版本范围的地方可以写一个url指向一个压缩包，模块安装的时候会把这个压缩包下载下来安装到模块本地。

#### Git URLs依赖

git URL可以写成这样：

```
git://github.com/user/project.git#commit-ish
git+ssh://user@hostname:project.git#commit-ish
git+ssh://user@hostname/project.git#commit-ish
git+http://user@hostname/project/blah.git#commit-ish
git+https://user@hostname/project/blah.git#commit-ish
```
commit-ish 可以是任意tag，hash，或者可以检出的分支，默认是master分支。

#### github URLs

支持github的 username/modulename 的写法，#后边可以加后缀写明分支hash或标签,如下：

```
{
  "name": "foo",
  "version": "0.0.0",
  "dependencies": {
    "express": "visionmedia/express",
    "mocha": "visionmedia/mocha#4727d357ea"
  }
}
```

#### 本地路径

npm2.0.0版本以上可以提供一个本地路径来安装一个本地的模块，通过npm install xxx --save 来安装，格式如下：

```
../foo/bar
~/foo/bar
./foo/bar
/foo/bar
```
package.json 生成的相对路径如下:

```
{
  "name": "baz",
  "dependencies": {
    "bar": "file:../foo/bar"
  }
```

这种属性在离线开发或者测试需要用npm install的情况，又不想自己搞一个npm server的时候有用，但是发布模块到公共仓库时不应该使用这种属性。

### devDependencies

如果别人只想使用你的模块，而不需要开发和测试所需要的依赖的时候，这种情况下，可以将开发测试依赖的包，写到devDependencies中。

这些模块会在npm link或者npm install的时候被安装，也可以像其他npm配置一样被管理，详见npm的config文档。
对于一些跨平台的构建任务，例如把CoffeeScript编译成JavaScript，就可以通过在package.json的script属性里边配置prepublish脚本来完成这个任务，然后需要依赖的coffee-script模块就写在devDependencies属性种。
例如:

```
{ "name": "ethopia-waza",
  "description": "a delightfully fruity coffee varietal",
  "version": "1.2.3",
  "devDependencies": {
    "coffee-script": "~1.6.3"
  },
  "scripts": {
    "prepublish": "coffee -o lib/ -c src/waza.coffee"
  },
  "main": "lib/waza.js"
}
```

prepublish脚本会在publishing前运行，这样用户就不用自己去require来编译就能使用。并且在开发模式中（比如本地运行npm install）会运行这个脚本以便更好地测试。

### peerDependencies

有时，你的项目和所依赖的模块，都会同时依赖另一个模块，但是所依赖的版本不一样。比如，你的项目依赖A模块和B模块的1.0版，而A模块本身又依赖B模块的2.0版。

大多数情况下，这不构成问题，B模块的两个版本可以并存，同时运行。但是，有一种情况，会出现问题，就是这种依赖关系将暴露给用户。

最典型的场景就是插件，比如A模块是B模块的插件。用户安装的B模块是1.0版本，但是A插件只能和2.0版本的B模块一起使用。这时，用户要是将1.0版本的B的实例传给A，就会出现问题。因此，需要一种机制，在模板安装的时候提醒用户，如果A和B一起安装，那么B必须是2.0模块。

peerDependencies字段，就是用来供插件指定其所需要的主工具的版本。

例如：

```
{
  "name": "tea-latte",
  "version": "1.3.5",
  "peerDependencies": {
    "tea": "2.x"
  }
}
```

上面这个配置确保再npm install的时候tea-latte会和2.x版本的tea一起安装，而且它们两个的依赖关系是同级的：

```
├── tea-latte@1.3.5
└── tea@2.2.0
```

这个配置的目的是让npm知道，如果要使用此插件模块，请确保安装了兼容版本的宿主模块。


### bundledDependencies

指定发布的时候会被一起打包的模块。

### optionalDependencies

如果一个依赖模块可以被使用， 但你也希望在该模块找不到或无法获取时npm不中断运行，你可以把这个模块依赖放到optionalDependencies配置中。这个配置的写法和dependencies的写法一样，不同的是这里边写的模块安装失败不会导致npm install失败。
但是需要自己处理模块缺失的情况，例如：

```
try {
  var foo = require('foo')
  var fooVersion = require('foo/package.json').version
} catch (er) {
  foo = null
}
if ( notGoodFooVersion(fooVersion) ) {
  foo = null
}
// .. then later in your program ..
if (foo) {
  foo.doFooThings()
}
```

optionalDependencies 中的配置会覆盖dependencies中同名的配置，最好只在一个地方写。

### engines

你可以指定项目的node的版本：

```
{ "engines" : { "node" : ">=0.10.3 <0.12" } }
```

和dependencies一样，如果你不指定版本范围或者指定为*，任何版本的node都可以。
也可以指定一些npm版本可以正确的安装你的模块，例如：

```
{ "engines" : { "npm" : "~1.0.20" } }
```

记住，除非用户设置engine-strict标记，F否则这个字段只是建议值。

### engineStrict

注意：这个属性已经弃用，将在npm 3.0.0 版本干掉。

### os

指定你的模块只能在哪个操作系统上跑：

```
"os" : [ "darwin", "linux" ]
```

也可以指定黑名单而不是白名单：

```
"os" : [ "!win32" ]
```

操作系统是由process.platform来判断的，这个属性允许黑白名单同时存在，虽然没啥必要.

### cpu

如果你的代码只能运行在特定的cpu架构下，你可以指定一个：

```
"cpu" : [ "x64", "ia32" ]
```

也可以设置黑名单:

```
"cpu" : [ "!arm", "!mips" ]
```

cpu架构通过 process.arch 判断

### preferGlobal

如果你的模块主要是需要全局安装的命令行程序，就设置它为true，就会提供一个warning，这样来只在局部安装的人会得到这个warning。

它不会真正的防止用户在局部安装，只是防止该模块被错误的使用引起一些问题。

### private

如果这个属性被设置为true，npm将不会发布它。

这是为了防止一个私有模块被无意间发布出去。如果你想让模块被发布到一个特定的npm仓库，如一个内部的仓库，可与在下面的publishConfig中配置仓库参数。

### publishConfig

这是一个在publish-time时会用到的配置集合。当你想设置tag、registry或access时特别有用，所以你可以确保一个给定的包无法在没有被打上"latest"标记时就被发布到全局公共的registry。

任何配置都可以被覆盖，当然可能只有"tag", "registry"和"access"和发布意图有关。

参考[npm-config](https://docs.npmjs.com/misc/config)来查看那些可以被覆盖的配置项列表。

### DEFAULT VALUES

npm会根据包的内容设置一些默认值。

```
"scripts": {"start": "node server.js"}
```

如果模块根目录下有一个server.js文件，那么npm start会默认运行这个文件。

```
"scripts":{"preinstall": "node-gyp rebuild"}
```

如果模块根目录下有binding.gyp, npm将默认用node-gyp来编译preinstall的脚本

```
"contributors": [...]
```

若模块根目录下有AUTHORS 文件，则npm会按Name (url)格式解析每一行的数据添加到contributors中，可以用#添加行注释


参考资料

* [semver](https://docs.npmjs.com/misc/semver)
* [npm-init](https://docs.npmjs.com/cli/init)
* [npm-version](https://docs.npmjs.com/cli/version)
* [npm-config](https://docs.npmjs.com/cli/config)
* [npm-config](https://docs.npmjs.com/misc/config)
* [npm-help](https://docs.npmjs.com/cli/help)
* [npm-faq](https://docs.npmjs.com/misc/faq)
* [npm-install](https://docs.npmjs.com/cli/install)
* [npm-publish](https://docs.npmjs.com/cli/publish)
* [npm-uninstall](https://docs.npmjs.com/cli/uninstall)
