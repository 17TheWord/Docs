# 使用说明

## 环境
- `Python 3.10.5`
    - `websockets 10.3`


- `nb-cli 0.6.7`
    - `nonebot-adapter-onebot 2.1.1`
    - `nonebot2 2.0.0b4`
    - `nonebot-plugin-guild-patch`


- `OpenJDK 17`


- `Minecraft 1.18.1`


- `Spigot 1.18.1`

---

## 安装

### NoneBot

- pip安装

  - 下载 **/** 新建 `mc_qq_config.py` 配置文件到 `src` 目录下
     - 否则会报错  
    `ImportError: cannot import name 'group_list' from 'src.mc_qq_config' (unknown location)`

  - ~~安装频道适配补丁 `pip install nonebot-plugin-guild-patch`~~  
  频道适配补丁已写入插件依赖中，无需手动安装 

  - 安装插件 `pip install nonebot-plugin-mcqq`

  - 在 `nonebot2` 项目中设置 `load_plugin()`  
     `nonebot.load_plugin('nonebot_plugin_mcqq')`

- 手动安装
  - 下载频道适配补丁 `pip install nonebot-plugin-guild-patch`
  - 下载 **/** 新建 `mc_qq_config.py` 配置文件到 `src` 目录下
  - 下载 `nonebot_plugin_mcqq` 到 `plugins` 文件夹

```python
# 在此填入 WebSocket 地址
# 一般修改只修改端口号
ws_url = "ws://localhost:8765"

# 开启功能的群和频道列表
group_list = {
    # 群列表
    "group_list": [
        # 群号
        123456789,
    ],
    # 频道列表
    "guild_list": [
        {
            # 频道 ID
            "guild_id": 12345678909876543,
            # 子频道 ID
            "channel_id": 1234567,
        },
    ],
}

```

- 目录结构参考：

```
📦 test_bot
├── 📂 plugins
│   ├── 📂 nonebot_plugin_mcqq      # mcqq 插件
│   └── 📂 nonebot_plugin_guild_patch        # 频道适配插件
├── 📂 src                 # 或是 test_bot
│   └── 📜 mc_qq_config.py
├── 📜 .env                # 可选的
├── 📜 .env.dev            # 可选的
├── 📜 .env.prod           # 可选的
├── 📜 .gitignore
├── 📜 bot.py
├── 📜 docker-compose.yml
├── 📜 Dockerfile
├── 📜 pyproject.toml
└── 📜 README.md
```

### Minecraft Server

- 将 `MC_QQ.jar` 放入 `Minecraft` 服务器 `plugins` 文件夹
- 启动服务器后插件将自动生成配置文件并写入默认信息
- 默认信息参考如下：

```yaml
# 是否启用插件
# 默认为 true
enable_mc_qq: true

# 请在冒号后填写 WebSocket 服务的地址端口号。
# 只填写数字即可。
# 冒号后需要空一格！
# 若不填写，则地址默认为 0.0.0.0 ，端口默认为 8765
websocket_server:
  address: "0.0.0.0"
  port: "8765"

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

---

## 完成

如果一切顺利的话，到这里你的消息互通已经搭建完成了。