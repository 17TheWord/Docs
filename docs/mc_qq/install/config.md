# 配置

## NoneBot2

::: warning 注意！
安装完插件后，请在机器人的配置文件，如：`.env.dev` 中写入相关配置信息  
添加配置项只需在 .env.* 文件最底下另起一行直接添加即可。

::: details 示例（点我展开）

```json
MC_QQ_GROUP_LIST=[]
MC_QQ_GUILD_LIST=[[]]
MC_QQ_IP=""
MC_QQ_WS_PORT=
MC_QQ_MCRCON_PASSWORD=""
MC_QQ_MCRCON_PORT=
```
:::

### MC_QQ_GROUP_LIST

默认值：[]

填写需要开启互通的群号

```json
MC_QQ_GROUP_LIST=[QQ群号]
```

---

### MC_QQ_GUILD_LIST

默认值：[[]]

填写需要开启互通的群号

```json
MC_QQ_GUILD_LIST=[[频道ID,子频道ID]]
```

---

### MC_QQ_IP

默认值："127.0.0.1"

MC 服务器 IP

```json
MC_QQ_IP="127.0.0.1"
```

---

### MC_QQ_WS_PORT

默认值：8765

MC 服务器 WebSocket 端口（MC_QQ插件的端口）

```json
MC_QQ_WS_PORT=8765
```

---

### MC_QQ_MCRCON_PASSWORD

默认值：Null

MC 服务器 Rcon 密码

```json
MC_QQ_MCRCON_PASSWORD=""
```

---

### MC_QQ_MCRCON_PORT

默认值：[]

MC 服务器 Rcon 端口

```json
MC_QQ_MCRCON_PORT=25575
```

---

## Minecraft Server

::: warning 注意！
若安装方式为：[MCRcon + 日志读取程序安装](/mc_qq/install/mcrcon.html)  
则需要在服务端根目录手动创建内容如下、名为 `config.yml` 的配置文件
:::

```yaml
# 是否启用插件
# 默认启用
enable_mc_qq: true

# 请在冒号后填写 WebSocket 服务的地址端口号。
# 只填写数字即可。
# 冒号后需要空一格！
# 若不填写，则地址默认为 127.0.0.1 ，端口默认为 8765
websocket_hostname: 127.0.0.1
websocket_port: 8765

# 发送到群消息中，玩家昵称与消息之间的符号
# 默认为 “说：”
# 例如：
#   17TheWord ： 你好
say_way: "说："

# 是否启用 玩家死亡事件监听
# 开启后，当玩家死亡时，Bot会推送信息
# 默认启用
death_message: true

# 是否启用 加入/离开 服务器监听
# 开启后，当玩家 加入/离开 服务器时，Bot会随推送信息
# 默认打开
# 例如：
#   17TheWord 加入了服务器
#   17TheWord 离开了服务器
join_quit: true

```
