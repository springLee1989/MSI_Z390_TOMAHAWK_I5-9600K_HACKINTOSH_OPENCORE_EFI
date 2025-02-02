## MSI MAG Z390 TOMAHAWK + i5-9600K 

### 当前版本信息

| 信息                                                         | 版本                   |
| ------------------------------------------------------------ | ---------------------- |
| 系统                                                         | macOS Catalina 10.15.6 |
| [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) | 0.6.7                  |
| 模拟机型                                                     | iMac19,1               |
| [Lilu.kext](https://github.com/acidanthera/Lilu/releases)    | 1.5.1                  |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases) | 1.2.1                  |
| [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases) | 1.4.8                  |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases) | 1.5.8                  |
| [IntelMausi.kext](https://github.com/acidanthera/IntelMausi/releases) | 1.0.5                  |
| [CPUFriend.kext](https://github.com/acidanthera/CPUFriend)   | 1.2.3                  |

### 电脑配置信息

| 硬件     | 型号                                  |
| :------- | ------------------------------------- |
| 处理器   | Intel i7-8700 apple                    |
| 主板     | MSI MAG Z390 TOMAHAWK                 |
| 内存     | 16GB DDR4 3200MHz * 4  64GB           |
| 硬盘     | HIKVISION C2000 PRO 1T                |
| 显卡     | AMD Radeon Pro 555 2G                 |
| 无线蓝牙 | Broadcom BCM94360CS2 Wireless LAN SoC |
| 电源     | 先马 金牌  全模组 750w                     |
| 散热器   | id cooling 240水冷               |
| 显示器   | 飞利浦276E   27'' 4K                   |
| 机箱     | 先马 静音机箱                             |

### 功能完善程度

- [x] 显卡：UHD630核显 + RX590独显 双硬解，可输出4k+和HEVC解码
- [x] 声卡：Realtek ALC892 已驱动，输出输入均正常
- [x] 网卡：Intel I219-V + Intel I211AT 已驱动
- [x] WiFi：BCM94360CS2 免驱
- [x] 蓝牙：BCM94360CS2 免驱
- [x] USB：USB2.0 + USB3.0 + USB-C接口均已定制
- [x] Airdrop隔空投送：功能正常
- [x] Handoff接力：功能正常
- [ ] Sidecar随航：未测试，有核显应可正常使用
- [ ] FaceTime/iMessage：未测试，使用白码应可正常使用
- [x] CPU睿频 / HWP变频：功能正常
- [x] 睡眠唤醒：功能正常

### 安装教程

#### BIOS设置

> 本人当前BIOS版本：E7B18IMS.160，如下面设置选项未找到，请[更新最新版本](https://cn.msi.com/Motherboard/support/MAG-Z390-TOMAHAWK)。
>
> 同时请设置语言为简体中文并进入高级模式（F7）。

必要设置：

- OC(Overclocking) -> CPU 特征 -> Intel 虚拟化技术 **[允许]**
- OC(Overclocking) -> CPU 特征 -> Intel VT-D 技术 **[禁止]**
- OC(Overclocking) -> CPU 特征 -> CFG锁定 **[禁止]**

按需设置：

- STTINGS -> 高级 -> 内建显示配置 -> 设置第一显卡 **[PEG]**  *(仅同时拥有核显及独显需要手动设置)*
- STTINGS -> 高级 -> 内建显示配置 -> 集显共享内存 **[64M]** *(如果使用拥有核显的处理器)*
- STTINGS -> 高级 -> 内建显示配置 -> 集成显卡多显示器 **[允许]** *(如果使用拥有核显的处理器)*
- STTINGS -> 高级 -> PCI子系统设置 -> Above 4G memory/Crypto Currency mining **[允许]**
- STTINGS -> 高级 -> USB设置 -> XHCI Hand-off **[允许]**
- STTINGS -> 高级 -> USB设置 -> 传统USB支持 **[允许]**
- STTINGS -> 高级 -> 电源管理设置 -> ErP Ready **[允许]**
- STTINGS -> 高级 -> Windows操作系统的配置 -> Windows 10 WHQL支持 **[允许]**
- STTINGS -> 高级 -> 唤醒事件设置 -> 唤醒事件管理 **[BIOS]**
- STTINGS -> 高级 -> 唤醒事件设置 -> USB设备从S3/S4/S5唤醒 **[允许]** *(设置后我这边出现关机下键盘灯仍亮着情况。如出现一样情况，建议关闭，可按电源键唤醒)*

#### 修改config.plist文件

> 修改plist文件建议用[ProperTree](https://github.com/corpnewt/ProperTree)工具。
>
> 修改参考这两位大神的文章：[xjn 博客](https://blog.xjn819.com/?p=543) [黑果小兵博客](https://blog.daliansky.net/OpenCore-BootLoader.html)

- 修改三码
  1. 使用[GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)脚本生成三码+ROM（机型填`iMac19,1`）
  2. 用[ProperTree](https://github.com/corpnewt/ProperTree)工具打开`config.plist`文件，进入`PlatformInfo` -> `Generic ` 填入三码。

### 结语

现在黑苹果的安装上手难度已经非常低了，希望这个EFI文件能够帮助你尽快上手黑苹果。

本EFI文件可随意使用。不出意外的话，本人将会止步在10.15版本，后续不再升级macOS新版本。

### 更新记录

- 2021年03年08日
  - 更新OpenCore 0.6.7
  - 更新Kexts到新版本
  - 修复核显UHD 630驱动
- 2021年01月11日
  - 更新OpenCore 0.6.5，此Core应该支持macOS Big Sur 11.0.1版本，请自行尝试，如有问题，欢迎Issues
  - 更新Kexts到新版本
- 2020年08月09日
  - 更新OpenCore 0.6.0
  - 更新Kexts到新版本
  - 修复USB内建定制问题

### 预览截图

![](./Screenshots/Screenshot01.png)

![](./Screenshots/Screenshot02.png)

![](./Screenshots/Screenshot03.png)

![](./Screenshots/Screenshot04.png)

![](./Screenshots/Screenshot05.png)

![](./Screenshots/Screenshot06.png)

![](./Screenshots/Screenshot07.png)

![](./Screenshots/Screenshot08.png)

![](./Screenshots/Screenshot09.png)

![](./Screenshots/Screenshot10.png)

![](./Screenshots/Screenshot11.png)


### 鸣谢

- [acidanthera / OpenCorePkg](https://github.com/acidanthera/OpenCorePkg)
- [Opencore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/
  )
- [xjn](https://blog.xjn819.com/)
- [黑果小兵](https://blog.daliansky.net/)
- [远景论坛](http://bbs.pcbeta.com)
- [GeQ1an](https://github.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI)

