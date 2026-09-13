# Automatic Server Login

![icon](icon.jpg)

进入指定服务器后**自动发送登录指令**的 Fabric 客户端模组，无需再手动输入 `/l 密码`。

- **作者**：阿余（[ay811-cn](https://github.com/ay811-cn)）
- **开源地址**：<https://github.com/ay811-cn/automatic-server-login>
- **运行环境**：Minecraft 1.20.1 · Fabric Loader · Fabric API · Java 17+
- **协议**：MIT

## 功能

- 首次启动自动生成配置文件，主界面（标题画面）底部显示中文引导，填好后自动消失
- 进入指定服务器后自动发送 `登录指令 + 空格 + 密码`，指令与密码之间**自动补空格**
- 发送时机延迟 2 秒，等服务器登录插件就绪；发送失败自动重试（最多 3 次）
- **防重复登录**：登录服与主服使用同一域名（BC / Velocity 群组切服）时，同一条连接只发送一次，彻底断开后重连才会再次登录
- 配置热读取：改完保存，下次进服自动生效，无需重启游戏
- 兼容 UTF-8（含 BOM）与 GBK 编码，Windows 记事本直接保存也不会读坏

## 配置

配置文件位置：`.minecraft/config/automatic_server_login.json`

```json
{
  "指定登录服务器": "mc.example.com",
  "密码": "你的密码",
  "登录指令": "/l"
}
```

例如服务器要求登录指令为 `/l 123456`，则填写上面三项，模组进服后会自动发送 `/l 123456`。

说明：

| 字段 | 填什么 |
| --- | --- |
| 指定登录服务器 | 服务器域名或 IP，带不带端口均可（`ap.ss` 与 `ap.ss:25565` 视为同一个） |
| 密码 | 登录密码 |
| 登录指令 | 登录命令，**不要带密码**，开头的 `/` 可写可不写 |

> 注意：是 `"密码": "123456"`、`"登录指令": "/l"`，两栏不要填反。

## 安装

1. 安装 Fabric Loader（1.20.1）与 [Fabric API](https://modrinth.com/mod/fabric-api)
2. 将本模组 jar 放入 `.minecraft/mods` 文件夹
3. 启动一次游戏生成配置文件，填写后重新进入服务器即可

## 构建

```bash
./gradlew build
```

产物在 `build/libs/automatic-server-login-<version>.jar`。

## 开源协议

[MIT License](LICENSE) © 阿余
