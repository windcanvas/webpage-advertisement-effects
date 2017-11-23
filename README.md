# webpage-advertisement-effects
HTML+CSS+JavaScript实现绚丽的网页广告特效
## 使用JS实现右下角广告特效

### 我们常用的在a标签中有点击事件

**1**. ```
a href="javascript:js_method();"```


这是我们平台上常用的方法，但是这种方法在传递```this```等参数的时候很容易出问题，而且```javascript:```协议作为```a```的```href```属性的时候不仅会导致不必要的触发```window.onbeforeunload```事件，W3C标准不推荐在href里面执行```javascript```语句

**2**. ```a href="javascript:void(0);" onclick="js_method()"```


```void(0)```返回```undefine```d，地址不发生跳转。而且这种方法不会像第一种方法一样直接将js方法暴露在浏览器的状态栏

### 利用css定义广告出现在页面右下角

提示：元素的```position```属性


```
position: fixed;//相对浏览器窗口固定位置
bottom: 0;
right: 0;
```


### 利用传参（id）,获取相应元素

提示: 

**1**. 定义一个通用方法，传一个参数进去（本案例用到的是id，所以传id）,得到相应的控制，不必每次获取元素都要```document.getElementById()```

**2**. 定义时，记得要```return```，否则定义的控件无法引用


```
var $ = function(id) { 

     document.getElementById(id);
//return就是执行完$这个方法，
//就能得到一个控件的引用，
//如果没有return，那就是不能拿到控件的引用了
}
```



### 给相应的元素进行触发事件（```onmouseover```及```onclick```）

提示:

**1**. ```id="clickMe"```进行鼠标划过事件，让广告层（id="showPic"）显示

**2**. ```id="closeBtn"```进行鼠标点击事件，让广告层（id="showPic"）隐藏

### 在样式表里定义两个样式，显示与隐藏

提示: ```className```改变显示与隐藏  className（添加样式）

注意：页面初次加载时，右下角广告是隐藏状态



```
/*
var TipBox = $("tipCon");
var ClickMe = $("clickMe");
var showPic = $("showPic");
var closeBtn = $("closeBtn");
*/

$("clickMe").onmouseover = function() { //鼠标划过事件

/*
$("showPic").style.display = 'block';
$("closeBtn").style.display = 'block';
*/

$("showPic").className = 'show';
$("closeBtn").className = 'show';
}

$("closeBtn").onclick = function(){//鼠标点击事件
			
/*
$("showPic").style.display = 'none';
$("closeBtn").style.display = 'none';
*/

$("showPic").className = 'hide';
$("closeBtn").className = 'hide';
}
```
