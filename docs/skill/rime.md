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

## 是是

### 一、皮肤选择
win11系统中右下角，右键小狼毫图标选择“输入法设定”，点击“中”，然后就可以选择皮肤了。

## 是是
### 二、候选词个数和更改候选词框为横向

#### **小狼毫初始的候选词个数只有5个，允许范围是 1-9 个候选**
win11系统中右下角，右键小狼毫图标选择“用户文件夹”，打开Rime的用户文件夹（在 用户目录AppDataRoamingRime下），找到“default.custom.yaml”文件，如果没有就新建一个，在后面加上这几行
patch:
"menu/page_size": 7
注意：如果原内容已有patch:不可重复patch:这一行。

#### **候选框是竖向的改成横向的，用户文件夹找到“weasel.custom.yaml”文件，在后面加上这些**
patch:
"style/horizontal": true

### 三、导入搜狗词库
很多词打不出来比较难受，所以我决定导入搜狗词库。

#### **方法1:直接下载词库：**
点击下载搜狗标准词库转化后的版本：[luna_pinyin.sogou.dict.yaml](https://note.youdao.com/yws/api/personal/file/WEBd5257ae39e75ae22a880361ff11110e6?method=download&shareKey=5a50b27e09e0a205aef4abbf7731d25e)

#### **方法2:自己动手下载词库转换词库：**
首先去搜狗官网下载[搜狗标准词库](https://pinyin.sogou.com/dict/detail/index/11640)，这个时候是.scel文件，然后用[深蓝词库转换工具](https://note.youdao.com/yws/api/personal/file/WEB88925041ceb5b7da7e6b0da8deedfe10?method=download&shareKey=13c1e229923310cc2f5acc5163371b3f)将文件转换为Rime词库适用的txt格式。 然后将转换后的txt文件最前面加上以下内容，并将其重命名为”luna_pinyin.sogou.dict.yaml“
# Rime dictionary
# encoding: utf-8

---
name: luna_pinyin.sogou
version: "2015.12.24"
sort: by_weight
use_preset_vocabulary: true
import_tables:
- luna_pinyin
...
配置过程 将这个”luna_pinyin.sogou.dict.yaml“文件移动到Rime的用户文件夹。
然后在用户文件夹新建”luna_pinyin_simp.custom.yaml“文件，在里面输入这些
patch:
translator/dictionary: luna_pinyin.sogou

### 四、快捷输出当前日期/时间
目前最新的版本已经自带了这个函数，只需要改下配置就可以使用。

#### 在用户文件夹——bulid文件夹下找到 luna_pinyin.schema.yaml （如果是要在朙月拼音输入法下打日期就选择这个luna，其他输入法类推）
在engine - translators （在第40行）下面加入
- lua_translator@time_translator

#### 在用户文件夹下新建一个文件，添加如下内容后，改名为rime.lua
function time_translator(input, seg, env)
if (input == "rq") then
local cand = Candidate("date", seg.start, seg._end, os.date("%Y-%m-%d"), "")
cand.quality = 1
yield(cand)
end
if (input == "sj") then
local cand = Candidate("time", seg.start, seg._end, os.date("%H:%M"), " ")
cand.quality = 1
yield(cand)
end
end


### 四、快捷输出当前日期/时间

[官方的定制指南](https://github.com/rime/home/wiki/CustomizationGuid/)
[RIME中州韵输入法引擎](https://rime.im/download/)官网下载输入法
设置方法：在已启动 RIME条件下，按Ctrl+grave（Tab上面的~）进行方案选择
├── default.custom.yaml  # 全局设置
├── squirrel.custom.yaml # 鼠须管的皮肤设置
├── weasel.custom.yaml   # 小狼毫的皮肤设置,会根据你的命令修改weasel.yaml，wealsel.yaml文件在RIME更新时将被重置为默认设置。

├── pinyin_simp.schema.yaml # 拼音方案（关键配置文件）
├── pinyin_simp.dict.yaml   # 挂载词库
├── cn_dicts/               # 词库目录
├── symbols.custom.yaml     # 自定义的 symbols，单独拆分出来了

├── melt_eng.schema.yaml # 英文方案
├── melt_eng.dict.yaml   # 挂载词库
├── en_dicts/            # 词库目录

├── fixed.txt         # 固顶字
├── opencc/           # 词语映射
├── rime.lua          # lua 脚本
└── zh-hans-t-essay-bgw.gram  # 八股文语言模型

中文输入模式，打 /fh，候选框就会出现特殊符号了。打 /xl，候选框就会出现希腊字符了。
| **方案ID** | **方案名称** | 
| --- | --- |
| luna_pinyin | 朙月拼音 | 
| bopomofo | 注音 | 
| bopomofo_express | 注音-快打方式 | 
| bopomofo_tw | 注音-台湾正体 | 
| cangjie5 | 仓颉五代 | 
| cangjie5_express | 仓颉五代-快打模式 | 
| luna_pinyin_fluency | 朙月拼音·语句流 | 
| luna_pinyin_simp | 朙月拼音·简化字 | 
| luna_pinyin_tw | 朙月拼音·台湾正体 | 
| luna_quanpin | 全拼 | 
| stroke | 五笔画 | 
| terra_pinyin | 地球拼音 | 

### 五、模糊音定制
在用户文件夹下新建一个文件，添加如下内容后，改名为luna_pinyin.custom.yaml
# luna_pinyin.custom.yaml
#
# 【朙月拼音】模糊音定制模板
#   佛振配制 :-)
#
# 位置：
# ~/.config/ibus/rime  (Linux)
# ~/Library/Rime  (Mac OS)
# %APPDATA%\Rime  (Windows)
#
# 于重新部署后生效
#

patch:
'speller/algebra':
- erase/^xx$/                      # 第一行保留

# 模糊音定义
# 需要哪组就删去行首的 # 号，单双向任选
#- derive/^([zcs])h/$1/             # zh, ch, sh => z, c, s
#- derive/^([zcs])([^h])/$1h$2/     # z, c, s => zh, ch, sh

- derive/^n/l/                     # n => l
- derive/^l/n/                     # l => n

# 这两组一般是单向的
#- derive/^r/l/                     # r => l

#- derive/^ren/yin/                 # ren => yin, reng => ying
#- derive/^r/y/                     # r => y

# 下面 hu <=> f 这组写法複杂一些，分情况讨论
#- derive/^hu$/fu/                  # hu => fu
#- derive/^hong$/feng/              # hong => feng
#- derive/^hu([in])$/fe$1/          # hui => fei, hun => fen
#- derive/^hu([ao])/f$1/            # hua => fa, ...

#- derive/^fu$/hu/                  # fu => hu
#- derive/^feng$/hong/              # feng => hong
#- derive/^fe([in])$/hu$1/          # fei => hui, fen => hun
#- derive/^f([ao])/hu$1/            # fa => hua, ...

# 韵母部份
#- derive/^([bpmf])eng$/$1ong/      # meng = mong, ...
#- derive/([ei])n$/$1ng/            # en => eng, in => ing
#- derive/([ei])ng$/$1n/            # eng => en, ing => in

# 样例足够了，其他请自己总结……

# 反模糊音？
# 谁说方言没有普通话精确、有模糊音，就能有反模糊音。
# 示例爲分尖团的中原官话：
#- derive/^ji$/zii/   # 在设计者安排下鸠佔鹊巢，尖音i只好双写了
#- derive/^qi$/cii/
#- derive/^xi$/sii/
#- derive/^ji/zi/
#- derive/^qi/ci/
#- derive/^xi/si/
#- derive/^ju/zv/
#- derive/^qu/cv/
#- derive/^xu/sv/
# 韵母部份，只能从大面上覆盖
#- derive/^([bpm])o$/$1eh/          # bo => beh, ...
#- derive/(^|[dtnlgkhzcs]h?)e$/$1eh/  # ge => geh, se => sheh, ...
#- derive/^([gkh])uo$/$1ue/         # guo => gue, ...
#- derive/^([gkh])e$/$1uo/          # he => huo, ...
#- derive/([uv])e$/$1o/             # jue => juo, lve => lvo, ...
#- derive/^fei$/fi/                 # fei => fi
#- derive/^wei$/vi/                 # wei => vi
#- derive/^([nl])ei$/$1ui/          # nei => nui, lei => lui
#- derive/^([nlzcs])un$/$1vn/       # lun => lvn, zun => zvn, ...
#- derive/^([nlzcs])ong$/$1iong/    # long => liong, song => siong, ...
这个办法虽从拼写上做出了区分，然而受词典制约，候选字仍是混的。
只有真正的方音输入方案纔能做到！但“反模糊音”这个玩法快速而有效！

模糊音定义先于简拼定义，方可令简拼支持以上模糊音
- abbrev/^([a-z]).+$/$1/           # 简拼（首字母）
- abbrev/^([zcs]h).+$/$1/          # 简拼（zh, ch, sh）

以下是一组容错拼写，《汉语拼音》方案以前者爲正
- derive/^([nl])ve$/$1ue/          # nve = nue, lve = lue
- derive/^([jqxy])u/$1v/           # ju = jv,
- derive/un$/uen/                  # gun = guen,
- derive/ui$/uei/                  # gui = guei,
- derive/iu$/iou/                  # jiu = jiou,

自动纠正一些常见的按键错误
- derive/([aeiou])ng$/$1gn/        # dagn => dang
- derive/([dtngkhrzcs])o(u|ng)$/$1o/  # zho => zhong|zhou
- derive/ong$/on/                  # zhonguo => zhong guo
- derive/ao$/oa/                   # hoa => hao
- derive/([iu])a(o|ng?)$/a$1$2/    # tain => tian

分尖团后 v => ü 的改写条件也要相应地扩充：
#'translator/preedit_format':
#  - "xform/([nljqxyzcs])v/$1ü/"

### 六、在Win11将Rime（小狼毫Weasel）设为默认输入法？
Win11系统的设置time&language——language&region——options，Keyboards添加小狼毫 然后advanced keyboard设置修改默认输入法即可

### 七、RIME个人词库配置同步（针对文件installation.yaml，文件夹sync）
RIME本身不可以实现云同步，但我们可以借助第三方云盘实现此功能。 第一步打开用户文件夹中的installation.yaml文件，修改sync_dir指向位置（这个位置将是RIME的词典与配置存储的地方） 另外也可修改installation_id为自己喜欢的名称（为字母下划线数字，也可以不修改） 第二部做好上述修改后，点击用户同步。右击即可实现设置。

### 八、拼音和英文混输
[融合拼音rime_melt](https://github.com/tumuyan/rime-melt)是一个拼音-英文混合输入的Rime输入法的输入方案，基于【袖珍简化字拼音】【Easy English】
[Rime Easy English 英文输入法](https://github.com/BlindingDark/rime-easy-en)
**最后在windows任务栏小狼毫的图标上右键选择”重新布署“，就可以使用小狼毫Weasel了。**
