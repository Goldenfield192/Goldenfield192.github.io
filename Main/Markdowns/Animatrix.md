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
|     readout     |      String      |    对应的READOUT名。建议使用控制组，与上一行二选一    |
|    animatrix    | ResourceLocation | 对应的动画文件位置。一个控制组，至少一个部件不应该有两个动画文件  |
|      mode       |      String      |              动画播放方式               |
|     offset      |      float       |           把动画变量加这个值后再执行           |
|     invert      |     boolean      |         反转，等效于`INVERT`修饰符         |
| frames_per_tick |      float       | 每游戏刻播放几帧动画，如果你做的是60fps的就填3.0，其他同理 |
|      sound      | ResourceLocation |     播放动画时播的声音，详细设置详见下一节最后一小节      |

所有可用于`mode`的动画播放方式：

|     字段名      |            	含义            |
|:------------:|:-------------------------:|
|    VALUE     | 直接由动画变量控制动画状态，动画变量即为动画百分比 |
| PLAY_FORWARD |      当动画变量大于0.75时正放       |
| PLAY_REVERSE |      当动画变量小于0.75时倒放       |
|  PLAY_BOTH   |          把前两个加起来          |
|     LOOP     |      动画变量大于0.95时循环播放      |
|  LOOP_SPEED  |      循环播放，但速度随动画变量变化      |


