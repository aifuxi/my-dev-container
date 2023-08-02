## CentOS7 切换阿里镜像源

1. 切换 yum 源

> 参考 [centos 镜像\_centos 下载地址\_centos 安装教程-阿里巴巴开源镜像站](https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b11M79BTK) 其中的 CentOS7 部分

```shell
# 从阿里的网站下载Centos-7.repo文件，存放到/etc/yum.repos.d/CentOS-Base.repo里
$ curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

# 把换好的CentOS-Base.repo里面的阿里内网地址改掉 mirrors.cloud.aliyuncs.com这个地址是阿里云ECS用户才能访问
$ sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo

# 清除本地旧缓存
$ yum clean all

# 构建新缓存
$ yum makecache

```

2. 安装 epel 并配置阿里的 epel 源

> epel 里有很多好用的包，具体可看这个[介绍](https://docs.fedoraproject.org/en-US/epel/)。

```shell

# 安装 epel-release
$ yum -y install epel-release

# 切换到阿里的 elep 源
$ curl -o /etc/yum.repos.d/epel.repo https://mirrors.aliyun.com/repo/epel-7.repo

# 再次重建缓存

# 清除本地旧缓存
$ yum clean all

# 构建新缓存
$ yum makecache
```

## 参考的链接

- [CentOS7 系统配置国内 yum 源和 epel 源](https://developer.aliyun.com/article/653767)

- [centos 镜像安装教程-阿里巴巴开源镜像站](https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b11M79BTK) 其中的 CentOS7 部分

- [yum 缓存命令：yum makecache fast 和 yum clean all](https://blog.csdn.net/A___LEi/article/details/118340579)

- [为 centos7 添加 EPEL 源](https://www.jianshu.com/p/d9337b89bfd0)
