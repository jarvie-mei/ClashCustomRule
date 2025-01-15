# 打造一个属于自己的clash分流配置

- 仅保证支持 clash 内核软件 (clashx, openclash, clash for windows 等等...)
- 需要使用订阅转换服务，(我用的 https://url.v1.mk/ ，理论上有「远程配置」或「自定义配置功能」的订阅转换服务都可以，有能力也可以自建 https://github.com/tindy2013/subconverter )，这里都订阅转换服务的安全性不做保证，自行判断。

## 太长不看
> 如果不想了解什么规则，只想快点用上，可以按照这个步骤生成转换的订阅连接:

## 写在前面
鉴于每人的需求不同，建议 fork 本仓库，将以下规则链接你的仓库的链接，以便灵活改动

[**推荐方案二!!**](#方案二)

### 方案一：

1. 直接复制[配置总规则](#配置总规则)从`[custom]`开始到方框末尾也就是`luck`的位置
2. 打开 https://sub.v1.mk/ 
3. 在第一个框填入你机场的订阅连接
4. 点击底部`[上传自定义配置]`，将第一步复制的内容粘贴进去
5. 其他不用动，点击生成订阅链接
6. 随后将生成的订阅链接添加到 clash 软件的订阅配置
7. 更新完订阅后，你可以在 clash 面板自由的选择 DisneyPlus 和 Netflix 需要走哪个节点。

步骤 4 如下图位置
![](custom_config.png)

由于一般订阅转换服务如果配置自定义的分流规则，一般只保存三个月，所以有方案二。
### 方案二
1. 在 Github 新建一个属于自己的仓库(如: MyClashRule)(具体注册账号，新建仓库就不赘述了)
2. 在 MyClashRule 下新建一个文件（如本仓库的[share_remote_config](share_remote_config)），不熟悉 Github 的在仓库首页找到 「Add file」 按钮，在编辑框粘贴进「方案一」步骤 1 的内容，点击下方 commit changs 按钮
3. 完成步骤 2 后会跳转到建好的文件界面，右上角找到「Raw」点击跳转到文件下载链接，浏览器地址栏复制该链接
4. 在订阅转换网站找到「远程配置」，粘贴步骤 3 复制的链接，然后在下拉框选择该链接的选项。

后续步骤如方案一

步骤 4 如下图位置
![](custom_remote_config.png)

## 策略组分组效果
![](https://raw.githubusercontent.com/chinnsenn/BlogFigureBed/master/blogimg/021fade30e0d64eec424492ac4a0970f.png)

为多个流媒体平台建了策略组，并建了不同地区的手动选择策略组(香港，台湾，日本，美国等)，当流媒体选择具体地区时，再去具体地区的策略分组选择尝试具体节点

以下配置是我从 [ACL_自动测速](https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/config/ACL4SSR_Online_Full_AdblockPlus.ini)拷贝而来，并且根据自己需求做了大量的改动
> 想要根据自己需求配置策略组或节点分组可以继续往下拉

### 配置总规则
```
[custom]
;不要随意改变关键字，否则会导致出错
;acl4SSR规则

;去广告：支持
;自动测速：支持
;微软分流：支持
;苹果分流：支持
;增强中国IP段：支持
;增强国外GFW：支持

;设置规则标志位
;有个小技巧，下列不同列表可能会有重复规则，可以将想要命中的规则尽量提前
ruleset=🚀 节点选择,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/proxies.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/direct.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/LocalAreaNetwork.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/UnBan.list
ruleset=🛑 广告拦截,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanAD.list
ruleset=🍃 应用净化,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanProgramAD.list
ruleset=🆎 AdBlock,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanEasyList.list
ruleset=🆎 AdBlock,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanEasyListChina.list
ruleset=🆎 AdBlock,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/ad.list
ruleset=🛡️ 隐私防护,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/BanEasyPrivacy.list
ruleset=📢 谷歌FCM,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/GoogleFCM.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/GoogleCN.list
ruleset=Ⓜ️ 微软云盘,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/OneDrive.list
ruleset=Ⓜ️ 微软服务,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Microsoft.list
ruleset=🍎 苹果服务,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Apple.list
ruleset=📲 Telegram,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Telegram.list
ruleset=🎮 游戏平台,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Epic.list
ruleset=🎮 游戏平台,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Sony.list
ruleset=🎮 游戏平台,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Steam.list
ruleset=🎮 Nintendo,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/Nintendo.list
ruleset=🤖 OpenAI,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/openai.list
ruleset=🤖 DeepL,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/deepl.list
ruleset=🎵 TikTok,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/TikTok.list
ruleset=📹 YouTube,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/YouTube.list
ruleset=🎥 Netflix,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Netflix.list
ruleset=🎥 Netflix,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/NetflixIP.list
ruleset=🎥 Disney+,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/DisneyPlus.list
ruleset=📽️ PrimeVideo,https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/AmazonPrimeVideo/AmazonPrimeVideo.yaml
ruleset=🌪 Gitlab,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/Gitlab.list
ruleset=🎼 Spotify,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/spotify.list
ruleset=🍑 DMMCOJP,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/dmmjp.list
ruleset=📺 巴哈姆特,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Bahamut.list
ruleset=📺 Bilibili,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/Bilibili.list
ruleset=📺 Bilibili,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Ruleset/BilibiliHMT.list
ruleset=🌏 国内媒体,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/ChinaMedia.list
ruleset=🌍 国外媒体,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/ProxyMedia.list
ruleset=📰 微博,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/weibo.list
ruleset=💬 微信,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/wechat.list
ruleset=🍠 小红书,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/XiaoHongShu.list
ruleset=🕺 字节跳动,https://raw.githubusercontent.com/jarvie-mei/ClashCustomRule/refs/heads/master/ByteDance.list
ruleset=🚀 节点选择,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/ProxyGFWlist.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/ChinaDomain.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/ChinaCompanyIp.list
ruleset=🎯 全球直连,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Download.list
ruleset=🎯 全球直连,[]GEOIP,CN
ruleset=🐟 漏网之鱼,[]FINAL
;设置规则标志位

;设置分组标志位
custom_proxy_group=🚀 节点选择`select`[]♻️ 自动选择`[]🔯 故障转移`[]🚀 手动切换`[]DIRECT`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点
custom_proxy_group=🚀 手动切换`select`.*
custom_proxy_group=♻️ 自动选择`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9])))`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🔯 故障转移`fallback`.*`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🐟 漏网之鱼`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=📲 Telegram`select`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🚀 手动切换
custom_proxy_group=📹 YouTube`select`[]🚀 节点选择`[]♻️ 自动选择`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🚀 手动切换
custom_proxy_group=🎼 Spotify`select`[]🚀 节点选择`[]♻️ 自动选择`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🚀 手动切换
custom_proxy_group=🤖 OpenAI`select`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点
custom_proxy_group=🤖 DeepL`select`.*`[]DIRECT
custom_proxy_group=🎵 TikTok`select`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点
custom_proxy_group=🎥 Netflix`select`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点`[]🇦🇺 澳大利亚节点
custom_proxy_group=🎥 Disney+`select`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点
custom_proxy_group=📽️ PrimeVideo`select`[]🇭🇰 香港节点`[]🇨🇳 台湾节点`[]🇯🇵 日本节点`[]🇸🇬 狮城节点`[]🇺🇲 美国节点
custom_proxy_group=🇭🇰 香港节点`select`(港|HK|Hong Kong)
custom_proxy_group=🇯🇵 日本节点`select`(日本|川日|东京|大阪|泉日|埼玉|沪日|深日|JP|Japan)
custom_proxy_group=🇺🇲 美国节点`select`(美|美国|波特兰|达拉斯|俄勒冈|凤凰城|费利蒙|硅谷|拉斯维加斯|洛杉矶|圣何塞|圣克拉拉|西雅图|芝加哥|United States|(?<![a-zA-Z])US(?![a-zA-Z])|(?<![a-zA-Z])USA(?![a-zA-Z])|(?<![a-zA-Z])USD(?![a-zA-Z]))
custom_proxy_group=🇨🇳 台湾节点`select`(台|新北|彰化|TW|Taiwan)
custom_proxy_group=🇸🇬 狮城节点`select`(新加坡|坡|狮城|SG|Singapore)
custom_proxy_group=🇰🇷 韩国节点`select`(KR|Korea|KOR|首尔|韩|韓)
custom_proxy_group=🇭🇰 香港节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:港|香港|HongKong|HK|Hong Kong)).*$)`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🇯🇵 日本节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:日本|川日|东京|大阪|泉日|埼玉|沪日|深日|JP|Japan)).*$)`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🇺🇲 美国节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:美|美国|波特兰|达拉斯|俄勒冈|凤凰城|费利蒙|硅谷|拉斯维加斯|洛杉矶|圣何塞|圣克拉拉|西雅图|芝加哥|United States|(?<![a-zA-Z])US(?![a-zA-Z])|(?<![a-zA-Z])USA(?![a-zA-Z])|(?<![a-zA-Z])USD(?![a-zA-Z]))).*$)`http://www.gstatic.com/generate_204`300,,150
custom_proxy_group=🇨🇳 台湾节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:台|新北|彰化|TW|Taiwan)).*$)`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🇸🇬 狮城节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:新加坡|坡|狮城|SG|Singapore)).*$)`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=🇰🇷 韩国节点-自动`url-test`(^(?!.*x(?:[2-9]|[1-9][0-9]))(?=.*(?:KR|Korea|KOR|首尔|韩|韓))`http://www.gstatic.com/generate_204`300,100
custom_proxy_group=📺 巴哈姆特`select`[]🇨🇳 台湾节点-自动`[]🚀 节点选择`[]🚀 手动切换`[]DIRECT
custom_proxy_group=🍑 DMMCOJP`select`[]🇯🇵 日本节点
custom_proxy_group=📺 Bilibili`select`[]DIRECT`[]🎯 全球直连`[]🇨🇳 台湾节点-自动`[]🇭🇰 香港节点-自动
custom_proxy_group=🌪 Gitlab`select`[]DIRECT`[]🎯 全球直连`[]🇨🇳 台湾节点-自动`[]🇭🇰 香港节点-自动
custom_proxy_group=🌍 国外媒体`select`[]🚀 节点选择`[]♻️ 自动选择`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇸🇬 狮城节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🚀 手动切换`[]DIRECT
custom_proxy_group=🌏 国内媒体`select`[]DIRECT`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇸🇬 狮城节点-自动`[]🇯🇵 日本节点-自动`[]🚀 手动切换
custom_proxy_group=📢 谷歌FCM`select`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=Ⓜ️ 微软云盘`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=Ⓜ️ 微软服务`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=🍎 苹果服务`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=🎮 游戏平台`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=📰 微博`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择`[]🇸🇬 狮城节点-自动`[]🇭🇰 香港节点-自动`[]🇨🇳 台湾节点-自动`[]🇯🇵 日本节点-自动`[]🇺🇲 美国节点-自动`[]🇰🇷 韩国节点-自动`[]🇬🇧 英国节点`[]🇩🇪 德国节点`[]🇨🇦 加拿大节点`[]🇧🇷 巴西节点`[]🇮🇳 印度节点`[]🇱🇺 卢森堡节点`[]🇳🇱 荷兰节点`[]🇮🇹 意大利节点`[]🇨🇭 瑞士节点`[]🇫🇷 法国节点`[]🇸🇦 沙特阿拉伯节点`[]🇮🇱 以色列节点`[]🇦🇪 迪拜节点`[]🇲🇽 墨西哥节点`[]🇨🇱 智利节点`[]🇦🇷 阿根廷节点`[]🇿🇦 南非节点`[]🇸🇪 瑞典节点`[]🇹🇷 土耳其节点`[]🇦🇺 澳大利亚节点`[]🇵🇰 巴基斯坦节点`[]🇹🇭 泰国节点`[]🇵🇭 菲律宾节点`[]🇷🇺 俄罗斯`[]🚀 手动切换
custom_proxy_group=💬 微信`select`[]DIRECT`[]REJECT`[]🚀 手动切换
custom_proxy_group=🍠 小红书`select`[]DIRECT`[]REJECT`[]🚀 手动切换
custom_proxy_group=🕺 字节跳动`select`[]DIRECT`[]REJECT`[]🚀 手动切换
custom_proxy_group=🎮 Nintendo`select`[]🚀 节点选择`.*
custom_proxy_group=🎯 全球直连`select`[]DIRECT`[]🚀 节点选择`[]♻️ 自动选择
custom_proxy_group=🛑 广告拦截`select`[]REJECT`[]DIRECT
custom_proxy_group=🍃 应用净化`select`[]REJECT`[]DIRECT
custom_proxy_group=🆎 AdBlock`select`[]REJECT`[]DIRECT
custom_proxy_group=🛡️ 隐私防护`select`[]REJECT`[]DIRECT
custom_proxy_group=🇬🇧 英国节点`select`(UK|英|伦敦)
custom_proxy_group=🇩🇪 德国节点`select`(DE|德)
custom_proxy_group=🇨🇦 加拿大节点`select`(CA|Canada|加拿大|枫)
custom_proxy_group=🇧🇷 巴西节点`select`(BA|巴西)
custom_proxy_group=🇮🇳 印度节点`select`(IN|印度)
custom_proxy_group=🇱🇺 卢森堡节点`select`(LU|卢森堡)
custom_proxy_group=🇳🇱 荷兰节点`select`(NL|荷兰)
custom_proxy_group=🇮🇹 意大利节点`select`(IT|意大利|意)
custom_proxy_group=🇨🇭 瑞士节点`select`(CH|瑞士)
custom_proxy_group=🇫🇷 法国节点`select`(FR|法|巴黎)
custom_proxy_group=🇸🇦 沙特阿拉伯节点`select`(沙|沙特|阿拉伯)
custom_proxy_group=🇮🇱 以色列节点`select`(IL|以色列)
custom_proxy_group=🇦🇪 迪拜节点`select`(UAE|迪拜|杜拜|Dubayy)
custom_proxy_group=🇲🇽 墨西哥节点`select`(墨西哥|mexico|México|Mexican)
custom_proxy_group=🇨🇱 智利节点`select`(智利|Chile|CL)
custom_proxy_group=🇦🇷 阿根廷节点`select`(阿根廷|Argentina|AR)
custom_proxy_group=🇿🇦 南非节点`select`(南非|Zuid-Afrika)
custom_proxy_group=🇸🇪 瑞典节点`select`(瑞典|Sweden|Sverige)
custom_proxy_group=🇹🇷 土耳其节点`select`(TR|土耳其|土)
custom_proxy_group=🇦🇺 澳大利亚节点`select`(土澳|澳大利亚|澳|AUS)
custom_proxy_group=🇵🇭 菲律宾节点`select`(菲|PH)
custom_proxy_group=🇹🇭 泰国节点`select`(泰|TH)
custom_proxy_group=🇵🇰 巴基斯坦节点`select`(巴基斯坦|PK)
custom_proxy_group=🇷🇺 俄罗斯`select`(俄|俄罗斯|RUS|RF)
;设置分组标志位

enable_rule_generator=true
overwrite_original_rules=true
skip_failed_links=true

#过滤节点，正则匹配
exclude_remarks=(IPV6|重置|流量|用户|本站|漏洞|永久虚通路|车|邀|免翻|邀请|eevpn|域名|机场|刷新|禁止|备用登录|计划|面板|忘记|到期|套餐|官网|更多|关注|25倍率|http|增加|持续|渠道|购买|QQ|Ins|二手)

;luck
```

## 进阶配置

以下规则说明均摘自 [订阅转换规则](https://github.com/tindy2013/subconverter/blob/master/README-cn.md#%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

### ruleset

> 从本地或 url 获取规则片段
>
> 格式为 `Group name,[type:]URL[,interval]` 或 `Group name,[]Rule `
>
> 支持的type（类型）包括：surge, quanx, clash-domain, clash-ipcidr, clash-classic
>
> type留空时默认为surge类型的规则
>
> \[] 前缀后的文字将被当作规则，而不是链接或路径，主要包含 `[]GEOIP` 和 `[]MATCH`(等同于 `[]FINAL`)。

    -   例如：

    ```ini
    ruleset=🍎 苹果服务,https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Apple.list
    # 表示引用 https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/Apple.list 规则
    # 且将此规则指向 [proxy_group] 所设置 🍎 苹果服务 策略组
    
    ruleset=Domestic Services,clash-domain:https://ruleset.dev/clash_domestic_services_domains,86400
    # 表示引用clash-domain类型的 https://ruleset.dev/clash_domestic_services_domains 规则
    # 规则更新间隔为86400秒
    # 且将此规则指向 [proxy_group] 所设置 Domestic Services 策略组
    
    ruleset=🎯 全球直连,rules/NobyDa/Surge/Download.list
    # 表示引用本地 rules/NobyDa/Surge/Download.list 规则
    # 且将此规则指向 [proxy_group] 所设置 🎯 全球直连 策略组
    
    ruleset=🎯 全球直连,[]GEOIP,CN
    # 表示引用 GEOIP 中关于中国的所有 IP
    # 且将此规则指向 [proxy_group] 所设置 🎯 全球直连 策略组
    
    ruleset=!!import:snippets/rulesets.txt
    # 表示引用本地的snippets/rulesets.txt规则
    ```

### custom_proxy_group

> 为 Clash 、Mellow 、Surge 以及 Surfboard 等程序创建策略组, 可用正则来筛选节点
>
> \[] 前缀后的文字将被当作引用策略组

```ini
custom_proxy_group=Group_Name`url-test|fallback|load-balance`Rule_1`Rule_2`...`test_url`interval[,timeout][,tolerance]
custom_proxy_group=Group_Name`select`Rule_1`Rule_2`...
# 格式示例
custom_proxy_group=🍎 苹果服务`url-test`(美国|US)`http://www.gstatic.com/generate_204`300,5,100
# 表示创建一个叫 🍎 苹果服务 的 url-test 策略组,并向其中添加名字含'美国','US'的节点，每隔300秒测试一次，测速超时为5s，切换节点的延迟容差为100ms
custom_proxy_group=🇯🇵 日本延迟最低`url-test`(日|JP)`http://www.gstatic.com/generate_204`300,5
# 表示创建一个叫 🇯🇵 日本延迟最低 的 url-test 策略组,并向其中添加名字含'日','JP'的节点，每隔300秒测试一次，测速超时为5s
custom_proxy_group=负载均衡`load-balance`.*`http://www.gstatic.com/generate_204`300,,100
# 表示创建一个叫 负载均衡 的 load-balance 策略组,并向其中添加所有的节点，每隔300秒测试一次，切换节点的延迟容差为100ms
custom_proxy_group=🇯🇵 JP`select`沪日`日本`[]🇯🇵 日本延迟最低
# 表示创建一个叫 🇯🇵 JP 的 select 策略组,并向其中**依次**添加名字含'沪日','日本'的节点，以及引用上述所创建的 🇯🇵 日本延迟最低 策略组
custom_proxy_group=节点选择`select`(^(?!.*(美国|日本)).*)
# 表示创建一个叫 节点选择 的 select 策略组,并向其中**依次**添加名字不包含'美国'或'日本'的节点
```

有了以上规则，理论上你可以自己配置所有你想要方式
