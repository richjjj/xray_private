vps 测试脚本

## 1. 测速
三网测试（包括延迟）
参考repo https://github.com/i-abc/Speedtest
```
bash <(curl -sL bash.icu/speedtest)
# 8 10 12分别为电信移动联调测速
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

## 3. ChatGPT checker
https://github.com/missuo/OpenAI-Checker
```
bash <(curl -Ls https://cdn.jsdelivr.net/gh/missuo/OpenAI-Checker/openai.sh)
```

## 4. 流媒体解锁测试
https://github.com/lmc999/RegionRestrictionCheck
```
bash <(curl -L -s check.unlock.media)

# 英文版
bash <(curl -L -s check.unlock.media) -E
```