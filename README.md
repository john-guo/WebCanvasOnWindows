 WebCanvasOnWindows
display web canvas on windows screen

This project can display any web canvas in a transparent form. So you can use any canvas technology on your screen in windows environment. Even if a canvas that has alpha channel you can see an irregular window on your screen. And also it provides some tricks so that the web can control the window,track the mouse, etc. 

[Some Details]

I defined two render modes:auto or manual.

In auto mode, you can just open a uri that contains a canvas, and it will locate the canvas with a xpath you specified. Then the canvas display on your screen. If it cleard with alpha color you can see an irregular window. But webgl in this mode may not work correctly. If you want to use webgl, the webgl context must be specified the "preserveDrawingBuffer:true" attribute.

In manual mode, you must use the winapp.js(in the project) to do "explicit render". And you can obtain some properties of the display window, you can control these properties.

The application will auto determine the render mode. If your html file used winapp.js, the render mode will be the manual mode.

[More Details]

As default the application will open index.html in same folder, you can change this in config file(WpfGecko.exe.config), and also the xpath locating the canvas is in it.

You can set debug config to true to enable a browser window. This window cannot debug your js code but can load other html file that contains canvas to test.

3 demo html5 in the project/web folder. 

The live2d demo showes how to canvas track the mouse globally.

The threejs demo showes how to use this with threejs.

The last demo showes how to control the window in html.

Use VS2017 to Build the project, copy demo into the exe folder, run it and enjoy.

# 中文说明 #
本项目是一个把任意网站页面中的canvas画到windows屏幕上的工具。只要网站页面中包含有canvas使用本工具都能把canvas绘画到windows的桌面前台上，并且可以随意拖动。如果canvas采用了alpha通道，那么windows桌面上画出来的就是一个裁剪过的图像。但是对于运用了webgl的canvas需要在创建webgl上下文的时候指定preserveDrawingBuffer:true参数才能保证正确工作。

使用方法很简单，在wpfgecko.exe.config文件中指定要打开的html的uri就行，并且如果在config中把debug设置为true，则会显示一个测试用浏览器方便输入网址测试。

如果想对绘画窗口获得更多控制，比如控制它移动，感知桌面鼠标移动等等，就需要在自己定制的html中引入winapp.js，使用这个js来进行更多的控制权。

项目目录下有个web目录，里面有3个例子：

live2d展示了如何追踪桌面鼠标

threejs展示了如何运用threejs

序列帧动画则展示了如何控制窗口移动

## 绘画模式 ##

这里采用了2种不同的方式进行canvas的再渲染绘画
 
 *自动模式*
 自动模式下，工具会根据配置文件中的CanvasXPath用xpath搜索方法找到页面上的目标canvas，然后以配置文件种的刷新率进行绘画刷新。
 
 *手动模式*
 手动模式下，需要目标页面引用winapp.js，后面会有winapp.js的详细介绍。

工具会自动检测目标页面的渲染模式。

## 全局配置文件 ##

配置文件，也就是wpfgecko.exe.config，这里包含了全局的配置，有些配置可以用js调用winapp.config进行覆盖
 `Url`
 启动加载的地址，默认是exe当前目录的index.html
 
 `Debug`
 是否启用调试模式，默认是false，可用winapp.confg覆盖。
 
 `FPS`
 刷新率，默认是60，刷新率影响着自动模式下的渲染频率，以及手动模式下的事件推送频率，可用winapp.config覆盖。
 
 `CanvasXPath`
 自动模式下的xpath,默认是//canvas


## winapp.js的使用 ##

`WinApp.config(settings)` 
初始化配置，此方法最好在js最开始调用，目前支持的配置字段有 

 `{debug:bool}` 
 启用或关闭debug模式

 `{fps:int}` 
 指定刷新率，默认是60
 
 `WinApp.createWindow(id)`
  创建与canvas关联的windows浮动窗口，需要指定一个唯一的字符串id（类似于dom的elementId)，返回一个win对象
  
   ### win对象 ####
   
   属性
   
   `id` 
   唯一id

   事件
   
   `dblclick` 
   浮动窗口被双击。
   
   `mousemove` 
   鼠标移动事件（非窗口，而是全屏），事件参数为{x:横坐标，y:纵坐标}
      
   `moveNotify`
   窗口移动通知，事件参数为{x:窗口左边界坐标,y:窗口顶部坐标}
   
   `resizeNotify`
   窗口改变通知，事件参数为{w:窗口宽,h:窗口高}
   
   `opacityNotify`
   窗口透明度改变通知，事件参数为{opacity:不透明度0-1}
   
   方法
   
   `render(canvasElement)`
   绘制方法，把目标canvasElement画到浮动窗口上
   
   `move(x,y)`
   增量移动浮动窗口，参数x和y不是绝对坐标，而是增量，比如向右移动1个单位就是move(1,0)
   
   `setWidth(w)`
   `setHeight(h)`
   `resize(w,h)` 
   改变浮动窗口大小
   
   `setOpactiy(opacity)`
   改变浮动窗口透明度

具体使用请参考live2d以及sequence_frames这2个例子。

## 最后 ##
在自己写的canvas页面的时候，推荐可先用firefox浏览器对页面进行调试，因为本工具不带js调试功能，只会在exe同目录输出js日志文件console.log。

目前暂时没提供编译后的执行文件包，只提供了完整项目，可以先用vs2017编译，然后把例子文件及相关目录复制到exe所在目录就能看到演示效果。
