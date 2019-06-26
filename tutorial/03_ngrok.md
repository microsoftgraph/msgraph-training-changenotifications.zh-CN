<!-- markdownlint-disable MD002 MD041 -->

为了使 Microsoft Graph 向您的开发计算机上运行的应用程序发送通知, 您需要使用 ngrok 之类的工具从 internet 向您的开发计算机进行隧道调用。 Ngrok 允许将来自 internet 的呼叫定向到本地运行的应用程序, 而无需创建防火墙规则。

在继续操作之前, 您应在开发计算机上安装[ngrok](https://ngrok.com) 。 如果您没有 ngrok, 请访问 "下载选项" 和 "说明" 的 "上一步" 链接。

通过从命令行执行以下命令来运行 ngrok:

```shell
ngrok http 5000
```

这将启动 ngrok, 并将从外部 ngrok url 到端口5000上的开发计算机的隧道请求。

复制 https 转发地址。 在下面的示例中, 应`https://787b8292.ngrok.io`为。 稍后将需要它。

> [!IMPORTANT]
> 每次重新启动 ngrok 时, 都会生成一个新地址, 你将需要重新复制它。

```shell
ngrok by @inconshreveable

Session Status                online
Account                       ???? ???? (Plan: Free)
Version                       2.3.15
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://787b8292.ngrok.io -> http://localhost:5000
Forwarding                    https://787b8292.ngrok.io -> http://localhost:5000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```
