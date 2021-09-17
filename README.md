# CoreBookX-14-Hackintosh
EFI for Chuwi CoreBookX 14 (i5-8259U) By @weachy & @王刚

## 当前版本（Version）
**OpenCore-CoreBookX14-210910** （OpenCore 0.7.3）

如果你想了解更多关于 CoreBookX14 黑果玩机技巧，请查阅我的 [知乎专栏](https://www.zhihu.com/column/c_1419721568574013440) （
If you want to learn more about hackintosh with CoreBookX14. Please visit: My [Zhihu Column](https://www.zhihu.com/column/c_1419721568574013440) ）

## 配置（Specification）
- **Processor**: Intel Core i5-8259U @ 2.3GHz (Coffee Lake)
- **Graphic**: Intel® Iris® Plus Graphics 655 (共享显存 1536MB)
- **Wi-Fi**: 
   - （自带）Intel 7265 (不完美) / Realtek 8821CE (无解) 
   - （硬改）Broadcom BCM94360CS2 from Macbook（完美工作)
- **Ethernet**: No
- **Bluetooth**: 
   - （自带）Intel 7265 (与Wi-Fi共用一根天线，干扰严重) / Realtek 8821CE (无解) 
   - （硬改）Broadcom BCM94360CS2 from Macbook（完美工作)
- **Audio**: Realtek ALC897 ()
- **Touchpad**: SYNA3602
- **Storage**: 512GB Kingston RBUSNS8154P3512GJ M.2 NVME SSD
- **TF Card Reader**: BayHubTech Integrated SD Controller (无解)
- **WebCam**: USB 2.0 Camera (from Sonix Technology Co., Ltd.)
- **Battery**: 46 Wh Battery

## 前言（Preface）
上月联系国光兄弟一起完善 CoreBookX 的代码，无奈大佬去意已决，挽留未果，目前我和 @王刚 在继续维护 CoreBookX 14 的引导，并研究出了网卡硬改方案以解决 Apple 生态互联功能以及在此笔记本上 Intel 蓝牙信号奇差等问题。我们创建了一个交流Q群（631070738），欢迎大家加入。

在将 EFI 重新完整梳理一遍之后，发现之前的版本存在很多细节缺漏，现先将若干棘手问题修复做一版更新。


## 更新日志（Change Log）

### 2021-09-10，本次修复问题：
1. 上一个版本中合盖睡眠在唤醒时偶发内核崩溃的问题
2. 修复充电状态延迟问题
3. 修复键盘波浪键（~）被映射为（±）的问题
4. 修正 Fn+F10 对应的播放暂停功能
5. 插入/移除耳机自动切换输出源（耳机->扬声器）
6. 重新整理 EFI 中，各项不规范的地方，增加稳定性：重新梳理 USB 定制、SSDT方式修改按键映射、完善触摸板相关（SSDT-GPI0.aml）、更正操作系统补丁（SSDT-OC-XOSI.aml）、添加 PNLF 重命名等等

#### 之前所做修复已提交给国光兄弟（详见 [CHUWI-COREBOOK-X-I5-8259U GitHub](https://github.com/sqlsec/CHUWI-COREBOOK-X-I5-8259U) ）
1. 实现合盖睡眠、开盖自动唤醒（由于 ACPI 不完整，会造成唤醒偶发内核崩溃）
2. 功能键调节亮度暂时无解，建议手动修改“系统偏好设置--键盘--快捷键--显示器”中的亮度快捷键，例如改为 F6、F7。
3. 提高触控板三指触控的稳定性
4. 对调 Command、Option 按键映射，遵循白苹果的按键布局
5. 显示器设置中新增自动调节亮度选项（没有实际效果），接通电源屏幕亮度会提高

