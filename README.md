
# TinyFileManager-offline

## 项目介绍


TinyFileManager 是GitHub上已有的开源文件管理后台(PHP)项目, 部署简单, 只需把php文件放置到要管理的文件目录中即可, 支持文件上传下载, 支持创建目录, 支持文本预览等等, 非常小巧好用;
因其依赖的web资源, 如CSS和JS 等等, 需要在浏览器有外网的环境下才能正常加载使用,  恰巧一些公司内网环境下没有任何外网访问权限(云桌面,沙盒等等), 所以造成了离线环境下此软件不可用的状态;

TinyFileManager-offline 项目把原有的TinyFileManager相关的JS和CSS缓存下载到Nginx相关目录中,修改代码中相关资源的访问路径为本地Nginx路径, 并封装Nginx和PHP 环境到Docker镜像中;
最终打造出一款 `离线环境下 开箱即用 的 文件管理服务器` (docker for TinyFileManager in offline environment);


**GitHub地址**: [https://github.com/mxcall/tinyfilemanager-offline](https://github.com/mxcall/tinyfilemanager-offline)

**DockerHub地址**: [https://hub.docker.com/r/weiqi1217/tinyfilemanager-offline](https://hub.docker.com/r/weiqi1217/tinyfilemanager-offline)

## 项目使用

### 快速使用
此项目镜像已上传至DockerHub, 可以直接pull使用, 不需本地Build;
安装: 
```
# 创建待管理的文件夹
mkdir -p /myfiles
# 授权
chmod 777 /myfiles
# 启动
docker run -d -p 80:80 -v /myfiles:/var/www/html  weiqi1217/tinyfilemanager-offline:latest
```

测试: 
```
浏览器输入 ip:port 即可访问和使用
```

### 进阶配置
若要修改配置, 直接修改挂载目录的此文件即可, 相关配置说明参考 [Tiny File Manager](https://tinyfilemanager.github.io/)
```
/挂载目录如myfiles/index_files/index_config.php
```


### 自助构建

```
# clone 此项目, cd 进入, 然后执行如下命令
docker build -t tinyfilemanager-offline:1.0.0 .
```

### 导入导出镜像
可以在外网把镜像打包成文件, 把文件上传到内网中, 然后在内网中 将文件恢复为镜像, 这样就可以在内网环境下使用了;
```
## 导出镜像
docker save tinyfilemanager-offline:1.0.0 | gzip > tinyfilemanager-offline.tar.gz
## 导入镜像
docker load -i tinyfilemanager-offline.tar.gz
```



# 参考链接

1. Docker镜像制作参考: 

- [kodexplore](https://github.com/KodCloud-dev/kodexplorer)

- [tinyfilemanager-docker](https://github.com/minostauros/tinyfilemanager-docker)

2. TinyFileManager配置参考(修改tinyfilemanager\index_files\index_config.php): 

- [Tiny File Manager](https://tinyfilemanager.github.io/)







