#常用的javascript实例代码

###1.回到顶部代码
```javascript
window.onload = function(){
	var clientH = document.documentElement.clientHeight || document.body.clientHeight;
	var btn = document.getElementById('btn');
	var timer = null;
	window.onscroll = function(){
		var scrollT = document.documentElement.scrollTop || document.body.scrollTop;
		if (scrollT > clientH){
			btn.style.display = "block";
		} else {
			btn.style.display = "none";
		}
	}
	btn.onclick = function(){
		timer = setInterval(function(){
			var scrollT = document.documentElement.scrollTop || document.body.scrollTop;
			var ispeed = Math.floor(-scroll/6);
			document.documentElement.scrollTop = document.body.scrollTop = scrollT + ispeed;
			    console.log(scrollT);
			if (scrollT == 0){
				clearInterval(timer);
			}
		}, 30);
	}
}
```
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
