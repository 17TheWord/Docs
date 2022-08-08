# 关于

## NoneBot 端

- 插件只需要新添加 `websockets` 依赖即可

## Minecraft Server 端

- 版本支持：
  - 理论上支持所有版本

  - 目前已编译的版本有：`1.16.5`、`1.18.1`，其他版本需要自行编译

  - 插件使用的接口有：
    - `AsyncPlayerChatEvent` 异步玩家聊天事件
    - `PlayerJoinEvent` 玩家加入事件
    - `PlayerQuitEvent` 玩家离开事件

  - 理论上支持以上三个接口的服务端都可以编译后使用
