---
title: 神舟Z7-KP5D1黑苹果安装教程
date: 2018-07-26 15:30:50
tags:
categorise: 技术贴
copyright:
---


# 前言
在做这个教程之前，在自己的笔记本电脑上尝试了很多次，期间重启、更换镜像、爬帖等等，直到做出了我认为暂时比较完美的黑苹果系统。特此记录一下自己这段时间的制作流程和心得体会。
**坚持不懈，不断试错** 这是自己这段时间总结的制作黑苹果的核心启发，希望对读者有些帮助，在黑苹果的道路上共勉！<!-- more -->

下面是具体的制作过程：

> * 准备工作
> * 制作流程
> * 后期调试

------

# 准备工作



## 准备以下几项工具 [Todo 列表](https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown#13-待办事宜-todo-列表)


- [x] 一个大于8G的U盘
- [x] Windows下的工具
 - [x] TransMac
 - [x] DiskGenius
 - [x] EasyUEFI_Free
 [x] MAC OS下的工具
 - [x] Clover Configurator
 - [x] Kext Utility.app
- [x] 系统镜像



# 制作流程

##  在Windows下安装TransMac

安装完成后，右键以管理员身份运行该软件

## 制作MAC OS安装盘 

 1. 选择目标U盘
 2. 右键选“Format Disk for Mac”等待转换完成
 3. 右键选择“Restore with Disk Image”选择下载好的dmg文件，后续等待完成即可

## 划分磁盘分区

 1. 利用DG查看系统盘中EFI分区（又名ESP分区）空间是否大于200M,小于的话需要备份之后重建200M的分区，之后再将备份好的EFI文件拷入新建的EFI分区
 2. 在目标磁盘中分出约50G的空间用于安装MAC OS（格式选择NTFS(MS Basic Data)）

## 安装MAC OS 

 1. 重启进入BIOS
 2. 设置UEFI为第一启动
 3. CSM需要关闭（如果有的话）
 4. 开启AHCI
 5. 关闭secure boot
 6. 在BIOS设置U盘为第一启动，进入安装界面之后直接点击Boot OX X install from macOS High Sierra
 7. 跑完代码之后点击“磁盘工具”，选择刚才划分的50G磁盘，格式为APFS，抹掉。
 8. 关闭窗口，选择安装mac OS,选择目标盘即可
 9. 跑完之后，随后自动重启以U盘进入，选择Boot macOS from "你的目标盘的名字"
 10. 之后还有两次跑代码，重复第五步两次，最后会设置键盘布局以及账号之类的。
 11. 重启之后在Windows系统中利用DG将U盘中的ESP中的EFI的CLOVER文件拷入硬盘的ESP分区中的EFI中。**提示**：拷贝的时候可以右键目标盘建立盘符后操作；两个磁盘的话（即Windows一个盘，MAC OS一个盘），只需将ESP中的EFI的CLOVER文件拷入Windows硬盘的ESP分区中的EFI中即可。
 12. 安装UEFI Free后，选择添加启动项，选择linux或者其他操作系统，描述中填写启动项的名字，然后选择Windows下的ESP分区，文件路径中选择EFI-CLOVER-CLOVERX64.EFI，点击“确定”后。
 13. 重启选择Boot macOS from "你的目标盘的名字"进入MAC OS系统。

# 后期调试
## 驱动安装和系统维护 

 1. 由于I5-7300HQ的核显是HD630,因此，可以选择只驱动独显或者只驱动核显都可以，看个人需要。选择的时候将笔者提供的EFI中的CLOVER文件拷贝Windows下的ESP分区中的EFI中即可（二选一）
 2. 由于PH65的主板上的ALC892声卡驱动的问题复杂性，笔者在尝试过多次之后（包括最新的万能声卡以及相关的驱动软件，均可驱动，但无声音），因此只能选择耳机可用，声卡由于主板的特殊性，不能光看型号，因此具有一定的残缺。
 3. USB驱动、电源驱动、有线网卡驱动以及亮度调节等等都可以正常使用，后续有能力的话可在这个基础上进行修改。
 4. 关于无线网卡驱动，笔者选择暂时采用HoRNDIS驱动，在官网[HoRNDIS](https://www.joshuawise.com/horndis)上下载最新版安装后选择USB网络共享，并且支持移动蜂窝网络和无线网络共享速度基本能达到本身宽带峰值。**注意**：MIUI系统的话需要开启USB调试功能。

------
[**相关工具下载**    w79j](https://pan.baidu.com/s/1AR7BeYsY1nG9JDxXHAfRNQ)
[**镜像下载**    9wtt](https://pan.baidu.com/s/1eNBN-WeKgvevmn8D2s6s8w)

作者 [@BUAA-RongYi]  
2018 年 07月 26日    

