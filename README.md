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

## winapp.js的使用 ##
[holderplace]

## 最后 ##
目前暂时没提供编译后的执行文件包，只提供了完整项目，可以先用vs2017编译，然后把例子文件及相关目录复制到exe所在目录就能看到演示效果。
