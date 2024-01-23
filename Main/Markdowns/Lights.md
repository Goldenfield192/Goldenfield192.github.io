IR直接通过READOUT来添加灯光。

## 头灯

你可以为对象添加`HEADLIGHT_[pos]_[num]`来标记这是一盏头灯。

可以在`HEADLIGHT_[pos]_[num]`后添加形如`_0xFFFFFF`的十六进制颜色来定义灯光颜色。

这里的`[pos]`用来声明头灯位置，最常见的是FRONT_LOCOMOTIVE，前车架。这个`[pos]`可缺省。

在对应车辆的json中可以对头灯进行自定义，

### 你需要在与`properties`并列的层级内添加它们（可选）：

```json
{
  "lights": {
    "HEADLIGHT_FRONT_LOCOMOTIVE_1": {
      "texture": "RL",
      "castsLight": false,
      "reverseColor": "0xFFFFFF",
      "blinkIntervalSeconds": 10,
      "blinkoffsetSeconds": 10,
      "blinkFullBright": false
    },
    "HEADLIGHT_2": {
      ...
    }
  }
}
```

你需要在`lights`中添加对应的READOUT名(`HEADLIGHT_[num]`)，而后在其中添加自定义内容。


|          名称          |        类型        |            	含义            |
|:--------------------:|:----------------:|:-------------------------:|
|       texture        | ResourceLocation |   IR使用的灯光贴图，缺省则使用默认贴图。    |
|      castsLight      |     boolean      | 是否牺牲部分质量来优化性能表现，默认为`true` |
|     reverseColor     |      十六进制颜色      |         车辆倒行时显示颜色         |
| blinkIntervalSeconds |      float       |            WIP            |
|  blinkoffsetSeconds  |      float       |            WIP            |
|   blinkFullBright    |     boolean      |            WIP            |

>[!NOTE]
>IR头灯的工作原理是在对象前方渲染一个对应大小和颜色的、自发光的灯光贴图

![就像这样](../Textures/pic11.png ':size=50%')

## 普通灯光

可用的READOUT：

|   READOUT名   |        用途         |
|:------------:|:-----------------:|
| `FULLBRIGHT` |   标记该部件在被充能时应发光   |
|  `INTERIOR`  | 标记该部件在被充能时的夜晚时应发光 |

机车启动时/车厢连接到启动的机车时称作被充能。

如果添加了`INTERIOR`，那么
### 你需要在`properties`中添加它们：

```json
{
      "properties": {
          "interiorLightLevel": 1.0
      }
}
```
|         名称         |  类型   |         	含义          |
|:------------------:|:-----:|:--------------------:|
| interiorLightLevel | float | 车内灯光亮度，取值范围[0.0,1.0] |

尽管这没什么影响，看亮度还得`FULLBRIGHT`，所以`INTERIOR`只适用于大面积车内光照。

>[!NOTE]
>你可以将一个部件分为多个对象并向其中一些添加`FULLBRIGHT`或`INTERNAL`来使一个部件拥有多种效果
> 
> 比如向一扇车门的内侧部分添加`INTERIOR`而外侧不添加来实现车内照明
> 
> 光照修饰符只会作用于对应物体，而非整个READOUT。