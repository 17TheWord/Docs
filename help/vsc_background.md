# 安装拓展

- 运行 `VSCode`，安装作者名为 `shalldie` 的 `background` 拓展

---

# 设置

- 通过拓展右下角的`小齿轮`进入拓展设置，取消勾选 `Use Default`（使用默认图片）
- 在拓展设置界面找到 `Custom Images` 下方的 `setting.json` 进入设置界面

---

# 修改代码

- 复制以下代码并根据自身需求修改

    ```
    // background 的相关配置
    "update.enableWindowsBackgroundUpdates": false,
    "background.useFront": true,
    "background.useDefault": false, //是否使用默认图片
    "background.customImages": ["file:///E:/Pictures/Example.jpg"], //图片路径
    "background.style": {
        "content":"''",
        "pointer-events":"none",
        "position":"absolute",
        "width":"100%",
        "height":"100%",
        "z-index":"99999",
        "background.repeat":"no-repeat",
        "background.position":"center",
        "background.attachment":"fixed",
        "background-size":"cover",
        "opacity":0.35 //透明度
    },
    ```

---

# 更多设置

- 按 `Ctrl+S` 键保存当前设置，右下角会提示重启VSCode来加载设置。

    - VSCode支持多张背景图片（最多三张，在你分屏时使用）
    - 在代码段：在路径中填写两张图片地址，在 `style` 中写两次背景样式

    ```
    // background 的相关配置
    "update.enableWindowsBackgroundUpdates": false,
    "background.useFront": true,
    "background.useDefault": false, //是否使用默认图片
    "background.customImages": ["file:///E:/Pictures/Example1.jpg","file:///E:/Pictures/Example2.jpg"], //图片路径
    "background.style": [
        {
        "content":"''",
        "pointer-events":"none",
        "position":"absolute",
        "width":"100%",
        "height":"100%",
        "z-index":"99999",
        "background.repeat":"no-repeat",
        "background.position":"center",
        "background.attachment":"fixed",
        "background-size":"cover",
        "opacity":0.35 //透明度
        },
        {
        "content":"''",
        "pointer-events":"none",
        "position":"absolute",
        "width":"100%",
        "height":"100%",
        "z-index":"99999",
        "background.repeat":"no-repeat",
        "background.position":"center",
        "background.attachment":"fixed",
        "background-size":"cover",
        "opacity":0.35 //透明度
        }],
    ```
