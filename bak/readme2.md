# 替换

$ sed -i 's/plugins=(git)/plugins=(git zsh-syntax-highlighting zsh-autosuggestions)/g' ~/.zshrc

# 添加

$ echo 'fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src' >> ~/.zshrc

sed -i '/^source $ZSH\/oh-my-zsh.sh$/i fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src' ~/.zshrc
ZSH_THEME="robbyrussell"
ZSH_THEME="spaceship"

sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="spaceship"/g' ~/.zshrc

    # 安装 oh my zsh
    && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" \

    # 安装 oh my zsh 插件，自动补全、命令高亮
    && git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1 \
    && ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme" \
    && sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="spaceship"/g'  ~/.zshrc \
    && sed -i '/^source $ZSH\/oh-my-zsh.sh$/i fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src' ~/.zshrc \
    && source ~/.zshrc

    https://github.com/zsh-users/zsh/archive/refs/tags/zsh-5.9.tar.gz

    https://codeload.github.com/zsh-users/zsh/tar.gz/refs/tags/zsh-5.9

     73d3173

         && yum -y install git vim wget ncurses-devel yodl autoconf gcc perl-ExtUtils-MakeMaker \

    && git clone --branch zsh-5.9 --depth 1 https://github.com/zsh-users/zsh.git \

    && cd zsh \

    && ./Util/preconfig \
    && ./configure \
    && make \
    && make install \

    && chsh -s /usr/local/bin/zsh \

    # 安装 oh my zsh
    && sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"





    ## 源码编译
    # yum -y groupinstall 'Development Tools' # 一系列的make可能用到的工具
    # tree sudo

https://udomain.dl.sourceforge.net/project/zsh/zsh/5.9/zsh-5.9.tar.xz
