# <a name="microsoft-graph-training-module---using-change-notifications-and-track-changes-with-microsoft-graph"></a>Microsoft Graph 培训模块-在 Microsoft Graph 中使用更改通知和跟踪更改

本模块将介绍如何使用更改通知 (webhook) & 跟踪 Microsoft Graph 中的更改 (delta 查询)。

## <a name="lab---change-notifications-and-track-changes-with-the-microsoft-graph"></a>在 Microsoft Graph 中进行实验室更改通知和跟踪更改

在此实验室中, 将创建一个 .NET Core 控制台应用程序, 该应用程序在对 Azure Active Directory (Azure AD) 中的用户帐户进行更新时接收来自 Microsoft Graph 的更改通知。 应用程序将管理更改通知订阅并使用 Microsoft Graph 中的跟踪更改, 以确保不会丢失任何更改。

- [实验室手册](./Lab.md)

## <a name="demos"></a>演示

- [创建 .NET Core 应用程序](./demos/01-create-application)
- [添加订阅生命周期](./demos/02-subscription-management)
- [添加修订](./demos/03-track-changes)

## <a name="watch-the-module"></a>观看模块

此模块已记录并在 Office 开发 YouTube 频道中可用:[更改通知并使用 Microsoft Graph 跟踪更改](https://youtu.be/MvJ15BHTdHA)

## <a name="contributors"></a>参与者

| 角色                | 作者 (s)                                               |
| -------------------- | ------------------------------------------------------- |
| 实验室手册/幻灯片 | Andrew Connell (Microsoft MVP, Voitanos) @andrewconnell |
| 承办人/支持    | Jeremy Thake (Microsoft) @jthake                        |

## <a name="version-history"></a>版本历史记录

| 版本 | 日期           | 注释             |
| ------- | -------------- | -------------------- |
| 1.1     | 2019 年 4 月 9 日 | 添加了截屏视频链接 |
| 1.0     | 2019 年 3 月 14 日 | 新模块已提交 |

## <a name="disclaimer"></a>免责声明

**此代码_按_原样提供, 无需任何明示或暗示的担保, 包括对特定目的适用性、适销性或不侵权的任何暗示担保。**

<img src="https://telemetry.sharepointpnp.com/msgraph-training-changenotifications" />
