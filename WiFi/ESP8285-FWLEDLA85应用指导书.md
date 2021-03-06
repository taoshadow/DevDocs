# 		                                           ESP8285-FWLEDLA85应用指导书 



<img>![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LOGO.bmp)

**版本V1.0** 

**版权©2019** 





##                                                                                                                                                                                                                            	     关于本手册



             本手册介绍了ESP8285-FWLEDLA85应用指导书产品参数，包含以下章节。 

| 章     | **标题**     | **内容**                          |
| :----- | :----------- | :-------------------------------- |
| 第一章 | 产品简介     | 概述ESP8285-FWLEDLA85的特点和功能 |
| 第二章 | 芯片管脚说明 | 介绍ESP8285管脚功能和管脚定义     |
| 第三章 | 功能说明     | 介绍ESP8285芯片所提供的功能       |
| 第四章 | 电气特性     | 介绍ESP8285芯片电气参数           |
| 第五章 | WIFI射频指标 | 介绍ESP8285芯片的射频指标         |
| 第六章 | 管脚定义     | 提供ESP8285芯片管脚分布图         |
| 第七章 | 封装信息     | 提供ESP8285芯片封装信息           |







## 一、  产品简介																																		

​	

               ESP8285-FWLEDLA85 是深圳酷宅科技有限公司（简称：酷宅科技）基 ESP8285 开发的通用多通道智能调光

芯片。同时提供了一套高度集成的Wi-Fi SoC解决方案，其低功耗、紧凑设计和高度稳定性可以满足用户的需求。

ESP8285-FWLEDLA85能够实现Wi-Fi的搜索连接，网络服务器的通讯，手机app的控制等基本功能，实现远程控

制，专为移动设备和物联网应用设计，主要应用领域：家庭自动化、智能调光场合。

​      

   **产品特性**

- 内置 32 位 MCU，可兼作应用处理器 
- 支持无线802.11 b/g/n 标准
- Wi-Fi @2.4 GHz，支持WPA/WPA2安全模式
- 802.11b 模式下+20.5dBm的最大输出功率
- UMA认证标准
- 支持W（冷）、Y（暖）智能调光
- 支持 Wi-Fi 远程控制 
- 支持OTA升级





## 二、芯片管脚说明



| 管脚 | 名称     | 功能                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| 1    | VDDA     | 模拟电源2.5V~3.6V                                            |
| 2    | LNA      | 射频天线接口， 建议保留π型匹配网络对天线进行匹配。           |
| 3    | VDD3P3   | 射频电源 2.5V~3.6V                                           |
| 4    | VDD3P3   | 射频电源 2.5V~3.6V                                           |
| 5    | NC       | NC                                                           |
| 6    | NC       | NC                                                           |
| 7    | CHIP_EN  | 芯片使能端高电平：有效；低电平：关闭。<br/>注：外部上拉 1~10K 电阻，接 100nF 电容到地。 |
| 8    | NC       | NC                                                           |
| 9    | MTMS     | GPIO14：暖光控制PWM输出端（channel1）                        |
| 10   | MTDI     | GPIO12：冷光控制PWM输出端（channel0）                        |
| 11   | VDDPST   | 数字/IO 电源 (1.8V ~ 3.3V)                                   |
| 12   | STATUS   | GPIO13：Wi-Fi 状态指示灯，低电平有效。                       |
| 13   | MTDO     | GPIO15：红灯光控制PWM输出端（channel2）<br> 注：芯片配置脚，需要下拉（1~4.7K）电阻到地 |
| 14   | GPIO2    | UART1_TX                                                     |
| 15   | GPIO0    | APP配置引脚，低电平有效，当低电平>5S进入配置模式。           |
| 16   | GPIO4    | GPIO4：绿灯光控制PWM输出端（channel3）                       |
| 17   | VDDPST   | 数字/IO 电源 (1.8V ~ 3.3V)                                   |
| 18   | NC       | NC                                                           |
| 19   | NC       | NC                                                           |
| 20   | NC       | NC                                                           |
| 21   | NC       | NC                                                           |
| 22   | NC       | NC                                                           |
| 23   | NC       | NC                                                           |
| 24   | GPIO5    | GPIO5：蓝灯光控制PWM输出端（channel4）                       |
| 25   | U0RXD    | 用于烧写Flash时UART RX                                       |
| 26   | U0TXD    | 用于烧写Flash时UART TX                                       |
| 27   | XTAL_OUT | 晶振输出端                                                   |
| 28   | XTAL_IN  | 晶振输入端                                                   |
| 29   | VDDD     | 模拟电源 2.5V~3.6V                                           |
| 30   | VDDA     | 模拟电源 2.5V~3.6V                                           |
| 31   | RES12K   | 串联 12 kΩ （1%）电阻到 GND                                  |
| 32   | EXT_RSTB | 外部重置信号（低电平有效）                                   |
| 33   | GND      | 电源地引脚                                                   |

      芯片功能为  ESP8285-FWLEDLA85  特定功能，非 ESP8285 芯片原有功能。

      芯片底部散热焊盘为 GND 焊盘。 







