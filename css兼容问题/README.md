#css的浏览器兼容性问题

###1.ie6下兼容position:fixed
固定于顶部
```css
#top { 
  _position: absolute; 
  _bottom: auto; 
  _top: expression(eval(document.documentElement.scrollTop)); 
}
```
固定于底部
```css
#bottom { 
  _position: absolute;
  _bottom: auto; 
  _top: expression(eval(document.documentElement.scrollTop+document.documentElement.clientHeight-this.offsetHeight-(parseInt(this.currentStyle.marginTop,10)||0)-(parseInt(this.currentStyle.marginBottom,10)||0))); 
}
```
这两段代码只能实现在最底部跟最顶部，你可以使用`_margin`修改其中的数值控制元素的位置。

经过以上处理后还有bug，被固定定位的元素在滚动滚动条的时候会出现一闪一闪的情况。解决这个问题的办法是在 CSS 文件中加入：
```css
* html{ 
  background-image:url(about:blank); 
  background-attachment:fixed; 
}
```
#其他的一些兼容总结
ie8仍然不支持rgba

inline元素的display属性设置为inline-block时，所有的浏览器都支持；

block元素的display属性设置为inline-block时，IE6/IE7浏览器是不支持的；

css的border-spacing属性可以控制单元格之间的距离，但是IE7和更低的版本不支持，因此需要使用老式但可靠的cellspacing属性。

IE7级以下版本不支持轮廓outline

IE7及以下版本不支持在除链接之外的其他元素上使用伪类选择器，但是所有的现代浏览器都支持。

IE6及更低版本不支持属性选择器.不支持

ie6和ie7中z-index有一个bug，如果只是对一个子元素设置z-index，就算再大也覆盖不了与父元素同级的其他元素。所以通用的解决办法实在父元素设置一个z-index；

IE7及更低的版本不支持在除链接之外的其他元素上使用伪类选择器。

ie6只注意应用于链接的伪类选择器，会忽略focus。IE7在任何元素上都支持hover。

IE7和更高版本都支持子选择器。但是在IE7中有一个小bug，如果父元素和子元素之间有HTML注释，就会有问题。

