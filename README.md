## Docker-for-Nezha-Argo-server-v1.x，兼容v0

#### 节点与哪吒融于一体，即可当哪吒面板，也可当节点使用

========================

v1版参数设置:

增加6个变量(均为可选，非必须):

#### 1.变量UUID，可选，设置则开启自带节点，否则不开启，支持vless和vmess协议

开启节点后可设置变量:SUB_NAME:节点名称;变量CF_IP:优选ip或域名

节点订阅地址是域名/uuid，也可以在日志中查看

#### 2.变量DASH_TOKEN,可选，客户端的哪吒key，不填则自动生成

#### 3.变量API_TOKEN,可选，设置与变量DASH_TOKEN相同值，支持客户端设置节点名称

此功能，需要配合玩具脚本，在客户端设置SUB_NAME为节点名称，则哪吒面板会自动生成相应节点名称。

特别提醒: 名称设置不是立即生效，需要等待1-2分钟才会生效。

玩具脚本地址(游戏机,Docker机，VPS通用版本):
```
https://github.com/dsadsadsss/java-wanju.git
```

## 建议配置(本人在koyeb部署配置，仅供参考,512m以上内存，资源不够的，去掉UUID和API_TOKEN)

| 变量名 | 描述 | 说明 | 是否必需 | 示例 |
|--------|------|------|------|------|
| `ARGO_DOMAIN` | Cloudflare Argo 隧道域名 |  | 是| `example.com` |
| `ARGO_AUTH` | Argo 隧道认证信息 | token/JSON | 是 | `token值` 或 `{"AccountTag":"xxx","TunnelSecret":"yyy"}` |
| `GH_CLIENTSECRET` | GitHub OAuth 客户端密钥 | 绑定GitHub需要，使用密码则填 | 否 | `ghs_xxxxxxxxxxxxxxxxxxxx` |
| `GH_CLIENTID` | GitHub OAuth 客户端 ID | 绑定GitHub需要，使用密码不用填 | 否 | `Iv1.xxxxxxxxxxxxxxxx` |
| `GH_USER` | GitHub 用户名 | 绑定GitHub需要，使用密码不用填 | 否 | `username` |
| `GH_PAT` | GitHub绑定app需要的密钥 | 备份需要，不用备份则不填 | 否 | 无|
| `GH_EMAIL` |GitHub账号  | 备份需要，不用备份则不填 | 否 | 无 |
| `GH_REPO` | GitHub备份仓库 | 备份需要，不用备份则不填 | 否 | 无 |
| `DASH_TOKEN` | 客户端使用的哪吒KEY | 即客户端使用的哪吒KEY | 是| 可以使用节点的UUID值 |
| `API_TOKEN` | 客户端节点设置名字的token | 设置与上面DASH_TOKEN相同的值 | 否|不设置则不支持客户端设置名字 |
#### docker镜像(PORT设置端口，默认面板端口80):
```
jian27/nezha-v1
```

建议利用action制作自己的镜像

#### 注意哪吒v1绑定GitHub与v0不同

1、回调地址不同

v0为 `https://你的面板域名/oauth2/callback`

v1为 `https://你的面板域名/api/v1/oauth2/callback` 

2、需要登陆面板后台绑定

在配置好 OAuth 2.0 信息后，登录哪吒面板后台，点击右上角头像进入个人设置。

在个人信息页的卡片列表里可以看见 OAuth 2 绑定的字样，其中有您所填写的 OAuth 2.0 配置名及其对应用户。
点击配置名右侧的 绑定 按钮就可以跳转到认证页面进行账户绑定。

其他变量设置与v0完全相同即可，部署教程除了上面说的一点区别，其他也一样

不清楚问题可以查看官方教程和F大哪吒v0教程

# 附上F大哪吒v0面板原始教程地址:

[使用 Argo 隧道的哪吒服务端](https://github.com/fscarmen2/Argo-Nezha-Service-Container.git)

## 免责声明:
* 本程序仅供学习了解, 非盈利目的，请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
* 使用本程序必循遵守部署免责声明。使用本程序必循遵守部署服务器所在地、所在国家和用户所在国家的法律法规, 程序作者不对使用者任何不当行为负责。
