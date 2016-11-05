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
