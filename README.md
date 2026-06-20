整合完整说明（包含陀螺仪说明 + 后期轻量化AI补充方案，中英双语）
 
中文完整版介绍
 
项目概述
 
本项目仅为我个人针对驾驶辅助系统的原创构想，核心目标是把车载感知与控制的硬件、算力成本压缩到极致。我将全套几何测距、多传感器冗余思路整理后交由AI推演评估，AI判定整套纯几何架构理论可行。
 
整套方案核心硬件为普通USB摄像头、低成本MPU6050六轴陀螺仪、入门老旧手机ARM开发板，全套硬件总成本可控制在300元以内；依靠陀螺仪实时采集车身俯仰/侧倾角度，动态修正上下坡、加减速点头、路面颠簸带来的测距角度误差，再搭配国标道路标线自动校准、双目视差三重冗余测距，大幅降低远距离2~5米的原生测量误差。
 
系统全程不依赖大算力车载芯片、激光雷达、高价毫米波雷达，依靠小孔成像、解析几何、互补滤波、PID闭环控制实现FCW前碰撞预警、LDW车道偏离、LKA车道保持、简易ACC跟车、窄路会车提醒、弯道限速等基础主动安全功能，适配高速、国道、铺装乡村这类结构化道路。
 
现存短板与分阶段优化路线
 
1. 纯几何方案只能算出障碍物距离、运动速度，无法区分行人、货车、锥桶、路面杂物，容易对塑料袋、石块做出误判；无标线夜间场景识别稳定性大幅下降。
2. 针对该缺陷，后续可分阶段迭代，引入极小体量轻量化目标检测AI模型（仅区分5类基础目标：轿车、货车、行人、非机动车、交通锥，模型仅数MB，低端ARM板无压力运行）；
3. 架构分工清晰：几何算法负责计算距离、轨迹、车辆控制，微型AI只负责物体分类，二者结合，不用大模型就能补齐识别短板，依旧维持低成本定位。
 
项目定位与重要声明
 
1. 项目定名：Open Geometry Drive
副标题：开源纯几何低成本ADAS主动安全系统，不宣传全自动驾驶，仅限定L2级结构化道路辅助；
2. 仅用于个人开源学习分享，无车规认证；如果需要商用落地，所有实地路测、安全校验、合规手续全部需要使用者自行完成；
3 大雾、暴雨、无照明黑夜、城市复杂非机动车路段系统感知能力大幅衰减，驾驶员必须全程手握方向盘，不能脱离人工监控。
 
English Full Introduction
 
Project Overview
 
This project is only my personal original idea for driver assistance systems. My core goal is to minimize the hardware and computing cost of vehicle perception and control to the extreme. I sorted out the complete ideas of geometric ranging and multi-sensor redundancy and submitted them for AI evaluation. The AI concluded that this pure geometric architecture is theoretically feasible.
 
The core hardware of this solution includes ordinary USB cameras, low-cost MPU6050 6-axis gyroscopes, and entry-level outdated mobile ARM boards. The total hardware cost can be controlled within 300 RMB. The gyroscope collects real-time vehicle pitch and roll angles to dynamically correct ranging angle errors caused by uphill/downhill, vehicle pitching during acceleration and braking, and road bumps. Combined with national standard road marking calibration and binocular disparity ranging, three redundant ranging modes are formed to greatly reduce the inherent measurement error of 2~5 meters at long distances.
 
The system does not rely on high-computing vehicle chips, LiDAR or expensive millimeter-wave radars. Based on pinhole imaging, analytic geometry, complementary filtering and PID closed-loop control, it realizes basic active safety functions including FCW forward collision warning, LDW lane departure warning, LKA lane keeping, simple ACC car following, narrow-road passing reminder and curve speed limit. It is suitable for structured roads such as highways, national highways and paved rural roads.
 
Existing Defects & Phased Optimization Roadmap
 
1. The pure geometric scheme can only calculate the distance and moving speed of obstacles, but cannot distinguish pedestrians, trucks, traffic cones and road debris. It is easy to produce misjudgment on plastic bags and stones, and the recognition stability drops sharply at night without lane lines.
2. To solve this problem, we can iterate in phases and introduce an extremely lightweight tiny object detection AI model later. It only classifies 5 basic targets (cars, trucks, pedestrians, two-wheelers, traffic cones) with a file size of only several MB, which can run smoothly on low-end ARM boards.
3. Clear architecture division: geometric algorithms calculate distance, trajectory and vehicle control, while the tiny AI is only responsible for object classification. The combination of the two can make up for the identification shortcomings without large models, and still maintain the ultra-low-cost positioning.
 
Project Position & Important Disclaimer
 
1. Project Name: Open Geometry Drive
Subtitle: Open-source Low-cost Geometry-based ADAS Active Safety System. It does not claim fully autonomous driving, and is limited to L2-level assistance on structured roads.
2. It is only for personal open-source learning and sharing, without automotive standard certification. If users intend to apply it for commercial use, all field road tests, safety verification and compliance procedures shall be completed independently.
3. The perception performance of the system will decrease significantly in heavy fog, heavy rain, unlit nights and complex urban roads with numerous non-motor vehicles. Drivers must hold the steering wheel and keep human supervision all the time.
