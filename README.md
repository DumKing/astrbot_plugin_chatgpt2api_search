# ChatGPT2API 网页搜索

AstrBot 函数工具 `chatgpt2api_search` 将搜索问题发到自建 ChatGPT2API 的 `POST /v1/search`，返回答案和来源链接。当前对话模型需要支持函数工具。

ChatGPT2API 在上游调用 ChatGPT 网页端的聊天联网搜索。这里返回的是上游模型综合后的回答和它引用的来源，结果的新鲜度、覆盖范围和链接数量取决于上游。接口可能复用已有结果，无法保证每次查询都重新检索，也无法保证实时行情、比分等信息的时效。

## 安装

需要 AstrBot 4.29.4 至 5.0 之前的版本，以及提供 `/v1/search` 的 ChatGPT2API 实例。可在 AstrBot 插件管理中选择从 Git 仓库安装，填入本仓库地址。也可上传插件 ZIP，或把此目录放入 `data/plugins/` 后加载插件。依赖为 `aiohttp`，见 `requirements.txt`。

## 配置

在 **插件管理 → ChatGPT2API 网页搜索 → 配置** 填写以下配置。

| 配置 | 说明 |
| --- | --- |
| `api_base` | AstrBot 能访问的 ChatGPT2API 服务地址。同一 Docker 网络可填 `http://chatgpt2api/v1`，跨服务器时使用 HTTPS 地址。 |
| `api_path` | 搜索接口路径，默认 `/v1/search`。如果反向代理改了入口，填写实际路径，如 `/proxy/search`。自定义路径时，服务地址建议只填域名和端口。 |
| `api_key` | ChatGPT2API 服务的 Bearer Key。在 AstrBot 配置页填写，妥善保管配置文件。 |

## 使用

对机器人说「用 ChatGPT2API 搜索 AstrBot 官方文档，附上来源链接」。工具参数 `prompt` 是要搜索的公开问题。该工具不依赖特定消息平台。搜索问题会发送到配置的 ChatGPT2API 实例，由该实例处理联网请求。

## 上游与许可证

搜索由 [ChatGPT2API](https://github.com/basketikun/chatgpt2api) 提供。本插件通过 HTTP 调用它。

本插件采用 [MIT License](LICENSE)。
