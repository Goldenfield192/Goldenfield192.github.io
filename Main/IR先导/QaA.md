 >1.什么是READOUT？
   * IR使用对象名来区分组件，这些对象名中可被识别的语素即为READOUT。
   * 如对于车架对象，其名称应包含`FRAME`，`FRAME`即为其对应的READOUT。
   * READOUT应直接写在blender的对象名中。
   * READOUT是无序的。
   * 除READOUT外的字符均可自定义，前提是不与其他对象混淆。 
   * 下文约定：
     - [pos]表示前/后(FRONT或REAR)，这是对应READOUT的一部分。
     - [side]表示左/右(LEFT或RIGHT)，这是对应READOUT的一部分。
     - [num]表示任意不与其他同类物体重复的数字，这是对应READOUT的一部分。

 >2.我该使用什么软件？
   * 我们通常使用blender为IR制作模型。
     * 导出模型时，为了正确显示动画，应使用`Wavefront(.obj)(legacy)`模式，且只勾选OBJ物体。
   
   !>注意，Metasequoia无法为obj模型导出对象数据，不可用于IR追加包制作。
   * 贴图可使用Paint.net等。
   * 音效可使用Adobe Audition等。
   * JSON可使用VS Code等。

 >3.注意事项
  * 所有字符串均应只使用小写字母和数字