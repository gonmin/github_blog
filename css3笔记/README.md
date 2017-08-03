#css3笔记
1.css3长度单位vh。 相对于视口的高度。视口被均分为100单位的vh

2.background-size: contain 把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。

3.CSS3的calc()，border、margin、pading、font-size和width等值设置动态值。
###2016 11 23
1.transition-timing-function 属性规定过度效果的速度曲线。值为linear时以相同的速度开始和结束。值为ease-in，以慢速开始的速度的曲线。

### 2017 06 29


1.css实现箭头
content:" ";
display:inline-block;
height:6px;
width:6px;
border-width:2px 2px 0 0;
border-color:#C8C8CD;
border-style:solid;
-webkit-transform:matrix(0.71, 0.71, -0.71, 0.71, 0, 0);
transform:matrix(0.71, 0.71, -0.71, 0.71, 0, 0);
position:relative;
top:-2px;
position:absolute;
top:50%;
margin-top:-4px;
right:2px;

### 2017 08 03
1. 最老版的flex布局 display: box; box-flex: 1;
