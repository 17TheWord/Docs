# 使用方法

### 前置

- [nonebot-plugin-guild-patch](https://github.com/mnixry/nonebot-plugin-guild-patch)：频道适配补丁。

- Python 3.10.5 （本人环境）

- 当前适配HarukaBot版本：`v1.4.1a60 测试版`

---

### 下载

- 前往 [Releases](https://github.com/17TheWord/HarukaBot_Guild_Patch/releases) 下载补丁文件

---

### 安装

#### 脚手架安装

<CodeGroup>
  <CodeGroupItem title="pip">

```shell
# 安装 Haruka
pip install haruka_bot

# 安装频道适配补丁
pip install nonebot-plugin-guild-patch
```

  </CodeGroupItem>
</CodeGroup>

---

#### NoneBot2 插件商店安装

<CodeGroup>
  <CodeGroupItem title="pip">

```shell
# 安装 nb-cli
pip install nb-cli

# 安装 Haruka、频道补丁
nb plugin install haruka_bot
nb plugin install nonebot-plugin-guild-patch
```

  </CodeGroupItem>
</CodeGroup>

---

#### 目录结构参考：
```

📦 HarukaBot                             # Bot项目
├── 📂 haruka                            # Bot
└── 📂 venv                              # 虚拟环境
    └── 📂 Lib
        └── 📂 site-packages
            └── 📂 haruka_bot            # 通过脚手架或nb商店下载的haruka_bot
                ├── 📂 database          # 替换
                │   ├── 📜 db.py
                │   └── 📜 models.py
                ├── 📂 plugins
                │   ├── 📂 guildadmin    # 增加
                │   │   ├── 📜 __init__.py
                │   │   ├── 📜 add_guild_admin.py
                │   │   ├── 📜 del_guild_admin.py
                │   │   └── 📜 guild_admin_sub.py
                │   ├── 📂 pusher        # 替换
                │   │   ├── 📜 dynamic_pusher.py
                │   │   └── 📜 live_pusher.py
                │   ├── 📂 sub           # 替换
                │   │   ├── 📜 add_sub.py
                │   │   └── 📜 delete_sub.py
                │   └── 📜 __init__.py   # 替换
                └── 📂 utils             # 替换
                    └── 📜 __init__.py
```

- 在虚拟环境 `venv` 目录找到 `haruka_bot`，并设此为此时的根目录
  - **修改数据库存储方式**
    - 替换 `database` 目录的 `models.py`
    - 替换 `database` 目录的 `db.py`


  - **修改工具包**
    - 替换 `utils` 目录的 `__init__.py`

  - **修改关注与推送的方法**
    - 替换 `plugins` 目录的 `__init__.py`
    - 替换 `plugins` --> `sub` 目录的 `add_sub.py` 和 `delete_sub.py`
    - 替换 `plugins` --> `pusher` 目录的 `dynamic_pusher.py` 和 `live_pusher.py`

  - **增加频道管理员操作命令**
    - 复制 `plugins` 目录下的 `guildadmin` 到 `plugins`

  - **增加清空订阅列表命令**
    - 替换 `plugins` 目录的 `auto_delete.py`

---

### 使用

- **其他命令与 `Haruka` 无异**


- **设置频道管理员：**
    - 在频道中使用命令 `添加 / 取消 @xxx` 即可进行管理员的增减操作
    - 可在一次命令中对多个用户进行操作
    - 管理员可以使用 `关注 / 取关` 功能
    - 只有 **超级用户** 才可以增减管理员
    - 通过 `@` 对管理员进行增减操作


- **设置频道管理员身份组：**
    - 新建一行，写入 `Haruka_GUILD_ADMIN_NAME = ["xxx", "xxxx"]`，
    - 将 `xxx` 替换为你的频道管理员的身份组的名称，
    - 支持多个身份组（其实是目前没有一键挪人的功能，干脆直接多个组解决）。


- 设置频道超级用户
    - 新建一行
    - `Haruka_Guild_Super_User_List = ["xxxxxxxxxx"]`
    - 将 `xxxxxxxxxx` 替换为超级用户的ID

- 清空订阅列表
  - 命令：`清空列表`
  - 一键清除 `群 / 频道` 中的订阅列表

---

### 配置
```
# 配置文件参考

HOST=127.0.0.1

PORT=8080

LOG_LEVEL=DEBUG

# Windows 用户请将此项设置为false
FASTAPI_RELOAD=false    
      
# 超级用户（频道不可用）
SUPERUSERS=["xxxxxx"]  
       
# Bot 昵称
NICKNAME=["Haruka_Bot"]        
           
# 命令头
COMMAND_START=["","/"]  
          
# 关闭 @ 前置
Haruka_TO_ME=False

# 开启下播通知
HARUKA_LIVE_OFF_NOTIFY=True
     
# 频道管理员身份组（仅Haruka）
Haruka_Guild_Admin_Group_List=["Haruka"]

# 频道超级用户（仅Haruka）
Haruka_Guild_Super_User_List=["xxxxxxxx"]
```
