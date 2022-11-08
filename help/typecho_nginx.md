# 配置文件

- 编辑 `Typecho` 的 `Nginx` 配置文件，在其中写入如下伪静态代码

   ```
       if (!-e $request_filename) {
           rewrite ^(.*)$ /index.php$1 last;
       }
       
       location / {
               if (-f $request_filename/index.html){
                       rewrite (.*) $1/index.html break;
               }
               if (-f $request_filename/index.php){
                       rewrite (.*) $1/index.php;
               }
               if (!-f $request_filename){
                       rewrite (.*) /index.php;
               }
       }
   ```

- 若单独写入以下代码会造成 `403 NOT FOUND`

   ```
       if (!-e $request_filename) {
           rewrite ^(.*)$ /index.php$1 last;
       }
   ```

- 若单独写入以下代码会造成 `404 - 页面没找到`

   ```
       location / {
           if (-f $request_filename/index.html){
                   rewrite (.*) $1/index.html break;
           }
           if (-f $request_filename/index.php){
                   rewrite (.*) $1/index.php;
           }
           if (!-f $request_filename){
                   rewrite (.*) /index.php;
           }
       }
   ```

# 某些问题：

## `Nginx` 在 `Centos` 没有 `sites-available` 和 `sites-enabled` 目录

- 在 `Nginx` 目录下创建 `sites-available` 和 `sites-enabled` 文件夹
- `vim nginx.conf` 修改 `Nginx` 配置文件
- 编辑 http 块内部，在合适位置添加如下内容

```
include /etc/nginx/sites-enabled/*;
```
