# 多人开发项目-代码提交流程

提交时将换行符改为`LF`格式

``` bash
git config --global core.autocrlf input
```


主分支禁止直接提交

分支名以具体开发功能命名

1. 新建分支
2. 开发分配给自己的功能
3. 完成功能后合并主分支代码并解决冲突
4. 提交代码合并，通知项目管理员，进行代码审计
5. 审计通过则合并分支，不通过则打回修改并重复上述流程


