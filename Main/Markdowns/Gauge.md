IR通过`assets/immersiverailroading/rolling_stock`中的`gauges.json`文件注册新轨距。该文件格式如下：
```json
{
    "register": {
        "name1": 1,
        "name2": 2
    }
}
```

每个轨距定义由两部分组成：轨距名和轨距（float类型），在示例中为轨距为1格的`name1`和轨距为2格的`name2`

定义更多的轨道则为在`"register"`中继续添加。

轨距值的单位为米(格)，轨距名建议使用纯小写英文字母，以便添加翻译文件。

轨距在游戏里默认显示为`immersiverailroading:gauge.轨距名`。你可以在`assets/immersiverailroading/lang`下创建语言文件来覆盖其名称。