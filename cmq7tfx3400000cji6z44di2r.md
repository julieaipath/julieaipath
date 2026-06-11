---
title: "30分钟拥有私人助理：OpenClaw + 阿里云 + 飞书小白指南"
datePublished: 2026-06-10T08:37:45.674Z
cuid: cmq7tfx3400000cji6z44di2r
slug: 30-openclaw

---


30分钟拥有私人助理：OpenClaw \+ 阿里云 \+ 飞书小白指南

很多朋友问我，OpenClaw 看着酷，但怎么能真正把它跑起来？今天不聊虚的，直接上干货喂饭级教程。哪怕你是小白什么都不懂，只要会点鼠标，30分钟内搞定私人助理！

我们今天的目标只有一个：买台云服务器，让 OpenClaw 运行在服务器上，并连通飞书，实现一个能 24 小时自动回复、自动执行任务的“私人助理”。

# 关系梳理：为什么非要折腾这套方案？

在动手之前，我必须先帮你理清，它们都是干嘛的？

以下以阿里云为例说明（无广，本人纯属顺手），其他任意云厂商操作类似。国内其他选择：腾讯云，华为云，百度云等。海外其他选择：AWS，Azure等，按需购买。

**云服务器**：这是OpenClaw的运行环境，使用云服务好处是，有专门的公司运营维护，确保它 24 小时不掉线。（这也是私人助理能24小时为你服务的原因）

**OpenClaw**：这是 AI Agent，它有执行力，能操作文件和插件。类似电脑中运行的软件。

**大模型**：这是 AI 的“大脑”，提供逻辑思考能力。OpenClaw执行任务时，会反复和大模型交互，来确定下一步怎么做。

**飞书**：这是你和 AI 沟通的“对讲机”。通过飞书这样的聊天工具，你在手机上就能指挥远程的Agent执行任务。

# 第一阶段：买服务器

目前的云厂商竞争非常激烈，新用户简直是上帝。新手原则就是哪个便宜选哪个，先薅羊毛跑起来再说，等后期业务发展后，再根据你的业务选择更合适的。

## 1\.购买步骤：

登录阿里云控制台：选择“轻量应用服务器”。

薅羊毛姿势：找新用户活动页，选那个 9\.9 元/月 的套餐。我是老用户没这个福利了😭

硬性指标：内存必须 2GiB 及以上，否则 OpenClaw 跑起来会卡顿。

地域选择：默认选美国（弗吉尼亚）。别问为什么，选这个地域在调用国际大模型 API 时，网络几乎是秒连，不需要你再额外折腾。

## 2\.关键捷径（必看）

在下单购买时，有一个应用镜像选项。一定要选择官方OpenClaw镜像，选择它后相当于帮你把毛坯房的硬装全部搞定了。你就可以直接跳过最痛苦的 Linux 环境配置过程。节省时间的最关键步骤！

# 第二阶段：配置 OpenClaw

服务器买好后，进入实例操作页。我们要通过以下 3 步，在硬装基础上增加软装，让毛坯变精装房。

## 步骤 1：端口放通

很多小白自己手动配置完OpenClaw，发现私人助理不理人，90% 都是忘了开放端口。

点击实例名，进入概览页，点击【应用详情】。

找到“OpenClaw 使用步骤”区域，点击【端口放通】下的【执行命令】。这一步是阿里云开放OpenClaw服务运行端口的防火墙。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZDVlOTA1YWIwNzhjMDNkYjFiOGQ0OGU4MjM3NzE1NTNfZjIzNjZkZmRmY2NlNWY2YmQ1YWU3ZjYzMzNmNzM1ODVfSUQ6NzYyMzMyNjAyODU0NzE5ODE3Ml8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OTViYmU5Y2Y5MTI0OWI5YmEwMzgxNDIyNDA5NzE0YzhfYjZkM2I4OTcwMWNiYjc4NzAyODkwOTQyY2U4MjZiNjBfSUQ6NzYyMzMyNjAyNzUxMTQ1MDU4OF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 2：配置大模型参数

