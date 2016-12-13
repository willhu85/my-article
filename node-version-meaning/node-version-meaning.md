# nodejs中每个版本形式的含义

我们在写`package.json`的时候，会在`dependencies`和`devDependencies`中看下各种格式的版本号：类似

```
{
  "devDendencies": {
    "browser-sync": "^2.16.0",
    "gulp": "^3.9.1",
    "gulp-concat": "^2.6.0",
    "jshint": "^2.9.3",
    "require-dir": "^0.3.0",
    "streamqueue": "^1.1.1"
  }
}
```

实际这些版本号遵循[semver 2.0](http://semver.org/)的语义化版本规则。

版本号分为三部分组成：主版本号.次版本号.修订号
版本号递增规则如下：
* 主版本号：当你做了不兼容的API 修改，
* 次版本号：当你做了向下兼容的功能性新增，
* 修订号：当你做了向下兼容的问题修正。
* 先行版本号及版本编译信息可以加到“主版本号.次版本号.修订号”的后面，作为延伸。

表达式 | 版本范围 | 说明
--|---|--
1.2.1  | 1.2.1 |  匹配指定版本，这里是匹配1.2.1。
^1.0.0  | >=1.0.0 且 <2.0.0 |  `^`表示与指定的版本兼容，左边第一个非0字段不可变，后面的可变，即1.X.X但不得到2.0.0
^0.0.3 | >=0.0.3 且 <0.0.4 | 同上
^5.x | >=5.0.0 且 <6.0.0 | 同上
~0.1.1 | >=0.1.1 且 <0.2.0 | `~`表示约等于版本，如果存在次版本号，则允许修订号为最高的，否则允许次版本为最高，如 ~1匹配>=1.0.0 且 <2.0.0
\* | 匹配 >=0.0.0 |
\>=3.0.0 | >=3.0.0 | 其他符号还有<,<=,>,>=,=.字面意思。可使用空格表示 AND，\|\| 表示 OR，範例：
1.2.7 \|\| >=1.2.9 <2.0.0 表示可包含 1.2.7、1.2.9 和 1.4.6，不可包含 1.2.8 或 2.0.0
1.30.2 - 2.30.2 | >=1.30.2 且 <=2.30.2 | 字面意思
git://github.com/user/project.git#commit-ish | Git URL形式的依赖 | 还支持URL、GitHub URL、本地 URL，详见 [URLs as Dependencies](https://docs.npmjs.com/files/package.json#urls-as-dependencies)
latest | 当前发布的版本 | 这是一个tag,常见的还有next stable beta canary，详情参考[dist-tag npm Documentation](https://docs.npmjs.com/cli/dist-tag)


参考：
* https://docs.npmjs.com/files/package.json
* http://blog.kankanan.com/article/package.json-65874ef6-dependencies-4e2d7684540479cd7248672c53f75f625f0f.html
