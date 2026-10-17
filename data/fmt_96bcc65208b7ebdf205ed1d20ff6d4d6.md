
描述：图 6.13 显示了停车系统的逐步处理过程。活动流包含了管理员和用户流程。

# 实现

## 模块

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_97_0.png)

图 6.13 活动图。

- 位置和区域的选择。
- 检查车位状态。
- 车位更新。
- 可视化。

## 架构

该架构代表了停车系统的整体工作原理（图 6.14）。它由两个模块实现：硬件实现和 Web 服务器。两个模块都会更新车位状态并在屏幕上显示输出。在第一个模块中，我们实现了硬件组件，使用 Arduino 板板开发停车系统。Arduino 板板作为微控制器工作并控制整个系统。停车系统中有一个入口和出口门，用于允许车辆进入系统。

红外传感器用于感知车辆并向 Arduino 发送有关车辆状态的信号。Wi-Fi 模块用于将 Arduino 与 Web 服务器集成，以更新车位状态。

Web 服务器使用 Arduino IDE 开发，用于为用户更新车位状态。在 Web 服务器中，用户可以选择位置和特定的停车区域。当选择特定区域时，Web 服务器将向用户显示车位状态。

车位详细信息存储在数据库中以维护记录。管理员可以定期监控停车系统并每三分钟更新一次状态。该系统将帮助用户了解当前的可用状态，并缩短寻找停车的时间。

# 区块链与物联网

![](img/7237166d8c6f79ea99cc6e305e5ec1f5_98_0.png)

图 6.14 架构图。

## 模块描述

### 位置和区域的选择

此模块用于选择搜索停车位的位置和区域。用户将选择位置。该模块将使用 GPS 选择位置。通过使用该模块，用户可以检查他们所需区域的状态。

### 检查车位状态

车位状态显示在 LCD 和 Web 服务器上。LCD 将固定在停车系统中，用于向用户显示状态。Web 服务器与停车系统集成。

### 更新车位

此模块由管理员控制。管理员可以监控停车系统并每三分钟更新一次状态。车位详细信息存储在数据库中。

### 可视化

生成的结果是可视化的。管理员可以监控系统。

# 测试

## 手动测试

基于物联网的停车系统

| 测试用例 | 测试描述 | 测试步骤 | 预期结果 | 实际结果 |
| --- | --- | --- | --- | --- |
| 1 | 检查 Arduino 是否安装 | 安装 Arduino | Arduino 可以安装 | Arduino 已安装 |
| 2 | 检查 IDE 是否可以打开 | 打开 IDE | IDE 可以打开 | IDE 已打开 |
| 3 | 检查 Arduino 是否可以编译 | 编译 Arduino | Arduino 可以编译 | Arduino 已编译 |
| 4 | 检查代码是否可以执行 | 执行代码 | 代码可以执行 | 代码已执行 |
| 5 | 检查代码是否可以编译 | 编译代码 | 代码可以编译 | 代码已编译 |
| 6 | 检查代码是否可以执行 | 执行代码 | 代码可以执行 | 代码已执行 |
| 7 | 检查状态是否可以显示 | 显示状态 | 状态可以显示 | 状态已显示 |
| 8 | 检查状态是否正确 | 显示状态 | 状态显示正确 | 状态显示正确 |
| 9 | 检查用户是否可以选择位置 | 选择位置 | 用户可以选择位置 | 用户已选择位置 |
| 10 | 检查用户是否可以选择特定区域 | 选择区域 | 用户可以选择区域 | 用户已选择特定区域 |
| 11 | 检查系统是否每三分钟更新 | 更新系统 | 系统可以每三分钟更新 | 系统已每三分钟更新 |

表 6.1（持续）

Arduino 实现测试

| 测试用例 ID | 测试描述 | 测试步骤 | 预期结果 | 实际结果 |
| --- | --- | --- | --- | --- |
| T-1 | 检查 Arduino 板是否正常工作 | 测试 Arduino 板 | Arduino 板可以工作 | Arduino 板已工作 |
| T-2 | 检查 ESP8266 NodeMCU 是否正常工作 | 测试 ESP8266 NodeMCU | ESP8266 NodeMCU 可以工作 | ESP8266 NodeMCU 已工作 |
| T-3 | 检查舵服是否正常工作 | 测试舵服 | 舵服可以工作 | 舵服已工作 |
| T-4 | 检查红外 (IR) 传感器是否正常工作 | 测试红外传感器 | 红外传感器可以工作 | 红外传感器已工作 |
| T-5 | 检查 LCD 显示器是否正常工作 | 测试 LCD 显示器 | LCD 显示器可以工作 | LCD 显示器已工作 |
| T-6 | 检查舵服是否可以打开关闭入口门 | 测试入口门 | 入口门可以打开关闭 | 入口门已打开关闭 |
| T-7 | 检查舵服是否可以打开关闭出口门 | 测试出口门 | 出口门可以打开关闭 | 出口门已打开关闭 |

表 6.2

## 表 6.2（续）

Arduino 实现的测试

