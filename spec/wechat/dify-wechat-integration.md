# 零代码，使用 Dify 两分钟接入企业微信 AI 机器人

## **前置准备**

- 企业微信的管理员权限；
- 一个 Dify 的帐号（[https://dify.ai/](https://link.zhihu.com/?target=https%3A//dify.ai/)）；
- 一个 Laf 云的帐号（[https://laf.run/](https://link.zhihu.com/?target=https%3A//laf.run/)）；
- （可选）一个 OpenAI 的 API Key。如果没有，可以使用 Dify 免费提供的 200 次调用机会用于测试；
- （可选）在电脑上新建一个 env.txt 的文件，将下面内容复制到 env.txt 中。在接下来的教程中，我们会一步步把相关的信息填入这个文件。需要保存信息的步骤会**高亮显示。**

```text
WXWORK_TOKEN=""
WXWORK_AESKEY=""
WXWORK_CORPID=""
WXWORK_AGENTID=""
WXWORK_CORPSECRET=""
DIFY_APPTOKEN=""
```

## **在 Dify 上创建应用**

这一章节将会介绍如何创建一个法律知识的数据集，并将数据集和应用关联起来。

**搭建法律知识数据集**

为了让“知法”了解到更多的上下文，我们需要创建一个法律知识的数据库。

**1. 导入文档：** 从电脑上导入法律知识的 PDF 文档。

![](https://pic3.zhimg.com/80/v2-aefb6ea5f17f10090a0198d22f89cd8a_1440w.webp)

**2. 文本分段和清洗**：上传的文本需要经过二次加工，才能被大语言模型理解。这里我们不需要关注具体的实现逻辑，直接选择自动分段即可，然后点击“保存并处理”。

![](https://pic3.zhimg.com/80/v2-946d2185a314a01878835531d3578022_1440w.webp)

**3. 文本嵌入：** 大约 30s 时间，数据集就创建成功了。你可以随时回来向数据库里添加更多文件。

![](https://pic3.zhimg.com/80/v2-9e39ab9b553dfd51dc76a6641368eb7a_1440w.webp)

*（查看 Dify 官方文档中关于搭建数据集的更多操作：[https://docs.dify.ai/v/zh-hans/advanced/datasets](https://link.zhihu.com/?target=https%3A//docs.dify.ai/v/zh-hans/advanced/datasets)）*

## **搭建应用**

**1. 创建应用：** 根据图中的指示，创建一个对话型应用，并命名为“知法”。

![](https://pic1.zhimg.com/80/v2-82b6ad1d4db23b4a718e133dbadc847c_1440w.webp)

**2. 关联数据集：** 在“提示词编排”页，在“上下文”模块中添加选择刚刚创建的数据集。

![](https://pic3.zhimg.com/80/v2-c013b0fc8bf9e6ea56f4f3b776f4b842_1440w.webp)

**3. 发布模型：** 完成关联数据集后，点击页面右上角的“发布”，使模型生效。

![](https://pic2.zhimg.com/80/v2-57b010795b3fc01b7028eaeac85b9561_1440w.webp)

**4. 获取 API 访问密钥。** 在“访问 API”页面，**创建一个 API 密钥并复制保存为 `DIFY_APPTOKEN`**。请注意不要把密钥泄漏给任何人，以免造成财产损失。

![](https://pic2.zhimg.com/80/v2-4f1f966c94df78dcf3a1c8902320dc21_1440w.webp)

*（查看 Dify 官方文档中关于创建应用的更多操作：[https://docs.dify.ai/v/zh-hans/application/creating-an-application](https://link.zhihu.com/?target=https%3A//docs.dify.ai/v/zh-hans/application/creating-an-application)）*

## **创建企业微信应用**

**1. 记录企业信息：** 进入企业微信管理后台-我的企业，**记录这里的企业 ID 为 `WXWORK_CORPID。`**

![](https://pic3.zhimg.com/80/v2-683c518230328b38118c5ffe5dc6e0ce_1440w.webp)

**2. 创建企业微信应用：** 进入应用管理页面，点击【创建应用】进入创建页面，填写应用信息后点击【创建应用】。如果已经有现成的应用，可以跳过此步骤。

![](https://pic4.zhimg.com/80/v2-ccf6a63154a68acbbe793facf9350407_1440w.webp)

![](https://pic4.zhimg.com/80/v2-0919953189a1328562b720532ae1be87_1440w.webp)

**3. 记录企业微信应用信息：** 在应用管理页面点击刚刚创建好的应用，进入应用详情页面。记录这里的 AgentId 和 Secret（需要点击获取按钮，在企业微信聊天窗口里面获取），**分别为 WXWORK_AGENTID 和 WXWORK_CORPSECRET。**

![](https://pic3.zhimg.com/80/v2-d63c1dfa1f8ca5e29c8d5361250b4dba_1440w.webp)

**4. 企业微信应用接收信息：** 在应用详情页面，接收消息处点击【设置 API 接收】。

![](https://pic1.zhimg.com/80/v2-a7c8c250779c9cc990b87d7d38fc6e7c_1440w.webp)

在 API 接收消息页面，点一下两个【随机获取】按钮，它会自动生成一个 Token 和 EncodingAESKey，**我们分别记为 WXWORK_TOKEN 和 WXWORK_AESKEY。** 注意，不要关掉这个页面，Laf 侧配置完毕后我们再来填写 URL。

![](https://pic2.zhimg.com/80/v2-365562e535ca7d1c7f9f30da822c983d_1440w.webp)

## **在 Laf 云上创建云函数**

**1. 新建 Laf 云应用：** 进入 Laf 后，点击新建，创建一个云应用。这里选择免费的计划即可。

![](https://pic3.zhimg.com/80/v2-f3fc6c367421e8b6432762c50eadc52e_1440w.webp)

**2. 添加依赖：** 企业微信应用需要添加`@wecom/crypto`, `xml2js` 两个依赖。添加好后，你的依赖列表应该像下面一样。

![](https://pic3.zhimg.com/80/v2-8eaef12194b40d6452a165ed1a1d10fa_1440w.webp)

**3. 添加环境变量：** 从第二行开始，将上面步骤中收集到的所有内容全部粘贴到这里，点击更新。

![](https://pic3.zhimg.com/80/v2-77a753900ebb25b8ef54604f65702fba_1440w.webp)

**4. 创建云函数：** 点击创建一个云函数，注意“请求方法”中勾选上 `POST`, `GET`，点击确定。

![](https://pic2.zhimg.com/80/v2-3be8e14208b21104ffc34b55874a4129_1440w.webp)

在创建好云函数中，删除默认的代码，并将本文下方 **“附录”** 中的代码全部粘贴到这里。

![](https://pic4.zhimg.com/80/v2-7054dbc4be02adb80d6b09295892dd93_1440w.webp)

**5. 点发布云函数：** 点击发布后，云函数就生效了。

![](https://pic4.zhimg.com/80/v2-0ccd51b4d795aa1b6cabb9d2b8d914f3_1440w.webp)

现在把 URL 粘贴到企业微信后台【设置 API 接收】的页面中刚刚留白的地方，然后点击保存。

![](https://pic1.zhimg.com/80/v2-5fa93dc09e18f10ddb803cf9a86d55dc_1440w.webp)

**6. 配置 IP 白名单：** 在企业微信中找到刚刚创建应用，发送一句消息。不出意外收不到任何消息。这是因为企业微信默认屏蔽了 Laf 云的 IP。点击日志，应当能看到这样一条报错'`not allow to access from your ip`'

![](https://pic2.zhimg.com/80/v2-74ce6d6e5024944714d73bd1baf97699_1440w.webp)

点击查看这条日志详情，记录日志中给出的 Laf 云 IP：

![](https://pic1.zhimg.com/80/v2-8b2309eae0deddcd320fcd499b0d1f68_1440w.webp)

回到企业微信的管理后台，点击刚刚创建的应用，为应用配置可行 IP：

![](https://pic1.zhimg.com/80/v2-b85a46f80c1d0c196e9ff3d4fb2b25d0_1440w.webp)

在这里把刚刚的日志中记录的 IP 填入即可：

![](https://pic4.zhimg.com/80/v2-0cbe42cabb42c82f1d3166e9ed4f4133_1440w.webp)

## **验证效果**

**1. 测试聊天：** 在企业微信中找到刚刚创建应用，发送一句消息。现在应当能收到推送的消息了。

![](https://pic2.zhimg.com/80/v2-93fe2f02c21e556e5c10e8ed1b5a7b35_1440w.webp)

## **附录**

**企业微信应用代码 - (伪流式响应)**

```text
import cloud from '@lafjs/cloud'
import { decrypt, getSignature } from '@wecom/crypto'
import xml2js from 'xml2js'
​
function genConversationKey(userName) {
  return `${process.env.WXWORK_AGENTID}:${userName}`
}
​
function genWxAppAccessTokenKey() {
  return `${process.env.WXWORK_AGENTID}:access-token`
}
​
async function getToken() {
  console.log('[getToken] called')
​
  const cache = cloud.shared.get(genWxAppAccessTokenKey())
  if (cache && cache.expires >= Date.now()) return cache.token
​
  const res = await cloud.fetch({
    url: 'https://qyapi.weixin.qq.com/cgi-bin/gettoken',
    method: 'GET',
    params: {
      corpid: process.env.WXWORK_CORPID,
      corpsecret: process.env.WXWORK_CORPSECRET,
    }
  })
​
  const token = res.data.access_token
  cloud.shared.set(genWxAppAccessTokenKey(), { token, expires: Date.now() + res.data.expires_in * 1000 })
  return token
}
​
async function sendWxMessage(message, user) {
  console.log('[sendWxMessage] called', user, message)
​
  const res = await cloud.fetch({
    url: 'https://qyapi.weixin.qq.com/cgi-bin/message/send',
    method: 'POST',
    params: {
      access_token: await getToken()
    },
    data: {
      "touser": user,
      "msgtype": "text",
      "agentid": process.env.WXWORK_AGENTID,
      "text": {
        "content": message
      },
      "safe": 0,
      "enable_id_trans": 0,
      "enable_duplicate_check": 0,
      "duplicate_check_interval": 1800
    },
  })
  console.log('[sendWxMessage] received', res.data)
}
​
async function sendDifyMessage(message, userName, onMessage) {
  console.log('[sendDifyMessage] called', message, userName)
​
  const conversationId = cloud.shared.get(genConversationKey(userName)) || null
  let newConversationId = ''
  let responseText = ''
​
  try {
    const response = await cloud.fetch({
      url: 'https://api.dify.ai/v1/chat-messages',
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${process.env.DIFY_APPTOKEN}`
      },
      data: {
        inputs: {},
        response_mode: "streaming",
        query: message,
        user: userName,
        conversation_id: conversationId
      },
      responseType: "stream"
    })
​
    let firstHalfMessage = ''
    response.data.on('data', (data) => {
      let message = data.toString()
      try {
        if (firstHalfMessage) {
          message += firstHalfMessage
          firstHalfMessage = ''
        }

        // 检查是不是sse协议
        if (!message.startsWith('data: ')) return

        const parsedChunk: Record<string, any> = JSON.parse(message.substring(6))

        if (!newConversationId) {
          newConversationId = parsedChunk.conversation_id
          cloud.shared.set(genConversationKey(userName), newConversationId)
        }
        const { answer } = parsedChunk
        responseText += answer

        // 伪流式响应
        if (answer.endsWith('\n\n') || (responseText.length > 120 && /[?。；！]$/.test(responseText))) {
          onMessage(responseText.replace('\n\n', ''))
          console.log('[sendDifyMessage] received', responseText, newConversationId)
          responseText = ''
        }
      } catch (e) {
        firstHalfMessage = message
        console.error('[sendDifyMessage] error', message)
      }

    })

    // stream结束时把剩下的消息全部发出去
    response.data.on('end', () => {
      onMessage(responseText.replace('\n\n', ''))
    })
  } catch (e) {
    console.error("[sendDifyMessage] error", e)
  }
}
​
async function asyncSendMessage(xml) {
  console.log('[asyncSendMessage] called', xml)
​
  if (xml.MsgType[0] !== 'text') return
​
  const message = xml.Content[0]
  const userName = xml.FromUserName[0]
​
  if (message === '/new') {
    // 重置conversation id
    cloud.shared.set(genConversationKey(userName), null)
    sendWxMessage('新建成功，开始新的对话吧~~', userName)
    return
  }
​
  sendWxMessage('AI思考中, 请耐心等待~~', userName)
​
  try {
    sendDifyMessage(message, userName, (message) => {
      sendWxMessage(message, userName)
    })
  }
  catch (e) {
    console.error('[sendDifyMessage] error', e)
    sendWxMessage('接口请求失败，请联系管理员查看错误信息', userName)
  }
}
​
export default async function (ctx: FunctionContext) {
  const { query } = ctx
  const { msg_signature, timestamp, nonce, echostr } = query
  const token = process.env.WXWORK_TOKEN
  const key = process.env.WXWORK_AESKEY
  console.log('[main] called', ctx.method, ctx.request.url)
​
  // 签名验证专用
  if (ctx.method === 'GET') {
    const signature = getSignature(token, timestamp, nonce, echostr)
    if (signature !== msg_signature) {
      return { message: '签名验证失败', code: 401 }
    }
    const { message } = decrypt(key, echostr)
    return message
  }
​
  const payload = ctx.body.xml
  const encrypt = payload.encrypt[0]
  const signature = getSignature(token, timestamp, nonce, encrypt)
  if (signature !== msg_signature) {
    return { message: '签名验证失败', code: 401 }
  }
​
  const { message } = decrypt(key, encrypt)
  const {
    xml
  } = await xml2js.parseStringPromise(message)
  // 由于GPT API耗时较久，这里提前返回，防止企业微信超时重试，后续再手动调用发消息接口
  ctx.response.sendStatus(200)
​
  await asyncSendMessage(xml)
​
  return { message: true, code: 0 }
}
```

*引用：这篇深度参考以下文章，感谢原作者的辛勤付出：[https://forum.laf.run/d/556/2](https://link.zhihu.com/?target=https%3A//forum.laf.run/d/556/2)*

*（完）*

> 关于 Dify：Dify.AI 是一款 LLMOps 平台，帮助开发者更简单、更快速地构建 AI 应用。它的核心理念是通过可声明式的 YAML 文件定义 AI 应用的各个方面，包括 Prompt、上下文和插件等。Dify 提供了可视化的 Prompt 编排、运营、数据集管理等功能。这些功能使得开发者能够在数天内完成 AI 应用的开发，或将 LLM 快速集成到现有应用中，并进行持续运营和改进，创造一个真正有价值的 AI 应用。
