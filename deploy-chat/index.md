# Railway部署ChatGPT

## 简介
- 本文主要介绍Railway免费部署一个网页版的ChatGPT
- 可用OpenAI官方提供的API keys
- 可用access_token
## 准备条件
- API keys [点击获取](https://platform.openai.com/account/api-keys)
  - 点击 Create new secret key
  - 复制保存
- access_token [点击获取](https://chat.openai.com/api/auth/session)
  - 获取前提是需要 [登录ChatGPT](https://chat.openai.com)
  - 登录后再点击获取
- Github账号 [点击注册](https://github.com/signup)
- Railway账号 [点击注册](https://vercel.com/signup)
  - 需要Github账号注册满一年
## 开始
- 先Fork一下[项目](https://github.com/Chanzhaoyu/chatgpt-web)
- 等待创建完成后往下滑动找到Deploy To Railway,点击部署：
{{<figure src="/images/gpt-deploy-web/one.png">}}
### 部署配置
- 填写API keys 或者 access_token
  - 如果两个都填写了则会优先使用 API keys
- 如果想跟[官网](https://chat.openai.com)的ChatGPT一样就只填写access_token
{{<figure src="/images/gpt-deploy-web/two.png" width="60%">}}
- 填写完成之后点击Deploy部署
### 等待部署完成
- 同时，你可以取创建域名
- 点击Setting 下滑找到Domains
  - 注意：这边是已经创建过了，所以不可再次创建
{{<figure src="/images/gpt-deploy-web/three.png" width="60%">}}
### 点击给定的域名访问
- 部署成功结果如下
{{<figure src="/images/gpt-deploy-web/four.png" width="80%">}}
## 问题解决
遇到如下错误：
undefined
[fetch failed]
尝试更换调用的Web API代理地址 <br>
如上教程没有填写该变量，所以需要添加变量如下：
```markdown
# 变量名
API_REVERSE_PROXY
# 变量
https://api.pawan.krd/backend-api/conversation
```
{{<figure src="/images/gpt-deploy-web/varialbles-setting-one.png" width="60%">}}
- 更改完成之后直接到项目管理面板重新部署，Redeploy
## 说明
- 以上内容均以学习参考之用，请勿滥用。
- 感谢：[Chanzhaoyu](https://github.com/Chanzhaoyu/chatgpt-web)
