#css的浏览器兼容性问题

###1.ie6下兼容position:fixed
/*固定于顶部*/
```css
#top { 
_position: absolute; 
_bottom: auto; 
_top: expression(eval(document.documentElement.scrollTop)); 
}
```
/*固定于底部*/
#bottom { 
  _position: absolute; 
  _bottom: auto; 
  _top: expression(eval(document.documentElement.scrollTop+document.documentElement.clientHeight-this.offsetHeight-(parseInt(this.currentStyle.marginTop,10)||0)-(parseInt(this.currentStyle.marginBottom,10)||0))); 
}

###2.js焦点轮播图代码
```javascript
var wrap=document.getElementById('wrap'),
    pic=document.getElementById('pic'),
    list=document.getElementById('list').getElementsByTagName('li'),
    next=document.getElementById('next'),
    prev=document.getElementById("prev"),
    index=0,
    timer=null;

function auto(){
  timer=setInterval(function(){
    index++;
    if(index>=list.length){
      index=0;
    }
    change(index);
  },2000);  
}
auto();
function change(curIndex){
  pic.style.marginTop=-170*curIndex+'px';
  for(var n=0;n<list.length;n++){
      list[n].className='';
  }
  list[curIndex].className='on';
  index=curIndex;
}
wrap.onmouseover=function(){
  clearInterval(timer);
}
wrap.onmouseout=auto;
for(var i=0;i<list.length;i++){
  list[i].id=i;
  list[i].onmouseover=function(){
    change(this.id);          
  }
}
next.onclick = function(){
  index++;
  if (index >= list.length){
    index = 0;
  }
  change(index);
};
prev.onclick = function(){
  index--;
  if (index < 0){
    index = list.length-1;
  }
  change(index);
};
```
###tab切换代码
通过className属性添加类名时，会覆盖元素原来的类名，所以这里封装一个函数解决
```javascript
var tab = document.getElementById('tab');
var as = tab.getElementsByTagName('a');
var box = document.getElementById('box');
var forms = box.getElementsByTagName('form');
for (var i = 0; i < as.length; i++) {
  as[i].id = i;
  as[i].onclick = function(){
    for (var j = 0; j < as.length; j++) {
      as[j].className = '';
      forms[j].style.display = 'none';
    }
    this.className = 'on';
    forms[this.id].style.display = 'block';
  }
}
```
