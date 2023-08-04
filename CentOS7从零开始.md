```shell
yum -y install git zsh wget vim which


git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
# source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh

git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.zsh/zsh-syntax-highlighting
# source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

echo "source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
echo "source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc

echo 'eval "$(starship init zsh)"' >> ~/.zshrc

# z
git clone https://github.com/rupa/z.git ~/.zsh/z
echo ". ~/.zsh/z/z.sh" >> ~/.zshrc


# 安装 Go
wget https://go.dev/dl/go1.20.7.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.zshrc
source ~/.zshrc

# 开启go module
go env -w GO111MODULE=on

# 使用阿里云的代理
go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct


# nvm
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash

echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> ~/.zshrc
echo 'export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node/' >> ~/.zshrc

# node
nvm install v16.20.1
nvm alias default v16.20.1
npm config set registry=https://registry.npmmirror.com
```

~/.zshrc

```
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
eval "$(starship init zsh)"
. ~/.zsh/z/z.sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node/
export PATH=$PATH:/usr/local/go/bin
```
