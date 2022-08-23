---
<<<<<<< HEAD
abbrlink: 0
=======
title: Arduino开发ESP8266环境配置
date: '2022-08-23 18:29'
>>>>>>> ccf16a29a30c366f5579d72687a93ffb50596fa2
---
# Arduino开发ESP8266环境配置

## 一、添加 ESP8266 支持

首先从 [Arduino 官网](https://www.arduino.cc/en/main/software) 下载最新版本的 **Arduino IDE** 软件并安装。
 安装完成以后，进入**首选项**（Preferences），找到**附加开发板管理器地址**（Additional Board Manager URLs），并在其后添加如下信息：
 `http://arduino.esp8266.com/stable/package_esp8266com_index.json`

![](http://ezblog.gnway.cc/i/2022/08/23/6304a2ed3cb98.png)

之后点击**工具** - **开发板** - **开发板管理器**，进入开发板管理器界面：

![](http://ezblog.gnway.cc/i/2022/08/23/6304a336832f3.png)

## 二、找到 *esp8266* 并安装：

![](http://ezblog.gnway.cc/i/2022/08/23/6304a37033daf.png)

这里安装ESP8266需通过GitHub网络问题可能安装不成功。

安装完成后，重启 Arduino IDE 软件。在**工具** - **开发板**选项中即会看到 ESP8266 开发板的选项：

![](http://ezblog.gnway.cc/i/2022/08/23/6304a3a5ca113.png)

## 三、代码开发

**注意事项**

例程程代码和实际开发板对应的引脚不一样，需找打对应的规则。如图：例程中D1对应8266开发板的GPIO 5对应数字是5

![](http://ezblog.gnway.cc/i/2022/08/23/6304a3d194fd6.png)

## 四、编译上传

![](http://ezblog.gnway.cc/i/2022/08/23/6304a40339b9b.jpeg)

1是编译、2是上传

**上传是需先将开发板重启然后按住FLASH等待出现connect字样后松开FLASH按键**