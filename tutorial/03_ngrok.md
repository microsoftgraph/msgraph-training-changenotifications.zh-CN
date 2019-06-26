<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="d59d9-101">为了使 Microsoft Graph 向您的开发计算机上运行的应用程序发送通知, 您需要使用 ngrok 之类的工具从 internet 向您的开发计算机进行隧道调用。</span><span class="sxs-lookup"><span data-stu-id="d59d9-101">In order for the Microsoft Graph to send notifications to your application running on your development machine you need to use a tool such as ngrok to tunnel calls from the internet to your development machine.</span></span> <span data-ttu-id="d59d9-102">Ngrok 允许将来自 internet 的呼叫定向到本地运行的应用程序, 而无需创建防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="d59d9-102">Ngrok allows calls from the internet to be directed to your application running locally without needing to create firewall rules.</span></span>

<span data-ttu-id="d59d9-103">在继续操作之前, 您应在开发计算机上安装[ngrok](https://ngrok.com) 。</span><span class="sxs-lookup"><span data-stu-id="d59d9-103">Before you continue you should have [ngrok](https://ngrok.com) installed on your development machine.</span></span> <span data-ttu-id="d59d9-104">如果您没有 ngrok, 请访问 "下载选项" 和 "说明" 的 "上一步" 链接。</span><span class="sxs-lookup"><span data-stu-id="d59d9-104">If you do not have ngrok, visit the previous link for download options and instructions.</span></span>

<span data-ttu-id="d59d9-105">通过从命令行执行以下命令来运行 ngrok:</span><span class="sxs-lookup"><span data-stu-id="d59d9-105">Run ngrok by executing the following from the command line:</span></span>

```shell
ngrok http 5000
```

<span data-ttu-id="d59d9-106">这将启动 ngrok, 并将从外部 ngrok url 到端口5000上的开发计算机的隧道请求。</span><span class="sxs-lookup"><span data-stu-id="d59d9-106">This will start ngrok and will tunnel requests from an external ngrok url to your development machine on port 5000.</span></span>

<span data-ttu-id="d59d9-107">复制 https 转发地址。</span><span class="sxs-lookup"><span data-stu-id="d59d9-107">Copy the https forwarding address.</span></span> <span data-ttu-id="d59d9-108">在下面的示例中, 应`https://787b8292.ngrok.io`为。</span><span class="sxs-lookup"><span data-stu-id="d59d9-108">In the example below that would be `https://787b8292.ngrok.io`.</span></span> <span data-ttu-id="d59d9-109">稍后将需要它。</span><span class="sxs-lookup"><span data-stu-id="d59d9-109">You will need this later.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d59d9-110">每次重新启动 ngrok 时, 都会生成一个新地址, 你将需要重新复制它。</span><span class="sxs-lookup"><span data-stu-id="d59d9-110">Each time ngrok is restarted a new address will be generated and you will need to copy it again.</span></span>

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
