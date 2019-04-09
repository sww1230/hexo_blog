---
title: js常见数据校验
date: 2019-04-07
tags:
---

  1.**输入字符必须为中文**
  ```` javascript
  String.prototype.checkChinese(str){
    var reg = new RegExp('^[\\u4E00-\\u9FFF]+$','g')
    return reg.test(str);
  }
  ````

  2.**去除字符两边的空格**

  ```` javascript
  String.prototype.trim = function(){
    return this.replace(/^\s+|\s+$/gm, '')
  }
  ````

  3.**邮箱验证**
  ```` javascript
  String.prototype.checkEmaila = function(){
    var reg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/;
    return reg.test(this);
  }
  ````

  4.**手机号码验证**
  ```` javascript
  String.prototype.checkPhone = function(){
    return /^1[345789]\d{9}$/.test(this);
  }
  ````

  5.**身价证号码验证**
  ```` javascript
  String.prototype.checkIdentityCode = function(){
      var city = {11:"北京",12:"天津",13:"河北",14:"山西",15:"内蒙古",21:"辽宁",22:"吉林",23:"黑龙江 ",31:"上海",32:"江苏",33:"浙江",34:"安徽",35:"福建",36:"江西",37:"山东",41:"河南",42:"湖北 ",43:"湖南",44:"广东",45:"广西",46:"海南",50:"重庆",51:"四川",52:"贵州",53:"云南",54:"西藏 ",61:"陕西",62:"甘肃",63:"青海",64:"宁夏",65:"新疆",71:"台湾",81:"香港",82:"澳门",91:"国外 "};
      var tip = "";
      var pass= true;

      if(!this || !/^\d{6}(18|19|20)?\d{2}(0[1-9]|1[012])(0[1-9]|[12]\d|3[01])\d{3}(\d|X)$/i.test(this)){
          tip = "身份证号格式错误";
          pass = false;
      }else if(!city[this.substr(0,2)]){
          tip = "地址编码错误";
          pass = false;
      }else{
        //18位身份证需要验证最后一位校验位
        if(this.length == 18){
            var code = this.split('');
            //∑(ai×Wi)(mod 11)
            //加权因子
            var factor = [ 7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2 ];
            //校验位
            var parity = [ 1, 0, 'X', 9, 8, 7, 6, 5, 4, 3, 2 ];
            var sum = 0;
            var ai = 0;
            var wi = 0;
            for (var i = 0; i < 17; i++)
            {
                ai = code[i];
                wi = factor[i];
                sum += ai * wi;
            }
            var last = parity[sum % 11];
            if(parity[sum % 11] != code[17]){
                tip = "校验位错误";
                pass =false;
            }
        }
    }
    return pass || tip;
  }
  ````

  6.**日期格式化**
  ```` javascript
  Date.prototype.formatDate = function(fmt) { //author: meizz
      var o = {   
        "M+" : this.getMonth()+1,                 //月份
        "d+" : this.getDate(),                    //日
        "H+" : this.getHours(),                   //小时
        "m+" : this.getMinutes(),                 //分
        "s+" : this.getSeconds(),                 //秒
        "q+" : Math.floor((this.getMonth()+3)/3), //季度
        "S"  : this.getMilliseconds()             //毫秒
      };   
      if(/(y+)/.test(fmt))   
        fmt=fmt.replace(RegExp.$1, (this.getFullYear()+"").substr(4 - RegExp.$1.length));   
      for(var k in o)   
        if(new RegExp("("+ k +")").test(fmt))   
      fmt = fmt.replace(RegExp.$1, (RegExp.$1.length==1) ? (o[k]) : (("00"+ o[k]).substr((""+ o[k]).length)));   
      return fmt;   
  } 

  String.prototype.formatDate = function(fmt) {
    if(/^(\d{13}|\d{10})$/.test(this)){
      return new Date(Number(this)).formatDate(fmt)
    }
    return new Date(this).formatDate(fmt)
  } 
  
  // new Date().formatDate('yyyy年MM月dd日 HH:mm:ss')
  // new Date().formatDate('HH:mm:ss')

  // new Date(1554373056366).formatDate('yyyy/MM/dd')
  // new Date('2019-08-02').formatDate('yyyy/MM/dd')

  // '2018-09-23 12:23:10'.formatDate('yyyy年MM月dd日 HH时mm分ss秒')
  // '1537676590000'.formatDate('yyyy/MM/dd HH:mm:ss')

  ````

  7.**合法IP**
  ```` javascript
  String.prototype.checkIP = function(){
    var reg = /^(?=(\b|\D))(((\d{1,2})|(1\d{1,2})|(2[0-4]\d)|(25[0-5]))\.){3}((\d{1,2})|(1\d{1,2})|(2[0-4]\d)|(25[0-5]))(?=(\b|\D))$/;
    return reg.test(this);
  }
  ````

  8.**输入字符类型为数字，且长度不能越过n值**
  ```` javascript
  // symbols: > || < || >= || <= || != || == || len
  String.prototype.numJudge = function(symbols, value){
    if(/^\d+\.?\d+$/.test(this)){
      if (symbols == 'len' && !/\./.test(this) && this.length == value){
        return true
      }
      if(symbols != 'len' && eval(this + ' '+ symbols +' ' + value)){
        return true
      }
    }
    return false
  }
  ````