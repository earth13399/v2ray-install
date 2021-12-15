## v2ray + Shadowsocks-TCP 手动安装教程

0.安装curl
```
apt update -y && apt install -y curl
```

1.安装v2ray
```
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
```

2.下载[路由规则文件加强版](https://github.com/Loyalsoldier/v2ray-rules-dat)
```
curl -Lo /usr/local/share/v2ray/geosite.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat && curl -Lo /usr/local/share/v2ray/geoip.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat
```

3.下载配置文件
```
curl -Lo /usr/local/etc/v2ray/config.json https://raw.githubusercontent.com/chika0801/v2ray-install/main/Shadowsocks-TCP/config_server_dns_routing_enhance.json
```

4.设置v2ray开机启动
```
systemctl enable v2ray
```

5.启动v2ray
```
systemctl restart v2ray && systemctl status v2ray
```

6.1下载和设置v2rayN

[打开链接](https://github.com/2dust/v2rayN/releases) 点击最新版本栏里的“▸ Assets `4`”，找到名为`v2rayN-Core.zip`的链接并下载。把压缩包解压，找到`v2rayN-Core`文件夹里的`v2rayN.exe`并双击运行。

- 点击 设置 — 参数设置 — v2rayN设置，勾选“更新Core时忽略Geo文件”，将“Core类型”改为“v2fly_core”，确定。
- 点击 设置 — 路由设置，将“域名解析策略”改为“IPIfNonMatch”，取消勾选“启用路由高级功能”，将“域名匹配算法”改为“mph”，点击“基础功能”，点击“一键导入基础规则”，确定，确定。
- 右键点击屏幕右下角的v2rayN图标，点击“系统代理 — 自动配置系统代理”。

6.2.在v2rayN中添加服务器

点击“服务器 — 添加[Shadowsocks]服务器”
- 服务器地址：`你VPS的IP`
- 服务器端口：`50001`
- 密码：`8tetnZHnBJcrnbjIpTi9fQ==`
- 加密方式：`aes-256-gcm`

确定

点击“检查更新”
- 点击“v2fly-Core — 是否下载? — 是”。
- 点击“Update GeoSite — 是否下载? — 是”。
- 点击“Update GeoIP — 是否下载? — 是”。

## 注意事项

1.[禁止了VPS访问CN域名和IP](https://github.com/XTLS/Xray-core/discussions/593#discussioncomment-845165)

2.若在客户端未正确设置CN域名和IP直连，`将在VPS端被阻止`

3.请使用v2ray_core的Shadowsocks连接VPS

4.请勿使用Xray_core的Shadowsocks连接VPS，[否则会造成端口很快被封](https://github.com/XTLS/Xray-core/issues/625)

4.请选择带有v2ray_core的手机端APP连接VPS，`并正确设置CN域名和IP直连`（如[v2flyNG](https://github.com/2dust/v2flyNG/releases)）

5.密码建议使用[20位或更强的](https://1password.com/password-generator/)

