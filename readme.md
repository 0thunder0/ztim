# tvim使用说明文档
## 安装流程说明:

### 安装oh-my-zsh

```
sudo apt install zsh -y
sudo chsh -s $(which zsh)
echo $SHELL
sudo apt install git -y
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 安装vim依赖安装包,更新vim到最新版

```
sudo apt install tmux git tree python3-dev ctags build-essential cmake python-dev silversearcher-ag -y
sudo add-apt-repository ppa:jonathonf/vim
sudo apt update -y
sudo apt install vim -y
```

### 安装vim-plug

```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### 安装tvim配置

```
cp .vimrc ~/.vimrc -f
cp -f .zshrc ~/.zshrc
cp -f .tmux.conf ~/.tmux.conf
```

### 添加开启自启动

```
echo 'aria2c --conf-path=/root/.aria2/aria2.conf -D' >> /etc/rc.d/rc.local
#需要自启动的内容写到/etc/rc.d/rc.local文件中
echo '/etc/init.d/shadowsocks-r start' >> /etc/rc.d/rc.local
```

## 插件介绍:

>>外观-左窗口：NERDtree：目录管理工具    Plug 'https://github.com/scrooloose/nerdtree.git'

>>外观-状态栏：Airline:状态栏    Plug 'https://github.com/vim-airline/vim-airline.git'

>>外观-状态栏：Vim Powerline是一个显示vim状态栏插件，它能够显示vim模式、操作环境、编码格式、行数/列数等信息	Plug 'https://github.com/Lokaltog/vim-powerline.git'

>>外观-主题切换：change-colorscheme:快速切换主题的插件    Plug 'https://github.com/chxuan/change-colorscheme.git'

>>外观-主窗口启动页：vim-startify    Plug 'https://github.com/mhinz/vim-startify.git'

>>外观-右窗口：tagbar:tagbar是一个taglist的替代品，比taglist更适合c++使用，函数能够按类区分，支持按类折叠显示等，显示结果清晰简洁    Plug 'https://github.com/majutsushi/tagbar.git'

>>外观-下窗口：ctrlp:全局搜索是一个基于文件名的搜索功能，可以快速定位一个文件。这是ctrlp这个插件提供的功能    Plug 'https://github.com/kien/ctrlp.vim.git'

>>外观-下窗口：ctrlp-funky：可以模糊搜索文件内容的方法名     Plug 'https://github.com/tacahiroy/ctrlp-funky.git'

>>外观：WinManager：文件浏览器和缓冲区管理器    Plug 'https://github.com/vim-scripts/winmanager.git'

>>外观：vim-devicons：文件图标    Plug 'https://github.com/ryanoasis/vim-devicons.git'

>>外观：tabular：代码对齐。    Plug 'https://github.com/godlygeek/tabular.git'

>>外观：indentLine：更加美观的显示缩进对齐线  Plug 'https://github.com/Yggdroot/indentLine.git'

>>扩展增强：vim-mkdir：当你在Vim中新建文件的时候，自动帮你创建不存在的目录。    Plug 'https://github.com/pbrisbin/vim-mkdir.git'

>>扩展增强：rename.vim：在Vim中为文件重命名。    Plug 'https://github.com/danro/rename.vim.git'

>>基础：vim-multiple-cursors:多行编辑插件. 		Plug 'https://github.com/terryma/vim-multiple-cursors'

>>基础：vim-surround：快速的删除、修改和添加括号、引号、XML标签等等。    Plug 'https://github.com/tpope/vim-surround.git'

>>基础：syntastic：语法检查插件    Plug 'https://github.com/vim-syntastic/syntastic.git'

>>基础：auto-pairs:隆重推荐括号补全插件    Plug 'https://github.com/jiangmiao/auto-pairs.git'

>>代码向python：pydiction:python 自动补全 Plug 'git@github.com:vim-scripts/Pydiction.git'

>>代码向php：phpcomplete.vim：php补全    Plug 'https://github.com/shawncplus/phpcomplete.vim.git'

>>代码向html：vim-coloresque:css颜色可视化    Plug 'https://github.com/gko/vim-coloresque.git'

>>代码向html：emmet-vim：Emmet的Vim版。    Plug 'https://github.com/mattn/emmet-vim.git'

>>代码向html：CLOSETAG:成对标签补全 Plug 'https://github.com/docunext/closetag.vim.git'

>>代码向c/c++：OmniCppComplete:vim-c/c++自动补全，主要提供输入时实时提供类或结构体的属性或方法的提示和补全。跟Talist一样，OmniCppComplete也是一个Vim插件，同样依赖与Ctags工具生成的tags文件。安装步骤跟Taglist类似。    Plug 'https://github.com/vim-scripts/OmniCppComplete.git'

