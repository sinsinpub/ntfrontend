# NDS rom tool Frontend (NTFrontend) v1.70 #
  * Attach:NTFrontend.png by sin\_sin
  * Latestly built on 2007-12-7
![http://sinblog.512j.com/up/1197025516.png](http://sinblog.512j.com/up/1197025516.png)

## 关于ndstool和NTFrontend ##
Nintendo DS rom tool(ndstool.exe)是一个用于查看、处理、分解、整合Nintendo DS游戏ROM头部及内部文件系统数据的Windows控制台工具。

NTFrontend是一个运行于Windows系统下的NDS rom tool图形界面前端工具。

前端NTFrontend将ndstool的控制台命令行操作简化为Windows标准GUI对话操作，主要为提取、收集NDS ROM头部数据提供便利。也提供对ROM文件系统的查看、分解、整合等提供支持。主要功能依赖于ndstool本身，所以对于banner图标、文本等只提供简单支持。

ndstool目前版本为2007/10编译的v1.36，网上流行版本为v1.31，目前以v1.3以上为主要支持对象。由于旧版本差异较大，如果要使用其它的请做好BUG多多的心理准备XD 又因为v1.36文件大小比v1.33大了一倍多，所以包内仍然附送v1.33囧rz


## NTFrontend目前特性 ##
  * 提供ROM Header信息的收集和校验，支持-i开关和-v选项
  * 支持zip、rar和7z压缩的ROM（自动解压到临时文件夹）
  * 支持ROM的Secure Area加密或解密（-s开关）
  * 支持ROM的Header CRC修复（-f开关）
  * 支持ROM文件系统的浏览（-l开关）和分解（-x开关）
  * 支持ROM的重整合（-c开关）
  * Banner图标和文本的读取、显示与保存，这里开始已经和ndstool无关了
  * Banner的图标和文本以及游戏标识的修改（不通过ndstool）
  * 扫描文件夹，并读取所有找到的ROM的Header的自动过程
  * 一张用于收集Header信息并能自定义表列标题的数据表
  * ROM文件的缩减，缩减到安全大小
  * 支持给ROM打IPS补丁，IPS1/IPSPro受付中
  * 支持给需要用FATLib驱动的自制软件打“流行性”DLDI补丁
  * 支持给ROM打BSD补丁（通过bspatch）
  * 其它附加小功能，为ROM“用户”提供小贴士
  * 控制台日志将被一一记录，除了查看还可以随时复制到剪贴板或清除
  * 支持界面从5种语言切换，目前有英、简中、繁中，谁帮偶加点啊～
  * 支持仿XP界面控件效果
  * -p开关和-k开关由于未经测试也很少使用，决定不予以支持


## NTFrontend已知并暂时不想/不能解决的BUG ##
  * 注意ndstool的-se开关也就是Secure Area加密并不是完全的，可以看到它自己加密都自称为“mask ROM”而不是“encrypted”。目前版本使用的Nintendo加mask功能和某淫写那个eNDryptS Advanced v1.2加密得到的SA并不一样……所以如果想要真SA encrypted的话，还是用那个比较好。
  * ndstool本身较旧的原因，个别特殊的header会不能正常识别，主要体现在缺失部分字段的枚举信息。不过如果偶遇到过的话就会加上相应的识别的。
  * 特别要注意在打开DEMO、homebrew之类时，如果勾上了-v，特别是加上了SC loader等不明物体的ROM文件（比如`*`.sc.nds），由于ndstool本身的问题，将会导致PC内存无限的被吞噬造成程序假死……这时请立即打开任务管理器taskmgr将ndstool.exe进程强制结束，否则你物理内存装多少也不够它花的-v-
  * 正因为上面那条原因……想要给加了SC、M3 loader的ROM加图标也不能直接实现，虽然知道仅仅只是偏移512字节，但ndstool不能提供有效的数据全得自己取的话……干脆就别当它的前端自立门户算了莔 所以偶……忍了！
  * 由于使用了WideCharToMultiByte，像日文SJIS里那个半角的“·”等类似符号在简体系统下必然是个“?”，这点就表奇怪了囧（现在可以通过另存为Unicode文本文件来暂时解决）


## Special Thanks ##
还是那句，感谢所有辛勤劳作者XD，感谢ndstool的作者（们），感谢帮偶测试的sammychen、redalertwei、ffsky……感谢父母、感谢国家、感谢党、感谢CCTV、感谢……#@$#%@!@#$#@$\\


## 下载、问题反馈与建议 ##
  * http://sinsin.blog.edu.cn
  * http://www.ndsbbs.com
  * http://sinblog.512j.com/pmwiki/index.php/OLData/NTFrontend
或者
http://sin-sin.ys168.com (pw=nb)
  * [Mofile下载(v1.70)](http://pickup.mofile.com/8007600767467049)


## NTFrontend更新日志 ##
  * 2007-12-7	v1.70
    * 新增：扫描过程的详细记录志和控制台日志的自动保存。。。只要程序目录下有个叫NTFrontend.Console.log的文件，日志就会在里面了。要小心别让文件变得太大哦-v-
    * 变更：好久没更新过devkitARM，[r20](https://code.google.com/p/ntfrontend/source/detail?r=20)、r21对偶来说竟然都是新的。。。于是就把ndstool.exe换成1.33的了，其实对偶来说没有什么本质上的区别嘛`-_-`
    * 变更：File Explorer的搜索从全选择式改为一条条逐一搜索，每按一次<sup>F会去找下一个，遍历完后显示会定位在列表末尾。原来的全选式关联到</sup>L键上了
    * 变更：Banner小窗的背景图换了个用No$GBA截的，颜色实在是不够真实，而且偶想要日版画面的说-.-
    * 更新：更新了Publisher和Wiki连接。提前祝X'mas和Happy New Year！