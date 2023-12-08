!>每个轨道的json名都不应相同，即使它们分属不同的资源包。尽管这样可以加载，但会导致不可预见的情况发生。
</br>**你已经被警告过了。**

IR通过`assets/immersiverailroading/track`中的`track.json`文件识别轨道。
该文件格式如下：
```
{
	"pack": "String3",
	"types" : [
	"name1",
	"name2"... //后续同理
  ]
}
```
IR而后会在`assets/immersiverailroading/track`中寻找对应的json，在本案例中为`name1.json`、`name2.json`等。

这些json内容应该像这样：
```
{
    "name": "TrackDemo",
    "modeler": "String2",
    "pack": "String3",
    "models": {
        ">1": "immersiverailroading:models/abcd.obj",
        ">0": "immersiverailroading:models/abc.obj"
    },
    "model_gauge_m": double,
    "model_spacing_m": double,
    "clack": bollean,
    "bumpiness"; float,
    "cog": boolean,
    "materials": {
      "TIE": [
          {
              "item": "ore:ingotIron",
              "cost": 1
          },
          {
              "item": "ore:stone",
              "cost": 2
          }
      ],
      "RAIL": [
          {
              "item": "ore:ingotIron",
              "cost": 1
          }
        ]
    }
}
```

|   名称    |   类型   |                   	用途                   |
|:-------:|:------:|:---------------------------------------:|
|  name   | String | 游戏内显示的轨道名，**缺省会导致NullPointerException** |
| modeler | String |            游戏内显示的作者名，如缺省则不显示            |
|  pack   | String |           游戏内显示的资源包名，如缺省则不显示            |

![awa](../Textures/pic5.png "对于案例来说是这样")

|       名称        |              类型               |                         	用途                         |
|:---------------:|:-----------------------------:|:---------------------------------------------------:|
|     models      | 无序集合（String，ResourceLocation） | 当轨距满足前一部分表达式的条件时，<br/>渲染后一部分指向的模型<br/>如有多个满足，渲染最接近的 |
|  model_gauge_m  |             float             |                 模型在blender中的轨距，单位m                  |
| model_spacing_m |             float             |                   模型在X轴方向上的长度，单位m                   |
|    materials    |              不明               |               轨道在生存模式下的配方。此部分建议直接复制上文               |
|      clack      |            boolean            |                     推测与音效有关，WIP                     |
|    bumpiness    |             float             |                     推测与音效有关，WIP                     |
|       cog       |            boolean            |                     推测与音效有关，WIP                     |

所有可用的READOUT：

|         READOUT          |    用途     |
|:------------------------:|:---------:|
| `RAIL_LEFT`和`RAIL_RIGHT` |  左、右侧钢轨   |
|          `TIE`           |   推测为轨枕   |
|          `BED`           |   推测为路基   |
|       `RAIL_BASE`        | 除以上部分外的全部 |


>一段轨道至少应该拥有`RAIL_BASE`、`RAIL_LEFT`和`RAIL_RIGHT`三种READOUT。