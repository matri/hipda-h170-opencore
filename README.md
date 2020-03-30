hipda搞机小分队自用云轩h170 opencore引导文件，特别鸣谢微信群：@beyond291，@酱油喵，@数不清，本EFI来自 @beyond291，稍作修改。

任何人都可以免费使用、修改或者分发该repo内容，hipda搞机小分队对于使用该repo的任何后果均不负任何责任，<mark>use at your own risk！！！</mark>



云轩H170群内基本配置：



- 技嘉h170-stx主板

- 魔改bios支持8、9代u，可使用es版本cpu（推荐8700es）

- 硬盘只支持m2 sata，可再加入一个2.5 sata ssd

- 风扇限高45mm，推荐is40x，hp400，大镰刀s950m

- 内存可支持到32G双通道

- 网卡推荐使用转接线+白苹果网卡，或者 dw1820a，dw1802a推荐0vw3t3以及08pkF4

- 天线可使用pcb平板天线或者胶棒天线（胶棒需自行在外壳打孔）



使用opencore引导之前的准备工作：



配置bios：

参考张大妈的这篇文章配置bios：[bios设置](https://post.smzdm.com/p/ag827k43/)



解锁bios cfg-lock设置：

按道理说直接bios解锁最方便，但是云轩提供的bios并没有做这个事情，所以只能手动解锁，步骤如下：

1. 找一个u盘（可以启动的那种），格式化成 fat 格式，然后把：Tools/解锁cfg lock/ 里面的EFI文件夹整个拖到u盘根目录

2. 启动，按F12，选择该U盘（可能会有2个EFI分区，随便试，一个不行就另外一个，直到进入一个命令行界面）

3. setup_var 0x4EF 0x00（或者 setup_var_3 ），运行完以后，应该会在一堆英文里面提示有一个什么值从 0x01 变成 0x00。（注意：每次bios换电池以后都需要解锁一下）

4. 关机



使用opencore引导：



1. 还是刚才那个可以启动的U盘，把EFI文件夹删除，然后把repo里的EFI文件夹拷贝进去；

2. 开机按f12，选择U盘启动，进入boot menu的时候，先选reset nvram清除一下nvram，然后再次u盘启动进入系统看看有没有问题；

3. 确认所有东西都ok以后，使用你喜欢的任何工具挂载硬盘上的EFI分区，然后删除掉原来就有的EFI文件夹（<mark>注意备份</mark>），然后把U盘里面的EFI文件夹拷贝进去；

4. 重启，硬盘启动，老样子，先清一遍nvram，然后启动；

5. 进系统以后自己用tools里面的hackintool算序列号什么的，然后编辑 EFI分区下的 /EFI/OC/config.plist 文件，在systeminfo里面注入三码啊，序列号啊这些。

6. enjoy！



目前支持状态：

- [x] cpu变频

- [x] 显卡驱动，metal、opencl、硬解

- [x] 上述无线网卡以及蓝牙，handoff，智能热点，airdrop

- [x] typec转3.5声卡，hdmi音频，dp音频

- [x] dp输出4k 60hz，hdmi输出4k 30hz，hidpi

- [x] 休眠、唤醒正常

- [x] 内置有线网卡

- [x] 所有usb端口



目前问题：

暂无




