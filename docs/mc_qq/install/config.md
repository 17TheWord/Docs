# 配置

## NoneBot2

::: warning 注意！
安装完插件后，请在机器人的 `src` 目录下创建名为 `mc_qq_config.py`、内容如下的配置文件  
或 [从 GitHub 下载](https://github.com/17TheWord/nonebot-plugin-mcqq/releases/download/V0.0.5/mc_qq_config.py)，将文件复制到对应目录并修改
:::

```python
# 在此填入服务器连接信息

# 服务器IP
mc_ip = "127.0.0.1"
# 服务器 WebSocket 端口
ws_port = "8765"
# 服务器 MCRcon 密码，插件安装的用户可以删除此行
mcrcon_password = "你的Rcon密码"
# 服务器 MCRcon 端口，插件安装的用户可以删除此行
mcrcon_port = 25575


# 开启功能的群和频道列表
group_list = {
    # 群列表
    "group_list": [
        # 群号
        # 123456789,
    ],
    # 频道列表
    "guild_list": [
        # {
            # # 频道 ID
            # "guild_id": 12345678909876543,
            # # 子频道 ID
            # "channel_id": 1234567,
        # },
    ],
}
```

## Minecraft Server

::: warning 注意！
若安装方式为：[MCRcon + 日志读取程序安装](/mc_qq/install/mcrcon.html)  
则需要在服务端根目录手动创建内容如下、名为 `config.yml` 的配置文件
:::

```yaml
# 是否启用插件
# 默认为 true
enable_mc_qq: true

# 请在冒号后填写 WebSocket 服务的地址端口号。
# 只填写数字即可。
# 冒号后需要空一格！
# 若不填写，则地址默认为 127.0.0.1 ，端口默认为 8765
websocket_hostname: 127.0.0.1
websocket_port: 8765

# 发送到群消息中，玩家昵称与消息之间的符号
# 默认为中文冒号 “：”
# 例如：
#   17TheWord ： 你好
say_way: "说："

# 是否启用 加入/离开 服务器监听
# 开启后，当玩家 加入/离开 服务器时，Bot会随推送信息
# 默认打开
# 例如：
#   17TheWord 加入了服务器
#   17TheWord 离开了服务器
join_quit: true
```
