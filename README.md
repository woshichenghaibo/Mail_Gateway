# Mail_Gateway简单部署
Guao Mail Gateway

在项目的变量和机密中，添加纯文本变量 FROM_EMAIL，值为发件人邮件地址，一般是绑定在resend.com后台的域名邮箱；添加纯文本变量 RESEND_API_KEY，值为api授权码，在resend.com后台新建API Keys，比如 re_iAyRTBZQ_2N3vsxj45yukr5cMxCRCSZ9B。

以Post方法为例：

```bash
curl -X POST "https://mail.guao.de/send" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "snail@qq.com",
    "subject": "邮件标题",
    "fromName": "运维系统",
    "text": "备用纯文本内容",
    "html": "<h2 style=\"color:blue;\">HTML 内容</h2><p>这是富文本格式</p>"
  }'
```

以Get方法为例：

```bash
curl -G "https://mail.guao.de/" \
  --data-urlencode "to=snail@qq.com" \
  --data-urlencode "subject=邮件标题" \
  --data-urlencode "fromName=运维系统" \
  --data-urlencode "text=备用纯文本内容" \
  --data-urlencode "html=<h2 style='color:blue;'>HTML 内容</h2><p>这是富文本格式</p>"
```
