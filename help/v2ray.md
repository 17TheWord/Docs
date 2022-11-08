# 安装

- 安装脚本：

  ```
  https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh
  ```

- v2ray安装包：

  ```
  https://github.com/v2fly/v2ray-core/releases
  ```

- 根据自己操作系统来下载对应版本，一般情况下都是 `v2ray-linux-64.zip`；
- 如果遇到网络打不开或慢导致下载失败，推荐先手动下载，然后上传至服务器。

- 依次执行：

    1. 切换至你的上传目录
    ```
    cd 你的上传目录
    ```

    2. 添加执行权限
    ```shell
    chmod +x ./install-release.sh
    ```

    3. 指定包执行安装
    ```shell
    ./install-release.sh -l ./v2ray-linux-64.zip
    ```

- 安装成功

- 默认配置文件路径：`/usr/local/etc/v2ray/`

- 开启自启

  ```shell
  systemctl enable v2ray
  ```

# 配置

- 将以下配置保存为 `config.json` 文件，并替换掉 `/usr/local/etc/v2ray/config.json`。
- 执行 `systemctl restart v2ray` 重启。

Ps：该配置非常简单，含义是以 `tcp` + `vmess` 方式进行流量传输。

```json
{
  "log": {
    "access": "/var/log/v2ray/access.log",
    "error": "/var/log/v2ray/error.log",
    "loglevel": "warning"
  },
  "inbounds": [
    {
      "port": 6688,
      "protocol": "vmess",
      "settings": {
        "clients": [
          {
            "id": "8c042a38-71c1-1dcb-00df-54880236e0dc"
          }
        ]
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "freedom"
    }
  ]
}
```