现在 OpenClaw 还不能智能执行任务，我们需要给它接上大脑（大模型）。

**获取 API Key**：我用的阿里百炼大模型（目前新人免费送 30 天额度，不用白不用）。在百炼后台创建一个 API Key，并复制那一串长长的字符。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MjNkZTVkY2Q1ZjM3NmYxZmJhNmYyZDliMzI1M2UxNDZfMjJmZTQ4OTBmM2YxMDhiNGExMjExY2RhYzRlMGE5ZWZfSUQ6NzYyMzMyNjAyOTY3OTM2NTA4MV8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

**填入配置**：回到阿里云应用详情页的【配置OpenClaw】，点击执行命令，把 API Key 粘贴进去。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NDIzNTEzN2EzNjlmNmZjZWM4YWEwNjBmZmIyN2EyZTBfNzQyNDA5ZWI1NTgwMzg4YWM5OWQ5ZThhMjExMjNjNTJfSUQ6NzYyMzMyNjAyODgyODA4NTE3N18xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 3：WebUI 测试

在应用详情页的【访问WebUI面板】，点击执行命令，你会得到WebUI的访问链接，打开OpenClaw的管理后台网页。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YjY5Mzk4ZmVhZWM1ZWU4M2U2MjlhY2Q5ODIwODQ1YTVfNjVhMDE4Y2I4YzM5OWI2MTBjNzk5Y2Y0OWZkN2M0NGVfSUQ6NzYyMzMyNjAyODIzMjc3MjU0MF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

在对话框发任何信息，如果它能准确回复你，说明大模型和OpenClaw已经配置成功了。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTdjNzRlZTcwZmU2NzIzM2I4ZDc3Y2YxM2ZmNzFlYjhfOWM5YWMyOWJmZDIyZTU3NGEyNjA2NmE0OWY4ZmQwZTFfSUQ6NzYyMzMyNjAyNzY0MTc1MjUxN18xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NjM2NmQ0Y2MyZTAwYjM3MTYzZmVlODg4YWI4OWQxZGZfZmM3Njk0YzdmZTI1ZGYzYWJmZjVjMzdhYjUwYjVlYzNfSUQ6NzYyMzMyNjAzMDY2OTA0MDg2OF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

# 第三阶段：连接飞书

这是最关键的一步，也是最有成就感的一步。我们要让飞书机器人变成 OpenClaw 的传话筒。让你能随时随地安排私人助理干活。

## 步骤 1：飞书开放平台配置

访问飞书开放平台，点击【创建企业自建应用】。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZDM0NDdjZmE3YWU1OGRlNGIzY2YzN2RhZjI4ZTM5YjJfZDQ1Zjg5NGE2OGNjMDcyMjY2ZmE0ZjQzYWMxYzU3YmNfSUQ6NzYyMzMyNjAyNzA1MDM3MjMwMF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

填入名字（比如：OpenClaw）和图标。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NDIwYjY2YjAxYmVhYmQ4ZTU3NmMzZjNiNTQ5ODQ4MTJfODQyZGRhZDZiYjQxNmNiYjYwMDAzZjkyMDZkMjM0N2VfSUQ6NzYyMzMyNjAyNzM4OTk5NjIyMl8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

关键数据：在【凭证与基础信息】里，你会看到 **App ID** 和 **App Secret**。拿小本本记下来，后面要填回阿里云服务器。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTVhNzgyMWRmYjYyNjg5NjM5NjljMGZmMjc5MzlhNGJfYjllNzE4ODIwZDAyNGEzMmFjNjE5Njc0YmEzMmEwOWNfSUQ6NzYyMzMyNjAzNjY1ODg1MDc0Nl8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 2：添加机器人能力

左侧导航栏点击【添加应用能力】，选择【按能力添加】【机器人】。点一下“添加”按钮，这一步完成后，你的飞书APP里就能搜到这个机器人了。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=OTA2MGFlOThhMzdkMzNkNzJiZGVmZmRiNDQyZjE1MDhfZWM2ZDg0MzQ4ODU1MTRmZWIyOGI5MjRlMjkzYjBkNWRfSUQ6NzYyMzMyNjAzNjc2Nzc3MTg0Nl8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 3：权限管理

