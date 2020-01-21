## github pages自动更新
#### 使用Travis IC
1. 进入其官网：https://travis-ci.org/（免费版）https://travis-ci.ocom/（付费版）
2. 登录自己的github，并为相应的仓库添加服务
3. click`setting`，打开左边两个按钮
4. 新开github网页，生成密钥
5. 将新的密钥填入setting的相应位置
#### 以上步骤参考百度或其他文章可完成
6. 添加`.travis.yml`文件
7. 配置`.travis.yml`文件：
    ```
        # os : windows
        language: node_js # 构建所需的语言环境
        node_js:
          - "v10.16.3"
        branches:
          only:
          - master    # 构建的分支
        cache:
          directories:
          - node_modules # 依赖缓存的目录
        before_install:
        - export TZ='Asia/Beijing'  # 设置时区
        install:
        - npm install -g yarn # 安装编译工具
        - yarn install   # 安装依赖项
        script:
        - yarn build
        deploy:
          provider: pages
          skip-cleanup: true
          github-token: $bilibili # github 上的token环境变量
          local-dir: ./build/ 
          keep_history : true
          target-branch: gh-pages
          verbose: true
          on:
            branch: master
    ```
### 问题
#### 问题一：`can not find 'glashThis'`

问题分析：包管理器安装错误

解决方案：
    ```
    yarn install  #安装相应的包管理器，例:npm/cnpm
    ```

#### 问题二：`failed to deploy`

问题分析：原因位置

解决方案：暂未解决

#### 问题三：其他
### Task失败
1. 初步认为该Task的解决方案错误
2. 暂未完成