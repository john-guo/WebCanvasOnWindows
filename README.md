 WebCanvasOnWindows
display web canvas on windows screen

This project can display any web canvas in a transparent form. So you can use any canvas technology on your screen in windows environment. Even if a canvas than has alpha channel you can see an irregular window on your screen. And also it provides some tricks so that the web can control the window,track the mouse, etc. 

[Some Details]

I defined two render modes:auto or manual.

In auto mode, you can just open a uri that contains a canvas, and it will locate the canvas with a xpath you specified. Then the canvas display on your screen. If it cleard with alpha color you can see an irregular window. But webgl in this mode may not work correctly. If you want to use webgl, the webgl context must be specified the "preserveDrawingBuffer:true" attribute.

In manual mode, you must use the winapp.js(in the project) to do "explicit render". And you can obtain some properties of the display window, you can control these properties.

The application will auto determine the render mode. If your html file used winapp.js, the render mode will be the manual mode.

