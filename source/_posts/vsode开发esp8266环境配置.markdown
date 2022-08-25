---
title: vscode 安装 ESP8266 开发环境
date: '2022-08-25 16:00'
categories: ESP8266
tags:
    - ESP8266
    - 硬件编程
---
# vscode开发esp8266环境配置

## 一、安装VSCODE

## 二、安装VScode-arduino插件

<!--![安装arduino插件](%E5%AE%89%E8%A3%85arduino%E6%8F%92%E4%BB%B6.jpg)-->
![安装arduino插件](http://ezblog.gnway.cc/i/2022/08/25/63073c441f4b0.jpeg)

## 三、配置arduino环境

在设置中搜索arduino，将Arduino：Path的值改成自己的arduino安装目录。

<!--![arduino插件设置](arduino%E6%8F%92%E4%BB%B6%E8%AE%BE%E7%BD%AE.jpg)-->
![arduino插件设置](http://ezblog.gnway.cc/i/2022/08/25/63073c8f5ec79.jpeg)

## 四、创建工程

### 1.创建一个文件夹

### 2.创建.ino文件

### 3.修改配置

在自己的目录下创建.ino文件或打开例程一般会自动创建.vscode文件夹，里面包括三个文件，分别是arduino.json、c_cpp_properties.json、setting.json。其中c_cpp_properties.json主要用来配置程序的引用，.ino文件中的include的头文件必须在c_cpp_properties.json中的includepath属性中配置

<!--![c_cpp_properties文件配置](c_cpp_properties%E6%96%87%E4%BB%B6%E9%85%8D%E7%BD%AE.jpg)-->
![c_cpp_properties文件配置](http://ezblog.gnway.cc/i/2022/08/25/63073ce623cc4.jpeg)

**注：**引用头文件后还可能报错，可以在setting中进行如下设置

<!--![报错](%E6%8A%A5%E9%94%99.jpg)-->
![报错](http://ezblog.gnway.cc/i/2022/08/25/63073d136b3a4.jpeg)

<!--![setting设置](setting%E8%AE%BE%E7%BD%AE.jpg)-->
![setting设置](http://ezblog.gnway.cc/i/2022/08/25/63073df002394.jpeg)

### 4.编译上传

在窗口右下角 点击<Select Board Type>选择板子类型和<Select Serial Port>选择串口

<!--![选择板子和串口](%E9%80%89%E6%8B%A9%E6%9D%BF%E5%AD%90%E5%92%8C%E4%B8%B2%E5%8F%A3.jpg)-->
![选择板子和串口](http://ezblog.gnway.cc/i/2022/08/25/63073e122433d.jpeg)

**注：** arduino插件0.4.6版本有bug进入<Select Board Type>后无法选择板子，改下载0.4.5版本重启后正常。

<!--![选择板子](%E9%80%89%E6%8B%A9%E6%9D%BF%E5%AD%90.jpg)
-->
![选择板子](http://ezblog.gnway.cc/i/2022/08/25/63073e2dd7c6e.jpeg)
根据自己的板子类型选择即可。

点击上传。

![上传](%E4%B8%8A%E4%BC%A0.jpg)

**注：** 默认情况上传代吗的输出会显示乱码。

![乱码](%E4%B9%B1%E7%A0%81.jpg)

将文件C:\Users\ZXD\.vscode\extensions\vsciot-vscode.vscode-arduino-0.4.5\out\src\common\util.js中的codepage行注释掉即可。

![util注释](util%E6%B3%A8%E9%87%8A.jpg)

重启vscode后输出正常。

![正常输出](%E6%AD%A3%E5%B8%B8%E8%BE%93%E5%87%BA.jpg)

**至此就可以正常使用vscode进行esp8266进行开发工作**

**PS:**关闭360能够显著提高编译速度