这项操作是为了让机器人有权读取你的消息、发送文件、甚至在群里 @ 你等。

点击左侧【权限管理】。

为了方便大家，我准备了一个权限 JSON文档（有需要的同学**评论区留言**）。你只需要点击右上角的【批量导入/导出权限】，直接粘贴进去确认即可。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=ZjkwNzlmMGQzZmQ2MmIyNzg0ODM5Zjk1MDU1OWE5NDJfYTYwNDAyNDZlYjVhNjkwMjVjNzExNDE4YTBmMmE4N2NfSUQ6NzYyMzMyNjAzNzY3NzY4OTgwM18xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 4：建立信号长连接

这步是告诉飞书：一旦有人给机器人发消息，立刻通知 OpenClaw。

**回阿里云**：在服务器的【应用详情】\>【通道配置】\>【飞书】区域，把刚才记下的 App ID 和 App Secret 填入，点【应用】。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=NGU0N2IzYmEwMmM3MjQ5Y2Y4ODJlMDBiNjUxMGFiNzdfOWJjYjg1YjQ4NzY5ODdkMzI5OGIyY2IxYzE3ODg4N2NfSUQ6NzYyMzMyNjAzODA1MjUyMjk0OF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

**回飞书后台**：点击【事件与回调】。

**重要设置**：订阅方式必须选【使用长连接接收事件】。

**添加事件**：点“添加事件”按钮，搜索关键词 im\.message\.receive\_v1，勾选并确认。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YWQxZDk2YTNlNDBiMDQ0MTBkMTVhMTI4MTY4ZDA0ZDlfM2ZkNWIxNjM1OWM5Y2M3YzAxMTIwZmE2NDU1MmI1M2VfSUQ6NzYyMzMyNjAzNjEwOTIwMDMyOV8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

## 步骤 5：版本发布

在【版本管理与发布】点击【创建版本】。

版本号随便填，如 1\.0\.0，随便写点描述，点击【保存】。

点击【申请发布】。因为是自建应用，一般你自己就是管理员，可以秒批。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=MzFjZjU3MWQ0YTkzMjc1MTlkNTAxNDdkMjI3NzgyOWZfZTNjNzJmYmQ5ZTE3NjM3MmUzMTEyYmUzZGUwMWM2ZGNfSUQ6NzYyMzMyNjAzNTY2NDk4MTE5OF8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

# 那些我替你踩过的“坑”

在实际操作中，大家最容易在以下三个地方卡住：

1. **配置大模型API Key的坑**： 百炼API Key和百炼地域是一一匹配的，在大模型地域选择北京，对应的是北京地域创建的API Key。我当时填成美国创建的API Key后，导致出错。排查了快2个小时才搞定。😭
  
2. **API 额度限制**： 虽然百炼免费送了额度，但如果你调用的频率非常高（比如让它去抓取大量网页数据），额度会快速耗尽。建议在百炼后台开启“免费额度用完即停”，避免钱包受不住。
  
3. **飞书权限未更新**： 每次你在飞书开放平台修改了权限，都必须重新创建一个新版本并发布，否则机器人还是旧的权限，会导致它能收到消息但回不了消息。
  

🎉恭喜你，到这里你已经配置成功了，别只把它当成 聊天机器人，让它开始帮你干活吧。你会发现，一旦你拥有了这种“长了手”的 AI私人助理，你节省的不仅仅是时间，更是一种从重复劳动中解脱出来的“数字自由”。

![Image](https://internal-api-drive-stream.feishu.cn/space/api/box/stream/download/authcode/?code=YTYzMzUyMzRmYzU0ODZmMzA1NDE1YWNkOTc0OWFlMDBfODZhYjdjNTU2NmE4YjZmYjdlZTcyNjUyN2UzNzE3MGVfSUQ6NzYyMzMyNjAzNjI2ODgxMzUzMV8xNzgxMDc5NDYzOjE3ODExNjU4NjNfVjM)

