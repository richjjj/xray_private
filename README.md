# v2ray大杂烩

## v2ray客户端

winxray

v2rayN

## 自定义路由规则

## 节点

https://raw.githubusercontent.com/freefq/free/master/v2

https://raw.fastgit.org/freefq/free/master/v2

## 命令参考

v2ray info 查看 V2Ray 配置信息

v2ray config 修改 V2Ray 配置

v2ray link 生成 V2Ray 配置文件链接

v2ray infolink 生成 V2Ray 配置信息链接

v2ray qr 生成 V2Ray 配置二维码链接

v2ray ss 修改 Shadowsocks 配置

v2ray ssinfo 查看 Shadowsocks 配置信息

v2ray ssqr 生成 Shadowsocks 配置二维码链接

v2ray status 查看 V2Ray 运行状态

v2ray start 启动 V2Ray

v2ray stop 停止 V2Ray

v2ray restart 重启 V2Ray

v2ray log 查看 V2Ray 运行日志

v2ray update 更新 V2Ray

v2ray update.sh 更新 V2Ray 管理脚本

v2ray uninstall 卸载 V2Ray

## x-ui及BBR加速

bash <(curl -Ls https://raw.githubusercontent.com/sprov065/x-ui/master/install.sh)

项目地址  https://github.com/vaxilu/x-ui

wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"

chmod +x tcp.sh

./tcp.sh

# xray一键安装
安装/更新方式（Nginx 前置）
支持配置方式

VLESS + TCP + TLS + Nginx + WebSocket

wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/wulabing/Xray_onekey/nginx_forward/install.sh" && chmod +x install.sh && bash install.sh

安装/更新方式（Xray 前置）
支持配置方式

VLESS + TCP + XTLS / TLS + Nginx

VLESS + TCP + XTLS / TLS + Nginx 及 VLESS + TCP + TLS + Nginx + WebSocket 回落并存模式

wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/wulabing/Xray_onekey/main/install.sh" && chmod +x install.sh && bash install.sh



## 优化 V2Ray
可以尝试使用含有 mKCP 的传输协议，这个 mKCP 的东东，简单一点说就像 Kcptun 一样加速，并且还能进行伪装 (可选)，但是由于 mKCP 是使用 UDP 协议的，也许运营商会限速得更加厉害，网络变得更加慢。但不管怎么样，你都可以随时尝试一下。
服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再接着选择 mKCP 相关的传输协议即可

## 路由规则
替换geosit.dat文件，包含的分类参考 https://github.com/v2fly/domain-list-community/tree/master/data 

例子: 
      geosite:github,
      
      gesite:microsoft,
      
      geosite:steam@cn

## 参考项目
https://github.com/Loyalsoldier/v2ray-rules-dat

https://github.com/233boy/v2ray/wiki/V2Ray%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E8%84%9A%E6%9C%AC

https://github.com/wulabing/Xray_onekey
