## 启用PHP存储库

- 执行如下命令启用 `ondrej/php` 的 `PHP` 存储库：

    ```shell
    sudo apt update
    sudo apt install software-properties-common  
    sudo add-apt-repository ppa:ondrej/php
    ```

- 更新库文件

    ```shell
    sudo apt update
    sudo apt install php8.1-fpm
    ```

## 启用 PHP （Nginx）

- 在Nginx虚拟服务器配置文件中写入以下代码：

    ```
    location ~ \.php$ {
        # 设置监听（ 端口 与 UNIX 只能二选一）
        # unix段中路径请参考修改，端口一般为9000
        # fastcgi_pass   127.0.0.1:9000; 
        fastcgi_pass   unix:/run/php/php8.1-fpm.sock;
        # 设置nginx的默认首页文件(上面已经设置过了，可以删除)
        fastcgi_index  index.php;
        # 设置脚本文件请求的路径
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        # 引入fastcgi的配置文件
        include        fastcgi_params;
    }
    ```

### 监听（`Unix` 与 `端口` 的区别）

> TCP是使用TCP端口连接 `127.0.0.1:9000`
> > fastcgi_pass 127.0.0.1:9000
>
> Socket是使用 `unix domain socket` 连接套接字 `/run/php/php8.1-fpm.sock`
> > fastcgi_pass unix:/run/php/php8.1-fpm.sock
>
> 在服务器压力不大的情况下，`tcp` 和 `socket` 差别不大，但在压力比较满的时候，用套接字方式，效果确实比较好。

### 常用拓展

```shell
apt install php8.1-PDO php8.1-Mbstring php8.1-Tokenizer php8.1-GD php8.1-XML php8.1-Ctype php8.1-JSON php8.1-fileinfo php8.1-zip php8.1-mysql
```
