# 一：安装要求

 vim 版本需大于7.4.1578， 并且支持python2或python3。 测试版本用 vim --version 命令，如果是7.4，就要看下面的Included patches: 1-1689 ，要保证1-z中的z>=1578. 测试是否支持python2 或 python3 在vim中用命令：:echo has('python') || has('python3')， 如果输出1则是支持的，如果不满足要用源码编译vim 或升级一下。[源码编译vim](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source)

# 二：安装步骤
## 1. 克隆vim IDE文件夹
```
$ git clone https://github.com/huzhaoyangcode/VimIDE.git
```
## 2.安装.vimrc文件
```
//备份家目录下的.vimrc
$ mv ~/.vimrc ~/.vimrc_bak  
//链接VimIDE文件夹中的.vimrc到家目录下
$ cd /path/of/VimIDE
$ ln -s `pwd`/.vimrc ~/.vimrc
```

## 3.下载插件
```
//下载Vundle插件管理
 $ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
 //用Vundle下载其他插件
 $ vim +PluginInstall
```
## 4.把mysnippets文件夹拷贝到.vim/bundle/ultisnips中
```
//ultisnips 插件是用来模板补全的插件，mysnippets中的文件是写的规则
$ cd /path/of/VimIDE
$ cp -r ./mysnippets/ ~/.vim/bundle/ultisnips/
```
## 5.编译YCM

```
//ubuntu16.04 
$ sudo apt install build-essential cmake python3-dev
$ cd ~/.vim/bundle/YouCompleteMe
$ sudo python3 install.py --clang-completer --clangd-completer
```

## 6.YCM使用说明
### database使用：
该方法会自动根据CMakeList.txt自动生成flag数据库用于补全参考。
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON ..
然后把生成的compile_commands.json 拷贝到build 外层

### flags使用：
使用.ycm_extra_conf.py 进行手动定义编译flag. VimIDE中的
ycm_conf_file中的模板拷贝到项目然后根据项目修改文件
或者放在家目录下，

NOTE: 两种方式都是为了让YCM告诉判断编译器对于某个文件使用那些flag.YCM会从内到外搜索数据库和.ycm_extra_conf.py 数据库和配置文件二选一进行使用。
# 三：参考文档：
[总中文参考文档](https://github.com/yangyangwithgnu/use_vim_as_ide)
[YCM安装文档](https://github.com/Valloric/YouCompleteMe)


