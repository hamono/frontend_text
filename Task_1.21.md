### 继续 github pages 自动部署

错误提交 13 次，暂决定放弃该任务

### 问题

#### 问题一

问题描述：运行错误代码，导致 github 项目文件丢失
  
 Showing 99 changed files with 6 additions and 10,955 deletions.

解决方案：git 回滚

具体操作：

```
git reflog  #查询历史版本
git reset --hard abcd  #abcd为版本号
git push -f  #强制推送
git pull  #重新合并
```

完成
