# 安装

- 添加 `deadsnakes PPA` 到源列表

    ```shell
    add-apt-repository ppa:deadsnakes/ppa apt update
    ```

- 更新资源

    ```shell
    apt update
    apt upgrade
    ```

- 安装 `Python3.10`

    ```shell
    apt install python3.10
    ```

---

# 修改默认版本（以下方法任选一）

## `update-alternatives` 命令

- 查看所有python版本

    ```shell
    ls -l /usr/bin/python*
    ```

- 更换版本

    ```shell
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
    ```

- 选择默认版本

    ```shell
    update-alternatives --config python3
    ```

---

## 软连接

- 查询 `Python3.10` 的安装路径（按照上方步骤默认为：`/usr/bin/python3`）

    ```shell
    which python3.10
    ```

- 得到结果

    ```shell
    /usr/bin/python3.10
    ```

- 删除原有链接

    ```shell
    rm /usr/bin/python3
    ```

- 建立新链接

    ```shell
    ln -s /usr/bin/python3.10 /usr/bin/python3
    ```

---

## 环境变量

- 编辑 `.bashrc` 文件

    ```shell
    vim  ~/.bashrc
    ```

- 找到 `alias python='xxx'`

- 将路径改为 `Python3.10` 的路径

    ```bash
    alias python='/usr/bin/python3.10'
    ```

- 使环境变量生效

    ```shell
    source ~/.bashrc
    ```

---

# 修复文件

- 报错（`pip` 相关命令可能会报这些错误）：

    ```shell
    ModuleNotFoundError: No module named 'apt_pkg'
    
    ModuleNotFoundError: No module named 'distutils.util'
    ```

- 修复

    ```shell
    apt install python3.10-distutils
    ```

- 重装 `pip` （确保为 `Python3.10` 成功安装 `pip`）

    ```shell
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python3 get-pip.py
    ```

- 如果您看到任何权限错误，您可能需要使用

    ```shell
    python3 get-pip.py --user
    ```

---

# 修改 pip 指向（以下方法任选一）

## `pip` 配置文件

- 编辑 `pip` 配置文件

    ```shell
    vim /usr/local/bin/pip3
    ```

- 把第一行 `/usr/bin/python` 换成 `python3`

    ```
    #!/usr/bin/python3
    # -*- coding: utf-8 -*-
    import re
    import sys
    from pip._internal.cli.main import main
    if __name__ == '__main__':
        sys.argv[0] = re.sub(r'(-script\.pyw|\.exe)?$', '', sys.argv[0])
        sys.exit(main())
    ```

## 软连接

- 查询 `pip3` 位置

    ```shell
    which pip3
    ```

- 删除旧链接

    ```shell
    rm /usr/bin/pip3
    ```

- 修改软连接

    ```shell
    ln -s /usr/bin/pip3 /usr/bin/pip3
    ```
