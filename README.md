基于ESP8266和MAX7219 LED点阵模块的多功能数字时钟，支持WiFi连接、NTP时间同步和多种信息显示。

功能特性
WiFi连接：自动连接到指定WiFi网络
NTP时间同步：使用阿里云NTP服务器进行时间同步
多页面显示：循环显示时间、日期、星期
LED显示屏：使用MAX7219模块驱动的LED点阵显示屏
屏幕旋转：支持180度旋转显示
串口调试：提供详细的串口日志信息
硬件要求
ESP8266开发板（如NodeMCU、Wemos D1 Mini等）
MAX7219 LED点阵模块（4个级联）
连接线若干
接线说明
MAX7219引脚	ESP8266引脚	NodeMCU引脚
VCC	         3.3V	        3.3V
GND	         GND          GND
DIN        	GPIO13	      D7
CS	        GPIO15       	D8
CLK         GPIO14	      D5
所需库文件
本项目依赖以下Arduino库：

1. MD_Parola
功能：LED矩阵文本显示库，提供文本动画和显示效果
版本：推荐使用最新版本
安装方法：
Arduino IDE: 工具 → 管理库 → 搜索"MD_Parola" → 安装
或从GitHub下载：https://github.com/MajicDesigns/MD_Parola
2. MD_MAX72xx
功能：MAX7219/MAX7221 LED驱动器控制库
版本：推荐使用最新版本
安装方法：
Arduino IDE: 工具 → 管理库 → 搜索"MD_MAX72xx" → 安装
或从GitHub下载：https://github.com/MajicDesigns/MD_MAX72XX
3. NTPClient
功能：简化NTP时间获取的Arduino库
版本：推荐使用最新版本
安装方法：
Arduino IDE: 工具 → 管理库 → 搜索"NTPClient" → 安装
或从GitHub下载：https://github.com/arduino-libraries/NTPClient
库之间的关系：
MD_Parola (文本显示)
    ↓
MD_MAX72xx (硬件驱动)
    ↓
ESP8266WiFi (WiFi连接)
    ↓
NTPClient (时间同步)
安装步骤
打开Arduino IDE
进入 工具 → 管理库
搜索并安装以下库：
MD_Parola
MD_MAX72xx
NTPClient
重启Arduino IDE
配置说明
在代码开头修改以下配置：

cpp
const char* ssid = "你的WiFi名称";
const char* password = "你的WiFi密码";
显示页面
时钟会循环显示以下信息：

时间显示（10秒）

格式：HH:MM
冒号每秒闪烁
日期显示（5秒）

格式：MM-DD
例如：12-25
星期显示（3秒）

格式：英文星期缩写
SUN, MON, TUE, WED, THU, FRI, SAT


屏幕旋转
代码默认设置屏幕旋转180度，如需调整，请修改以下代码：

cpp
// 屏幕旋转180度
display.setZoneEffect(0, true, PA_FLIP_UD);  // 上下翻转
display.setZoneEffect(0, true, PA_FLIP_LR);  // 左右翻转
使用方法
安装所需库文件
修改WiFi配置信息
编译并上传代码到ESP8266
连接硬件
上电运行
串口调试
波特率：115200

系统会输出详细的启动和运行日志，便于调试和监控。

许可证
GUN License


贡献
欢迎提交Issue和Pull Request来改进这个项目。
