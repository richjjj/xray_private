# 翻墙+个人网盘cloudreve配置

### 1.参考[mack-a/v2ray-agent: （VLESS+TCP+TLS/VLESS+TCP+XTLS/VLESS+gRPC+TLS/VLESS+WS+TLS/VMess+TCP+TLS/VMess+WS+TLS/Trojan+TCP+TLS/Trojan+gRPC+TLS/Trojan+TCP+XTLS）+伪装站点、八合一共存脚本，支持多内核安装 (github.com)](https://github.com/mack-a/v2ray-agent) 完成xray的安装

### 2.参考[快速开始 - Cloudreve](https://docs.cloudreve.org/getting-started/install)安装配置cloudreve

### 3.配置nginx反向代理

修改 /etc/nginx/conf.d/alone.conf 文件最后部分为

```
server {
        listen 127.0.0.1:31300;
        server_name fun.just4.top;
        #root /usr/share/nginx/html;
        location /s/ {
                add_header Content-Type text/plain;
                alias /etc/v2ray-agent/subscribe/;
        }
        location / {
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $http_host;
                proxy_redirect off;
                proxy_pass http://127.0.0.1:5212;

                # 如果您要使用本地存储策略，请将下一行注释符删除，并更改大小为理论最大文件尺寸
                client_max_body_size 20000m;
                add_header Strict-Transport-Security "max-age=15552000; preload" always;
        }
}
```