| 测试用例 ID | 测试描述 | 测试步骤 | 测试输入 | 预期结果 | 实际结果 |
|---|---|---|---|---|---|
| T-8 | 检查红外传感器是否正确检测到物体 | 将物体放在传感器附近 | 传感器将检测到物体。 | 传感器必须检测到物体并向 Arduino 板发送信号。 | 传感器必须检测到物体并向 Arduino 板发送信号。 |
| T-9 | 检查 LCD 是否正确显示车位状态 | 供电并测试输入 | 必须将物体放入槽内以检查 LCD | LCD 必须正确显示车位状态。 | LCD 显示显示了状态。 |
| T-10 | 检查 ESP256 NodeMCU 是否与 Web 服务器集成。 | | 编译 Web 服务器代码。 | 服务器在 Arduino 板上正确显示状态。 | 服务器在 Arduino 板上正确显示了状态。 |

# 基于区块链的停车系统

## 表 6.3

## 硬件需求测试

| 测试 ID | 描述 | 状态 |
| --- | --- | --- |
| T1-1 | 检查 Arduino 中是否安装了 Arduino IDE。 | 通过 |
| T1-2 | 检查 Arduino IDE 是否正常打开。 | 通过 |
| T1-3 | 检查是否为 Arduino 板实现了代码。 | 通过 |
| T1-4 | 检查实现的 Arduino 板代码是否已执行。 | 通过 |
| T1-5 | 检查代码是否已在 Web 服务器上实现。 | 通过 |
| T1-6 | 检查实现的 Web 服务器是否与 Arduino 板集成。 | 通过 |
| T1-7 | 检查 Web 服务器是否显示车位状态。 | 通过 |
| T1-8 | 检查服务器是否允许用户选择位置。 | 通过 |
| T1-9 | 检查服务器是否允许用户选择特定区域。 | 通过 |
| T1-10 | 检查系统是否每 3 分钟更新一次。 | 通过 |
| T1-11 | 检查 Arduino 板工作是否正常。 | 通过 |
| T2-1 | 检查 ESP8266 NodeMCU 是否工作正常 | 通过 |
| T2-2 | 检查舵机是否工作正常。 | 通过 |
| T2-3 | 检查红外 (IR) 传感器是否工作正常。 | 通过 |
| T2-4 | 检查 LCD 显示器是否工作正常 | 通过 |
| T2-5 | 检查舵机是否打开和关闭出口闸。 | 通过 |
| T2-6 | 检查红外传感器是否正确检测到物体。 | 通过 |
| T2-7 | 检查 LCD 是否正确显示车位状态。 | 通过 |
| T2-8 | 检查 ESP8266 NodeMCU 是否与 Web 服务器集成。 | 通过 |

# 源代码

## Arduino 实现

```cpp
#include <Servo.h> #include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2); const int analogInPin = A0;
int sensorValue = 0; int servoPin = 10; int i = 90;
Servo servo;
const int analogIn1 = A1; int sensorValue1 = 0;
int servoPin1 = 9; int i = 90;
Servo servo;
const int analogIn2 = A2; int sensorValue2 = 0;
const int analogIn3 = A3; int sensorValue3 = 0;
const int analogIn4 = A4;
int sensorValue4 = 0;
const int analogIn5 = A5; int sensorValue5 = 0;
int LIGHT1 = 13; int LIGHT2 = 8; int LIGHT3 = 7; int LIGHT4 = 6;
```

## 区块链与物联网

```cpp
void setup()
{
  Serial.begin(9600); pinMode(LIGHT1, OUTPUT); pinMode(LIGHT2, OUTPUT);
  pinMode(LIGHT3, OUTPUT); pinMode(LIGHT4, OUTPUT);
  servo.attach(servoPin); servo.attach(servoPin1); lcd.begin
  (16, 2);
}
void loop()
{
  lcd.setCursor(1,1); lcd.println("FILL ");
  lcd.setCursor(0,0); lcd.println("EMPTY ");
  if(sensorValue2 = analogRead(analogIn2) < 600)
    digitalWrite(LIGHT1, HIGH); lcd.setCursor(6,1); lcd.println("1 ");
  else
    digitalWrite(LIGHT1, LOW); Serial.println(sensorValue2);
    lcd.setCursor(6,0); lcd.println("1 ");
  if(sensorValue3 = analogRead(analogIn3) < 600)
    digitalWrite(LIGHT2, HIGH); lcd.setCursor(8,1); lcd.println("2 ");
  else
    digitalWrite(LIGHT2, LOW); Serial.println(sensorValue3);
    lcd.setCursor(8,0); lcd.println("2");
  if(sensorValue4 = analogRead(analogIn4) < 600)
    digitalWrite(LIGHT3, HIGH); lcd.setCursor(10,1); lcd.println("3 ");
  else
    digitalWrite(LIGHT3, LOW); lcd.setCursor(10,0); lcd.println("3");
  if(sensorValue5 = analogRead(analogIn5) < 600)
    digitalWrite(LIGHT4, HIGH); lcd.setCursor(12,1); lcd.println("4 ");
  else
    digitalWrite(LIGHT4, LOW); lcd.setCursor(12,0); lcd.println("4");
  if(sensorValue = analogRead(analogInPin) < 700){
    if (int i = 0; i<=90) { servo.write(i); delay(15); }
  else
    if (int i = 90; i>= 0) { servo.write(i); delay(15); }
  if(sensorValue = analogRead(analogIn1) < 700){
    if (int i = 0; i<=90) { servo.write(i); delay(15); }
  else
    if (int i = 90; i>= 0) { servo.write(i); delay(15); }
}
```

## Web 实现
