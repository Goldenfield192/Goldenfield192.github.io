不局限于蒸汽机车，IR中所有车辆均可拥有自动生成的连杆动画，你只需要写好对应的READOUT。

如果想为你的车辆添加连杆，
### 你需要在车辆json中的`properties`中添加它们：
```json
{
  "properties": {
    "valve_gear": "WALSCHAERTS"
  }
}
```

|       关键字种类        |           含义           |
|:------------------:|:----------------------:|
|    WALSCHAERTS     |     最常使用的一种连杆动画预设      |
| MALLET_WALSCHAERTS | 用于big boy等多连杆车辆的连杆动画预设 |
|     STEPHENSON     |          WIP           |
|     CONNECTING     |          WIP           |

## WALSCHAERTS

这个预设有如下READOUT定义：

|          READOUT名          |  用途   |
|:--------------------------:|:-----:|
|    `WHEEL_DRIVER_[num]`    | 车辆主动轮 |
|       `STEAM_CHEST`        |  蒸汽箱  |
|     `MAIN_ROD_[side]`      |  主杆   |
|     `SIDE_ROD_[side]`      |  侧杆   |
|    `PISTON_ROD_[side]`     |  活塞杆  |
|    `UNION_LINK_[side]`     | 结合连接器 |
| `COMBINATION_LEVER_[side]` | 组合杠杆  |
|  `ECCENTRIC_CRANK_[side]`  | 偏心曲柄  |
|   `ECCENTRIC_ROD_[side]`   |  偏心杆  |
|  `EXPANSION_LINK_[side]`   | 扩展连接器 |
|    `RADIUS_BAR_[side]`     |  活塞杆  |

只需要把车辆对应连杆部分按以上READOOUT命名即可。

*演示图制作中


## MALLET_WALSCHAERTS

用于[铰接车架式蒸汽机车](Main/Markdowns/CarsAdvanced.md)的连杆动画。

主车架部分与`WALSCHAERTS`相同，但对于前车架，READOUT较于主车架有所不同：

|        主车架READOUT名         |           前车架READOUT名            |
|:--------------------------:|:--------------------------------:|
|          `FRAME`           |          `FRONT_FRAME`           |
|          `SHEEL`           |          `FRONT_SHEEL`           |
|    `WHEEL_DRIVER_[num]`    |    `WHEEL_DRIVER_FRONT_[num]`    |
|       `STEAM_CHEST`        |       `STEAM_CHEST_FRONT`        |
|     `MAIN_ROD_[side]`      |     `MAIN_ROD_[side]_FRONT`      |
|     `SIDE_ROD_[side]`      |     `SIDE_ROD_[side]_FRONT`      |
|    `PISTON_ROD_[side]`     |    `PISTON_ROD_[side]_FRONT`     |
|    `UNION_LINK_[side]`     |    `UNION_LINK_[side]_FRONT`     |
| `COMBINATION_LEVER_[side]` | `COMBINATION_LEVER_[side]_FRONT` |
|  `ECCENTRIC_CRANK_[side]`  |  `ECCENTRIC_CRANK_[side]_FRONT`  |
|   `ECCENTRIC_ROD_[side]`   |   `ECCENTRIC_ROD_[side]_FRONT`   |
|  `EXPANSION_LINK_[side]`   |  `EXPANSION_LINK_[side]_FRONT`   |
|    `RADIUS_BAR_[side]`     |    `RADIUS_BAR_[side]_FRONT`     |

## STEPHENSON

>WIP

## Animatrix

你可以使用[Animatrix](Animatrix.md)功能自定义连杆动画：
```json
{
  "properties": {
    "valve_gear": {
      "-1.0": "ResourceLocation",//车辆后退时播放
      "0.0": "ResourceLocation",//车辆静止时播放
      "1.0": "ResourceLocation"//车辆前进时播放
      //你可以添加0.75、0.5、0.25等细分动画让整体动画更流畅。
    }
  }
}
```
