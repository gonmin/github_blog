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
###12月5
1.concat(),基于当前数组的所有项创建新的数组。

2.slice()基于当前数组的一项或多项建立一个新的数组。该方法接受一个或两个参数。一个参数时返回指定位置到结束。两个参数返回开始和结束位置之间的项，但不包括结束项

3.splice()，向数组中部插入项。接受两个参数或三个参数。三个参数时第二个参数为0，表示增加。

4.位置方法，indexOf，lastIndexOf.，返回数组的项，没有找到的话返回-1.

5.**es5**迭代方法every，每一个都正确时才返回true，some()，有一项正确时就返回true。filter()，返回符合条件的项。map()对每一项进行某些操作。forEach，遍历某些操作
6.缩小方法reduce()。
###2016 12 10
1.一个域名地址的组成包括。协议、子域名、主域名、端口号、请求资源的地址。比如https://github.com/gonmin/github_blog/edit/master/%E5%89%8D%E7%AB%AF%E6%97%A5%E8%AE%B0/README.md。。https为协议名。www为子域名，github.com为主域名。后面的一大串为请求资源的地址。

2.当协议、子域名、主域名、端口号中任何一个不一样的时候都算做是不同的域。
###2016 12 14
1.错误处理的try-catch语句

```javascript
try{
//可能出现错误的代码
}catch(error) {
//在错误发生时怎样去处理
}
```
error对象有两个属性，name和message提示错误的类型。name定义的是错误的类型。
###2016 12 27
1.fis release 将fis 投送到指定根目录
2.fis3 server start开启服务
4.fis3 sserver open  打开根目录
5.fis3 release -h 查看fis release 的帮助

###2016 12 30。表单提交
1.点击type的值为submit的input,或者button元素就会提交表单，或者是input元素的type属性值为image时，也会提交表单。以这种方式提交表单的时候，浏览器会在发送到服务器之前触发submit事件，这样就可以检验表单数据，阻止这个事件的默认行为就可以取消表单的提交。直接调用form的submit()方法也是可以提交表单，以这种方式不会触发submit事件，所以调用之前要验证表单数据。

2.其他，button按钮的type默认值是submit。所以直接提交。
###2017 1 5

1.vue，通过v-bind设置属性。
###2017 2 13

1.webpack文件目录，首先是build和config都是webpack配置相关
2.node_module。是通过npm安装的依赖代码库
3.src是存放项目源码
4.第三方静态资源
###2017 2 21
1.css-loader的作用是使能通过require请求css文件。style-loader的作用是将打包后的css文件放在引入到html中。

###2017 4 2

win+r。打开运行，然后的话键入 services.msc 找到windows更新

###2017 4/ 13

1.let 命令，只在所在的代码块内有效

2.for循环的计数器很适合用let。

3.不存在变量声明提升 let。

4.暂时性死区

5.不允许重复声明。

##2017 4 13

1./\d/  在//后面匹配加上i 。匹配大小写，以后一律放在博客园中。加上i为不区分大小写。就是默认是区分的。

2.比如你想找hi,但是hign。这些也会出来啊。请加上\b就是边界 \bhi\b

3.比如你想查找hi后面不远处的一个luck \bhi\b.*\bluck\b  *     这里.是元字符，代表匹配换行符之外的任意字符。 `*`也是元字符，匹配任意数量

4.\d 代表元字符。数字

5.\s匹配任意的空白符，包括空格，制表符(Tab)，换行符，中文全角空格等。\w匹配字母或数字或下划线或汉字等

6.+元字符代表至少有一个  ?代表0次或者一次  `^`查找开头，$查找结尾  转义符\

