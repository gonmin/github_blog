#封装的javascript函数

###1.共享onload事件
因为后面的window.onload会覆盖前面的
```javascript
function addLoadEvent(func) {
  var oldonload = window.onload;
  if (typeof window.onload != "function") {
    window.onload = func;
  } else {
    window.onload = function(){
      oldonload();
      func();
    }
  }
}
```
###2.单双行的交替样式的js文件
给表格的的行加上斑马条纹样式，参数elements为需要行的元素集合

ie9以上的浏览器可以直接用CSS3的:nth-child() 选择器，即:nth-child(odd)或nth-child(even)
```javascript
function Striped(elements) {
  var odd = false;
  for (var j=0; j<elements.length;j++){
    if (odd == true) {
      elements[j].style.backgroundColor = "red";
      odd = false;
    } else {
      odd = true;
    }
  }
}
```
###添加一个类名
通过className属性添加类名时，会覆盖元素原来的类名，所以这里封装一个函数解决
```javascript
function addClass(element,value){
  if (!element.className){
    element.className = value;
  } else {
    newClassName = element.className;
    newClassName += " ";
    newClassName += value;
    element.className = newClassName;
  }
 }
```
###删除一个类名
如果只是想删除元素的一个特定类名，可以通过如下函数解决
```javascript
function removeClass(element, value) {
  var classNames = element.className.split(" ");//把取得的类名字符串转成数组
  var pos = -1,
      i,
      len;
  for (i=0,len=classNames.length; i<len; i++) {
    if (classNames[i] == value) {
      pos=i;
      break;
    }
  }
  classNames.splice(pos,1);//splice() 方法向/从数组中添加/删除项目，然后返回被删除的项目
  element.className = classNames.join(" ");//再将数组转成字符串
 }
```
哈哈，这次你就认不出来了。
