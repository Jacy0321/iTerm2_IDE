Mac iTerm2 Config Step
=======

1. 安装oh-my-zsh：
    - `curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh`
    - `chsh -s /bin/zsh` #将默认的bash切换到zsh

2. 安装*PowerLine*：
    `pip install powerline-status`
3. 安装字体库fonts-master：
       执行`./install.sh`指令安装所有Powerline字体
4. 设置iTerm 2的Regular Font 和 Non-ASCII Font:

    安装完字体库之后，把iTerm 2的设置里的Profile中的Text 选项卡中里的Regular Font和Non-ASCII Font的字体都设置成 Powerline的字体，我这里设置的字体是12pt Meslo LG S DZ Regular for Powerline
5. 安装配色方案solarized：
    - 如果你使用的是 Terminal 的话，在 solarized/osx-terminal.app-colors-solarized 下双击 Solarized Dark ansi.terminal 和 Solarized Light ansi.terminal 就会自动导入两种配色方案 Dark 和 Light 到 Terminal.app 里。
    - 如果你使用的是 iTerm2 的话，到 solarized/iterm2-colors-solarized 下双击 Solarized Dark.itermcolors 和 Solarized Light.itermcolors 两个文件就可以把配置文件导入到 iTerm 里。

    -  给vim配色成solarized：
        - `cp solarized/vim-colors-solarized/colors/solarized.vim ~/.vim/colors/`
        - `vim ~/.vimrc` #添加syntax enable ；`set background=dark ；colorscheme solarized`
6. zsh 使用agnoster主题：
    - 在文件夹oh-my-zsh-agnoster-fcamblor-master内运行install文件， 主题将安装到~/.oh-my-zsh/themes目录下
    - 进入~/.zshrc打开.zshrc文件，然后将ZSH_THEME后面的字段改为agnoster。ZSH_THEME="agnoster"（agnoster即为要设置的主题）
7.  增加指令高亮效果——zsh-syntax-highlighting:

    在.zshrc文件内添加以下内容
    source /Users/Jacy/.zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
    plugins=(zsh-syntax-highlighting)
8. ls 在agnoster主题下不高亮：<br/>
	`git clone https://github.com/seebi/dircolors-solarized`

	`mv dircolors.256dark .dir_colors`

	`brew install coreutils`

	vim .zshrc 将下面的内容拷贝进去
    ```
	if brew list | grep coreutils > /dev/null ; then
	  PATH="$(brew --prefix coreutils)/libexec/gnubin:$PATH"
	  alias ls='ls -F --show-control-chars --color=auto'
	  eval `gdircolors -b $HOME/.dir_colors`
	fi
    ```

