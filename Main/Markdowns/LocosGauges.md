## 仪表

你可以通过一些READOUT来让控件使用来自车辆数据的动画变量，成为它们的仪表。

>[!TIP]
>这里大部分只是对其添加了`GAUGE_`的Readout。对于其详细定义，参见[Animatrix一节](Animatrix.md)。

|             READOUT             |          用途           |
|:-------------------------------:|:---------------------:|
|      `GAUGE_LIQUID_[num]`       |      监测`LIQUID`       |
|       `GAUGE_SPEED_[num]`       |       监测`SPEED`       |
|    `GAUGE_TEMPERATURE_[num]`    |    监测`TEMPERATURE`    |
|  `GAUGE_BOILER_PRESSURE_[num]`  |  监测`BOILER_PRESSURE`  |
|     `GAUGE_THROTTLE_[num]`      |     监测`THROTTLE`      |
|     `GAUGE_REVERSER_[num]`      |     监测`REVERSER`      |
|    `GAUGE_TRAIN_BRAKE_[num]`    |    监测`TRAIN_BRAKE`    |
| `GAUGE_INDEPENDENT_BRAKE_[num]` | 监测`INDEPENDENT_BRAKE` |
|     `BRAKE_PRESSURE_[num]`      |  监测`BRAKE_PRESSURE`   |


此处[num]仅作动画组件的区分之用，即`GAUGE_THROTTLE_1`和`GAUGE_THROTTLE_2`均监测控制组`THROTTLE`。