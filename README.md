# v2ray/xray-core 使用说明 

## 服务端安装
一下几种方案任选一种

1. https://github.com/wulabing/Xray_onekey
2. https://github.com/kirin10000/Xray-script
3. https://github.com/mack-a/v2ray-agent  (√)
## 协议
- 推荐[VLESS-TCP-XTLS-Vision](./VLESS-TCP-XTLS-Vision.md)
## v2ray客户端
- Windows
      [v2rayN](https://github.com/2dust/v2rayN)
- Linux
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

## x-ui及BBR加速

bash <(curl -Ls https://raw.githubusercontent.com/sprov065/x-ui/master/install.sh)

项目地址  https://github.com/vaxilu/x-ui

wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"

chmod +x tcp.sh

./tcp.sh

## 优化 V2Ray
可以尝试使用含有 mKCP 的传输协议，这个 mKCP 的东东，简单一点说就像 Kcptun 一样加速，并且还能进行伪装 (可选)，但是由于 mKCP 是使用 UDP 协议的，也许运营商会限速得更加厉害，网络变得更加慢。但不管怎么样，你都可以随时尝试一下。
服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再接着选择 mKCP 相关的传输协议即可


## 参考项目
https://github.com/Loyalsoldier/v2ray-rules-dat

https://github.com/wulabing/Xray_onekey

https://github.com/kirin10000/Xray-script