## 三、功能说明

​	

#### 3.1、Wi-Fi状态灯闪烁方式说明

       			设备端Wi-Fi状态灯的闪烁方式表征设备当前的网络工作状态，具体状态包括以下七种：

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/LED%E7%81%AF%E9%97%AA%E7%83%81%E8%AF%B4%E6%98%8E.bmp)

​	                                                  设备状态与Wi-Fi状态灯闪烁方式关系示意图



​	     Wi-Fi状态灯的闪烁特征以2秒为一个周期，如图所示，低电平灯亮，高电平灯灭。各状态详解：

A .  Normal : 设备正常工作，与云服务器连接正常。此时可以通过APP操控设备。在其它任何模式下，

​           都无法通过 APP操控设备。

B .  NO Wifi：设备无法连接到无线路由器。

C .  No Server：设备已经连接上无线路由器，但是无法连接到服务器（就是通常理解下的“无法上网”）。

D . Unregistered：表示设备还没有被绑定到任何账户下。一般的，设备需要与易微联账号绑定才可与云服务器      

      通信。在易微联APP“添加设备”可完成绑定操作。

E .  Upgrade：表示设备正在固件升级。

F .  Setting G1：表示设备正处于兼容配对模式。配置模式用于设备获取移动终端APP提供的加入服务网络的必要

     信息，包括路由器ssid、password和服务器ip、端口号等。

G . Setting G2：表示设备正处于快速配对模式。配置模式用于设备获取移动终端APP提供的加入服务网络的必要

      信息，包括路由器ssid、password和服务器ip、端口号等。两种配置，设备获取相关信息的方式不同，详见下

​          节所述。



#### 3.2、Wi-Fi模块的基本工作流程

​	I． 配置

      	      设备模块在未加入局域网时就是一个“信息孤岛”，设备端操作配合易微联APP设置，使设备获取加入服务

网络的必要信息，包括路由器ssid、password和服务器ip、端口号等。模块内置两种配置方式：

​	      1、兼容配对模式：移动终端作为station加入该AP组成局域网实现数据交互。快速配对模式（G状态，

​	      详情见3.1 Wi-Fi状态灯闪烁方式说明）下长按配置按键5S，设备进入兼容配对模式。点击易微联APP

       添 加设备（iOS移动终端需在“设置”菜单内手动连接ssid：ITEAD-10000XXXX， password12345678

       的热Android终端无需此操作），输入家庭路由器的ssid和password，完成设备的上线准备工作。

​	      2、快速配对模式：此方式Wi-Fi模块处于混杂模式（Wi-Fi Promiscuous），通过空快速配对模式：此方

       式Wi-Fi模块处于混杂模式（Wi-Fi Promiscuous），通过空空抓包的形式获取移动终端发出的包含ssid

       和password等信息的加密报文。上节所述A~D任意一个状态内长按配置按键5S，设备进入快速配对模

       式。点击易微联APP添加设备，输入家庭路由器的ssid和password，完成设备的上线配置工作。

​	

​	II． 上线

​	      设备模块从上电到连接服务器，需经历以下流程：

​		1、加入所配置路由器，连接Internet。

​		2、连接服务器。

​		3、注册设备，绑定至易微联账户。

​		4、获取设备应用参数，保持在线 。

​	      以上各个步骤，当连接/获取失败时，均有相应的退避策略和重连接机制，确保设备稳定、实时在线。



​	III． 升级

       模块设备连接升级服务器，下载更新至最新版本固件，实现设备的在线升级。



#### 3.3、定时器功能

​	      定时器功能通过APP配置，定时器分为以下四种:

1. 单次定时器：在指定时间执行操作。

2. 延时定时器：经过所设置的时间执行操作。

3. 循环定时器：周循环执行操作。

4. 重复定时器：日重复执行操作。

    

#### 3.4、定时功能说明

      ESP8285-FWLEDLA85 支持定时器操作，为了方便客户使用以及让其使用在更多的场景下，易微联APP提供了四种定时模式：

1. 单次定时：这个是最普通的定时设置，让用户可以设置这个设备的工作日程。比如那一天几点几分启动或者关

   闭，或者每周三几点几分启动或者关闭等。跟闹钟的设置类似，尤其是对重复在某些时刻要运行的设备，定时

   后使用起来非常方便。

2. 延时定时：延时是为了方便用户进行一次性快速的定时操作，比如在多久之后执行启动或者关闭的动作，可以

   非常方便的将某个设备打开后，让它运行一段时间然后关闭。本设备最多支持24小时的延时操作。		

3. 循环定时：对于某些设备，为了可以更方便的在某个场景下使用，易微联推出的循环定时设置，可以让一个设

   备从某个时刻开始，不断循环做一个事情。比如，让鱼缸的打氧泵从现在开始，每一小时启动一次，每次打氧

   20分钟后关闭，然后重复自动循环，保证鱼缸的氧气充足而无需人工干预。

