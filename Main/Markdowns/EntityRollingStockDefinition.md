>本节将讲解对于所有车辆均通用的部分。对于每种车辆的具体制作方法，参见后两节。
# JSON

IR通过`assets/immersiverailroading/rolling_stock`中的`stock.json`文件识别车辆。该文件格式如下：
```json
{
    //货车注册
    "freight": ["aa"],
    //机车注册
    "locomotives": [],
    //客车注册
    "passenger": [],
    //流体货车注册
    "tank": [],
    //煤水车注册
    "tender": [],
    //手摇车注册
    "hand_car": []
}
```
在示例中，我们定义了一个json名为`aa`的货车。定义更多车辆即为在对应类别处继续添加字符串。

而后IR会在`assets/immersiverailroading/rolling_stock`中寻找对应类别和文件名的json文件。

``` 文件结构示意
└─assets
    └─immersiverailroading
        ├─...
        └─rolling_stock
            ├─...
            ├─freight //在此文件夹内添加货车json
            |   └─aa.json
            ├─locomotives //在此文件夹内添加机车json
            ├─passenger //在此文件夹内添加客车json
            ├─tank //在此文件夹内添加流体罐车json
            ├─tender //在此文件夹内添加煤水车json
            ├─hand_car //在此文件夹内添加手摇车json
            └─stock.json
```

在示例中，IR会在`assets/immersiverailroading/rolling_stock/freight`中寻找`aa.json`。

