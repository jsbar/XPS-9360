## MacOS with xps-9360

### 使用情况

- [x] 声音
- [x] 显卡
- [x] 网卡
- [x] 雷电口热拔插
- [x] 触摸板
- [x] 睡眠
- [x] 蓝牙
- [x] 变频
- [ ] 睡眠变频
- [ ] iMessage


### 配置

型号 : 戴尔XPS 13-9360-R3905S

CPU : i7-8550U

显卡 : HD620

网卡 : DW1830

内存 : 16G

硬盘 : SM961(256G)

BIOS版本 : 2.8.1

系统版本 : 10.3.6 

### 安装前准备

1. 更换硬盘, PM981安装过程中无法识别,故需更换硬盘,推荐 SM961

2. 更换网卡,内置 killer1535 网卡无法驱动,故需更换网卡,推荐 DW1560/DW1830,DW1830有三根天线,原装网卡两根天线接口,所以需要加接口

3. 升级 BIOS, 升级最新即可

4. 调整 DVMT 值,参考 the-darkvoid（非常重要）

### 安装过程

1. 使用[黑果小兵](https://blog.daliansky.net/macOS-High-Sierra-10.13.4-17E199-Release-Version-and-Clover-4418-Original-Image.html)的系统及 EFI 进行安装,安装过程中会报两次错误,第一次报错重启继续安装,第二次报错后重启使用我的 EFI 文件进入系统即可

2. 使用 xps9360.sh 中相关命令注入声音驱动,打开第三方应用权限

3. 执行命令开启 HIDPI ,把分辨率设为1440*810,显示更清楚

### 一些问题
1. 蓝牙不稳定，无法使用，在config文件中boot选线添加dark=0解决

2. 声音问题，使用xps9360.sh解决

3. 触摸板驱动,使用 VoodooI2C 驱动使用双指即右击不灵敏,仅三指手势可用.故替换为VoodooPS2Controller，ApplePS2SmartTouchPad，支持双指右边缘左划，上边缘下划，三指向上，向下，左划右划，四指向上，向下，左划右划，双指放大缩小   

### 注意事项

 相对于 the-darkvoid,有以下改动

**kexts**
	
	删除 VoodooPS2Controller.kext
	添加 ApplePS2SmartTouchPad.kext
	添加 BT4LEContiunityFixup.kext
	添加 AirportBrcmFixup.kext
	添加 BrcmFirmwareData.kext BrcmPatchRAM2.kext

**themes** 

    添加主题文件
    
**ACPI**
    
    删除 SSDT-I2C 因为双击不灵敏
    替换 SSDT-UIAC，睡眠唤醒蓝牙驱动
    
### 致谢

### [the-darkvoid](https://github.com/the-darkvoid/XPS9360-macOS)

### [triton21](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1769152&highlight=hidpi)