4. 重复定时：重复定时是方便无需在次日进行同时间设置定时操作。比如，设定上班时间闹钟，时间设置好后，

   选择日期（日期天数为一周可选），闹钟就会在选择的日期内设定的时间开启。

   

#### 3.5、ESP8285-FWLEDLA85**功能说明**

      ESP8285-FWLEDLA85是一款智能Wi-Fi控制灯光方案，芯片通过输出两路PWM信号来实现LED的冷暖光调节。

仅需要极少的外部电路即可开发出完整智能调光产品。芯片内置我司物联网方案，用户无需了解复杂的TCP/UDP

及无线网络协议，即可实现设备的快速联网及控制。

##### 3.5.1、ESP8285-FWLEDLA85功能

      I． 冷暖光调节:

            在APP白光控制模式下，拉动进度条可实现对灯光的冷暖控制。

     II． 定时开关:

            在APP端设置定时开/关灯，至预定时间后设备执行开/关灯动作。

     III．断电记忆功能:

            当设备被APP添加成功过，下一次上电时，设备默认开启，灯光亮度保持为上一次断电前APP最后设置成    

            功的亮度。

##### 3.5.2、设备状态说明

     I． 新设备初次上电:

           新设备第一次上电时所有通道（颜色）的LED灯珠都会被点亮，此时整体灯光显示为白色。

     II．设备进入配置模式:

           设备进入配置模式后，冷暖光明暗逐渐交替呈呼吸状。

    III．正常工作模式:

           正常工作模式下，在APP端拉动进度条可实现对灯光的冷暖控制





## 四、ESP8285电气特性

​		

#### 	1 . 硬件参数

| 类型     | 参数                                  |
| -------- | ------------------------------------- |
| 芯片型号 | ESP8285                               |
| 工作电压 | 2.5V~3.6V                             |
| 工作电流 | 平均电流：80mA<br>最大工作电流：210mA |
| 工作温度 | -0℃~45℃                               |
| 封装大小 | 5mm×5mm                               |

#### 	2 . WI-FI参数

| 类型       | 参数                                                         |
| ---------- | ------------------------------------------------------------ |
| 无线标准   | IEEE 802.11b/g/n                                             |
| 频率范围   | 2.412GHz-2.484GHz                                            |
| 发射功率   | 802.11b: +20±2dBm (@11Mbps)<br>802.11g: +17±2dBm (@54Mbps)<br>802.11n: +14±2dBm (@HT20,MCS7) |
| 接收灵敏度 | 802.11b: -91 dBm (@11Mbps ,CCK)<br>802.11g: -75 dBm (@54Mbps, OFDM)<br>802.11n: -72 dBm (MCS7) |
| 天线类型   | PCB板载天线，外置天线，IPEX接口天线，陶瓷贴片天线            |







## 五、WIFI射频指标

| 描述                           | 最小值 | 典型值 | 最大值 | 单位 |
| :----------------------------- | :----: | :----: | :----: | :--: |
| 输入频率                       |  2412  |   -    |  2484  | MHz  |
| 输出阻抗                       |   -    | 39+j6  |   -    |  Ω   |
| 输入反射                       |   -    |   -    |  -10   |  dB  |
| 72.2Mbps 下， PA 的输出功率    |  15.5  |  16.5  |  17.5  | dbm  |
| 802.11b 模式下， PA 的输出功率 |  19.5  |  20.5  |  21.5  | dbm  |

#### 	1 . 灵敏度

| 描述                          | 最小值 | 典型值 | 最大值 | 单位mA |
| ----------------------------- | ------ | :----: | ------ | :----: |
| CCK 1Mbps                     |        |  -98   |        |  dBm   |
| CCK 11Mbps                    |        |  -91   |        |  dBm   |
| 6Mbps(1/2BPSK)                |        |  -93   |        |  dBm   |
| 54Mbps(3/4 64-QAM)            |        |  -75   |        |  dBm   |
| HT20，MCS7（65Mbps，72.2Mbps) |        |  -72   |        |  dBm   |

#### 	2 . 邻频抑制

| 描述         | 最小值 | 典型值 | 最大值 | 单位mA |
| ------------ | ------ | :----: | ------ | :----: |
| OFDM，6Mbps  |        |   37   |        |   dB   |
| OFDM，54Mbps |        |   21   |        |   dB   |
| HT20，MCS0   |        |   37   |        |   dB   |
| HT20，MCS7   |        |   20   |        |   dB   |







## 六、ESP8285管脚定义

​	

            	管脚定义如下图所示：



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/ESP8285%E5%BC%95%E8%84%9A%E5%8A%9F%E8%83%BD.bmp)









## 七、ESP8285封装信息



- 封装类型：QFN-32L

- 芯片尺寸大小：5mm x 5mm

  

![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/ESP8285%E5%B0%81%E8%A3%85%E5%B0%BA%E5%AF%B8%E5%9B%BE.bmp)

​	



------





 

   



![图片描述](https://raw.githubusercontent.com/june0854/june0854.github.io/%E5%9B%BE%E7%89%87/%E7%89%88%E6%9D%83%E8%AF%B4%E6%98%8E.bmp )