
```cpp
#include <ESP8266WiFi.h> #include <WiFiClient.h>
#include <ESP8266WebServer.h> const int ProxSensor=16;
char values;
const int ProxSensor=5; char values1;
const int ProxSensor=4; char values2;
const int ProxSensor=0; char values3;
const char* ssid = "wifi";
double data;
String readcurrent(){
  long state = digitalRead(ProxSensor); if(state == HIGH) {
    Serial.println(state); values='E';
  }
  else{
    Serial.println(state);
    values='F';
  }
  return String(values);
}
String readcurrent1(){
  long state = digitalRead(ProxSensor1); if(state == HIGH) {
    Serial.println(state); values1='E';
  }
  else
  {
    Serial.println(state1); values1='F';
  }
  return String(values1);
}
String readcurrent2() {
  long state2 = digitalRead(ProxSensor2); if (state2 == HIGH) {
    Serial.println(state2); values2='E';
  }
  else {
    Serial.println(state2); values2='F';
  }
  return String(values2);
}
String readcurrent3() {
  long state3 = digitalRead(ProxSensor3); if (state3 == HIGH) {
    Serial.println(state3); values3='E';
  }
  else {
    Serial.println(state3); values3='F';
  }
  return String(values3);
}
```

```html
<head>
<title>Font Awesome Icons</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://cdn.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<style>
body {
  background-image: url('https://c4.wallpaperflare.com/wallpaper/590/532/911/colors-of-the-dawn-wallpaper-preview.jpg');
  background-repeat: no-repeat; background-attachment: fixed;
  background-size: cover;
}
</style>
</head>
<body>
<center><font size="11"><p style="color:red">停车场</p></center>
<a></a>
<center>
<i class="fas fa-car-side" style="size:4px;color:black"> <font size="6"><span class="ds-labels">车位1 </span> <span style="color:blue">车位2 </span> <span style="color:blue">车位3 </span> <span style="color:blue">车位4 </span></font>
```

```javascript
String processor(const String &var) {
  if(var == "CAR PARK1") { return readcurrent(); }
  if(var == "CAR PARK2") { return readcurrent1(); }
  if(var == "CAR PARK3") { return readcurrent2(); }
  if(var == "CAR PARK4") { return readcurrent3(); }
  return "";
}
void setup(){
  Serial.begin(115200);
  WiFi.begin(ssid, password);
  Serial.println("");
  while (WiFi.status() != WL_CONNECTED) { delay(5000);
    Serial.print("");
  }
  Serial.println("");
  Serial.print("连接到 ");
  Serial.println(ssid);
  Serial.print("IP地址: ");
  Serial.println(WiFi.localIP());
  server.on("/", HTTP_GET, []() {
    server.send(200, "text/html", index_html);
  });
  server.on("/values", HTTP_GET, []() {
    server.send(200, "text/plain", readcurrent());
  });
  server.on("/values1", HTTP_GET, []() {
    server.send(200, "text/plain", readcurrent1());
  });
  server.on("/values2", HTTP_GET, []() {
    server.send(200, "text/plain", readcurrent2());
  });
  server.on("/values3", HTTP_GET, []() {
    server.send(200, "text/plain", readcurrent3());
  });
  server.begin();
  Serial.println("Web 服务器启动!");
}
void loop(){
  server.handleClient();
}
</script>
</body>
```

# 结论与未来改进

本研究实现了一种基于物联网的停车系统，该系统可以在线检查车位状态，并以此创建了检查状态的服务器。用户可以向服务器添加额外功能。在未来的改进中，研究人员希望提高服务器效率，并添加预订车位、从入口引导至车位以及支付选项的功能。这将有助于用户寻找停车位，并且更加用户友好。

# 基于物联网的区块链停车系统

## 参考文献

