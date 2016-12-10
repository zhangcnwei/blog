---
title: 用shadowsock加速git clone
date: 2015-12-08 13:44:42
tags: 
    - git 
    - proxy 
    - shadowsocks
---
#用shadowsock加速git clone
因为在天朝，用git clone 下载 github上的仓库的时候，速度很慢，才几十k每秒，稍微大点的仓库，要等到猴年马月。
利用shadowsocks的socks5代理，配置好后明显加速。用下面两条命令配置好后，保持shadowsocks客户端开启就行了。

``` bash
1 git config --global http.proxy 'socks5://127.0.0.1:1080'
2 git config --global https.proxy 'socks5://127.0.0.1:1080'
```
shadowsocks的本地端口默认是1080

git协议开启代理可以查看[这里](https://segmentfault.com/q/1010000000118837)

git仓库有的在国内有的在国外,国内的有gitcafe coding.net 开源中国git
所以用国内的就没必要设置了，反而会慢。

