# json

IR通过`assets/immersiverailroading/rolling_stock`中的`stock.json`文件识别车辆。该文件格式如下：
```json
{
    "freight": ["aa"],
    "locomotives": [],
    "passenger": [],
    "tank": [],
    "tender": [],
    "hand_car": []
}
```
|     名称      |  含义  |
|:-----------:|:----:|
|   freight   |  货车  |
| locomotives |  机车  |
|  passenger  |  客车  |
|    tank     | 流体罐车 |
|   tender    | 煤水车  |
|  hand_car   | 手摇车  |

在示例中则定义了一个json名为`aa`的货车，定义更多车辆即为在对应位置继续添加字符串。

而后IR会在`assets/immersiverailroading/rolling_stock`中对应位置寻找json文件。

```
└─assets
    └─immersiverailroading
        ├─...
        └─rolling_stock
            ├─...
            ├─freight //在此文件夹内添加货车json
            ├─locomotives //在此文件夹内添加机车json
            ├─passenger //在此文件夹内添加客车json
            ├─tank //在此文件夹内添加流体罐车json
            ├─tender //在此文件夹内添加煤水车json
            ├─hand_car //在此文件夹内添加手摇车json
            └─stock.json
```

本案例中为`assets/immersiverailroading/rolling_stock/freight/aa.json`。

对于客车、货车、流体罐车，其文件格式如下：
```json
{
	"name": "CarDemo1",
	"model": "Loc",
	"properties": {
		"weight_kg": 10000
	},
	"passenger": {
		"slots": 10,
		"center_x": 0,
		"center_y": 1.4,
		"length": 4.5,
		"width": 2
	},
	"freight": {
		"slots": 30,
		"width": 15
	},
    "tank": {
      "capacity_l": 20000
    },
	"pivot": {
		"front": 3.8, 
		"rear": -3.8
	},
	"couplers": {
		"front_offset": -0.08,
		"rear_offset": -0.08
	}
}

```

对于煤水车，`freight`应修改为`tender`，其余用法一致。

|     名称     |        类型        |          	含义          |
|:----------:|:----------------:|:---------------------:|
|    name    |      String      |       游戏内显示的车辆名       |
|  modeler   |      String      | 游戏内显示的作者名，如缺省则显示为N/A  |
|    pack    |      String      | 游戏内显示的资源包名，如缺省则显示为N/A |
|   model    | ResourceLocation |         模型位置          |

### properties
|    名称     |        类型        |          	含义          |
|:---------:|:----------------:|:---------------------:|
| weight_kg |       int        |    游戏内显示的车辆质量，单位kg    |

### passenger
|    名称    |   类型   |         	含义         |
|:--------:|:------:|:-------------------:|
|  slots   |  int   |     车厢最多可容纳的乘客数     |
| center_x | double |      行走范围的纵向中心      |
| center_y | double | 玩家模型底部的高度 **+0.35** |
|  length  | double |       行走范围的长度       |
|  width   | double |       行走范围的宽度       |

* 比如，对于
```json
  "center_x": 2,
  "center_y": 0.35,
  "length": 2,
  "width": 2
  ```
，则玩家的行动范围如下图所示

![awa](../Textures/pic8.png ':size=50%')
![awa](../Textures/pic9.png ':size=50%')


### freight/tender（仅货车、煤水车需要，客车可选）
|  名称   | 类型  |     	含义     |
|:-----:|:---:|:-----------:|
| slots | int | 车辆的物品容量，单位组 |
| width | int | 每行物品栏显示的组数  |

>slots建议为width的整数倍
### tank（仅流体罐车、煤水车需要）
|     名称     | 类型  |      	含义       |
|:----------:|:---:|:--------------:|
| capacity_l | int | 车辆的流体容量，单位升/毫桶 |

### pivot（旧为trucks）
|  名称   |  类型   |      	含义       |
|:-----:|:-----:|:--------------:|
| front | float | 前转向架旋转轴X坐标，单位m |
| rear  | float | 后转向架旋转轴X坐标，单位m |

* 转向架旋转中心Y坐标应为0

### couplers
|      名称      |  类型   |  	含义  |
|:------------:|:-----:|:-----:|
| front_offset | float | 前车钩偏移 |
| rear_offset  | float | 后车钩偏移 |

* 此处负值为向内偏移，正值为向外偏移。
* 对于绝大部分车辆，此处均为负值。准确值需自行尝试。

# 模型

可用的READOUT：

|          READOUT          |        用途        |
|:-------------------------:|:----------------:|
|          `FRAME`          |   车架，承载其他一切组件    |
|          `SHELL`          |     车壳，装饰性组件     |
|    `FRAME_WHEEL_[num]`    |    车架轮，随车架运动     |
|       `BOGEY_[pos]`       |      前/后转向架      |
| `BOGEY_[pos]_WHEEL_[num]` | 前/后转向架轮，随对应转向架运动 |
