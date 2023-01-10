## [Xray](https://xtls.github.io/Xray-docs-next/) [VLESS-TCP-XTLS-Vision](https://github.com/chika0801/Xray-examples/tree/main/VLESS-TCP-XTLS-Vision) 手动安装教程
# form https://github.com/chika0801/Xray-install
准备软件

- [Xshell 7 免费版](https://www.xshell.com/zh/free-for-home-school)
- [WinSCP](https://winscp.net/eng/docs/lang:chs)

重装系统

- Debian 10
- Debian 11
- Ubuntu 18.04
- Ubuntu 20.04

开始安装

- 使用Xshell 7登录你的VPS
- 使用root用户登陆

已有SSL证书

- 如果你之前用acme申请了SSL证书，将证书文件改名为`fullchain.cer`，将私钥文件改名为`private.key`，使用WinSCP登录你的VPS，将它们上传到`/etc/ssl/private`目录，执行下面的命令，跳过步骤1。

```
chown -R nobody:nogroup /etc/ssl/private
```

- [使用证书时权限不足](https://github.com/v2fly/fhs-install-v2ray/wiki/Insufficient-permissions-when-using-certificates-zh-Hans-CN)

#### 1.用[acme](https://github.com/acmesh-official/acme.sh)申请 SSL 证书

- 你先要购买一个域名，然后添加一个子域名，将子域名指向你VPS的IP。等待5-10分钟，让DNS解析生效。你可以通过ping你的子域名，查看返回的IP是否正确。确认DNS解析生效后，再执行下面的命令（每行命令依次执行）。
- 注意：将`chika.example.com`替换成你的子域名。

<details><summary>点击查看详细步骤</summary> 

```
apt install -y socat
```

```
curl https://get.acme.sh | sh
```

```
alias acme.sh=~/.acme.sh/acme.sh
```

```
acme.sh --upgrade --auto-upgrade
```

```
acme.sh --set-default-ca --server letsencrypt
```

```
acme.sh --issue -d chika.example.com --standalone --keylength ec-256
```

```
acme.sh --install-cert -d chika.example.com --ecc \
```

```
--fullchain-file /etc/ssl/private/fullchain.cer \
```

```
--key-file /etc/ssl/private/private.key
```

```
chown -R nobody:nogroup /etc/ssl/private/
```

</details>

- 备份已申请的SSL证书：使用WinSCP登录你的VPS，进入`/etc/ssl/private`目录，下载证书文件`fullchain.cer`和私钥文件`private.key`。
- SSL证书有效期是90天，每隔60几天会自动更新。[速率限制](https://letsencrypt.org/zh-cn/docs/rate-limits/)，超过次数会报错。

1. 安装程序

```
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install --beta
```

2. 下载配置

```
curl -Lo /usr/local/etc/xray/config.json https://raw.githubusercontent.com/chika0801/Xray-examples/main/VLESS-TCP-XTLS-Vision/config_server.json
```

3. 启动程序

```
systemctl restart xray
```

```
systemctl status xray
```

| 项目 | |
| :--- | :--- |
| 程序 | /usr/local/bin/xray |
| 配置 | /usr/local/etc/xray/config.json |
| 检查 | xray -test -config /usr/local/etc/xray/config.json |
| 路由规则文件 | /usr/local/share/xray/ |
| 查看日志 | journalctl -u xray --output cat -e |
| 实时日志 | journalctl -u xray --output cat -f |