>>代码向：YouCompleteMe:自动补全插件    Plug 'https://github.com/Valloric/YouCompleteMe.git'

>>代码向：nerdcommenter：快速注释    Plug 'https://github.com/scrooloose/nerdcommenter.git'

## 使用说明
1.控制:NERDTree
```
nmap <F3> :NERDTreeToggle<CR>
"让NERDTree显示隐藏文件
let NERDTreeShowHidden=1 
```
### 按F3键控制左侧NERDTree的开启
2.控制tagbar
```
let g:tagbar_width = 30
nmap <F4> :TagbarToggle<CR>
"开启自动预览(随着光标在标签上的移动，顶部会出现一个实时的预览窗口)
let g:tagbar_autopreview = 1
"关闭排序,即按标签本身在文件中的位置排序
let g:tagbar_sort = 0
```
### 按F4键控制右侧tagbar的开启
3.ctrlp插件的配置和使用
```
let g:ctrlp_cmd = 'CtrlP'
"<Leader>f搜索MRU文件
nmap <Leader>f :CtrlPMRUFiles<CR>
"<Leader>b显示缓冲区文件，并可通过序号进行跳转
nmap <Leader>b :CtrlPBuffer<CR>
"设置搜索时忽略的文件
let g:ctrlp_custom_ignore = {
    \ 'dir':  '\v[\/]\.(git|hg|svn|rvm)$',
    \ 'file': '\v\.(exe|so|dll|zip|tar|tar.gz|pyc)$',
    \ }
let g:ctrlp_working_path_mode = 0
let g:ctrlp_match_window_bottom = 1
"修改QuickFix窗口显示的最大条目数
let g:ctrlp_max_height = 15
let g:ctrlp_match_window_reversed = 0
"设置MRU最大条目数为500
let g:ctrlp_mruf_max = 500
let g:ctrlp_follow_symlinks = 1
"默认使用全路径搜索，置1后按文件名搜索，准确率会有所提高，可以用<C-d>进行切换
let g:ctrlp_by_filename = 1
"默认不使用正则表达式，置1改为默认使用正则表达式，可以用<C-r>进行切换
let g:ctrlp_regexp = 0
"自定义搜索列表的提示符
let g:ctrlp_line_prefix = '♪ '
```
### ctrl+p开启文件搜索
4.主题切换：change-colorscheme：该插件将会在 ~/.vim/colors搜索主题
```
nmap <F10> :NextColorScheme<CR>
nmap <F9> :PreviousColorScheme<CR>
```
### 91切换到上一个主题
### F10切换到下一个主题
5.代码对齐插件
```
let g:multi_cursor_start_key='<C-n>'
let g:multi_cursor_start_word_key='g<C-n>'
let g:multi_cursor_next_key='<C-n>'
let g:multi_cursor_prev_key='<C-p>'
let g:multi_cursor_skip_key='<C-x>'
let g:multi_cursor_quit_key='<Esc>'
```
6.多行编辑插件：vim-multiple-cursors
```
```
7.vim内重命名：rename.vim
```
:rename[!] {newname}
```
8.外观-状态栏：Vim Powerline
```
set encoding=utf-8
set fillchars+=stl:\ ,stlnc:\	
set laststatus=2	#状态线隐藏/只出现在分割窗口中！
set -g default-terminal "screen-256color"  #放在.tmux.conf
```
9.多行注释插件：nerdcommenter快速注释
```
" 注释的时候自动加个空格, 强迫症必配
let g:NERDSpaceDelims=1
```
### 使用
#### NERD_commenter定义的<Leader>cc映射，所以你按（一个接一个） \cc。
```
"默认状态下  <leader>  是 \
\cc   当前行加注释
\cu   解开当前行注释
\c<space>  加上/解开注释, 智能判断
\cy   先复制, 再注解(p可以进行黏贴)
注：多行注释，前面加数字，  2\cc  给当前2行加注释
"将<Leader>密钥从\角色更改为更易于访问的,密钥
let mapleader=","
set timeout timeoutlen=1500
```
10.文本对齐插件：tabular

:Tab /[str] 
> [str] 需要对讲机的字符

11.emmet基本规则:
1. E 代表HTML标签
2. E#id 代表标签E有id属性
3. E.class 代表E有class属性
4. E[attr=foo] 代表某个特定属性
5. E{info} 代表标签E包含的内容是info
6. E>N 代表N是E的子元素
7. E+N 代表N是E的同级元素
8. E^N 代表N是E的上级元素
