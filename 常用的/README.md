###多用的知识总结
1.有时候需要验证输入内容的长度，一个汉字2个字节，一个英文字母一个字节。这个如何实现呢。很明显需要判断出汉子汉字并进行处理。汉字的正则表单式范围是/[\u4e00-\u9fa5]/。下面为计算内容长度的一个函数
```javascript
function content_l(string){
  var string_length = 0;
  for (var i = 0; i < string.length; i++) {
    if((/[\u4e00-\u9fa5]/).test(string[i])){
      string_length +=2;
    }else {
      string_length +=1;
    }
  }
  return string_length;
}
```
