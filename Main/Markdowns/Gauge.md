IR通过`assets/immersiverailroading/rolling_stock`中的`gauges.json`文件加载新轨距。
```
{
    "register": {
        "name1": Int1,
        "name2": Int2...//后续同理
    }
}
```
其中轨距值单位为米(方块)，轨距名建议使用纯英文。

轨距在游戏里默认显示为`immersiverailroading:gauge.轨距名`，你可以在`assets/immersiverailroading/lang`下创建语言文件来覆盖其名称。