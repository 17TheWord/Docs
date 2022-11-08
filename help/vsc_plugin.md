# 快捷方式

- 快捷方式末尾添加如下参数，注意需一个空格

    ```
    code --extensions-dir "E:\VsCodeExtensions"
    ```

# 右键菜单

- 配置右键菜单，在注册表中进入

    ```
    计算机\HKEY_CLASSES_ROOT\*\shell\VSCode\command
    ```

- 将值修改为

    ```
    # 其中第一段为VSC路径，中间段为快捷方式中参数内容，最后为默认值
  
    "D:\Microsoft VS Code\Code.exe" --extensions-dir  "E:\Microsoft VS Code\Extensions" "%1"
    ```
