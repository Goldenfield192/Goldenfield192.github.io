每个轨道的json名都不应相同，即使它们分属不同的资源包。

IR通过`assets/immersiverailroading/track`中的`track.json`文件识别轨道。
该文件格式如下：
```
{
	"pack": "String1",
	"types" : [
	"轨道json名1",
	"轨道json名2" //后续同理
  ]
}
```
IR而后会在同路径中寻找对应的json，在本案例中为`轨道json名1.json`等。
这个json内容如下：
```
{
    "name": "String1",
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

|       名称        |         类型          |                      	用途                       |
|:---------------:|:-------------------:|:----------------------------------------------:|
|      name       |       String        |                   游戏内显示的轨道名                    |
|     modeler     |       String        |                   游戏内显示的作者名                    |
|      pack       |       String        |      游戏内显示的资源包名。如未定义，则使用`track.json`中的内容       |
|     models      | 无序集合（String，String） | 当满足前一部分的条件时，<br/>显示后一部分指向的模型<br/>如有多行满足，显示最接近的 |
|  model_gauge_m  |        float        |                 模型在blender中的轨距                 |
| model_spacing_m |        float        |                    模型X轴方向长度                    |
|    materials    |                     |                     可直接复制                      |
|      clack      |       boolean       |                      WIP                       |
|    bumpiness    |        float        |                      WIP                       |
|       cog       |       boolean       |                      WIP                       |

所有可用的READOUT：

|         READOUT          |  用途  |
|:------------------------:|:----:|
| `RAIL_LEFT`和`RAIL_RIGHT` |  钢轨  |
|          `TIE`           |  轨枕  |
|          `BED`           |  路基  |
|       `RAIL_BASE`        | 其余全部 |


>一段轨道至少应该拥有`RAIL_BASE`、`RAIL_LEFT`和`RAIL_RIGHT`三种READOUT。