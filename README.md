第一类：块状元素float后，有添加了横向的margin，在IE6下比设置的值要大（属于双倍浮动的bug）

解决方案：给float标签添加display：inline，将其转换为行内元素



第二类：表单元素行高不一致

解决方案：给表单元素添加float：left（左浮动）；或者是vertical-align：middle；（垂直对齐方式：居中）



第三类：设置较小高度的容器（小于10px），在IE6下不识别小于10px的高度；

解决方案：给容器添加overflow：hidden；



第四类：当在a标签中嵌套img标签时，在某些浏览器中img会有蓝色边框；

解决方案：给img添加border：0；或者是border：none；



第五类：min-height在IE6下不兼容

解决方案：

1）min-height：value；

      _height：value；

2）min-height：value；

     height：auto！important；

     height：value；



第六类：图片默认有间隙

解决方案：

1）给img标签添加左浮动float：left；

2）给img标签添加display：block；



第七类：按钮默认大小不一

解决方案：

1）用a标签来模拟按钮，添加样式；

2）如果按钮是一张背景图片，那么直接给按钮添加背景图；



第八类：百分比的bug

解决方案：父元素宽度为100%，子元素宽度各为50%，在IE6下各个元素宽度之和超过100%

解决方案：给右边浮动的子元素添加clear：right；



第九类：鼠标指针bug

描述：cursor：hand；只有ie浏览器识别，其他浏览器不识别

解决方案：cursor：pointer；IE6以上浏览器及其他内核浏览器都识别；



第十类：透明度属性

解决方案：针对IE浏览器：filter：alpha（opacity=value）；（取值范围1--100）

兼容其他浏览器：opacity：value；（取值范围0--1）



第十一类：上下margin的重叠问题

描述：给上边元素设置了margin-bottom，给下边元素设置了margin-top，浏览器只会识别较大值；

解决方案：margin-top和margin-bottom中选择一个，只设置其中一个值；



关于hack


我很少使用hacker的，可能是个人习惯吧，我不喜欢写的代码IE不兼容，然后用hack来解决。不过hacker还是非常好用的。使用hacker我可以把浏览器分为3类：IE6 ；IE7和遨游；其他（IE8 chrome ff safari opera等）

◆IE6认识的hacker 是下划线_ 和星号 *

◆IE7 遨游认识的hacker是星号 *

比如这样一个CSS设置：

height:300px;*height:200px;_height:100px;

IE6浏览器在读到height:300px的时候会认为高时300px；继续往下读，他也认识*heihgt， 所以当IE6读到*height:200px的时候会覆盖掉前一条的相冲突设置，认为高度是200px。继续往下读，IE6还认识_height,所以他又会覆盖掉200px高的设置，把高度设置为100px；

IE7和遨游也是一样的从高度300px的设置往下读。当它们读到*height200px的时候就停下了，因为它们不认识_height。所以它们会把高度解析为200px，剩下的浏览器只认识第一个height:300px;所以他们会把高度解析为300px。因为优先级相同且想冲突的属性设置后一个会覆盖掉前一个，所以书写的次序是很重要的。