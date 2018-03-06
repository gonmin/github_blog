```javascript
export default class Util {
    transTimestamp (timestamp) {
        let date = new Date(timestamp * 1000);
        let year = date.getFullYear();
        let month = date.getMonth() + 1;
        let day = date.getDate();
        let hour = date.getHours();
        let minute = date.getMinutes();
        let second = date.getSeconds();
        return Object.assign(
          {
            year,
            month,
            day,
            hour,
            minute,
            second
          }
        );
    }

    baseSlice(array, start, end) {
      var index = -1,
          length = array.length;

      if (start < 0) {
        start = -start > length ? 0 : (length + start);
      }
      end = end > length ? length : end;
      if (end < 0) {
        end += length;
      }
      length = start > end ? 0 : ((end - start) >>> 0);
      start >>>= 0;

      var result = Array(length);
      while (++index < length) {
        result[index] = array[index + start];
      }
      return result;
    }

    // 将数组转成多个数组
    chunk(array, size) {
      var length = array ? array.length : 0;
      if (!length || size < 1) {
        return [];
      }
      var index = 0,
          resIndex = 0,
          result = Array(Math.ceil(length / size));

      while (index < length) {
        result[resIndex++] = this.baseSlice(array, index, (index += size));
      }
      return result;
    }

    validate (value, type = 'require') {
        value = value.trim();
        // 非空验证。
        if (type === 'require') {
            return !!value;
        }
        // 手机号验证
        if (type === 'phone') {
            return /1\d{10}$/.test(value);
        }
        // 邮箱验证
        if (type === 'email') {
            return /^(\w)+(\.\w+)*@(\w)+((\.\w{2,3}){1,3})$/.test(value);
        }

        // 身份证验证
        if (type === 'idcard') {
            return /(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/.test(value);
        }
        
    }

    handleCompatible (proper, fn) {
      if (wx[proper]) {
        fn && fn();
      } else {
        wx.showModal({
          title: '提示',
          content: '当前微信版本过低，无法使用该功能，请升级到最新微信版本后重试。'
        })
      }

    }

    deleteSameCell (arr) {
      let result = [];
      for (var i = 0; i < arr.length; i++) {
          let n = 0;
        for (var j = i+1; j < arr.length; j++) {
          if (arr[i].id === arr[j].id ) {
            n++
          }
        }
        if (n === 0) {
            result.push(arr[i])
        }
      }
      return result;
    }
    // 转千分位格式
    addCommas(val) { 
      var aIntNum = val.toString().split('.'); 
      if (aIntNum[0].length >= 4) {
       aIntNum[0] = aIntNum[0].replace(/(\d)(?=(\d{3})+$)/g, '$1,');
      }
      if (aIntNum[1] && aIntNum[1].length >= 4) { 
        aIntNum[1] = aIntNum[1].replace(/(\d{3})/g, '$1 ');
      }
       return aIntNum.join('.');
    }

    // 将getDay() 方法返回的数字转成中文显示的日期
    chinessWeek (num) {
        let week;
        switch (num) {
            case 0:
              week = "星期天";
              break;
            case 1:
              week = "星期一";
              break;
            case 2:
              week = "星期二";
              break;
            case 3:
              week = "星期三";
              break;
            case 4:
              week = "星期四";
              break;
            case 5:
              week = "星期五";
              break;
            case 6:
              week = "星期六";
        }

        return week;
    }
    // 前端获取未来多少天的日期数组，参数为天数的数字
    //  结果为[{year: 2017, month: 10, day: 30},{year: 2017, month: 10, day: 31}] 的结构
    getFutureDays (num) {
      let MinusSecondArr = [];
      let nowMinusSecond = Date.now();
      MinusSecondArr.push(nowMinusSecond);
      for (var i = 1; i < num; i++) {
        MinusSecondArr.push(nowMinusSecond + i * 24 * 3600 * 1000)

      }
      let result = [];
      MinusSecondArr.forEach((item) => {
        result.push({
          year: new Date(item).getFullYear(),
          month: new Date(item).getMonth() + 1,
          day: new Date(item).getDate()
        })
      })

      return result;
    }

    formatNumber (n) {
      n = n.toString();
      return n[1] ? n : '0' + n;
    }

    // 只允许输入数字和小数点后两位
    clearNoNum(value){ 
      value = value.replace(/[^\d.]/g,"");  //清除“数字”和“.”以外的字符   
      value = value.replace(/\.{2,}/g,"."); //只保留第一个. 清除多余的   
      value = value.replace(".","$#$").replace(/\./g,"").replace("$#$",".");  
      value = value.replace(/^(\-)*(\d+)\.(\d\d).*$/,'$1$2.$3');//只能输入两个小数   
      if(value.indexOf(".")< 0 && value !=""){//以上已经过滤，此处控制的是如果没有小数点，首位不能为类似于 01、02的金额  
       value= parseFloat(value);  
      }  
      console.log(value);
      return value;
    }
}

```