关于车辆json，[这是](https://github.com/TeamOpenIndustry/ImmersiveRailroading/blob/master/src/main/resources/assets/immersiverailroading/rolling_stock/default/base.caml)官方模板，我对此的解释如下。

```json
{
	"name": "Demo1",
    "modeler": "String2",
    "pack": "String3",
  
	"model": "Loc",
    "model_gauge_m": 1.435,
    "recommended_gauge_m": 1.435,
    "darken_model": 0.05,
    "show_current_load_only": false,

    "sound_dampening_percentage": 0.75,
    "scale_pitch": true,
  
    "tex_variants": {
        "alpha": "alala"
    },
    "particles":{
        "smoke":{
           "texture": "immersiverailroading:your/particle.png"
        },
        "steam":{
            "texture": "immersiverailroading:your/particle.png"
        }
    },
	"properties": {
		"weight_kg": 10000,
        "independent_brake": false,
        "pressure_brake": false,
        "swayMultiplier": 1,
        "tiltMultiplier": 1
	},


    "passenger": {
	  	  "slots": 10,
	  	  "center_x": 0,
		  "center_y": 1.4,
		  "length": 4.5,
		  "width": 2
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
## 对json字段的解释

|              字段名              |        类型        |          	含义          |
|:-----------------------------:|:----------------:|:---------------------:|
|             name              |      String      |    游戏内显示的车辆名，不可缺省     |
|            modeler            |      String      | 游戏内显示的作者名，如缺省则显示为N/A  |
|             pack              |      String      | 游戏内显示的资源包名，如缺省则显示为N/A |
|             model             | ResourceLocation |         模型位置          |
|         model_gauge_m         |      double      |  模型在blender中的轨距，单位米   |
|      recommended_gauge_m      |      double      |   模型在游戏中显示的推荐轨距，单位米   |
|         darken_model          |      double      |  模型渲染时颜色加深系数。**已过时**  |
|    show_current_load_only     |     boolean      |          WIP          |
|  sound_dampening_percentage   | float（百分数的小数形式）  | 当玩家在车内时，听到的声音的音量减少多少？ |
|          scale_pitch          |     boolean      |    根据轨距设置音量倍率（待测试）    |

![关于darken_model](../Textures/pic10.png ':size=50%')

从左至右`darken_model`值依次为0.1、0.075、0.05、0.025、0。

>[!WARNING]
> 如果`model_gauge_m`与`properties`中填入数值对应的轨距不一致，则会导致数值出错。

### tex_variants
见[下文](Main/Markdowns/CarsAdvanced?id=涂装变体)。

### particles
定义用于粒子的贴图，`steam`内的贴图用于蒸汽机车，`smoke`内的用于内燃机车。

`smoke`内的贴图在内燃机车启动后明度会自动降低，以模拟真实机车启动的黑烟。
>[!NOTE]
> 其实IR默认粒子贴图和默认灯光贴图是同一张。


### properties
|        字段名        |   类型    |                	含义                 |
|:-----------------:|:-------:|:----------------------------------:|
|     weight_kg     |   int   |          游戏内显示的车辆质量，单位千克           |
| independent_brake | boolean |     车辆是否拥有独立制动，对于车厢来讲通常为`true`     |
|  pressure_brake   | boolean |   车辆是否拥有风压制动器，对于手摇车外的车辆通常为`true`   |
|  swayMultiplier   | double  | 车辆在`clack=true`的轨道上行驶和通过轨道接缝时的摆动系数 |
|  tiltMultiplier   | double  |         车辆过弯时的倾斜系数，模拟外轨超高          |


### passenger
|    字段名     |   类型    |                 	含义                 |
|:----------:|:-------:|:-----------------------------------:|
|   slots    |   int   |         车厢最多可容纳的实体数(玩家和村民)          |
|  center_x  | double  |            行走范围的纵向中心，单位米            |
|  center_y  | double  |      玩家模型底部的高度 **+0.35** ，单位米       |
|   length   | double  |            行走范围的长度/2，单位米            |
|   width    | double  |             行走范围的宽度，单位米             |
| should_sit | boolean | 玩家在车上时显示为站姿还是坐姿，默认则依轨距而定(轨距<1m时为坐姿) |

* 比如，对于
```json
{
   "passenger": {
      ...,
      "center_x": 2,
      "center_y": 0.35,
      "length": 1,
      "width": 2
   }
}
```
，则玩家在blender的可行动范围如下图所示

![awa](../Textures/pic8.png ':size=50%')
![awa](../Textures/pic9.png ':size=50%')

或许0.35并非常量而是轨面高度？

### pivot（旧为trucks）
|  字段名  |  类型   |          	含义           |
|:-----:|:-----:|:----------------------:|
| front | float | 前转向架旋转轴X坐标**的相反数**，单位米 |
| rear  | float | 后转向架旋转轴X坐标**的相反数**，单位米 |

* 转向架旋转中心Y坐标应为0
* 如果你的车没有转向架，不妨设置为前/后轮对坐标

### couplers
|     字段名      |  类型   |    	含义    |
|:------------:|:-----:|:---------:|
| front_offset | float |   前车钩偏移   |
| rear_offset  | float |   后车钩偏移   |
| front_slack  | float | 前车钩允许的滑动量 |
|  rear_slack  | float | 后车钩允许的滑动量 |

* RTM车辆连接时车辆长度根据trainDistance这个从车厢原点的绝对值算，IR不是。 IR根据从最靠前和最靠后的顶点算相对值，正数就是向外偏移，负数向内。
* ·对于滑动量，cam在Youtube上的[这个](https://www.youtube.com/watch?v=O-boGSqi_8c)视频能很好地说明。
* 两节车相连地方的车钩偏移和滑动量由相连车厢的相应值相加得到。就是说，首尾相连的两节车的偏移分别为0.5和一节1一节0等效。


# 模型

对所有车辆均可用的READOUT：

|         READOUT名          |        用途         |
|:-------------------------:|:-----------------:|
|          `FRAME`          |    车架，承载其他一切组件    |
|          `SHELL`          |     车壳，装饰性组件      |
|    `FRAME_WHEEL_[num]`    |     车架轮，随车架运动     |
|       `BOGEY_[pos]`       |      前/后转向架       |
| `BOGEY_[pos]_WHEEL_[num]` | 前/后转向架轮对，随对应转向架运动 |
>这意味着你最多可以使用两个转向架，但每个转向架的轮数没有限制