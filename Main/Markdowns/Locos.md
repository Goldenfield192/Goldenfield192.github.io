# json
在前文通用模板的基础上，机车有特殊部分需额外定义。

!>缺省会导致无法加载

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

* 对于手摇车：

    ```json
    {
        "properties": {
		    "horsepower": 6290,
		    "tractive_effort_lbf": 135375,
	    	"max_speed_kmh": 130,
        }
    }
    ```

  |         名称          |   类型   |                   	含义                   |
  |:-------------------:|:------:|:---------------------------------------:|
  |     horsepower      |  int   |               机车牵引力，单位马力                |
  | tractive_effort_lbf |  int   | 机车牵引力，单位为磅</br>*4.44822后用作游戏内显示数值，单位为牛顿 |
  |    max_speed_kmh    | double |           机车自身能达到的最大时速，单位千米每时           |

* 对于柴油机车：
    
    ```json
    {
        "properties": {
            "fuel_efficiency_%": 90,
            "fuel_capacity_l": 852,
            "horsepower": 300,
            "tractive_effort_lbf": 21000,
            "max_speed_kmh": 120,
        }
    }
    ```
    
    |         名称          |   类型   |       	含义       |
    |:-------------------:|:------:|:---------------:|
    |  fuel_efficiency_%  |  int   | 燃料效率，与配置文件中的值乘算 |
    |   fuel_capacity_l   |  int   | 机车的燃料容量，单位升/毫桶  |
    |     horsepower      |  int   |      同手摇车       |
    | tractive_effort_lbf |  int   |      同手摇车       |
    |    max_speed_kmh    | double |      同手摇车       |
* 对于蒸汽机车：

    ```json
    {
        "properties": {
	    	"max_psi": 300,
	    	"water_capacity_l": 95000, 
		    "slots": 30,
		    "width": 15,
            "tender_auto_feed": true,
		    "horsepower": 6290,
		    "tractive_effort_lbf": 135375,
	    	"max_speed_kmh": 130,
        }
    }
    ```

  |         名称          |   类型    |         	含义         |
  |:-------------------:|:-------:|:-------------------:|
  |       max_psi       |   int   | 机车蒸汽室最大压强，单位磅每平方英寸  |
  |  water_capacity_l   |   int   |    机车的水容量，单位升/毫桶    |
  |        slots        |   int   |       机车燃料槽位数       |
  |        width        |   int   |     每行物品栏显示的槽位数     |
  |  tender_auto_feed   | boolean | 是否允许从相连的煤水车自动补充燃料和水 |
  |     horsepower      |   int   |        同手摇车         |
  | tractive_effort_lbf |   int   |        同手摇车         |
  |    max_speed_kmh    | double  |        同手摇车         |

# 模型

* 手摇车没有特殊的功能性READOUT。
* 对于内燃机车：

    |    READOUT名     |    用途    |
    |:---------------:|:--------:|
    | `EXHAUST_[num]` | 用于烟囱的发烟器 |

    此外都是装饰性READOUT，暂不展开。
* 对于蒸汽机车，详见下一章。
