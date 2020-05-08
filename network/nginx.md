# Introduction #

Add your content here.


# 开发时权限问题 #
有时候当Nginx读取本地目录时会收到403错误，权限问题。
先来了解一下Nginx的用户管理，Nginx在以Linux service脚本启动时，通过start-stop-domain启动，会以root权限运行daemon进程。
 
然后daemon进程读取/etc/nginx/nginx.conf文件中的user配置选项，默认这里的user=nginx
也就是用nginx用户启动worker process。403错误就是因为nginx用户没有权限访问我当前开发用的用户目录，/home/dean/work/resources。
 
解决方法是将user=nginx替换成root，然后重新启动nginx，可以了。
其他方法也试过，比如给/home/dean/work/resources目录设置777权限，比如将nginx用户加入root组，都不行。
 
所以当开发的时候，就用user=root配置吧。至于产品环境下，resouces目录完全可以放到nginx用户目录下，所以问题不大。

# ubuntu 配置 #
```
/etc/nginx/sites-available/default
```

# 限速 #
```
server {
        location /200k {
                limit_rate 200k;
                autoindex on;
        }
}
```