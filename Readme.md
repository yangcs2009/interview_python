**Table of Contents** 

<!-- vim-markdown-toc GFM -->
* [how to use and update vim markdown toc](#how-to-use-and-update-vim-markdown-toc)
    * [生成 Table of Contents](#生成-table-of-contents)
    * [更新已存在的 Table of Contents](#更新已存在的-table-of-contents)
    * [删除 Table of Contents](#删除-table-of-contents)
    * [安装方法](#安装方法)

<!-- vim-markdown-toc -->


# how to use and update vim markdown toc

##生成 Table of Contents

将光标移动到想在后面插入 Table of Contents 的那一行，然后运行下面的某个命令：

`:GenTocGFM`

生成 GFM 链接风格的 Table of Contents。

适用于 GitHub 仓库里的 Markdown 文件，比如 README.md，也适用用于生成 GitBook 的 Markdown 文件。

`:GenTocRedcarpet`

生成 Redcarpet 链接风格的 Table of Contents。

适用于使用 Redcarpet 作为 Markdown 引擎的 Jekyll 项目或其它地方。

##更新已存在的 Table of Contents

通常不需要手动做这件事，保存文件时会自动更新已经存在的 Table of Contents。

除非是在配置里关闭了保存时自动更新，并且维持插入 Table of Contents 前后的 <!-- vim-markdown-toc -->，此时可使用 `:UpdateToc` 命令手动更新。

##删除 Table of Contents

`:RemoveToc` 命令可以帮你删除本插件生成的 Table of Contents。

##安装方法

推荐使用 Vundle 来管理你的 Vim 插件，这样你就可以简单三步完成安装：

在你的 vimrc 文件中添加如下内容：

```
Plugin 'mzlogin/vim-markdown-toc'
:so $MYVIMRC
:PluginInstall
```
使用 vim-plug 安装的过程的与此基本一样。

