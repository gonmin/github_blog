#前端日记
###2016 11 13
1.如果一个元素padding、margin、width、height的单位为em,其实际值为元素的字体大小乘以em的数值。example：假如p的font-size:20px;其padding-top为0.4em,即其padding-top为5px
###2016 11 14
1.svg文件的开头不能有注释及空行

2.`background-origin`css3背景中的属性，支持的浏览器为ie9+，有三个值padding-box，content-box，border-box，分别是背景图像相对于内边距，内容框，边框来定位
###2016 11 18
1.突然想到一个问题，如果被问ie6的浏览器兼容性问题怎么回答？

答：1.比如有ie6下的固定定位，通过一段css跟js的代码是可以解决的，这个我是复制下来用，其中的原理还是没有认真研究

2.很出名的双外边距问题，用display:inline

3.很多问题，可以通过尝试让ie6下拥有布局来解决，比如可以加上position: relative。width,heigt

4.ie6下定义小于12px的元素会自动扩展。可以设置字体为零。

###11月24日
1.:nth-child()选择器，:nth-last-child()选择器，:nth-of-type()选择器，支持的浏览器都是ie9及以上。

2.nth-last-child()选择器会受script元素影响。liu'lan'qi

3.CSS3 element1~element2 选择器，element1 之后出现的所有 element2。注意element1和element2必须有相同的父元素。
###11月28
1.：after选择器，在被选元素后面加入内容，使用**content**来指定加入的内容