- 1. Mazlan, Muhammad & A Hamis, Isedza Rahmi and Kamaludin, Halazila. ‘基于无线频率识别 (RFID) 的汽车停车系统’,JOIV: International Journal on Informatics Visualization, vol. 2, no. 4–2, 2018.
- 2. Aye, K. Kan, Zin Oo, P and Naing, W. ‘基于 RFID 的自动多层汽车停车系统’,International Journal of Science and Engineering Applications, Vol. 8, no. 07, pp. 172–175, 2019.
- 3. Abdullah, Omar, et al. ‘基于 WSN、RFID 和物联网的新型安全智能停车管理系统 (SPMS)’,第15次学习与技术会议 (L&T). IEEE, 2018.
- 4. Razinkavasil, Anastasia, Chol, Chun-Yan, and Jeong, Hong-Tae. ‘车辆的智能自动停车系统’,International Journal of Fuzzy Logic and Intelligent Systems, vol. 12, no. 3, pp. 226–231, 2012.
- 5. Ashzwanth, D., Mosby, Mithul Titten and Balachander, T. ‘自动化汽车停车系统’,纳米科学物理与光子学国际会议, vol. 162, pp. 1–9, 2019.
- 6. Patel, M. and Bhonga, N. ‘用于智能停车系统的无线传感器网络和 RFID’,International Journal of Emerging Technology and Advanced Engineering, vol. 3, no. 4, pp. 188–192, 2013.
- 7. DhimanReddy, P, Rajeshwarao, A. and Ahmed, D. Syed Musht. ‘基于图像技术的智能停车引导与信息系统’,International Journal of Advanced Research in Computer and Communication Engineering, vol. 2, no. 10, 2013.
- 8. Al-Karusi, H and Al-Bahady, I. ‘基于图像处理的智能停车’,World Journal of Engineering and Technology, vol. 2, no. 02, pp. 55–67, 2014.
- 9. Rahayu, Y. and Mustafa, F. ‘基于 GSM 技术的安全汽车预订系统’,International Journal of Computer and Communication Engineering, vol. 2, no. 4, 518, 2013.
- 10. Yee, H. C. and Rahayu, Y. ‘通过 ZigBee 技术监控停车可用性’,International Journal of Future Communication and Communication, vol. 3, no. 6, pp. 377, 2014.
- 11. Pooja, A. ‘基于 WSN 的安全车辆停车管理与预订系统’,通信、计算、电气科学与系统进展国家会议 (NCRACESS-2015), 2015.
- 12. Karbab, E., Djenouri, D., Boulkabul, S. and Bagula, A. ‘使用无线网络传感器和主动 RFID 的停车场管理’,2015 IEEE 电子/信息技术国际会议 (EIT), pp. 373–378. IEEE, 2015, May.
- 13. Orric, S., Silva, and Hanke, G. P. ‘一种无线智能停车系统’,工业电子协会, IEEE IECON 2015-14届 IEEE 年度会议, pp. 00410– 00414. IEEE, 2015.
- 14. Chen, Y., Lin, S. W. and Li, C. C. ‘基于代理的平台动态停车协商与引导’,Expert Systems with Applications, 35, no. 3, pp. 805–817, 2008.
- 15. Basavaraju, S. R. ‘利用物联网 (IoT) 的自动智能停车系统’,International Journal of Scientific and Research Publications, vol. 5, no. 12, pp. 629–632, 2015.
- 16. Gandhi, B. K. and Rao, M. K. ‘基于物联网的汽车停车系统原型’,Indian Journal of Science and Technology, vol. 9, no. 17, pp. 55–67, 2014.

## 基于区块链的在线考勤系统

### 引言

考勤实践随着物联网 (IoT)的发展而演变。许多应用程序使用区块链来安全地采集数据。但传统的考勤是通过记录簿完成的，这存在许多问题。

## 文献综述

