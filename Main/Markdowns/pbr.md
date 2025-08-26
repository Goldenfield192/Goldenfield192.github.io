IR支持指定PBR贴图但是方法有点不寻常...没关系，这就是这样一篇教程。

以下内容测试于Minecraft 1.12.2/OptiFine G5

## 高光与法线贴图
和漫反射贴图一样，IR的法线（Normal）和高光（Specular）贴图也需要在mtl文件内指定，而不是类似其他资源包的_n/_s。
> 关于他们的格式，[Iris](https://shaders.properties/current/how-to/pbr_standards/#formats)有详细讲解。
> 
> 这两种格式均可使用，但是要注意挑选支持对应格式的光影包。

为了添加他们，你需要在mtl文件的对应材质内将法线贴图指定到`map_Bump`，将高光贴图指定到`map_Ns`，就像这样：
```mtl
newmtl mat1_4k
Ka 0.145455 0.145455 0.145455
Ks 0.500000 0.500000 0.500000
Ke 0.000000 0.000000 0.000000
Ni 1.500000
d 1.000000
illum 3
map_Kd mat1_base.png
map_Bump mat1_base_n.png
map_Ns mat1_base_s.png
```
然后就能加载了。
>[!WARNING]由于IR的法线贴图加载没有占位符机制，所以对于一个指定了法线贴图的材质，对应mtl内所有材质必须全部指定法线贴图，否则一张也不会加载！
> 
> 高光贴图同理。

为了让光影包正确渲染他们，你可能还需要在配置文件`immersiverailroading_graphics.cfg`中修改`OpenFineEntityShader`为`Terrain`。
>[!TIP]当然你也可以在游戏内配置页面的`ConfigGraphic`里修改。

附录 经过我个人测试的光影包：
SEUS v10.1
SEUS Renewed v1.0.1
SEUS PTGI HRR v2.1
Kappa shader