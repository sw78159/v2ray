# 一句话说明
这是一个固定使用 Caddy v1.0.4 和 V2Ray v4.27.0 的 233一键脚本 v3.34

# 修改说明
- 本repo从233脚本 v3.34 fork过来

- 本repo修改了src/download-v2ray.sh 第3行，将最新V2Ray版本写死为 v4.27.0，不会跟随最新的V2Ray版本

- 233脚本v3.34已经在src/download-caddy.sh 第9行，固定下载v1.0.4的Caddy

- 获得IP方法修改为 
```
ip=$(curl -s https://www.cloudflare.com/cdn-cgi/trace | grep ip= | sed -e "s/ip=//g")
```

- 检查域名解析方法修改为 
```
test_domain=$(curl -sH 'accept: application/dns-json' "https://cloudflare-dns.com/dns-query?name=$domain&type=A" | jq -r '.Answer[0].data')
```

# 为什么这么做
- 我的个人观点是 "日常自用的自建梯子，用老版本的v2ray+caddy/nginx，走ws+tls+cdn就够了"。欢迎交流。
https://zelikk.blogspot.com/2022/01/v2ray-caddy-ws-tls-cdn.html

- 有些翻墙客户端上面的V2Ray不能更新到支持AlterID为0的内核版本

- 有些人的服务器原来是用233的脚本搭的，在重装服务器时，只想把原来的配置文件恢复进去就好。

# 如果已经跑过233脚本了
依次执行

```bash
v2ray uninstall
bash <(curl -L git.io/233v334.sh)
```

# 如果还没有跑过233脚本
执行

```bash
bash <(curl -L git.io/233v334.sh)
```
# 如果报错 `bash: curl: command not found` 可能你需要安装curl
```
apt update
apt install -y curl
```

# 后记

233的脚本从本地安装时，必须在 install.sh 脚本所在的目录执行

install.sh 的 795 行，检查$(pwd)/config目录

# 如果你想在最新的233脚本上指定下载某个版本的v2ray
https://zelikk.blogspot.com/2021/01/233v2ray-local.html

# 如果你想下载某个“旧版本”的233脚本
https://zelikk.blogspot.com/2021/08/233v2ray-github-commit.html

# 无人值守一把梭
https://zelikk.blogspot.com/2022/11/spawn-expect-afk-233v334.html
```
apt update && apt install -y expect wget && wget -N git.io/233v334.sh && wget -N https://github.com/crazypeace/v2ray/raw/master/afk.exp && expect afk.exp
```

## 用你的STAR告诉我这个Repo对你有用 Welcome STARs! :)

[![Stargazers over time](https://starchart.cc/crazypeace/v2ray.svg)](https://starchart.cc/crazypeace/v2ray)
