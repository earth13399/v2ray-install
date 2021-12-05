## v2ray + Shadowsocks-TCP 手动安装教程

0.安装curl wget
```
apt update -y && apt install -y curl wget
```

1.安装v2ray
```
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
```

2.下载路由规则文件加强版
```
curl -sSLo /usr/local/share/v2ray/geosite.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat && curl -sSLo /usr/local/share/v2ray/geoip.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat
```

3.下载配置文件
```
wget -O /usr/local/etc/v2ray/config.json https://raw.githubusercontent.com/chika0801/v2ray-examples/main/Shadowsocks-TCP/config_server_dns_routing_enhance.json
```

4.设置v2ray开机启动
```
systemctl enable v2ray
```

5.启动v2ray
```
systemctl start v2ray && systemctl status v2ray
```
