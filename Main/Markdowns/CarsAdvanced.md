## 涂装变体
我们假定你要为RL为`immersiverailroading:models/rolling_stock/passenger/demo/demo.obj`的客车添加涂装变体。

这是它的文件结构示意图：
``` 文件结构示意
└─assets
    └─...
       └─demo
           ├─tex1.png
           ├─tex2.png
           ├─tex3.png
           ├─tex4.png
           ├─demo.obj
           └─demo.mtl
```

### 你需要在车辆json中与`properties`并列的层级内添加它们：
```json
{
	"tex_variants": {
		"Test1": "test1",
        "Test2": "test2",
	},
}
```
定义更多涂装变体即为继续添加键值对。

|  |       键       |           值           |
|----|:-------------:|:---------------------:|
|  含义  | 对应变体在游戏内显示的名称 | 变体用于替换的贴图的路径|


在案例中，你添加了两个涂装变体：`Test1`和`Test2`。它们分别在`.../demo/test1`和`.../demo/test2`下寻找对应文件名的贴图，用于替换：
``` 文件结构示意
└─assets
    └─...
       └─demo
          ├─test1
              └─tex1.png
          ├─test2
              └─tex2.png
          ├─tex1.png
          ├─tex2.png
          ├─tex3.png
          ├─tex4.png
          ├─demo.obj
          └─demo.mtl
```

对于涂装变体文件夹内不存在但需要使用的文件，如`Test1`的`tex2.png`、`tex3.png`和`tex4.png`，则会使用原贴图。

在游戏中，你可以使用油漆刷切换列车涂装变体。

## 多车架设置

你可以为铰接车架式蒸汽机车设置一个相对独立的前车架，类似`Big Boy (4000 class)`。

在铰接车架式蒸汽机车上，前转向架(`BOGEY_FRONT`)位于前车架(`FRONT_FRAME`)，后转向架(`BOGEY_REAR`)位于主车架(`FRAME`)。

对于连杆和READOUT，详见[下一章](LocoValveGears.md)。

你还需要将车辆json的`pivot`中的`front`修改为前车架转动轴X坐标的相反数。

## 车厢货物显示

你可以给车厢添加READOUT为`CARGO_ITEMS_[num]`的**立方体**来设置货物显示，这些立方体不会被渲染。

![example](../Textures/pic12.png ':size=50%')
![example](../Textures/pic13.png ':size=50%')

这是一个装着煤的煤水车模型例子，两个立方体分别是`CARGO_ITEMS_1`和`CARGO_ITEMS_2`。模型作者[@WZL_Peter](https://space.bilibili.com/578451618)。

如果添加了多个立方体，那么货物会在分组后分别显示在每个立方体内。

如果立方体被`_IRSIZE`修饰，那么IR的物品会以1:1的尺寸显示。（可能对车辆运输车有用？