- 1. Mazlan 等人提出了基于 RFID 的汽车停车系统。
- 2. Aye 等人提出了基于 RFID 的自动多层汽车停车系统。
- 3. Abdullah 等人提出了基于 WSN、RFID 和物联网的安全智能停车管理系统。
- 4. Razinkavasil 等人提出了车辆智能自动停车系统。
- 5. Ashzwanth 等人提出了自动化汽车停车系统。
- 6. Patel 和 Bhonga 提出了无线传感器网络。
- 7. Dhiman Reddy 提出了智能停车引导。
- 8. Al-Karusi 和 Al-Bahady 提出了基于图像的停车系统。
- 9. Rahayu 和 Mustafa 提出了一种安全的汽车预订系统。
- 10. Yee 和 Rahayu 提出了通过 ZigBee 进行监控。
- 11. Pooja 提出了基于 WSN 的安全停车管理。
- 12. Karbab 等人提出了使用主动 RFID 的停车场管理。
- 13. Orric 等人提出了一种无线智能停车系统。
- 14. Chen 等人提出了动态停车协商。
- 15. Basavaraju 提出了利用物联网的智能停车系统。
- 16. Gandhi 和 Rao 提出了基于物联网的停车系统原型。

## 系统分析

所提出的系统使用 `MERN` 栈构建。与 `PHP` 相比，`MERN` 栈缺乏灵活性。因此，该 Web 应用程序是借助 `MERN` 栈（`MongoDB`, `Expressjs`, `Nodejs`, `Reactjs`）创建的。

## 需求规范

所系统的用例图如图 7.2 所示。这里涉及的角色有教师和管理员。场景是收集学生信息。

| 教师 | 管理员 |
| --- | --- |
| 用户 ID: Email | 用户 ID: Email |
| 密码: String | 密码: String |
| 登录() | 登录() |
| 选择部门() | 创建用户() |
| 选择年份() | 读取用户() |
| 选择班级() | 更新用户() |
| 签勤() | 删除用户() |
| 查看报告() | 查看报告() |
| 退出登录() | 下载报告() |
| | 退出登录() |

| 服务器 |
| --- |
| 服务器 ID: String |
| 维护数据库() |

# 基于区块链的在线考勤管理系统 101

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_113_0.png)

图 7.4 序图。

# 系统实现

## 系统实现中的模块

- 教师模块
- 管理员模块

## 架构图

该图（图 7.6）展示了考勤管理流程的整体工作原理。它通过两个模块实现：
1. 管理员模块
2. 教师模块

两个模块都从管理员和教师处查询数据，执行考勤流程并并生成结果。在第一个模块中，研究人员使用 `MERN` 栈创建了学生列表。实现该模块的原因是为了执行考勤流程。管理员可以操作学生详情，还可以按日期检查学生状态。然后，管理员还会生成考勤流程报告，并可以按日期查看报告。

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_114_0.png)

**图 7.5** 活动图。

在第二个模块中，研究人员使用 `MERN` 栈实现了学生考勤标记。使用 `React` 创建了界面并连接到 `MongoDB` 数据库。然后，由教师进行考勤标记。

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_115_0.png)

图 7.6 架构图。

考勤数据存储在 `MongoDB` 的 `attendance` 表中。考勤状态在页面显示。

### 模块描述

### 教师模块

在教师模块中，使用 `MERN` 栈设计了网页。姓名、性别、部门、出生日期 (`DOB`)、年级和班级等信息从 `MongoDB` 获取。教师可以查看考勤状态。

### 管理员模块

在管理员模块中，使用 `MERN` 栈设计了网页。管理员可以创建学生列表并修改学生列表内容。考勤状态被维护，并可以生成并下载 `CSV` 格式的考勤报告。

# 后端实现

### INDEX.JS

```javascript
// 中间件
app.use(morgan('dev'));
// 路由
const router1 = require('./SchemaRoutes/StudentRouter');
app.use('/router1');
const router2 = require('./SchemaRoutes/AttendanceRouter');
app.use('/Attendance', router2);
// 本地数据库连接
mongoose.connect('mongodb+srv://mohanraj:56832644@mern-db--ilfch.mongodb.net/Attendance-');
```

### Schema

```javascript
// 学生 Schema
const Students = new mongoose.Schema({
  Name: {},
  Regno: {
    type: Number,
    required: true,
    trim: true,
    min: 1000000000,
    max: 9999999999
  },
  Department: {},
});
```
