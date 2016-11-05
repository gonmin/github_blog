#常用的javascript函数

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
