# v2ray/xray-core 使用指南 
领先 GFW 两个版本
## 协议
- 推荐[VLESS-TCP-XTLS-Vision](VLESS-XTLS-Vision/readme.md)
- 推荐[VLESS-XTLS-uTLS-REALITY](VLESS-XTLS-uTLS-REALITY)，不需要域名（或者ssl证书）
- 推荐[VLESS-H2-uTLS-REALITY](VLESS-H2-uTLS-REALITY/README.md),不要要域名
## v2ray客户端
- Windows
      [v2rayN](https://github.com/2dust/v2rayN)
- Linux
      [xray](https://github.com/XTLS/Xray-core) |
      [Txray](https://github.com/hsernos/Txray)
- Android
      [v2rayNG](https://github.com/2dust/v2rayNG)

## 自定义路由规则
参考[Loyalsoldier](https://github.com/Loyalsoldier/v2ray-rules-dat)
替换geosit.dat文件，包含的分类参考 https://github.com/v2fly/domain-list-community/tree/master/data 

例子: 

      geosite:github,
      
      gesite:microsoft,
      
      geosite:steam@cn
## 命令参考

## BBR加速
```
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"
chmod +x tcp.sh
./tcp.sh
``` 

## 参考
https://github.com/Loyalsoldier/v2ray-rules-dat

https://github.com/XTLS/Xray-core

https://github.com/mack-a/v2ray-agent
