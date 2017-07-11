# eslint V4.1.1 规则简介

**规则说明：默认情况下不会启用任何规则。配置文件中的`"extends":"eslint:recommended"`属性可以启用一些默认的验证规则，默认的规则在下表会用R表示出来**

**使用`--fix`命令可以自动修复一些特定的规则(大部分为空格类规则)，下面用F表示**

## 规则说明
**0=off,1=warn, 2=error**

## 可能性的错误
**这些规则主要针对语法错误和逻辑错误**


| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| for-direction | for循环 需要往正确的方向循环,避免死循环 | | [案例](http://eslint.org/docs/rules/for-direction)| 
| no-await-in-loop | 禁止循环中有 await | | [案例](http://eslint.org/docs/rules/no-await-in-loop)|
| no-compare-neg-zero | 禁止和 -0 比较 | R | [案例](http://eslint.org/docs/rules/no-compare-neg-zero)|
| no-cond-assign | 禁止在条件表达式使用赋值 | R | [案例](http://eslint.org/docs/rules/no-cond-assign) |
| no-console | 禁止使用console | R | [案例](http://eslint.org/docs/rules/no-console)|
| no-constant-condition | 禁止在条件中使用常量表达式 | R | [案例](http://eslint.org/docs/rules/no-constant-condition)|
| no-control-regex| 禁止在正则中使用控制字符| R |[案例](http://eslint.org/docs/rules/no-console) |
| no-debugger| 禁止使用debugger| R F | [案例](http://eslint.org/docs/rules/no-debugger)|
| no-dupe-args| 禁止在函数定义中传入重复的参数| R | [案例](http://eslint.org/docs/rules/no-dupe-args)|
| no-dupe-keys| 禁止在对象字面量中使用重复的key| R | [案例](http://eslint.org/docs/rules/no-dupe-keys)|
| no-duplicate-case| 禁止在case中出现重复的标签| R | [案例](http://eslint.org/docs/rules/no-duplicate-case) |
| no-empty| 禁止块语句中的内容为空| R |[案例](http://eslint.org/docs/rules/no-empty) |
| no-empty-character-class| 禁止正则表达式中的[]内容为空| R | [案例](http://eslint.org/docs/rules/no-empty-character-class)|
| no-ex-assign| 禁止给catch语句中的异常参数赋值| R |[案例](http://eslint.org/docs/rules/no-ex-assign) |
| no-extra-boolean-cast| 禁止不必要的bool转换| R F |[案例](http://eslint.org/docs/rules/no-extra-boolean-cast) |
| no-extra-parens| 禁止不需要的括号 | F | [案例](http://eslint.org/docs/rules/no-extra-parens)|
| no-extra-semi| 禁止多余的分号| R F | [案例](http://eslint.org/docs/rules/no-extra-semi)|
| no-func-assign | 禁止重复的函数声明| R | [案例](http://eslint.org/docs/rules/no-func-assign)|
| no-inner-declarations| 禁止在块语句中使用声明（变量或函数）| R | [案例](http://eslint.org/docs/rules/no-inner-declarations)|
| no-invalid-regexp | 禁止无效的正则| R  | [案例](http://eslint.org/docs/rules/no-invalid-regexp)|
| no-irregular-whitespace| 禁止不统一的空格| R | [案例](http://eslint.org/docs/rules/no-irregular-whitespace)|
| no-obj-calls| 禁止重定义内置全局对象| R | [案例](http://eslint.org/docs/rules/no-obj-calls)|
| no-prototype-builtins | 禁止在对象上直接调用object.prototype方法| | [案例](http://eslint.org/docs/rules/no-prototype-builtins)|
| no-regex-spaces | 禁止在正则表达式字面量中使用多个空格| R F | [案例](http://eslint.org/docs/rules/no-regex-spaces)|
| no-sparse-arrays | 禁止稀疏数组| R | [案例](http://eslint.org/docs/rules/no-sparse-arrays)|
| no-template-curly-in-string | 禁止在模板中使用不同的符号 |  | [案例](http://eslint.org/docs/rules/no-template-curly-in-string)|
| no-unexpected-multiline | 禁止多行表达式 | R | [案例](http://eslint.org/docs/rules/no-unexpected-multiline)|
| no-unreachable | 禁止写无法执行的代码(return,throw,contine,break) | R | [案例](http://eslint.org/docs/rules/no-unreachable)|
| no-unsafe-finally | 禁止在finally中使用return,throw,contine,break | R | [案例](http://eslint.org/docs/rules/no-unsafe-finally)|
| no-unsafe-negation | 禁止在运算符左侧执行关系运算 | R F | [案例](http://eslint.org/docs/rules/no-unsafe-negation)|
| use-isnan | 禁止比较时使用NaN，只能用isNaN() | R | [案例](http://eslint.org/docs/rules/use-isnan)|
| valid-jsdoc | 强制验证jsdoc规则 |  | [案例](http://eslint.org/docs/rules/valid-jsdoc)|
| valid-typeof | 强制使用合法的typeof的值 | R | [案例](http://eslint.org/docs/rules/valid-typeof)|


## 最佳实践
**这些规则是能够帮助你避免一些问题的最好方法**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| accessor-pairs | 强制在对象中使用getter/setter |  | [案例](http://eslint.org/docs/rules/accessor-pairs)|
| array-callback-return | 强制在数组方法的回调中执行return |  | [案例](http://eslint.org/docs/rules/array-callback-return)|
| block-scoped-var | 强制使用它们定义的范围内的变量 |  | [案例](http://eslint.org/docs/rules/array-callback-return)|
| 	class-methods-use-this | 强制该类方法利用 this |  | [案例](http://eslint.org/docs/rules/class-methods-use-this)|
| complexity | 强制设置一个循环的最大值 |  | [案例](http://eslint.org/docs/rules/complexity)|
| consistent-return | 要求return语句要么始终有值要么始终没值 |  | [案例](http://eslint.org/docs/rules/consistent-return)|
| curly | 强制所有控制语句执行统一的括号风格 | F | [案例](http://eslint.org/docs/rules/curly)|
| default-case | switch语句中需要有default值 |  | [案例](http://eslint.org/docs/rules/default-case)|
| dot-location | 强制在点之前和之后执行一致的换行符 |  F| [案例](http://eslint.org/docs/rules/dot-location)|
| dot-notation | 强制使用.符号，避免[] | F | [案例](http://eslint.org/docs/rules/dot-notation)|
| eqeqeq | 使用 === 和 !== | F | [案例](http://eslint.org/docs/rules/eqeqeq)|
| guard-for-in | for in循环要用if语句过滤 |  | [案例](http://eslint.org/docs/rules/guard-for-in)|
| no-alert | 禁止使用alert,confirm,prompt |  | [案例](http://eslint.org/docs/rules/no-alert)|
| no-caller | 禁止使用arguments.caller或 arguments.callee |  | [案例](http://eslint.org/docs/rules/no-caller)|
| no-case-declarations | 禁止在case子句中使用词法声明，一定要用，封装在块中 | R | [案例](http://eslint.org/docs/rules/no-case-declarations)|
| no-div-regex | 禁止在正则表达式开头用除法 |  | [案例](http://eslint.org/docs/rules/no-div-regex)|
| no-else-return | if语句里面有return,后面禁止跟else语句 | F | [案例](http://eslint.org/docs/rules/no-else-return)|
| no-empty-function | 禁止空函数 |  | [案例](http://eslint.org/docs/rules/no-empty-function)|
| no-empty-pattern | 禁止空的解构模式 | R | [案例](http://eslint.org/docs/rules/no-empty-pattern)|
| no-eq-null | 禁止用类型检查运算符和null比较 |  | [案例](http://eslint.org/docs/rules/no-eq-null)|
| no-eval | 禁止使用eval() |  | [案例](http://eslint.org/docs/rules/no-eval)|
| no-extend-native | 禁止扩展native类型 |  | [案例](http://eslint.org/docs/rules/no-extend-native)|
| no-extra-bind | 禁止非必要的函数绑定 | F | [案例](http://eslint.org/docs/rules/no-extra-bind)|
| no-extra-label | 禁止非必要的label | F | [案例](http://eslint.org/docs/rules/no-extra-label)|
| no-fallthrough | 禁止switch穿透 | R | [案例](http://eslint.org/docs/rules/no-fallthrough)|
| no-floating-decimal | 禁止省略浮点数中的0 | F | [案例](http://eslint.org/docs/rules/no-floating-decimal)|
| 	no-global-assign | 禁止对本地对象或只读全局变量重定义 | R | [案例](http://eslint.org/docs/rules/no-global-assign)|
| no-implicit-coercion | 禁止隐式转换 | F | [案例](http://eslint.org/docs/rules/no-implicit-coercion)|
| no-implicit-globals | 禁止在全局范围内声明变量和函数 |  | [案例](http://eslint.org/docs/rules/no-implicit-globals)|
| no-implied-eval | 禁止使用隐式eval |  | [案例](http://eslint.org/docs/rules/no-implied-eval)|
| no-invalid-this | 禁止无效的this，只能用在构造器，类，对象字面量 |  | [案例](http://eslint.org/docs/rules/no-invalid-this)|
| no-extra-label | 禁止非必要的label | F | [案例](http://eslint.org/docs/rules/no-extra-label)|
| no-iterator | 禁止使用__iterator__ 属性 |  | [案例](http://eslint.org/docs/rules/no-iterator)|
| no-labels | 禁止标签声明 |  | [案例](http://eslint.org/docs/rules/no-labels)|
| no-lone-blocks | 禁止非必要的嵌套块 | F | [案例](http://eslint.org/docs/rules/no-lone-blocks)|
| no-loop-func | 禁止在循环中使用函数（如果没有引用外部变量不形成闭包就可以） | | [案例](http://eslint.org/docs/rules/no-loop-func)|
| no-magic-numbers | 禁止魔数字(硬写到代码里的数字常量) | | [案例](http://eslint.org/docs/rules/no-magic-numbers)|
| no-multi-spaces | 禁止多个空格） | F | [案例](http://eslint.org/docs/rules/no-multi-spaces)|
| no-multi-str | 禁止多行字符串(不能用/换行) | | [案例](http://eslint.org/docs/rules/no-multi-str)|
| no-new | 禁止在使用new构造一个实例后不赋值 | | [案例](http://eslint.org/docs/rules/no-new)|
| no-new-func | 禁止使用new Function | | [案例](http://eslint.org/docs/rules/no-new-func)|
| no-new-wrappers | 禁止使用new创建包装实例，new String new Boolean new Number | | [案例](http://eslint.org/docs/rules/no-new-wrappers)|
| no-octal | 禁止使用八进制数字 | R | [案例](http://eslint.org/docs/rules/no-octal)|
| no-octal-escape | 禁止使用八进制转义序列 |  | [案例](http://eslint.org/docs/rules/no-octal-escape)|
| no-param-reassign | 禁止重新定义参数 | | [案例](http://eslint.org/docs/rules/no-param-reassign)|
| no-proto | 禁止使用__proto__ | | [案例](http://eslint.org/docs/rules/no-proto)|
| no-redeclare | 禁止重复声明变量 | R | [案例](http://eslint.org/docs/rules/no-redeclare)|
| 	no-restricted-properties | 禁止在一些特定的对象上的特定属性 | | [案例](http://eslint.org/docs/rules/no-restricted-properties)|
| no-return-assign | return 语句中不能有赋值表达式 | | [案例](http://eslint.org/docs/rules/no-return-assign)|
| no-return-await | 禁止非必要的return await | | [案例](http://eslint.org/docs/rules/no-return-await)|
| no-script-url | 禁止使用javascript:void(0) | R | [案例](http://eslint.org/docs/rules/no-script-url)|
| no-self-assign | 禁止双方完全一致的任务 | R | [案例](http://eslint.org/docs/rules/no-self-assign)|
| no-self-compare | 禁止比较自身 | | [案例](http://eslint.org/docs/rules/no-self-compare)|
| no-sequences | 禁止使用逗号运算符 | | [案例](http://eslint.org/docs/rules/no-sequences)|
| no-throw-literal | 禁止抛出字面量错误 throw "error"; | | [案例](http://eslint.org/docs/rules/no-throw-literal)|
| no-unmodified-loop-condition | 禁止不变的循环条件 | | [案例](http://eslint.org/docs/rules/no-unmodified-loop-condition)|
| no-unused-expressions | 禁止无用的表达式 | | [案例](http://eslint.org/docs/rules/no-unused-expressions)|
| no-unused-labels | 禁止不用的label | R F | [案例](http://eslint.org/docs/rules/no-unused-labels)|
| no-useless-call | 禁止非必要的call和apply |  | [案例](http://eslint.org/docs/rules/no-useless-call)|
| no-useless-concat | 禁止不必要的连接文字或模板文字 |  | [案例](http://eslint.org/docs/rules/no-useless-concat)|
| no-useless-escape | 禁止不必要的转义字符 | R | [案例](http://eslint.org/docs/rules/no-useless-escape)|
| no-void | 禁止使用void | | [案例](http://eslint.org/docs/rules/no-void)|
| no-warning-comments | 禁止有警告备注 |  | [案例](http://eslint.org/docs/rules/no-warning-comments)|
| no-with | 禁止使用with声明 |  | [案例](http://eslint.org/docs/rules/no-with)|
| prefer-promise-reject-errors | 使用error对象作为Promise驳回原因 |  | [案例](http://eslint.org/docs/rules/prefer-promise-reject-errors)|
| radix | parseInt必须指定第二个参数 |  | [案例](http://eslint.org/docs/rules/radix)|
| require-await | 禁止async中无await表达式 |  | [案例](http://eslint.org/docs/rules/require-await)|
| vars-on-top | var必须放在作用域顶部 |  | [案例](http://eslint.org/docs/rules/vars-on-top)|
| wrap-iife | 立即执行函数表达式的小括号风格 | F | [案例](http://eslint.org/docs/rules/wrap-iife)|
| yoda | 禁止尤达条件 | F | [案例](http://eslint.org/docs/rules/yoda)|

## 严格模式
**这些规则是能够帮助你避免一些问题的最好方法**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| strict | 使用严格模式 | F | [案例](http://eslint.org/docs/rules/strict)|

## 变量
**这些规则与变量声明有关**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| init-declarations | 声明时必须赋初值 |  | [案例](http://eslint.org/docs/rules/init-declarations)|
| no-catch-shadow | 禁止catch子句参数与外部作用域变量同名 |  | [案例](http://eslint.org/docs/rules/no-catch-shadow)|
| no-delete-var | 禁止删除变量 | R | [案例](http://eslint.org/docs/rules/no-delete-var)|
| no-label-var | 禁止label名与var声明的变量名相同 |  | [案例](http://eslint.org/docs/rules/no-label-var)|
| no-restricted-globals | 禁止指定的全局变量 |  | [案例](http://eslint.org/docs/rules/no-restricted-globals)|
| no-shadow | 禁止外部作用域中的变量与它所包含的作用域中的变量或参数同名 |  | [案例](http://eslint.org/docs/rules/no-shadow)|
| no-shadow-restricted-names | 严格模式中规定的限制标识符不能作为声明时的变量名使用 |  | [案例](http://eslint.org/docs/rules/no-shadow-restricted-names)|
| no-undef | 不能有未定义的变量，除非在/*global */注释中 | R | [案例](http://eslint.org/docs/rules/no-undef)|
| no-undef-init | 禁止将变量初始化为undefined | F | [案例](http://eslint.org/docs/rules/no-undef-init)|
| no-undefined | 禁止使用undefined作为标识符 |  | [案例](http://eslint.org/docs/rules/no-undefined)|
| no-unused-vars | 禁止未使用的变量 | R | [案例](http://eslint.org/docs/rules/no-unused-vars)|
| no-use-before-define | 禁止在定义之前使用变量 |  | [案例](http://eslint.org/docs/rules/no-use-before-define)|


## Node.js and CommonJS
**这些规则与在Node.js中运行的代码相关联，或与使用CommonJS的浏览器相关：**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| callback-return | 避免多次调用回调 |  | [案例](http://eslint.org/docs/rules/callback-return)|
| global-require | 需要将require()调用放置在模块顶部 |  | [案例](http://eslint.org/docs/rules/global-require)|
| handle-callback-err | 在回调中需要错误处理 | | [案例](http://eslint.org/docs/rules/handle-callback-err)|
| no-buffer-constructor | 禁止使用Buffer()构造函数 | | [案例](http://eslint.org/docs/rules/no-buffer-constructor)|
| no-mixed-requires | 不允许调用与常规变量声明混合 |  | [案例](http://eslint.org/docs/rules/no-mixed-requires)|
| no-new-require | 禁止使用new require | | [案例](http://eslint.org/docs/rules/no-new-require)|
| no-path-concat | 禁止使用__dirname和__filename连接字符串 | | [案例](http://eslint.org/docs/rules/no-path-concat)|
| no-process-env | 禁止使用process.env |  | [案例](http://eslint.org/docs/rules/no-process-env)|
| no-process-exit | 禁止使用process.exit() | | [案例](http://eslint.org/docs/rules/no-process-exit)|
| no-process-env | 禁止使用process.env | | [案例](http://eslint.org/docs/rules/no-process-env)|
| no-restricted-modules | 禁止通过require加载指定的模块，用了会报错 | | [案例](http://eslint.org/docs/rules/no-restricted-modules)|
| no-sync | nodejs 禁止同步方法 | | [案例](http://eslint.org/docs/rules/no-sync)|

## 代码风格
**这些规则主要是关于代码风格的，主观因素较强**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| array-bracket-newline | 强制在数组的头尾括号之前执行换行 | F | [案例](http://eslint.org/docs/rules/array-bracket-newline)|
| array-bracket-spacing | 强制在数组括号内执行一致的间隔 | F | [案例](http://eslint.org/docs/rules/array-bracket-spacing)|
| array-element-newline | 强制在每个数组元素之后执行换行符 | F | [案例](http://eslint.org/docs/rules/array-element-newline)|
| block-spacing | 强制在单行块内实施一致的间距 | F | [案例](http://eslint.org/docs/rules/block-spacing)|
| brace-style | 强制块的括号风格统一 |  | [案例](http://eslint.org/docs/rules/brace-style)|
| camelcase | 强制驼峰命名 |  | [案例](http://eslint.org/docs/rules/camelcase)|
| capitalized-comments | 强制或禁止注释的第一个字母大写 | F | [案例](http://eslint.org/docs/rules/capitalized-comments)|
| comma-dangle | 逗号风格，换行时在行首还是行尾 | F | [案例](http://eslint.org/docs/rules/comma-dangle)|
| comma-spacing | 强制逗号前后的空格 | F | [案例](http://eslint.org/docs/rules/comma-spacing)|
| comma-style | 块的括号风格统一 |  | [案例](http://eslint.org/docs/rules/brace-style)|
| computed-property-spacing | 强制在计算属性括号内一致的间距 | F | [案例](http://eslint.org/docs/rules/computed-property-spacing)|
| consistent-this | 强制规定this别名 |  | [案例](http://eslint.org/docs/rules/consistent-this)|
| eol-last | 强制添加或禁止在文件末尾的换行 | F | [案例](http://eslint.org/docs/rules/eol-last)|
| func-call-spacing | 强制添加或禁止在函数标识符与其调用之间的间距 | F | [案例](http://eslint.org/docs/rules/func-call-spacing)|
| func-name-matching | 要求函数名称与其分配到的变量或属性的名称相匹配 | | [案例](http://eslint.org/docs/rules/func-name-matching)|
| func-names | 强制添加或禁止命名函数表达式 | | [案例](http://eslint.org/docs/rules/func-names)|
| func-style | 强制统一使用函数声明或表达式 |  | [案例](http://eslint.org/docs/rules/func-style)|
| id-blacklist | 禁止指定的标识符 | | [案例](http://eslint.org/docs/rules/id-blacklist)|
| id-length | 强制标识符长度最小和最大值 | | [案例](http://eslint.org/docs/rules/id-length)|
| id-match | 要求标识符与指定的正则表达式匹配 | | [案例](http://eslint.org/docs/rules/id-match)|
| indent | 强制统一的缩进 | F | [案例](http://eslint.org/docs/rules/indent)|
| jsx-quotes | 强制在JSX属性中一致地使用双引号或单引号 | F | [案例](http://eslint.org/docs/rules/jsx-quotes)|
| key-spacing | 强制在对象文字属性中强制实现键和值之间的一致间距 | F | [案例](http://eslint.org/docs/rules/key-spacing)|
| keyword-spacing | 强制在关键字前后执行一致的间距 | F | [案例](http://eslint.org/docs/rules/keyword-spacing)|
| line-comment-position | 强制规定注释的位置 | | [案例](http://eslint.org/docs/rules/line-comment-position)|
| linebreak-style | 强制换行风格 | F | [案例](http://eslint.org/docs/rules/linebreak-style)|
| lines-around-comment | 强制注释前后空行 | F | [案例](http://eslint.org/docs/rules/lines-around-comment)|
| max-depth | 强制嵌套的最大深度 | | [案例](http://eslint.org/docs/rules/max-depth)|
| max-len | 强制字符串最大长度 | | [案例](http://eslint.org/docs/rules/max-len)|
| max-lines | 强制每个文件的最大行数 | | [案例](http://eslint.org/docs/rules/max-lines)|
| max-nested-callbacks | 强制最大深度，回调可以嵌套 | | [案例](http://eslint.org/docs/rules/max-nested-callbacks)|
| max-params | 强制函数最大参数值 | | [案例](http://eslint.org/docs/rules/max-params)|
| max-statements | 强制在功能块中允许的最大数量的语句 | | [案例](http://eslint.org/docs/rules/max-statements)|
| max-statements-per-line | 强制每行允许的最大数量的语句 | | [案例](http://eslint.org/docs/rules/max-statements-per-line)|
| multiline-ternary | 强制三元表达式换行 | | [案例](http://eslint.org/docs/rules/multiline-ternary)|
| new-cap | 要求构造函数名称以大写字母开头 | | [案例](http://eslint.org/docs/rules/new-cap)|
| new-parens | new时，没有入参的话必须加小括号 | F | [案例](http://eslint.org/docs/rules/new-parens)|
| newline-per-chained-call | 链式调用后每次都需要换行符 | | [案例](http://eslint.org/docs/rules/newline-per-chained-call)|
| no-array-constructor | 禁止使用数组构造器 | | [案例](http://eslint.org/docs/rules/no-array-constructor)|
| no-bitwise | 禁止使用按位运算符 | | [案例](http://eslint.org/docs/rules/no-bitwise)|
| no-continue | 禁止使用continue | | [案例](http://eslint.org/docs/rules/no-continue)|
| no-inline-comments | 禁止代码后的内联注释 | | [案例](http://eslint.org/docs/rules/no-inline-comments)|
| no-lonely-if | 禁止else语句内只有if语句 | F | [案例](http://eslint.org/docs/rules/no-lonely-if)|
| no-mixed-operators | 禁止混合二进制运算符 | | [案例](http://eslint.org/docs/rules/no-mixed-operators)|
| no-mixed-spaces-and-tabs | 禁止混合空格和制表符缩进 | R | [案例](http://eslint.org/docs/rules/no-mixed-spaces-and-tabs)|
| no-multi-assign | 禁止使用链式赋值表达式 | | [案例](http://eslint.org/docs/rules/no-multi-assign)|
| no-multi-assign | 禁止使用链式赋值表达式 | | [案例](http://eslint.org/docs/rules/no-multi-assign)|
| no-multiple-empty-lines | 禁止多行空格 | F | [案例](http://eslint.org/docs/rules/no-multiple-empty-lines)|
| no-negated-condition | 禁止否定条件 | | [案例](http://eslint.org/docs/rules/no-negated-condition)|
| no-nested-ternary | 禁止嵌套的三元表达式 | | [案例](http://eslint.org/docs/rules/no-nested-ternary)|
| no-new-object | 禁止使用new Object() | | [案例](http://eslint.org/docs/rules/no-new-object)|
| no-plusplus | 禁止使用一元运算符++和-- | | [案例](http://eslint.org/docs/rules/no-plusplus)|
| no-restricted-syntax | 禁止指定语法 | | [案例](http://eslint.org/docs/rules/no-restricted-syntax)|
| no-tabs | 禁止所有tabs | | [案例](http://eslint.org/docs/rules/no-tabs)|
| no-ternary | 禁止使用三元表达式 | | [案例](http://eslint.org/docs/rules/no-ternary)|
| no-trailing-spaces | 禁止在行尾有空格 | F | [案例](http://eslint.org/docs/rules/no-trailing-spaces)|
| no-underscore-dangle | 禁止在标识符中用下划线 | | [案例](http://eslint.org/docs/rules/no-underscore-dangle)|
| no-unneeded-ternary | 在简单判断中，禁止使用三元表达式 | F | [案例](http://eslint.org/docs/rules/no-unneeded-ternary)|
| no-whitespace-before-property | 禁止在属性前加空白 | F | [案例](http://eslint.org/docs/rules/no-whitespace-before-property)|
| nonblock-statement-body-position | 强制单行声明的位置 | F | [案例](http://eslint.org/docs/rules/nonblock-statement-body-position)|
| object-curly-newline | 强制在大括号内执行一致的换行符 | F | [案例](http://eslint.org/docs/rules/object-curly-newline)|
| object-curly-spacing | 强制在大括号内统一的空格 | F | [案例](http://eslint.org/docs/rules/object-curly-spacing)|
| object-property-newline | 强制将对象属性放在不同的行上 | F | [案例](http://eslint.org/docs/rules/object-property-newline)|
| one-var | 强制变量在函数中一起声明或单独声明 | | [案例](http://eslint.org/docs/rules/one-var)|
| one-var-declaration-per-line | 强制单行声明的位置 | F| [案例](http://eslint.org/docs/rules/one-var-declaration-per-line)|
| operator-assignment | 在可能的情况下强制或禁止赋值运算符的简写 |F | [案例](http://eslint.org/docs/rules/operator-assignment)|
| operator-linebreak | 强制连接符统一的换行 | F | [案例](http://eslint.org/docs/rules/operator-linebreak)|
| padded-blocks | 强制或禁止在块内填充空格 |F | [案例](http://eslint.org/docs/rules/padded-blocks)|
| padding-line-between-statements | 强制或禁止在语句之间填充空格 | F | [案例](http://eslint.org/docs/rules/padding-line-between-statements)|
| quote-props | 强制对象字面量中的属性名双引号 | F | [案例](http://eslint.org/docs/rules/quote-props)|
| quotes | 强制统一使用反引号，双引号或单引号 | F | [案例](http://eslint.org/docs/rules/quotes)|
| require-jsdoc | 需要JSDoc 注释 |  | [案例](http://eslint.org/docs/rules/require-jsdoc)|
| semi | 强制语句分号结尾 | F | [案例](http://eslint.org/docs/rules/semi)|
| semi-spacing | 强制分号前后空格 | F | [案例](http://eslint.org/docs/rules/semi-spacing)|
| semi-style | 强制分号位置 | F | [案例](http://eslint.org/docs/rules/semi-style)|
| sort-keys | 要求对象键进行排序 |  | [案例](http://eslint.org/docs/rules/sort-keys)|
| sort-vars | 要求同一声明块中的变量进行排序 | | [案例](http://eslint.org/docs/rules/sort-vars)|
| space-before-blocks | 强制块区域内统一的间隔 | F | [案例](http://eslint.org/docs/rules/space-before-blocks)|
| space-before-function-paren | 强制在Function括号之前执行统一的间距 | F | [案例](http://eslint.org/docs/rules/space-before-function-paren)|
| space-in-parens | 强制在括号内用统一的间距 | F | [案例](http://eslint.org/docs/rules/space-in-parens)|
| space-infix-ops | 中缀操作符周围需要有空格 | F | [案例](http://eslint.org/docs/rules/space-infix-ops)|
| space-unary-ops | 强制在一元操作员之前或之后有统一的间距 | F | [案例](http://eslint.org/docs/rules/space-unary-ops)|
| spaced-comment | 强制在注释中的//或/ *之后用统一的间距 | F | [案例](http://eslint.org/docs/rules/spaced-comment)|
| switch-colon-spacing | 在switch语句的冒号附近加间隔 | F | [案例](http://eslint.org/docs/rules/switch-colon-spacing)|
| template-tag-spacing | 强制或禁止模板标签与其文字之间的间距 | F | [案例](http://eslint.org/docs/rules/template-tag-spacing)|
| unicode-bom | 强制或禁止Unicode字节顺序标记（BOM） | F | [案例](http://eslint.org/docs/rules/unicode-bom)|
| wrap-regex | 正则表达式字面量用小括号包起来 | F | [案例](http://eslint.org/docs/rules/wrap-regex)|

## ECMAScript 6
**这些规则涉及ES6(ES2015)：**

| 参数 | 描述 | 备注 | 例子 |
| --- | --- | --- | --- |
| arrow-body-style | 允许箭头函数 | F | [案例](http://eslint.org/docs/rules/arrow-body-style)|
| arrow-parens | 箭头函数用小括号括起来 | F | [案例](http://eslint.org/docs/rules/arrow-parens)|
| arrow-spacing | 箭头的前/后括号空格 | F | [案例](http://eslint.org/docs/rules/arrow-spacing)|
| constructor-super | 在构造函数中需要super()调用 | R | [案例](http://eslint.org/docs/rules/constructor-super)|
| generator-star-spacing | 在生成器函数中的*操作符周围保持统一的间距 | F | [案例](http://eslint.org/docs/rules/generator-star-spacing)|
| no-class-assign | 禁止重新分配Class成员 | R | [案例](http://eslint.org/docs/rules/no-class-assign)|
| no-confusing-arrow | 在可能会与对比运算符混淆的地方禁止箭头功能 | F | [案例](http://eslint.org/docs/rules/no-confusing-arrow)|
| no-const-assign | 禁止重新分配常量变量 | R | [案例](http://eslint.org/docs/rules/no-const-assign)|
| no-dupe-class-members | 禁止重复的class成员 | R | [案例](http://eslint.org/docs/rules/no-dupe-class-members)|
| no-duplicate-imports | 禁止重复模块导入 |  | [案例](http://eslint.org/docs/rules/no-duplicate-imports)|
| no-new-symbol | 禁止在Symbol对象用new操作符 | R | [案例](http://eslint.org/docs/rules/no-new-symbol)|
| no-restricted-imports | 通过import加载时禁止指定的模块 | | [案例](http://eslint.org/docs/rules/no-restricted-imports)|
| no-this-before-super | 在构造函数中调用super()之前禁止用this | R | [案例](http://eslint.org/docs/rules/no-this-before-super)|
| no-useless-computed-key | 禁止对象文字中不必要的计算属性键 | F | [案例](http://eslint.org/docs/rules/no-useless-computed-key)|
| no-useless-constructor | 禁止不必要的构造函数 |  | [案例](http://eslint.org/docs/rules/no-useless-constructor)|
| no-useless-rename | 禁止不必要的重命名 | F | [案例](http://eslint.org/docs/rules/no-useless-rename)|
| no-var | 用let,const代替var | F | [案例](http://eslint.org/docs/rules/no-var)|
| object-shorthand | 强制或禁止对象文字的方法和属性简写语法 | F | [案例](http://eslint.org/docs/rules/object-shorthand)|
| prefer-arrow-callback | 需要箭头功能作为回调 | F | [案例](http://eslint.org/docs/rules/prefer-arrow-callback)|
| prefer-const | 永不改变的变量用const | F | [案例](http://eslint.org/docs/rules/prefer-const)|
| prefer-destructuring | 需要从数组和/或对象中进行解构 |  | [案例](http://eslint.org/docs/rules/prefer-destructuring)|
| prefer-numeric-literals | 禁止parseInt()支持二进制，八进制和十六进制文字 | F | [案例](http://eslint.org/docs/rules/prefer-numeric-literals)|
| prefer-rest-params | 需要reset参数 |  | [案例](http://eslint.org/docs/rules/prefer-rest-params)|
| prefer-spread | 需要...操作符替代.apply() | F | [案例](http://eslint.org/docs/rules/prefer-spread)|
| prefer-template | 需要模板语法而不是字符串连接 | F | [案例](http://eslint.org/docs/rules/prefer-template)|
| require-yield | 生成器函数必须有yield | R | [案例](http://eslint.org/docs/rules/require-yield)|
| rest-spread-spacing | 强制rest和展开运算符的间距 | F | [案例](http://eslint.org/docs/rules/rest-spread-spacing)|
| sort-imports | 强制在模块中执行排序的导入声明 | F | [案例](http://eslint.org/docs/rules/sort-imports)|
| symbol-description | 需要Symbol说明 | | [案例](http://eslint.org/docs/rules/symbol-description)|
| template-curly-spacing | 强制或禁止模板字符串的嵌入式表达式周围有空格 | F | [案例](http://eslint.org/docs/rules/template-curly-spacing)|
| yield-star-spacing | 强制或禁止的yield *中的间距 | F | [案例](http://eslint.org/docs/rules/yield-star-spacing)|

## 弃用
**这些规则已经被新的规则替换，懒得写了**

[弃用列表](http://eslint.org/docs/rules/#deprecated)


## 删除
**旧版本ESLint的这些规则已被更新的规则所取代，懒得写了**

[删除列表](http://eslint.org/docs/rules/#removed)


