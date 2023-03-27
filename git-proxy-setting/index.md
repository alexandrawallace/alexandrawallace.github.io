# Git代理设置

## 简介
- 在大陆进入[GitHub](https://github.com)难免会出现网络问题
<br>所以大多数人使用GitHub都会进行科学上网
- 在使用Git上传代码到GitHub时，又难免会因为网络而上传失败
<br>虽然开启了科学上网，但是Git还是无法连接上科学网络
<br>进而需要对Git进行proxy配置
## 详细操作
### 设置http/https代理
- 打开Git，进行如下设置
```shell
# http代理
git config --global http.proxy "http://127.0.0.1:8888"
# https代理
git config --global https.proxy "https://127.0.0.1:8888"
```
### 设置socks5代理
- 打开Git，进行如下设置
```shell
# http代理
git config --global http.proxy 'socks5://127.0.0.1:8888'
# https代理
git config --global https.proxy 'socks5://127.0.0.1:8888'
```
- 如果只为当前提交项目设置代理，去掉 "--global" 即可。
## 关闭全局代理
```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```
- 同样的，卸载当前项目的代理配置，也是直接去掉"--global"即可
## 说明
- 如有问题请留言
