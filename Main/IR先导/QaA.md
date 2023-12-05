 >1.什么是READOUT？
   * IR使用对象名来区分组件，这些对象名中可被识别的语素即为READOUT。
   * 如对于车架对象，其应包含`FRAME`，`FRAME`即为其对应的READOUT。
   * READOUT是无序的。
   * 在不与其他对象混淆的情况下，除READOUT外的部分均可以自定义。 
   * 下文约定：
     - [pos]表示前/后(FRONT或REAR)
     - [side]表示左/右(LEFT或RIGHT)
     - [num]表示任意不与其他同类物体重复的数字
     - [xxx]表示任意**仅包含**小写字母/数字的字符串

 >2.我该使用什么软件？
   * 我们通常使用blender为IR制作模型。
     * 请注意，Metasequoia无法为obj模型导出对象数据，不可用于IR追加包制作。
   * 贴图可使用Paint.net等。
   * 音效可使用Adobe Audition等。
   * JSON可使用VS Code等。
 >3.WIP