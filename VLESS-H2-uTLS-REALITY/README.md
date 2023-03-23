# 安装指南
不需要域名和证书
## 服务端安装
```bash
# 安装xray
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install --beta
# 下载配置
curl -Lo /usr/local/etc/xray/config.json https://raw.githubusercontent.com/zcfblq/xray_private/main/VLESS-H2-uTLS-REALITY/config_server.json
# 启动
systemctl restart xray && sleep 0.2 && systemctl status xray
```

## 客户端配置
参考 config_client.json配置, 或者客户端直接导入config_client.json即可

支持VLESS-H2-uTLS-REALITY的客户端:
- v2rayN - V6.17以上
- v2rayNG - V1.8.0以上