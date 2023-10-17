vps 测试脚本

## 1. 测速
三网测试（包括延迟）
参考repo https://github.com/i-abc/Speedtest
```
https://github.com/i-abc/Speedtest
```

到本机的下载速度 speedtestx
```
curl -sSL https://get.docker.com/ | sh
systemctl start docker
systemctl enable docker

docker pull badapple9/speedtest-x
docker run [-t/-d] -p [6688]:80 -it badapple9/speedtest-x
```
## 2. 路由
nexttrace 参考repo https://github.com/nxtrace/NTrace-core
```
bash -c "$(curl http://nexttrace-io-leomoe-api-a0.shop/nt_install_v1.sh)"
nexttrace IP
```