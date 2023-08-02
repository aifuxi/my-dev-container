FROM centos:7

WORKDIR /root/aifuxi

ENV SHELL /bin/bash

COPY oh_my_zsh_install.sh /root/aifuxi/install.sh

# 设置时区为咱中国
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    # 切换为阿里的 yum 源
    && curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo \
    && sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo \

    # 清空之前的缓存，重建缓存
    && yum clean all \
    && yum makecache fast \

    # 安装 epel ，并配置为阿里的 epel 源
    && yum -y install epel-release \
    && curl -o /etc/yum.repos.d/epel.repo https://mirrors.aliyun.com/repo/epel-7.repo \

    # 清空之前的缓存，重建缓存
    && yum clean all \
    && yum makecache fast \

    # 安装 endpoint 前必须先安装 epel
    # 安装 endpoint ，endpoint 上面有很多版本较新的包，比如 git2.x
    && yum -y install https://packages.endpointdev.com/rhel/7/os/x86_64/endpoint-repo.x86_64.rpm  \

    # 安装一些常用的包 git这里会安装 2.x 的版本(因为这里我们之前安装了 endpoint，endpoint上面有git 2.x的版本 )
    # 普通的 yum 源里面都是 1.x 的 git
    # 因为用 VSCode DevContainer时，总是提示远端 CentOS 上的 Git 版本（1.8.x）过低，建议升级到 2.x 版本 
    && yum -y install git vim wget zsh tree sudo ncurses-devel \

    # 一系列的make可能用到的工具
    && yum -y groupinstall 'Development Tools' \

    # 安装 oh my zsh
    && sh -c /root/aifuxi/install.sh \
    && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting \
    && git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions \
    && git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions \
    && sed -i 's/plugins=(git)/plugins=(git zsh-syntax-highlighting zsh-autosuggestions)/g'  ~/.zshrc \
    && sed -i '/^source $ZSH\/oh-my-zsh.sh$/i fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src' ~/.zshrc \
    && rm -rf /root/aifuxi/install.sh
    
ENV SHELL /bin/zsh