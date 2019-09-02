<!-- vim-markdown-toc GFM -->

* [Test Header](#test-header)
    * [安装Fcitx五笔和LaTeX输入法](#安装fcitx五笔和latex输入法)
    * [自动造词](#自动造词)
    * [快捷键：](#快捷键)
    * [快速输入](#快速输入)
    * [皮肤](#皮肤)
    * [问题](#问题)

<!-- vim-markdown-toc -->

# Test Header

## 安装Fcitx五笔和LaTeX输入法



首先声明，本人是Fcitx五笔86用户。喜欢自动上屏，与之对应的肯定是不喜欢输入法自动造词。以下设置请其他输入法用户谨慎借鉴。
```bash
sudo apt remove --auto-remove ibus
sudo apt purge ibus
sudo apt install fcitx fcitx-table-wubi fcitx-config-gtk fcitx-module-kimpanel fcitx-bin fcitx-modules fcitx-libs fcitx-ui-classic fcitx-tools fcitx-table-wubi fcitx-table-latex fcitx-config-gtk qt4-qtconfig 
```

利用 fcitx-tools 添加用户词时,运行 txt2mb wbx.txt wbx.mb指令后若提示某些词组已经存在于码表中，则先将其删除，再次运行。否则，fcitx 一个也不会接受～～～最后一步：重新启动Fcitx ！就可以输入用户词组了

## 自动造词

Fcitx配置→附加组件→码表→配置→选择wbx.config→点击设置→“自动词组”。


- 它是自动造词和手动造词的开关。选中了它，就有自动造词，不过质量惨不忍睹（ 重启后所有的自动词组都会消失）；取消选中它，那在输入过程中就不能手动造词，如果老师布置一个关于 "卡门涡流式空气流量计的工作原理"的作业怎么办？虽然可以复制粘贴，但不是长久之计。这里还有一个开关 **自动词组长度**，我们把值设为1,只有一个字，就不会有乱七八糟的词组了。
- 往下还有一个“词组参与自动造词”。若取消它，手动造词的时候就只能一个一个字来打。
- 如果不慎让Fcitx自动制造了没用的词组，使得打字时出现重码（时间与易云音重码）而不能自动上屏，这是很恶心的一件事！不过别担心，只需把`~/.config/fcitx/table/wubi_LastAutoPhrase.tmp`这个文件删除，然后重启Fcitx，那些恶心的词组就没了Y(^__^)Y

## 快捷键：

1. C-A-P:在嵌入码之间转换，只有两种——有汉字和无汉字无编码.后者较好
2. Fcitx 配置→全局配置→快捷键→显示高级选项:取消“输入法切换时包含未激活状态”,这样的话,在各种非英文输入法之间切换时,不会切换到英文输入法.即英文输入法的快捷键只有<Ctrl-Space>。
3. 像δ+α=γ和其他各种特殊符号是通过 **LaTeX输入法**完成滴。添加并切换至 **LaTeX输入法**，还要按下触发键 **反斜杠**。
   1. Δ,30°,→,↓



## 快速输入

Fcitx 配置→附加组件→快速输入→配置。码表规则是“编码<SPACE>短语”

或者用commandline，打开如图高亮的文件，如果没有请手动添加。然后按照右侧内容的规则添加并重启Fcitx

![快速输入](/home/lxk/Pictures/mountains-1412683.jpg)

## 皮肤

Fcitx配置→附加组件→经典界面→配置→皮肤名称：classic

## 问题
ubuntu-Appindicator扩展好像与Fcitx不兼容，配置完成后，Fcitx的界面是这样滴。



![Classic](/home/lxk/Pictures/Fcitx_classic.png)

虽然有下拉菜单，但死活拉不下来 <(=－︿－=)> ，这是软件包`fcitx-ui-classic`与Gnome的不兼容造成的。有如下两种方法解决：

1. 虚拟键盘和输入法可用快捷键`Ctrl-Alt-b`切换，皮肤就按照之前的方法设置。

2. 在gnome-tweaks中禁用ubuntu-Appindicator扩展。Fcitx的界面就变了，下拉菜单也能工作了。不过这个方法不推荐，因为有些打开的程序会消失。

![qim](/home/lxk/Pictures/Fcitx_qim.png)

3. 删除`fcitx-ui-classic`，安装 `fcitx-ui-qimpanel`。此时，皮肤名称仍然是dark，但是一点儿也不dark，反而是透明的。挺漂亮，但是太透明了●﹏●，在段落间码字时根本看不清输入框<(=╯▽╰=)>

