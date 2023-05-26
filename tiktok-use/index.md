# TikTok免拔卡使用


## - 开始之前
- 支持: iOS
- 自备 Shadowrocket
- 下载：在 美区/日区/台区 App Store 搜索 TikTok 并下载 （港区已停止运营）
## 特别注意
1. 为什么要先卸载 TikTok，TikTok 会在第一次使用时触发限制，并导致之后无法通过 MiMt 解密。
2. 所以先配置好规则之后，然后在下载 TikTok，减少重定向的请求次数，降低风险，延长规则的寿命。
3. 为什么配置好之后还是无法使用，请检查软件的证书有没有安装，信任。 
4. 或者是 Https 解密（MiMt）与重写（Rewrite）有没有开启。
5. 或者是软件是不是盗版，比如用共享 ID 下载的，有设备限制，是无法使用重写脚本功能的。

## **操作步骤**

1、打开`Shadowrocket`  

2、开启**HTTPS解密**并**安装、信任**Shadowrocket证书：
    * `配置` → 你使用的配置文件后的`i` → `HTTPS解密` → 开启`HTTPS解密` → `生成新的CA证书` → 允许 → 返回点击`安装证书`，并点击`允许` → 前往手机的`设置`，不是Shadowrocket的 → 看到`已下载描述文件` → `安装` → 输入手机的解锁密码 → `安装` → `安装` → 前往手机的`设置` → `通用` → `关于本机` → `证书信任设置` → 找到`Shadowrocket…`点绿它以信任该根证书 → `继续`  

3、点击`配置` → `模块` → 右上角加号，添加想看国家的对应模块。

### 如下对应每个地区不同的配置
1. 打开链接 → 复制所有内容 → 粘贴到配置
**日本**
```
https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Shadowrocket/TiKTok-JP.conf
```

**台湾**
```
https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Shadowrocket/TiKTok-TW.conf
```

**韩国**
```
https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Shadowrocket/TiKTok-KR.conf
```

**美国**
```
https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Shadowrocket/TiKTok-US.conf
```

4、添加以下`分流`，点击`配置` → 你使用的配置后的`i` → `规则` → 右上角加号 → `类型` → 选择`RULE-SET` → 策略 → 选择`PROXY`或者其他你想使用的策略（一般是对应地区的代理服务器节点） → 规则集URL文本框内填写

```
https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Shadowrocket/TikTok.list
```

### 抖音無法觀看 </a>

在hostname中加上以下兩條
```
-*snssdk.com, -*amemv.com
```

---
### 抖音IP代理 </a>

订阅分流

```
https://raw.githubusercontent.com/Semporia/Quantumult-X/master/Filter/DouYin.list
```
