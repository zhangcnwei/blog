---
title: IIS7 HTTPS 绑定主机头
date: 2015-12-09 13:44:42
tags: 
    - IIS 
    - Server 
---

**IIS7** 下面默认 **HTTPS** 绑定是无法指定主机头的，但我们可以通过手工修改IIS配置来实现主机头绑定。

打开C:\Windows\system32\inetsrv\config\applicationHost.config

定位到如下位置：

                <bindings>

                    <binding protocol="https" bindingInformation="*:443" />
                    <binding protocol="net.tcp" bindingInformation="808:*" />

                    <binding protocol="net.pipe" bindingInformation="*" />

                    <binding protocol="net.msmq" bindingInformation="localhost" />

                    <binding protocol="msmq.formatname" bindingInformation="localhost" />

                    <binding protocol="http" bindingInformation="*:80:www.console.com" />

                </bindings>

找到https的配置项目，修改为：

`<binding protocol="https" bindingInformation="*:443:www.console.com" />`

注意这里的[www.console.com](http://www.console.com/)要换成你自己的域名，之后保存即可。