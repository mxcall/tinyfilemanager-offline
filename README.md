# TinyFileManager
容器化TinyFileManager(docker for TinyFileManager offline);

网上有现成的, 但是公司内网没有相关公共的js, css , 所以封装为docker做成离线的, 相关js,css挂到容器Nginx中;


Dockerfile参考的是 [kodexplorer](https://github.com/KodCloud-dev/kodexplorer)

# 自助构建

```
# clone 连接, cd 进去
docker build -t tinyfilemanager-offline:1.0.0 .
```



# 快速启动
```
docker run -d -p 80:80 tinyfilemanager-offline:1.0.0
```


# 启动+外挂文件

```
# 创建外挂文件
mkdir -p /myfiles
# 授权
chmod 777 /myfiles
# 启动 docker
docker run -d -p 80:80 -v /myfiles:/var/www/html tinyfilemanager-offline:1.0.0
```

# 参考链接

Docker镜像制作参考: 

[kodexplore](https://github.com/KodCloud-dev/kodexplorer)

[tinyfilemanager-docker](https://github.com/minostauros/tinyfilemanager-docker)

TinyFileManager配置参考(修改tinyfilemanager\index_files\index_config.php): 

[Tiny File Manager](https://tinyfilemanager.github.io/)









