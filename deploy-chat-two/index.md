# Vercel部署ChatGPT

## 简介
- 本文主要介绍Vercel免费部署一个网页版的ChatGPT
## 准备条件
- API keys [点击获取](https://platform.openai.com/account/api-keys)
  - 点击 Create new secret key
  - 复制保存
- Github账号 [点击注册](https://github.com/signup)
- Vercel账号（注册需要手机验证）[点击注册](https://vercel.com/signup)

## 开始
- 先Fork一下[项目](https://github.com/ddiu8081/chatgpt-demo)
  - 也可以clone到本地自己修改（可选）
- 登录[Vercel](https://vercel.com)
  - 原作者使用的部署平台是[Netlify](https://app.netlify.com/)
  - 如不用Vercel可以按照原作者项目文档说明进行部署

### 创建项目
{{<figure src="/images/gpt-deploy/one.png">}}
### 点击import刚才Fork的项目
{{<figure src="/images/gpt-deploy/two.png">}}
### 配置环境变量
{{<figure src="/images/gpt-deploy/three.png">}}
### 等待部署完成，点击链接访问
{{<figure src="/images/gpt-deploy/four.png">}}
## 部署成功后页面
- 以下页面经过了修改，原始页面请看原作者文档
{{<figure src="/images/gpt-deploy/gpt.png">}}

### 环境变量配置说明
|变量|说明|默认值|
| ----  |  ----  |  ----   |
|OPENAI_API_KEY	|您的 OpenAI API 密钥。 （必填）|null
|HTTPS_PROXY	|为 OpenAI API 提供代理。例如http://127.0.0.1:7890	|null
|OPENAI_API_BASE_URL	|OpenAI API 的自定义基本 url。	|https://api.openai.com
|HEAD_SCRIPTS	|</head>在页面之前注入分析或其他脚本	|null
|SECRET_KEY	|项目的秘密字符串。用于为 API 调用生成签名	null
|SITE_PASSWORD	|为站点设置密码。如果未设置，网站将公开	|null
|OPENAI_API_MODEL	|要使用的模型的 ID。列出型号	|gpt-3.5-turbo

## 说明
- 以上内容均以学习参考之用，请勿滥用。
- 感谢：[ddiu8081](https://github.com/ddiu8081/chatgpt-demo)

