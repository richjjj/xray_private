# 服务端安装指南
- 系统为Ubuntu 20.04以上
## 申请SSL证书
- 添加域名A记录到VPS ip，大概需要2分钟左右使其生效。假设 fun4.just4.top 已经解析到vps
- 可以cloudflare 解析域名
- [acme](https://github.com/acmesh-official/acme.sh)自动申请证书，每60天会自动更新ssl证书
- 申请的SSL证书在 **/etc/ssl/private** 目录
- 备选 cerbot

详细步骤：
```bash
apt install -y socat
curl https://get.acme.sh | sh
alias acme.sh=~/.acme.sh/acme.sh
acme.sh --upgrade --auto-upgrade
acme.sh --set-default-ca --server letsencrypt

acme.sh --issue -d fun4.just4.top --standalone --keylength ec-256

acme.sh --install-cert -d fun4.just4.top --ecc \
--fullchain-file /etc/ssl/private/fullchain.cer \
--key-file /etc/ssl/private/private.key

chown -R nobody:nogroup /etc/ssl/private
```

## 配置xray
```bash
# install xray
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install --beta

# install nginx
apt update
apt install -y gnupg2 ca-certificates lsb-release ubuntu-keyring && curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor > /usr/share/keyrings/nginx-archive-keyring.gpg && echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/mainline/ubuntu `lsb_release -cs` nginx" > /etc/apt/sources.list.d/nginx.list && echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" > /etc/apt/preferences.d/99nginx && apt update -y && apt install -y nginx && mkdir -p /etc/systemd/system/nginx.service.d && echo -e "[Service]\nExecStartPost=/bin/sleep 0.1" > /etc/systemd/system/nginx.service.d/override.conf && systemctl daemon-reload

# install config
curl -Lo /usr/local/etc/xray/config.json https://raw.githubusercontent.com/zcfblq/xray_private/main/VLESS-XTLS-Vision/config_server.json && curl -Lo /etc/nginx/nginx.conf https://github.com/zcfblq/xray_private/blob/main/VLESS-XTLS-Vision/nginx.conf

# 下载增强路由规则文件
curl -Lo /usr/local/share/xray/geoip.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat && curl -Lo /usr/local/share/xray/geosite.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat

systemctl restart xray && systemctl restart nginx && sleep 0.5 && systemctl status xray && systemctl status nginx
```

## 客户端配置
### Windows 客户端 [v2rayN](https://github.com/2dust/v2rayN) 6.17以上的版本或者3.39
| 名称 | 值 |
| :--- | :--- |
| 地址 | fun4.just4.top |
| 端口 | 443 |
| 用户ID | rich |
| 流控 | xtls-rprx-vision |
| 传输层安全 | tls |
| Fingerprint | chrome |

![image](https://user-images.githubusercontent.com/37280580/226632208-66bfb104-9d9c-41e8-9670-ff00c504743c.png)

### Android 客户端 [v2rayNG](https://github.com/2dust/v2rayNG)

| 名称 | 值 |
| :--- | :--- |
| 地址(address) | fun4.just4.top |
| 端口(prot) | 443 |
| 用户ID(id) | rich |
| 流控(flow) | xtls-rprx-vision |
| 加密方式(encryption) | none |
| 传输协议(network) | tcp |
| 伪装类型(type) | none |
| 伪装域名(host) |  |
| path |  |
| 传输层安全(tls) | tls |
| SNI |  |
| Fingerprint | chrome |
| Alpn |  |
| 跳过证书验证(allowInsecure) | false |




