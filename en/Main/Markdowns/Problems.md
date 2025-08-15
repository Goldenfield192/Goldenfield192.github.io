>1.车辆无法加载？

* 检查`latest.log`
* 文件中是否出现大写字母或非ASCII字符?仅允许小写字母、数字和下划线，且必须以小写字母开头。
* json是不是有语法错误？
* 通过资源包页添加资源包后需重启游戏，或者你也可以放在`.minecraft/config/immersiverailroading`下。

>2.我的游戏崩溃了怎么办？

* 我知道在1.16.5，与OptiFine共存时，切换光影包大概率会导致游戏崩溃，有时NotEnoughCrashes也无法阻止。并且崩溃时游戏会自动卸载所有资源包。
>所以你应该装在`.minecraft/config/immersiverailroading`下。
* 其他的大抵可以给IR[提issue](https://github.com/TeamOpenIndustry/ImmersiveRailroading/issues)了。