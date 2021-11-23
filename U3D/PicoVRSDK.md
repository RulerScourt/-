## PicoVRSDK

##### 1.导入PicoVR_Unity_SDK资源

​	Assets中Import Package选择Custom Package，在UnityProjects中打开PicoVR_Unity_SDK中的64位SDK文件

##### 2.插入Pvr_UnitySDK代替Main Camera

​	导入后记得删除Main Camera和Directional Light

##### 3.插入ControllerManager作为Pvr_UnitySDK的子类

​	其它部分不需要作任何修改

##### 4.建立头部控制HeadControl作为Pvr_UnitySDK的子类

​	建立HeadSetControl作为HeadControl的子类

​	为HeadSetControl添加Sprite Renderer组件和Pvr_UI Pointer脚本

​	为其选择Sprite和Color，并将Order in Layer设置为30000

##### 5.添加UI画布：Canvas

​	Hierarchy中创建UI中的Canvas

​	更改Layer为Default

​	更改Render Mode为World Space，添加Event Camera为Head，Additional Shader添加TexCoord1、Normal和Tangent。

​	按需求设置画布的面积和距离摄像头位置

​	添加Image组件

​	设置Source Image为背景Background，调整Color

​	添加Pvr_UI Canvas脚本和Pvr_Controller Demo脚本，分别添加Head Set Controller为HeadSetControl；Controller 0 为PvrController0；Controller 1 为PvrController1。

##### 6.在Event中添加Pvr_Input Module脚本

##### 7.可以随意为UI添加功能和事件了！