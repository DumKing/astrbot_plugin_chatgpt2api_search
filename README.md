# ChatGPT2API 网页搜索

AstrBot 函数工具 `chatgpt2api_search` 将搜索问题发到自建 ChatGPT2API 的 `POST /v1/search`，返回答案和来源链接。当前对话模型需要支持函数工具。

## 安装

需要 AstrBot 4.29.4 至 5.0 之前的版本，以及提供 `/v1/search` 的 ChatGPT2API 实例。可在 AstrBot 插件管理中选择从 Git 仓库安装，填入本仓库地址。也可上传插件 ZIP，或把此目录放入 `data/plugins/` 后加载插件。依赖为 `aiohttp`，见 `requirements.txt`。

## 配置

在 **插件管理 → ChatGPT2API 网页搜索 → 配置** 填写以下两项。

| 配置 | 说明 |
| --- | --- |
| `api_base` | AstrBot 能访问的 ChatGPT2API 服务地址。同一 Docker 网络可填 `http://chatgpt2api/v1`，跨服务器时使用 HTTPS 地址。 |
| `api_key` | ChatGPT2API 服务的 Bearer Key。在 AstrBot 配置页填写，妥善保管配置文件。 |

## 使用

对机器人说「用 ChatGPT2API 搜索 AstrBot 官方文档，附上来源链接」。工具参数 `prompt` 是要搜索的公开问题。该工具不依赖特定消息平台。搜索问题会发送到配置的 ChatGPT2API 实例，由该实例处理联网请求。

## 上游与许可证

搜索由 [ChatGPT2API](https://github.com/basketikun/chatgpt2api) 提供。本插件通过 HTTP 调用它。

本插件采用 [MIT License](LICENSE)。
