---
layout: default
title: rime
parent: skill
---

# Layout Utilities
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## rime/weasel/小狼毫
> [Rime](https://github.com/rime) 输入法是一款适用于多平台（Mac OSX, Linux, Windows）的开源输入法

Rime 在不同平台下的对应名称如下：
* Mac OSX: 鼠鬚管 ([Squirrel](https://github.com/rime/squirrel))
    配置目录：`~/Library/Rime/`
* Linux: 中州韻 (ibus-rime)
    配置目录：`~/.config/ibus/rime/`
* Windows: 小狼毫 (Weasel)
    配置目录：`%APPDATA%\Rime`

Rime 的配置文件不同平台的放置在不同的目录，
在配置目录中，主要使用 `yaml` 进行配置。
目录中自有的配置文件不建议直接修改，因为可能会被自动复写。
用户配置一般以原始配置文件名增加 .custom 二级后缀的方式，
例如：Mac OSX 下的原始配置 `squirrel.yaml`，对应的用户配置就是
`squirrel.custom.yaml` 文件。

修改 `.custom` 配置后，『重新部署』Rime 输入法会将用户的配置增加或更新到
对应的原始配置中。

## 相关资源


- 小狼毫输入法：<https://github.com/rime/weasel>、<https://rime.im/>
- 同文输入法：<https://github.com/osfans/trime>
- 简繁转换opencc(Open Chinese Convert)：<https://github.com/BYVoid/OpenCC> 

- Emoji 插件：<https://github.com/rime/rime-emoji>
- [Rime 定製指南](https://github.com/rime/home/wiki/CustomizationGuide)
- [說明書#同步用戶資料](https://github.com/rime/home/wiki/UserGuide#同步用戶資料)
- [如何从 QIM 迁移至 Squirrel（鼠鬚管）](http://cocoabob.ddns.net/?p=919)

## 操作说明

1. 安装[Rime输入法](https://rime.im/),别名：小狼毫,并注销或重启计算机
2. 下载仓库所有配置文件到本地
3. 将下载的除字体外的所有文件覆盖到用户设定文件夹
4. 安装字体花园明朝 ( font 目录)
5. 也可以在“用户文件夹”中查看
6. 右键点击rime输入法图标，点击重新部署，部署完毕即可用

> 每次修改需重新部署方可生效使用
用户设定文件夹在不同的系统下也有不同,如下:

**Windows**

- Weasel: %APPDATA%\Rime

**Mac OS X**

- Squirrel: ~/Library/Rime

**Linux**

- Bus: ~/.config/ibus/rime
- Fcitx: ~/.config/fcitx/rime

## 输入法配置说明

配置文件中大部分都有注释。

- `default.custom.yaml` 设置输入法、如何切换输入法、翻页等
- `double_pinyin_flypy.custom.yaml` 双拼方案，
- `squirrel.custom.yaml` 鼠须管( Mac 版本 )设置哪些软件默认英文输入，输入法皮肤等
- `weasel.custom.yaml` 小狼毫( Win 版本 )设置哪些软件默认英文输入，输入法皮肤等
- `custom_phrase.txt` 设置快捷输入，修改完成后要重新部署才能生效

### 皮肤选择
win11系统中右下角，右键小狼毫图标选择“输入法设定”，点击“中”，然后就可以选择皮肤了。

### 候选词个数和更改候选词框为横向

**小狼毫初始的候选词个数只有5个，允许范围是 1-9 个候选**

### 双拼默认简体

原作者是台湾人，所以默认是正体字输出，但是其实这个框架也提供了简体字的输出方式，只需要在设置目录里新建或者编辑double_pinyin_mspy.custom.yaml这个文件，如果你用的是其他双拼方案就把文件名作对应修改。文件内容增加（注意缩进和冒号后面的空格）

~~~
patch:
  switches:                  
    - name: ascii_mode
      reset: 0               
      states: [ 中文, 西文 ] 
    - name: full_shape       
      states: [ 半角, 全角 ]  
    - name: simplification
      reset: 1                
      states: [ 漢字, 汉字 ]
~~~

保存后重新部署鼠须管即可


