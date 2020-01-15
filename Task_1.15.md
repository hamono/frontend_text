| 名称 | 含义 |
|:--:|:--|
|.gitignore|我们做的每个Git项目中都需要一个“.gitignore”文件，这个文件的作用就是告诉Git哪些文件不需要添加到版本管理中。比如我们项目中的包它占的内存很大，一般我们用Git管理的时候是不需要添加的
|.npmrc|包含nmp的配置信息|
|package.json|项目的描述性文件，[package.json详解](https://www.cnblogs.com/paris-test/p/9760308.html)
|yarn.lock|官方解释：1. 由Yarn管理 您的yarn.lock文件是自动生成的，也完全Yarn来处理。当你使用Yarn CLI添加/升级/删除 依赖项的时，它将自动更新到您的yarn.lock文件。不要直接编辑这个文件，因为很容易破坏某些东西。 2.仅限当前包 在安装期间，Yarn将仅使用顶级yarn.lock文件，并将忽略依赖项中存在的任何yarn.lock文件。顶级yarn.lock文件包含Yarn需要锁定整个依赖关系树中所有包的版本的所有内容。自己理解：此文件会锁定你安装的每个依赖项的版本，这可以确保你不会意外获得不良依赖；
## VScode中ts环境的配置
1. 在命令行中切到目标目录下
2. 运行一下命令
```
tsc -init
```
3. 在改目录下打开VScode，打开生成的`tsconfig.json`文件，以下为常用的配置：
```
    {
      "compilerOptions": {
        "target": "es5",//编译为何种规范，一般设置为 ES5 或者 ES2016/2017
        "noImplicitAny": false,
        "module": "amd",
        "removeComments": false,
        "sourceMap": false,
        "outDir": "js"//你要生成js的目录
      }
    }
```
## TSLent
### TSLint是typescript格式验证工具
1. 安装

这里采用全局安装(这里使用`cnmp`)

```
cnmp -install -g tslent
```
2. 生成配置文件
```
tslent -init
```
3. 配置`tslent.json`

      [详细配置信息](https://blog.csdn.net/zw52yany/article/details/78688837)