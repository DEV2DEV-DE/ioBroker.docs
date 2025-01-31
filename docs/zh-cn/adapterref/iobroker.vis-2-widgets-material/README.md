---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.vis-2-widgets-material/README.md
title: ioBroker.vis 2.0 的材质小部件
hash: TeiCxaPScaGHK8dfWyOoWOaqsjzlFUgLU1XalKrs/og=
---
![标识](../../../en/adapterref/iobroker.vis-2-widgets-material/admin/vis-2-widgets-material.png)

![安装数量](http://iobroker.live/badges/vis-2-widgets-material-stable.svg)
![NPM版本](http://img.shields.io/npm/v/iobroker.vis-2-widgets-material.svg)
![下载](https://img.shields.io/npm/dm/iobroker.vis-2-widgets-material.svg)
![国家公共管理](https://nodei.co/npm/iobroker.vis-2-widgets-material.png?downloads=true)

# IoBroker.vis 2.0 的材质小部件
## 小部件
### 按钮和开关
![开关](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-switches.png)

![开关](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-switches-buttons.png)

![开关](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-switches-buttons-2.png)

＃＃＃ 钟
- 模拟

![时钟模拟](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-clock-analog-1.png)

- 模拟变化

![模拟时钟 2](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-clock-analog-2.png)

- 数字的

![数字的](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-clock-digital-1.png)

- Digital2（SVG 文本）

![数字2](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-clock-digital-2.png)

### 简单状态
使用此小部件，您可以控制一台设备。布尔值或数字。

- 数字

![简单状态](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-simple-state-1.png)

- 控制

![简单状态](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-simple-state-2.png)

### 在小部件中查看
![在小部件中查看](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-view-in-widget-1.png)

不作为按钮：视图可以全尺寸显示，并且您可以控制视图中的元素。

![在小部件中查看 - 按钮](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-view-in-widget-2.png)

作为按钮：您可以显示视图的小缩略图，按下它，它将以全尺寸显示。

### 恒温器
![恒温器](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-thermostat-1.png)

此外，如果您激活它，它还可以显示历史记录。

### 带图表的实际值
![实际价值](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-actual-value-1.png)

![实际值与图表](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-actual-value-2.png)

＃＃＃ 安全控制
![安全控制](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-security-0.png)

![安全控制](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-security-1.png)

您可以定义延迟（以秒为单位）。

激活后，定义的ID将被写入延迟秒数，延迟结束后，定义的ID将被设置为0，警报ID将被设置为true。

![安全控制](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-security-2.png)

### 玩家
![玩家](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-player.png)

＃＃＃ 地图
![玩家](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-map-1.png)

＃＃＃ 相机
![玩家](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-camera-1.png)

### HTML 模板
![玩家](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-html-1.png)

Html 模板可用于显示任何 html 代码。
此外，您也可以使用此小部件显示图像或 iframe。

### 百叶窗
![百叶窗](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-blinds-1.png)

![玩家](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-blinds-2.png)

### 彩色灯
通过RGB灯小部件，您可以控制不同类型的RGB灯。这里有些例子：

- RGB 颜色设置为一种状态，如“#RRGGBB”
- R/G/B颜色设置为0到255的不同状态
- RGBW 作为一个变量，如“#RRGGBBWW”
- R/G/B/W颜色设置为0到255的不同状态
- 色调/饱和度/亮度作为 3 种不同的状态
- 色温为从 2700 到 6500 的一种状态或由物体的最小/最大定义
- 白色模式状态可用于通过特殊状态在RGB和白色模式之间切换

![RGB灯1个](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-rgb-1.png)

![RGB灯2](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-rgb-2.png)

＃＃＃ 门锁
![门锁](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-lock.png)

＃＃＃ 吸尘器
该小部件主要适用于小米吸尘器。但它也可以用于任何其他真空吸尘器。

唯一的区别是小米支持房间清洁。

![吸尘器](../../../en/adapterref/iobroker.vis-2-widgets-material/img/material-vacuum.png)

### 时间选择器
＃＃ 去做
- 带百叶窗的百叶窗展开

<!-- 下一个版本的占位符（在行的开头）：

### **正在进行中** -->

## Changelog
### 1.3.14 (2023-12-05)
* (bluefox) Allowed with on click on the widget toggling the ON/OFF state of RGB widget
* (bluefox) Added class names to ON/OFF widgets to allow styling

### 1.3.11 (2023-11-17)
* (bluefox) Allowed opening/closing dialogs of some widgets by command

### 1.3.9 (2023-11-10)
* (bluefox) updated packages

### 1.3.8 (2023-11-08)
* (bluefox) Corrected RGB widget if minimal is equal with maximal

### 1.3.5 (2023-11-06)
* (bluefox) Corrected layout of RGB widget
* (bluefox) Added option for RGB widget to hide brightness control
* (bluefox) Added option for white mode in RGB widget

### 1.3.3 (2023-10-26)
* (bluefox) Corrected layout of RGB widget
* (bluefox) Added color settings to actual
* (bluefox) Vacuum settings were hidden

### 1.3.2 (2023-10-14)
* (bluefox) Small improvements done

### 1.3.1 (2023-10-13)
* (bluefox) Added the vacuum cleaner widget

### 1.2.1 (2023-09-18)
* (bluefox) Added door lock, rgb and thermostat to switches widget

### 1.1.3 (2023-09-10)
* (bluefox) Door lock improved

### 1.1.0 (2023-09-08)
* (bluefox) Added door lock

### 1.0.0 (2023-08-21)
* (bluefox) Added RGB widget

### 0.8.5 (2023-08-11)
* (bluefox) Improvement of the widget loading

### 0.8.4 (2023-08-10)
* (bluefox) Improvement of wizard

### 0.8.3 (2023-07-30)
* (bluefox) Font styles are applied to all buttons

### 0.8.2 (2023-07-19)
* (bluefox) Corrected small layout problems

### 0.8.0 (2023-07-18)
* (bluefox) Added wizard for widgets

### 0.7.1 (2023-07-02)
* (bluefox) Added washer widget

### 0.6.2 (2023-06-29)
* (bluefox) Allowed usage without a frame for all widgets

### 0.6.0 (2023-06-28)
* (bluefox) Added blinds to switches widget
* (bluefox) Allowed to place widgets in widgets

### 0.5.3 (2023-06-21)
* (bluefox) Corrected errors with view in widget

### 0.5.1 (2023-06-20)
* (bluefox) Added widget to switch the theme
* (bluefox) Improved HTML widget to show iframe and image

### 0.4.0 (2023-06-16)
* (bluefox) Added button texts for switches widget
* (bluefox) Removed static widget, as it was replaced by switches widget

### 0.3.1 (2023-06-14)
* (bluefox) Improved buttons widget

### 0.2.13 (2023-03-22)
* (bluefox) BREAKING CHANGE: The names of widgets must be entered anew 
* (bluefox) update packages

### 0.2.9 (2023-02-27)
* (bluefox) Made this adapter singleton

### 0.2.2 (2023-02-22)
* (bluefox) Update packages

### 0.2.1 (2022-11-26)
* (bluefox) Implemented the blinds widget

### 0.1.5 (2022-10-27)
* (bluefox) First beta version

### 0.1.2 (2022-10-21)
* (bluefox) initial commit

## License
The MIT License (MIT)

Copyright (c) 2022-2023 Denis Haev <dogafox@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.