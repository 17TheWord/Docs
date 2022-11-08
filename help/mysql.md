# 在 Ubuntu 中添加 MySQL APT 存储库

- `Ubuntu` 已经附带了默认的 `MySQL` 软件包存储库。
- 为了添加或安装最新的存储库，我们将安装其他软件包存储库。
- 使用以下命令下载存储库：

  ```shell
  sudo apt update
  sudo apt install wget -y
  wget https://dev.mysql.com/get/mysql-apt-config_0.8.12-1_all.deb
  ```

- 下载后，通过运行以下命令安装存储库：

  ```shell
  sudo dpkg -i mysql-apt-config_0.8.12-1_all.deb
  ```

- 在提示符下，选择 `Ubuntu Bionic`，然后单击 `确定`

- 下一个提示显示默认情况下选择的 `MySQL 8.0`。选择第一个选项，然后单击 `确定`

- 在下一个提示符中，选择 `MySQL 5.7` 服务器，然后单击 `确定`。

- 默认情况下，下一个提示选择 `MySQL5.7`。选择最后一个 `otpion` 确定，然后单击 `确定`

---

# 在Ubuntu上更新MySQL存储库

- 运行以下命令以更新系统软件包

  ```shell
  sudo apt-get update
  ```

- 现在使用apt缓存搜索 `MySQL 5，7`，如下所示：

  ```shell
  sudo apt-cache policy mysql-server
  
  # 返回以下信息
  mysql-server:
    Installed: (none)
    Candidate: 8.0.26-0ubuntu0.20.04.2
    Version table:
    8.0.26-0ubuntu0.20.04.2 500
      500 http://mirrors.digitalocean.com/ubuntu focal-updates/main amd64 Packages
      500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
    8.0.19-0ubuntu5 500
      500 http://mirrors.digitalocean.com/ubuntu focal/main amd64 Packages
    5.7.35-1ubuntu18.04 500
      500 http://repo.mysql.com/apt/ubuntu bionic/mysql-5.7 amd64 Packages
  ```

- `MySQl 5.7.31-1ubuntu18.04` 出现在列表中。

---

# 在 Ubuntu 20.04 Linux 计算机上安装 MySQL 5.7

- 在系统中找到 `MySQL 5.7` 后，使用以下命令安装 `MySQL 5.7` 客户端、`MySQL 5.7` 服务器：

  ```shell
  sudo apt install -f mysql-client=5.7* mysql-community-server=5.7* mysql-server=5.7*
  
  # 输出信息
  Reading package lists... Done
  Building dependency tree
  Reading state information... Done
  Selected version '5.7.35-1ubuntu18.04' (MySQL:repo.mysql.com [amd64]) for 'mysql-client'
  Selected version '5.7.35-1ubuntu18.04' (MySQL:repo.mysql.com [amd64]) for 'mysql-community-server'
  Selected version '5.7.35-1ubuntu18.04' (MySQL:repo.mysql.com [amd64]) for 'mysql-server'
  The following additional packages will be installed:
    libmecab2 libtinfo5 mysql-common mysql-community-client
  The following NEW packages will be installed:
    libmecab2 libtinfo5 mysql-client mysql-common mysql-community-client mysql-community-server mysql-server
  0 upgraded, 7 newly installed, 0 to remove and 90 not upgraded.
  Need to get 51.6 MB of archives.
  After this operation, 315 MB of additional disk space will be used.
  
  # 输入 y 键开始在 Ubuntu 20.04 Linux 上安装 MySQL 5.7。
  Do you want to continue? [Y/n] y
  ```

- 出现提示时输入并重新输入 `root` 密码

---

# 在 Ubuntu 20.04 上安全安装 MySQL 5.7

- 运行以下命令以保护 `MySQL`

  ```shell
  sudo mysql_secure_installation
  ```

- 按回车键。当系统提示输入密码时，请提供上面设置的 `root` 密码。

- 按如下方式回答提示：

  ```shell
  Enter current password for root (enter for none): <Enter password>
  VALIDATE PASSWORD PLUGIN can be used to test passwords
  and improve security. It checks the strength of password
  and allows the users to set only those passwords which are
  secure enough. Would you like to setup VALIDATE PASSWORD plugin?
  Press y|Y for Yes, any other key for No: Y
  
  There are three levels of password validation policy:
  
  LOW    Length >= 8
  MEDIUM Length >= 8, numeric, mixed case, and special characters
  STRONG Length >= 8, numeric, mixed case, special characters and dictionary
  
  Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 1
  Using existing password for root.
  Estimated strength of the password: 25  
  Change the password for root ? ((Press y|Y for Yes, any other key for No) : d
  Remove anonymous users? [Y/n] Y
  Disallow root login remotely? [Y/n] Y
  Remove test database and access to it? [Y/n] Y
  Reload privilege tables now? [Y/n] Y
  Thanks for using MariaDB!
  ```

---

# 检查Ubuntu 20.04上的MySQL 5.7版本

- 要确认安装的版本，首先，使用设置的 `root` 密码连接到 `MySQL`。

  ```shell
  mysql -u root -p
  
  # 输入密码
  Enter password:
  
  # 登录成功后输出以下信息
  Welcome to the MySQL monitor.  Commands end with ; or \g.
  Your MySQL connection id is 6
  Server version: 5.7.35 MySQL Community Server (GPL)
  
  Copyright (c) 2000, 2021, Oracle and/or its affiliates.
  
  Oracle is a registered trademark of Oracle Corporation and/or its
  affiliates. Other names may be trademarks of their respective
  owners.
  
  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
  
  mysql>
  ```

- 运行以下命令以显示版本

  ```
  SELECT VERSION();
  ```

  ```shell
  # 输出以下内容
  +-----------+
  | VERSION() |
  +-----------+
  | 5.7.35    |
  +-----------+
  1 row in set (0.00 sec)
  ```

---

# 创建MySQL用户（可选，仅限测试）

- 连接到 `MySQL` 时，运行以下命令以创建用户：

  ```
  CREATE USER 'user'@'%' IDENTIFIED BY 'MyStrongPass.';
  GRANT ALL PRIVILEGES ON * . * TO 'user'@'%';
  FLUSH PRIVILEGES;
  
  # 退出
  exit;
  ```

---

# 启用 MySQL 远程访问（可选）

- 默认情况下，`MySQL` 远程访问处于禁用状态。要启用它，我们需要编辑 `mysqld.cnf` 文件，如下所示：

  ```shell
  sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
  ```

- 查找行 `bind_address` 并更改如下：

  ```text
  # By default we only accept connections from localhost
  # bind-address   = 127.0.0.1
  bind-address   = 0.0.0.0
  ```

- 保存文件并重新启动 `MySQL`

  ```shell
  sudo systemctl restart mysql
  ```

- 允许通过防火墙进行远程连接

  ```shell
  sudo ufw allow from <remote_IP_address> to any port 3306
  sudo ufw enable
  ```

- 要从远程计算机访问数据库，请运行以下命令：

  ```shell
  mysql -u user -h ip -p
  ```

# 完成

- 您已成功在 `Ubuntu 20.04` 上安装了 `MySQL 5.7`。
