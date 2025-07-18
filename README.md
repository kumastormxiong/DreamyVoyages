# 幻梦之旅（Dreamy Voyage）本地版说明文档

## 游戏简介

幻梦之旅（Dreamy Voyage）是一个基于slowroads.io的音乐游戏，我提供所有原创音乐，所有游戏玩法均归属原作者。 WebGL 和 Three.js 的浏览器 3D 驾驶游戏，主打程序化生成的无限道路和风景，带来放松的驾驶体验。无需联网即可本地运行。

要想体验我的游戏，请访问：https://dreamy.voyage

---

## 功能架构总览

- **渲染引擎**：基于 Three.js 实现 3D 场景渲染。
- **地形生成**：使用噪声算法（如 Perlin/Alea）实时生成地形和道路。
- **车辆系统**：多种车型可选，支持动力、转向、物理参数自定义。
- **控制系统**：支持键盘、鼠标、手柄三种输入方式，均可自定义。
- **UI与设置**：可调节画质、音量、辅助功能、界面显示等。
- **音效系统**：原创背景音乐、支持环境音、车辆音效、操作提示音。

## 操作说明

- **方向键/WASD**：控制车辆移动
- **Q/E**：切换场景/模式
- **C**：切换摄像机视角
- **T**：自由视角
- **F**：自动驾驶开关
- **空格**：手刹
- **R**：重置车辆
- **U**：显示/隐藏UI
- **O**：上一首音乐
- **L**：下一首音乐
- **M**：静音
- **P**：暂停
- **F3**：调试模式

---

## 主要自定义参数与功能说明

### 1. 控制设置

- **键盘映射**：
  - Forward（前进）、Backward（后退）、Left/Right（转向）、Boost（加速）、Handbrake（手刹）、CameraMode（切换视角）、Autodrive（自动驾驶）、Reset（重置）、Mute（静音）、Pause（暂停）等。
  - 所有按键均可在设置中自定义。
- **鼠标控制**：
  - axisWidth（转向条宽度）、steerSmoothing（转向平滑度）、steerRange（最大转向角）、linearity（线性度）等。
- **手柄控制**：
  - steerSmoothing（转向平滑度）、steerRange（最大转向角）、linearity（线性度）、deadzone（死区）等。

### 2. 车辆参数

- **车型选择**：Roadster、Bus、Bike 等。
- **动力与物理**：
  - mode（驱动方式）、gripFactor（轮胎抓地力）、speedFactor（动力系数）、steerRotation（方向盘最大旋转角）、seatAdjustment（座椅前后）、seatHeight（座椅高度）、showWheel（显示方向盘）等。

### 3. 场景与画质

- **画质等级**：影响地形细节、远景距离、树木密度等。
- **天气与地形**：可切换不同天气、地形类型。
- **辅助功能**：ShowWorm（辅助线）、Barriers（障碍物）、AutoPause（自动暂停）等。

### 4. 音频设置

- **音量调节**、**静音**、**音效开关**。

---

## 主要函数（逻辑说明）

> 由于源码为压缩混淆版，以下为主要功能模块的逻辑说明：

- `l`、`p` 类：用于管理设置项（如键位、参数），支持本地存储和监听变化。
- 控制器相关：
  - `w`：输入监听与分发（键盘、鼠标、手柄）
  - `Y`：统一输入信号处理，负责将输入映射为游戏动作
- 车辆相关：
  - `be`：车辆物理与状态管理
  - `Ae`：当前车辆实例
- 地形与场景：
  - `oi`、`ci`：地形网格生成与管理
  - `wi`：地形高度图生成
- 配置与存档：
  - `te`、`We`：游戏设置与车辆设置的本地存储与恢复
- 其他：
  - `oe`：游戏主循环与状态管理
  - `xe`：音频管理

---

## 运行方法

1. 安装 Node.js（如未安装）
2. 全局安装 http-server：
   ```
   npm install -g http-server
   ```
3. 进入 slow-roads 目录，启动服务器：
   ```
   http-server -p 8080
   ```
4. 浏览器访问：
   ```
   http://localhost:8080
   ```
