## 仪表

你可以通过一些READOUT来让控件使用来自车辆数据的动画变量，成为它们的仪表。

|             READOUT             |     用途      |
|:-------------------------------:|:-----------:|
|      `GAUGE_LIQUID_[num]`       |  监测车辆液体容量   |
|       `GAUGE_SPEED_[num]`       |    监测车速     |
|    `GAUGE_TEMPERATURE_[num]`    | 监测内燃机车发动机温度 |
|  `GAUGE_BOILER_PRESSURE_[num]`  | 监测蒸汽机车蒸汽室温度 |
|     `GAUGE_THROTTLE_[num]`      |   监测节流阀大小   |
|     `GAUGE_REVERSER_[num]`      |   监测回转机状态   |
|    `GAUGE_TRAIN_BRAKE_[num]`    |   监测刹车状态    |
| `GAUGE_INDEPENDENT_BRAKE_[num]` |  监测独立刹车状态   |
|     `BRAKE_PRESSURE_[num]`      |    监测风压     |

此处[num]仅作动画组件的区分之用，即`GAUGE_THROTTLE_1`和`GAUGE_THROTTLE_2`均监测控制组`THROTTLE`。

这些值会在归一化后用作对应组件的动画变量。