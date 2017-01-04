# wap页面开发设配问题

> 可以作为web pages页面开发的init项目，基本解决的web pages页面开发的已到的设配问题（不包括兼容）

## head配置
- 以下代码是手机端页面开发的标配，使用以下配置和css3的媒体查询结合，即可开发出响应式页面
```
    <meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no, target-densitydpi=device-dpi" />
    <meta name="apple-mobile-web-app-capable" content="yes" />    
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
    <meta name="format-detection" content="telephone=yes"/>
    <meta name="msapplication-tap-highlight" content="no" />
```


## 字体大小适配
- 移动端比较多的适配问题都是由于不同手机的不同尺寸导致的，所以如何在不同手机屏幕上看到合适大小的界面成了重要话题。

- 这个代码使用的是rem单位
```
html{font-size: 62.5%}
//使用的时候若要设置16px的字体，只要设置为1.6rem即可
body{font-size: 1.6rem}
```

### rem与em的区别 （[参考 大漠老师的文章 ](http://www.w3cplus.com/css3/define-font-size-with-css3-rem)）

em是相对于其父元素来设置字体大小的，是一个相对值，其计算公式是   1 ÷ 父元素的font-size × 需要转换的像素值 = em值 （不是很会算）

```
body{font-size: 62.5%;  /* 10 ÷ 16 × 100% = 62.5% */}
p{font-size: 1.4em; /* 1.4em × 10 = 14px*/}
```

rem是相对于根元素来设置字体大小的，也是一个相对值，只是相对于html根元素

```
html{font-size: 62.5%; /* 10 ÷ 16 × 100% = 62.5% */}
body{font-size: 1.6rem; /* 1.6 × 10px = 16px */}
h1{font-size: 2.4rem; /* 2.4 × 10px = 24px */}
```


## 背景图
之前公司的设计师，总喜欢整个页面使用一张背景图来进行设计，所以，每次见到这样的设计稿都会很头疼，因为不同手机屏幕会把背景图拉伸...后来，和同事一起找到了这个相对较好的解决方案

```
window.onload = function(){
    var body = document.getElementsByTagName('body')[0];
    body.style.height = document.documentElement.clientHeight + 'px';
}
```
```
body{
    background: url("../images/thanks_bg.jpg") no-repeat;
    background-size: cover;
}
```
添加这两个代码之后，背景图就可以铺满整个手机屏幕


## 补充
- 一般的设计稿都是w640的，要注意把设计稿缩小一倍成w320进行开发；（出现失真后果）
- 一般只有字体大小设计为 rem ，其他设置继续使用px或者也使用rem；

### 参考文章

[rem是如何实现自适应布局的？（这里提供了使用rem的网站）](http://caibaojian.com/web-app-rem.html)
