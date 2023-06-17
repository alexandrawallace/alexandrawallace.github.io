# GitHub上传大文件

## 前言
*** GitHub ***托管代码提供许多便利，有时候需要上传大文件，会被提示超过100M无法上传的情况，这时候需要用到git-lfs来帮助我们上传大文件
## 下载git-lfs
`https://github.com/git-lfs/git-lfs`
## 操作步骤
如下忽略分支创建，git文件创建等等基础操作
### 一、生成.gitattributes文件
```
# filename是需要上传文件的文件名
git lfs track "filename"
```
### 二、上传.gitattributes
```
git add .gitattributes
git commit -m "submit message"
git push -u origin main
```
### 三、上传大文件
```
git add filename
git commit -m "update message"
git push -u origin main
```
### 四、等待文件上传成功即可
## 问题
- 通过git-lfs上传文件并不是无限制的，GitHub自带有空间限制
- 查看
    - 登录GitHub -→ 点击头像 -→ Setting -→ Billing
- 上传失败
    - 看具体报错信息
