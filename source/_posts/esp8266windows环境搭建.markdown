---
title: ESP8266 windows 开发环境搭建
date: '2022-08-25 16:00'
categories: ESP8266
tags:
    - ESP8266
    - 硬件编程
---
# ESP8266 windows开发环境搭建

## 一、软件准备

安信可一体化开发环境网上搜索即可

## 二、SDK编译

### 1.添加环境变量

安信可一体化开发环境解压后，将cygwin文件夹下的bin文件夹和opt\xtensa-lx106-elf\bin文件夹添加至系统环境变量。

<!--![安信可一体化开发环境](%E5%AE%89%E4%BF%A1%E5%8F%AF%E4%B8%80%E4%BD%93%E5%8C%96%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83.jpg)-->
![安信可一体化开发环境](http://ezblog.gnway.cc/i/2022/08/25/63073e67bc3eb.jpeg)

<!--![添加环境变量](%E6%B7%BB%E5%8A%A0%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F.jpg)-->
![添加环境变量](http://ezblog.gnway.cc/i/2022/08/25/63073e8773b4b.jpeg)
### 2.准备官方SDK

将官方SDK包里的third_party和driver_lib文件夹下的Makefile文件删除。导入eclipse。

<!--![官方sdk准备](%E5%AE%98%E6%96%B9sdk%E5%87%86%E5%A4%87.jpg)-->
![官方sdk准备](http://ezblog.gnway.cc/i/2022/08/25/63073ea761e84.jpeg)

选择Existing Code as Makefile Project

![导入eclipse](%E5%AF%BC%E5%85%A5eclipse.jpg)

选择SDK文件夹取消c++选项，选择Cygwin GCC。

<!--![eclipse导入设置](eclipse%E5%AF%BC%E5%85%A5%E8%AE%BE%E7%BD%AE.jpg)-->
![导入eclipse](http://ezblog.gnway.cc/i/2022/08/25/63073ef1b7ff8.jpeg)

### 3.修改SDK的Makefile文件设置。

<!--![修改Makefile文件](%E4%BF%AE%E6%94%B9Makefile%E6%96%87%E4%BB%B6.jpg)-->
![修改Makefile文件](http://ezblog.gnway.cc/i/2022/08/25/63073f1595e99.jpeg)

如图将SDK根目录Makefile文件中第25行至2行的进行更改这几行和官方[2a-esp8266-sdk_getting_started_guide_cn.pdf](https://www.espressif.com/sites/default/files/documentation/2a-esp8266-sdk_getting_started_guide_cn.pdf)中的sdk编译选项对应关系如图。

<!--![sdk编译设置](sdk%E7%BC%96%E8%AF%91%E8%AE%BE%E7%BD%AE.jpg)-->
![sdk编译设置.jpeg](http://ezblog.gnway.cc/i/2022/08/25/63073f452b386.jpeg)

```c
    BOOT?=new    # boot版本选择，old=boot_v1.1,new=boot_v1.2+,none=none
    APP?=1       #固件升级方式选择，Firmware Over-The-Air（FOTA，⽀持云端升级）和   
                 #non-FOTA（不⽀持云端升级）的 BIN ⽂件，0=不支持云端升级，1，2=支持云
                 #端升级。0=eagle.flash.bin,1=user1.bin,2=user2.bin
	SPI_SPEED?=40# 芯片频率选择，根据实际选择，一般40MHz
	SPI_MODE?=QIO#下载方式短则选QIO即可
	SPI_SIZE_MAP?=6 #FLASH芯片容量选择，1=256KB=2Kbit(一般不支持)，
	              #2=1MB=8Mbit(512KB+512KB)，#3=2MB=16Mbit(512KB+512KB)，
                  #4=8MB=32Mbit(512KB+512KB) ，
                  #5=2MB=16Mbit-C1(1024KB+1024KB)，
                  #6=8MB=32Mbit-C1(1024KB+1024KB) 
```

<!--![Makefile编译设置](Makefile%E7%BC%96%E8%AF%91%E8%AE%BE%E7%BD%AE.jpg)-->
![Makefile编译设置](http://ezblog.gnway.cc/i/2022/08/25/63073f63a7aca.jpeg)

设置好后，clean project和重新build project就可以了生成boot.bin和user1.4096.new.6.bin和flash下载地址。

<!--![编译成功](%E7%BC%96%E8%AF%91%E6%88%90%E5%8A%9F.jpg)-->
![编译成功](http://ezblog.gnway.cc/i/2022/08/25/63073f8fe4748.jpeg)

## 三、固件下载

### 1.文件准备

按照上述编译方法编译SDK后在SDK根目录的bin文件夹下生成.bin文件，如图所示

![bin文件](.bin%E6%96%87%E4%BB%B6.jpg)

其中user.4096.new.6.bin 在upgrade文件夹下。

### 2.软件准备。

可以用来下载固件的软件有flash_download_tool_3.9.0、FLASH_DOWNLOAD_TOOLS_V3.6.3、ESP8266Flasher和esptool可以使用，推荐使用FLASH_DOWNLOAD_TOOLS_V3.6.3，除esptool没用过之外，其他的都有坑，后面专门讲解。

<!--![flash-down-tool](flash-down-tool.jpg)-->
![flash-down-tool](http://ezblog.gnway.cc/i/2022/08/25/63073fe40144a.jpeg)

根据官方[2a-esp8266-sdk_getting_started_guide_cn.pdf](https://www.espressif.com/sites/default/files/documentation/2a-esp8266-sdk_getting_started_guide_cn.pdf)中下载地址的表格查看对应的flash地址。

<!--![flash地址关系](flash%E5%9C%B0%E5%9D%80%E5%85%B3%E7%B3%BB.jpg)-->
![flash地址关系](http://ezblog.gnway.cc/i/2022/08/25/6307402b66984.jpeg)

根据Makefile中设置的flash容量选择地址。

``` c
SPI_SIZE_MAP?=6 #FLASH芯片容量选择，
#1=256KB=2Kbit(一般不支持) 2=1MB=8Mbit(512KB+512KB) 3=2MB=16Mbit(512KB+512KB)，
#4=8MB=32Mbit(512KB+512KB) 5=2MB=16Mbit-C1(1024KB+1024KB) 6=8MB=32Mbit-C1(1024KB+1024KB) 
```

例如SPI_SIZE_MAP设置为6.对应4096KB（1024+1024）的flash芯片，地址对应0x3FB000 、0x3FC000、0x3FE000、0x0000、0x01000这一列，按照对应关系填固件下载软件即可，其中6对应FLASH_DOWNLOAD_TOOLS中的FLASHSIZE选择32Mbit-C1，其他对应关系如图。

**注** 取消Donotchgbin勾选。选中它后软件的FLASHSIZE使用默认设置4Mbit(256KB+256KB)，对应spi_size_map=0。

SPI_SIZE_MAP设置和FLASH_DOWNLOAD_TOOLS软件中的设置一致时，芯片上电后串口显示如图mismatch map 4是Makefile文件中的SPI_SIZE_MAP设置，spi_size_map 0是FLASH_DOWNLOAD_TOOLS软件中FLASH SIZE的设置。一般只要两者对应都能正确下载固件。但是SPI_SIZE_MAP=1或0不行。编译会提示"The flash map is not supported"。

<!--![spisize设置串口显示](spisize%E8%AE%BE%E7%BD%AE%E4%B8%B2%E5%8F%A3%E6%98%BE%E7%A4%BA.jpg)-->
![spisize设置串口显示](http://ezblog.gnway.cc/i/2022/08/25/6307405fd1937.jpeg)

选择正确的地址和频率后即可下载固件，正确运行的串口如图所示。正确输出hello world！！！！

<!--![成功执行](%E6%88%90%E5%8A%9F%E6%89%A7%E8%A1%8C.jpg)-->
![成功执行](http://ezblog.gnway.cc/i/2022/08/25/63074081e1508.jpeg)

# **四、坑** 

## 一、软件准备的坑。

​		推荐使用**安信可的一体化编译工具**，因为要使用cygwin和xtensa-lx106-elf这两个编译工具，其中cygwin相当于一个下载器，自己安装很难搞明白具体应该安装那些工具（其中工具列表有上千甚至上万个），**而官方提供的xtensa-lx106-elf不可用** ，至少缺少xt-xcc.exe这个工具，而安信可的工具已将这两个工具配置好了，免安装，只需要按照上面讲的配置环境变量就可以正常使用。

**注** 安装目录不能有中文字符。 

## 二、SDK的坑

​		对纯新手小白来说，很难弄清楚要将**driver_lib**文件下的**Makefile**文件和**third_party**文件夹删掉，并且将example文件夹下的demo文件夹复制到根目录。还有就是根目录下的Makefile设置。

## 三、固件下载软件的坑

### 1.flash_dowmload_tools3.9.0

固件下载软件有很大的坑，特别是官方的flash_dowmload_tools3.9.0版，如图所示flash_dowmload_tools3.9.0版不支持选择FLASH SIZE，只能使用默认的SPI_SIZE_MAP=0，对应4Mbit(256+256)，若是碰巧你的开发板使用的相同大小的flash可能碰巧可以正常使用，否则看命。

<!--![flash_download_tool_3.9.0](flash_download_tool_3.9.0.jpg)-->
![flash_download_tool_3.9.0](http://ezblog.gnway.cc/i/2022/08/25/630740ba558c3.jpeg)

### 2.ESP8266flasher

ESP8266flasher也能用，也可以选择flash size，但是这个软件版本很多，每个都有一些细小的差别，如图。

<!--![ESP8266flasher](ESP8266flasher.jpg)-->
![ESP8266flasher](http://ezblog.gnway.cc/i/2022/08/25/630740e6dbf3b.jpeg)

<!--![esp8266flasher2](esp8266flasher2.jpg)-->
![esp8266flasher2](http://ezblog.gnway.cc/i/2022/08/25/63074107ea2b8.jpeg)

ESP8266flasher存在一个问题不支持选择SPI_SIZE_MAP=5或6[5=2MB=16Mbit-C1(1024KB+1024KB) 6=8MB=32Mbit-C1(1024KB+1024KB) ],若使用的4MB的flash，如果碰巧设置SPI_SIZE_MAP=4下载后就正常，如果设置6，下载过程也正常，但是无法正常运行。

**注** 不论固件下载软件的FLASH SIZE如何选择，固件下载过程都正常，只有上电运行的使用后才会提示不可用。因此还是推荐使用FLASH_DOWNLOAD_TOOLS_V3.6.3，正确选择FLASHSIZE就可以了。

*另外，经过测试除SPI_SIZE_MAP=0或1外，只要Makefile和固件下载软件的flash地址和flash size设置对应上就可以正确运行。推测原因是由于容量大的FLASH芯片地址兼容容量小的FLASH芯片地址，但是如果存储的.bin文件过大超过了地址范围可能会出问题，建议正确选择FLASH芯片容量。*

最后，最坑的就是乐鑫官方提供的工具坑最多，对新手很不友好。对了官方的lubuntu系统编译按照官方[2a-esp8266-sdk_getting_started_guide_cn.pdf](https://www.espressif.com/sites/default/files/documentation/2a-esp8266-sdk_getting_started_guide_cn.pdf)提示操作即可，注意给SDK文件夹授权，出问题的主要原因还是在后边的固件下载工具上,不在单独写了。

``` linux
文件夹授权命令
chmod -R 777 文件地址
```

