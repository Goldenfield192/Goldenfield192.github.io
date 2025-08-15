# JSON
在前文通用模板的基础上，机车有特殊部分需额外定义。

!>缺省“需要的”的部分会导致无法加载

### 你需要在与`properties`并列的层级内添加它们：



```json
{
  "era": "diesel",
  "works": "CR"
}
```

|  名称   |   类型   |                	含义                 |
|:-----:|:------:|:----------------------------------:|
|  era  | String | 决定车辆为柴油机车(`diesel`)还是蒸汽机车(`steam`) |
| works | String |       游戏内显示的服务公司，如缺省则显示为N/A        |



### 你需要在`properties`中添加它们：
```json
{
    "properties": {
        "cab_car": false,
	    "horsepower": 6290,
	    "tractive_effort_lbf": 135375,
		"max_speed_kmh": 130,
        "toggle_bell": true,
        "cog": false,
        "multi_unit_capable":false,
    }
}
```

|         名称          |   类型    |                    	含义                    |
|:-------------------:|:-------:|:-----------------------------------------:|
|       cab_car       | boolean |     若为`true`，则代表车辆不提供动力，与动力有关的值均强制归零      |
|     horsepower      |   int   |                 机车功率，单位马力                 |
| tractive_effort_lbf |   int   |  机车牵引力，单位为磅</br>*4.44822后用作游戏内显示数值，单位为牛顿  |
|    max_speed_kmh    | double  |            机车自身能达到的最大时速，单位千米每时            |
|     toggle_bell     | boolean |        铃声为切换开/关(true)还是长按播放(false)        |
|         cog         | boolean |     若为`true`，则在`cog=true`的轨道上拥有无限牵引力      |
| multi_unit_capable  | boolean | 是否允许机车重联运行（在同列车内机车间同步设置节流阀、回转机、风压刹车与独立刹车） |
  * 对于柴油机车，你需要额外在对应块内添加：
    
      ```json
      {
          "properties": {
              "fuel_efficiency_%": 90,
              "fuel_capacity_l": 852,
              "horn_sustained": false,
    
            "throttle_notches": 8,
            "dynamic_traction_control": true
          }
      }
      ```
    
      |            名称            |   类型    |            	含义             |
      |:------------------------:|:-------:|:--------------------------:|
      |    fuel_efficiency_%     |   int   | 燃料效率，与配置文件中的值乘算（值域[1,99]）  |
      |     fuel_capacity_l      |   int   |       机车的燃料容量，单位升/毫桶       |
      |      horn_sustained      | boolean |  鸣笛时笛声是否循环播放（false则仅播放一次）  |
    |     throttle_notches     |   int   |     内燃机车挡位数，默认为8（尚不完善）     |
    | dynamic_traction_control | boolean |     车载电脑可否动态调控牵引力以防打滑      |

* 对于蒸汽机车，你需要额外在对应块内添加：

    ```json
    {
        "properties": {
	    	"max_psi": 300,
	    	"water_capacity_l": 95000, 
            "tender_auto_feed": true
        },
        "firebox": {
		    "slots": 30,
		    "width": 15
        } 
    }
    ```

  |         名称         |   类型    |         	含义         |
  |:------------------:|:-------:|:-------------------:|
  |      max_psi       |   int   | 机车蒸汽室最大压强，单位磅每平方英寸  |
  |  water_capacity_l  |   int   |    机车的水容量，单位升或毫桶    |
  |  tender_auto_feed  | boolean | 是否允许从相连的煤水车自动补充燃料和水 |
  |       slots        |   int   |       机车燃料槽位数       |
  |       width        |   int   |     每行物品栏显示的槽位数     |
* 对于手摇车，没有需额外添加的json，**但是你需要删去`era`语句。** 

>[!TIP]
> 如果进入对话框等鼠标可自由移动的情景，IR的控制台可以用鼠标交互！参见[自定义GUI](Main/Markdowns/CustomGUI.md)

# 模型

* 对于内燃机车：

    |    READOUT名     |     用途      |
    |:---------------:|:-----------:|
    |   `FUEL_TANK`   |  燃料箱，装饰性组件  |
    |  `ALTERNATOR`   |  发电机，装饰性组件  |
    | `ENGINE_BLOCK`  | 发动机座，装饰性组件  |
    |   `PISTON_X`    | 发电机活塞，装饰性组件 |
    | `EXHAUST_[num]` |  用于烟囱的发烟器   |

* 对于蒸汽机车：

    |         READOUT名         |     用途     |
    |:------------------------:|:----------:|
    |  `BOILER_SEGMENT_[num]`  | 锅炉部分，装饰性组件 |
    |        `FIREBOX`         | 燃烧室，装饰性组件  |
    |        `SMOKEBOX`        |  烟箱，装饰性组件  |
    |          `CAB`           | 司机室，装饰性组件  |
    |         `PIPING`         |  管道，装饰性组件  |
    | `PARTICLE_CHIMNEY_[num]` |  用于烟囱的发烟器  |
  |        `WHISTLE`         | 汽笛。鸣笛时会发烟  |

  * 对于连杆，详见下一章。

* 手摇车没有特殊的READOUT。