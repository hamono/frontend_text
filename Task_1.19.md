## 用github pages部署静态网页
1. 在`package.json`添加：
    ```
    "homepage": "http://GH.github.io"  
    ```
    其他两种方式请参考#其他还有两种方法请参考[link](https://create-react-app.dev/docs/deployment/#step-1-add-homepage-to-packagejson)
2. 安装`gh-pages`：
    ```
    yarn add gh-pages
    ```
    需要注意的是，这里的安装方法应该与项目的包管理器一致
3. 添加一些东西在`package.json`文件里：
    ```
      "scripts": {
     + "predeploy": "npm run build",
     + "deploy": "gh-pages -d build",
      "start": "react-scripts start",
      "build": "react-scripts build",
    ```
    注意值添加带`+`的命令
4. 在终端运行`npm run deploy`,将会新建一个`gh-pages`的分支，将`build`之后的文件放在这个分支下面。至此，一个静态页面就部署成功了。
### 关于官方文档
官方文档的
  ```
  "scripts": {
     "predeploy": "npm run build",
   - "deploy": "gh-pages -d build",
   + "deploy": "gh-pages -b master -d build",
  ```
请谨慎使用，在用之前务必分清项目页面和用户界面。否则将会非常危险。（原来的`master`分支将被`gh-pages`覆盖，项目文件将不复存在）
## 关联子域名
1. 购买相应的域名
2. 进行域名备案
3. 添加域名解析

    方法一：

    记录类型：A，记录值为`GH.github.io`的IP,用`ping`获取其IP地址:
    ```
    ping https://GH.github.io
    ```

    方法二：

    记录类型：CNAME，记录值为`GH.github.io`

    方法三：

    不推荐使用，记录类型：TEXT
    #### 注：推荐使用方法二
4. 在github仓库的`setting`的`github pages`中填写相应域名
5. 给相应域名安装SSL证书，打开`github pages`中`HTTPS`的选项(选做)
### 文章中的GH表示自己的github名称
