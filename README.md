# HelloManjaro

一个简单的Manjaro安装与配置帮助

------
* 使用安装介质安装系统
* 添加软件源archlinux

  打开`/etc/pacman.conf`,添加如下文本
  
  ```plain
  [archlinuxcn]

  SigLevel = Optional TrustedOnly

  Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
  ```
    
* 安装`archlinuxcn-keyring`

    ```shell
    sudo pacman -S archlinuxcn-keyring
    ```
* 全面更新系统

    ```shell
    sudo pacman -Syyu
    ```
* 安装`yaourt`（方便安装其他软件）

    ```shell
    sudo pacman -S yaourt
    ```
* 安装输入法

  - 安装`fcitx`

    ```shell
    yaourt fcitx
    ```
    选择`fcitx`本体以及需要安装的输入法模块

  - 将以下文本添加到`~/.xprofile`中

    ```shell
    export XMODIFIERS=@im=fcitx
    export QT_IM_MODULE=fcitx
    export GTK_IM_MODULE=fcitx

    ```
* 更换`shell`为`zsh`

  - 安装`zsh`

    ```shell
    sudo pacman -S zsh
    ```
    
  - 切换当前`shell`为`zsh` （如果需要安装`ohmyzsh`可以跳过这一步）
    
    ```shell
    chsh -s /usr/bin/zsh
    ```
  - 安装`ohmyzsh` [(ohmyz.sh)](https://ohmyz.sh)

    ```shell
    # 通过`curl`
    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    
    # 通过`wget`
    sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
    ```
    
  - 切换`zsh`主题为`agnoster`,并移除用户名和主机名

    * 打开`~/.zshrc`
    * 将`ZSH_THEME`的值由默认的`robbyrussell`变更为`agnoster`
    * 添加如下命令移除用户名和主机名的显示
    
        ```shell
        DEFAULT_USER=username # username为当前用户名
        ```
    
    * 使变更生效
    
        ```shell
        source ~/.zshrc
        ```

  - 安装`zsh-syntax-highlighting` [(zsh-syntax-highlighting)](https://github.com/zsh-users/zsh-syntax-highlighting)

    * 克隆`zsh-syntax-highlighting`仓库

        ```shell
        git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
        ```
        
    * 打开`~/,zshrc`添加`zsh-syntax-highlighting`插件
    
        ```shell
        plugins=( [plugins...] zsh-syntax-highlighting)
        ```
    * 使变更生效
    
        ```shell
        source ~/.zshrc
        ```

  - 安装 `zsh-autosuggestions` [(zsh-autosuggestions)](https://github.com/zsh-users/zsh-autosuggestions)
    
    * 克隆`zsh-autosuggestions`仓库
    
        ```shell
        git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
        ```
        
    * 添加如下命令到~/.zshrc
    
        ```shell
        source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
        ```

* 使用`vim`

  - 安装`vim`本体
  
      ```shell
      sudo pacman -S vim
      ```
        
  - 安装`The Ultimate Vim Configuration`[(The Ultimate Vim Configuration)](https://github.com/amix/vimrc)
        
      ```shell
      git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
      sh ~/.vim_runtime/install_awesome_vimrc.sh
      ```

  - 安装`Vundle`(此处不再过多说明Vundle的配置方法，可以点击链接进行查看)[(Vundle)](https://github.com/VundleVim/Vundle.vim)

* 显卡驱动

  可以直接使用Manjaro自带的`MHWD`来安装

* 使用其他软件(均可在Github上找到）

  - `ShadowSocket` （翻墙）

    ```shell
    sudo pacman -S shadowsocket-qt5
    ss-qt5
    ```
    

  - `TheFuck` （命令输错时推理）
    
    ```python3
    pip3 install thefuck -i https://pypi.douban.com/simple
    fuck
    ```
    
  - `npm` （node包管理）

    ```shell
    sudo pacman -S npm
    npm -h
    ```

  - `yarn` （node包管理，Facebook出品）
    
    ```shell
    sudo npm i -g yarn
    yarn -h
    # 安装npm软件时可以用`yarn global add <package>` 代替 `npm i -g <package>`
    ```

  - `tldr` （命令帮助简化，Too Long Don't Read，太长不看）
    
    ```shell
    sudo npm i -g tldr
    tldr -h
    ```
    
  - 等等
