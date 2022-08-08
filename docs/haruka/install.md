# 使用方法

### 前置需求

- [nonebot-plugin-guild-patch](https://github.com/mnixry/nonebot-plugin-guild-patch)：频道适配补丁。

- 目录结构参考：

```
📦 HarukaBot-master
├── 📂 plugins
│   ├── 📂 haruka_bot      # haruka_bot 的插件！不是 HarukaBot本身 
│   └── 📂 nonebot_plugin_guild_patch        # 频道适配插件
├── 📂 src                 # 或是 HarukaBot-master
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

### 目录结构

- 请在 `utils` 中的 `__init__.py` 中修改 第20行：


- `from plugins.nonebot_plugin_guild_patch import GuildMessageEvent`


- 中的 `plugins.nonebot_plugin_guild_patch` 部分，


- 替换为自己的频道适配补丁的位置。


- 在NoneBot中，`bot.py` 所在的目录为 `根目录`


- 可根据此 `根目录` 更改相对位置

---

### 环境设置

- 频道的 `@方式` 在最新频道补丁已实现，可以选择 `开启` 或 `关闭`。
    - 在你的环境配置文件中设置 （如：`.env.dev` 中），
    - 新建一行，写入：`Haruka_TO_ME=False`。
    - `Haruka_TO_ME=False` 关闭 @
    - `Haruka_TO_ME=True` 开启 @


- 设置频道管理员身份组：
    - 新建一行，写入：`HARUKA_GUILD_ADMIN_GROUPS=["xxx","Haruka"]`
    - 将 `xxx` 替换为你的身份组的名称
    - 详情见 `安装` --> `设置频道管理员身份组`

---

### 安装

- **假设 `haruka_bot` 目录为 `根目录`：**

    - 替换 `database` 目录下的 `models.py`
    - 替换 `database` 目录下的 `db.py`

    - 替换 `utils` 目录下的 `__init__.py`

    - 替换 `plugins` 目录下的 `__init__.py`
    - 替换 `plugins` --> `sub` 目录下的 `add_sub.py` 和 `delete_sub.py`
    - 复制 `plugins` 目录下的 `guildadmin` 到你的 `plugins` 目录


- **设置频道超级用户，以下步骤二选一 ！！！**
    1. 将 `GuildSuperUsers.py` 放到 `根目录 haruka_bot` 中：
        - 修改 `GuildSuperUserList = ["xxxxxx","xxxxxx"]`
        - 将 `xxxxxx` 替换为你要设置的超级用户的 `频道用户ID`
    2. 在 `根目录haruka_bot` 目录新建 `GuildSuperUsers.py`
        - 输入 `GuildSuperUserList = ["xxxxxx","xxxxxx"]`：
        - 将 `xxxxxx` 替换为你要设置的超级用户的 `频道用户ID`


- **设置频道管理员：**
    - 在频道中使用命令 `添加 / 取消 @xxx` 即可进行管理员的增减操作
    - 管理员可以使用 `关注 / 取关` 功能
    - 只有 **超级用户** 才可以增减管理员
    - 通过 `@` 对管理员进行增减操作


- **设置频道管理员身份组：**
    - 新建一行，写入 `Haruka_GUILD_ADMIN_NAME = ["xxx", "xxxx"]`，
    - 将 `xxx` 替换为你的频道管理员的身份组的名称，
    - 支持多个身份组（其实是目前没有一键挪人的功能，干脆直接多个组解决）。