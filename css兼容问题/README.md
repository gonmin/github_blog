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
