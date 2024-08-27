>~~WIP~~

对于一些复杂动画，直接用READOUT写未免过于令人头秃，而且有的还无法实现，比如一些多段动画。所幸Cam为我们提供了一条捷径：

## Animatrix(*.anim)

Cam在GitHub上发了个blender脚本，可以当插件装：[animatrix.py](https://github.com/TeamOpenIndustry/ImmersiveRailroading/blob/master/animatrix.py)

装了这个后你就可以导出一种扩展名为anim的文件，这里面存储着你在bld里做的动画。

这个动画没太大限制，可以用骨骼或者k帧，但不能用形态键。

然后
### 你需要在与`properties`并列的层级内添加它们：
```
{
    "animations":
        [
            {
                "control_group":"name",
                "animatrix": "RL",
                "mode": "LOOP",
                "offset": 0.0,
                "invert": false,
                "frames_per_tick": 3.0,
                "sound": "RL"
            }
        ]
}
```

有几个动画部件需要声明就在中括号里重复几次里面的大括号

|       字段名       |        类型        |                	含义                |
|:---------------:|:----------------:|:---------------------------------:|
|  control_group  |      String      |       对应的控制组名，如果你没用控制组就看下一行       |
|     readout     |      String      |        对应的READOUT名，与上一行二选一        |
|    animatrix    | ResourceLocation | 对应的动画文件位置。一个控制组，至少一个部件不应该有两个动画文件  |
|      mode       |      String      |              动画播放方式               |
|     offset      |      float       |           把动画变量加这个值后再执行           |
|     invert      |     boolean      |         反转，等效于`INVERT`修饰符         |
| frames_per_tick |      float       | 每游戏刻播放几帧动画，如果你做的是60fps的就填3.0，其他同理 |
|      sound      | ResourceLocation |     播放动画时播的声音，详细设置详见下一节最后一小节      |

所有有效Readout：

>[!TIP]
> 下文的“是否”控制的变量都是是为1否为0（类似C中布尔值表示方式）

|          字段名           |                              	解释                               |
|:----------------------:|:--------------------------------------------------------------:|
|         LIQUID         |                     若车辆可装载流体则为装载量百分比，否则为0                      |
|         SPEED          | 车辆当前速度与按轨距缩放的最大速度的比值（最大速度为机车时是json内数值/3.6，车辆为车厢时恒为200）（单位是m/s） |
|      TEMPERATURE       |              对于蒸汽机车返回当前温度/100，内燃机车为当前温度/150，否则为0               |
|    BOILER_PRESSURE     |            对于蒸汽机车为当前气缸压与按轨距缩放的json内`maxPSI`的比值，否则为0            |
|        THROTTLE        |                        对于机车为节流阀大小，否则为0                         |
|        REVERSER        |                对于机车为回转机状态（0倒车档，0.5默认，1前进档），否则为0                |
|      TRAIN_BRAKE       |                         对于机车为制动大小，否则为0                         |
|   TRAIN_BRAKE_LEVER    |                              WIP                               |
|   INDEPENDENT_BRAKE    |                            车辆独立制动大小                            |
|     BRAKE_PRESSURE     |                              WIP                               |
|     COUPLER_FRONT      |                            前车钩是否打开                             |
|      COUPLER_REAR      |                            后车钩是否打开                             |
|     COUPLED_FRONT      |                         前车钩是否已连接到其他车辆                          |
|      COUPLED_REAR      |                         后车钩是否已连接到其他车辆                          |
|  COUPLER_SLACK_FRONT   |                        前车钩滑动量与最大滑动量的比值                         |
|   COUPLER_SLACK_REAR   |                        后车钩滑动量与最大滑动量的比值                         |
|          BELL          |                            是否正在播放铃声                            |
|      HORN或WHISTLE      |                            是否正在播放笛声                            |
|         ENGINE         |                       对于内燃机车为是否已启动，否则为0                        |
|   FRONT_BOGEY_ANGLE    |                            WIP，待测试                             |
|    REAR_BOGEY_ANGLE    |                            WIP，待测试                             |
| FRONT_LOCOMOTIVE_ANGLE |                            WIP，待测试                             |
| REAR_LOCOMOTIVE_ANGLE  |                            WIP，待测试                             |
|     CYLINDER_DRAIN     |                        动画变量大于0.95时循环播放                         |
|       CARGO_FILL       |                     若车辆可装载货物则为装载量百分比，否则为0                      |
|       ENGINE_RPM       |             对于内燃机车则是车辆实际节流阀大小（GUI红线，与设置值有滞后性），否则为0             |

>[!WARNING]
> 这里的Readout仅可用于animatrix定义块内，不能用来设置为组件控制组。

所有可用于`mode`的动画播放方式：

|     字段名      |            	含义            |
|:------------:|:-------------------------:|
|    VALUE     | 直接由动画变量控制动画状态，动画变量即为动画百分比 |
| PLAY_FORWARD |      当动画变量大于0.75时正放       |
| PLAY_REVERSE |      当动画变量小于0.75时倒放       |
|  PLAY_BOTH   |          把前两个加起来          |
|     LOOP     |      动画变量大于0.95时循环播放      |
|  LOOP_SPEED  |      循环播放，但速度随动画变量变化      |


