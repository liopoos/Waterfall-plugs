# **jQuery搭建简单的瀑布流页面** #
![](https://blog.mayuko.cn/wp-content/uploads/2016/05/%E6%97%A0%E6%A0%87%E9%A2%98-3.jpg)
# 食用方法： #

## **1.加载js** ##

**使用该网格瀑布流布局需要引入jQuery和jaliswall.js文件。**

    <script src="tools/waterfall/js/jquery-2.1.1.min.js" type="text/javascript"></script>
    <script>window.jQuery || document.write('<script src="tools/waterfall/js/jquery-2.1.1.min.js"><\/script>')</script>
    <script type="text/javascript" src="tools/waterfall/js/jaliswall.js"></script>

## 2.添加页面内容 ##

该瀑布流特效使用一个<div>作为包裹容器，使用a元素来包裹图片和它的标题元素。

    <div class="wall">
     <a class="article" >
     <img src="tools/waterfall/img/1.jpg" />
     <h2>text</h2>
     </a>
     <div class="article">
     <img src="tools/waterfall/img/2.jpg" />
     <h2>text</h2>
     </div>
     <div class="article">
     <img src="tools/waterfall/img/3.jpg" />
     <h2>text</h2>
     </div>
     <div class="article">
     <img src="tools/waterfall/img/4.jpg" />
     <h2>text</h2>
     </div>
     <div class="article">
     <img src="tools/waterfall/img/5.jpg" />
     <h2>text</h2>
     </div>
    ···
    <div>

## 3.引入css ##
需要为该瀑布流特效添加下面的一些必要的CSS样式。

    * {
     margin: 0;
     padding: 0;
    }
    
    .article {
     display: block;
     margin: 0 0 30px 0;
     padding: 12px;
     background: white;
     border-radius: 3px;
     box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.05);
     transition: all 220ms;
    }
    .article:hover {
     box-shadow: 0px 2px 3px 1px rgba(0, 0, 0, 0.1);
     transform: translateY(-5px);
     transition: all 220ms;
    }
    .article > img {
     display: block;
     width: 100%;
     margin: 0 0 24px 0;
    }
    .article h2 {
     text-align: center;
     font-size: 14px;
     text-transform: uppercase;
     margin: 0 0 12px 0;
    }
    
    .wall {
     display: block;
     position: relative;
    }
    .wall-column {
     display: block;
     position: relative;
     /*width: 33.333333%;*/
     width: 25%;
     float: left;
     padding: 0 12px;
     box-sizing: border-box;
    }
    @media (max-width: 640px) {
     .wall-column {
     width: 50%;
     }
    }
    @media (max-width: 480px) {
     .wall-column {
     width: auto;
     float: none;
     }
    }
    
    @media screen and ( min-width: 48.9375em ) { /* 782px, mobile WP bar */
     .site-main {
     margin: 0 auto;
     }
     .content-area {
     float: none;
     width: 100%;
     max-width: 1500px;
     margin: 0 auto 3em;
     }
     #infinite-footer .container {
     padding: 0;
     width: 700px !important;
     }
    

其中.wall-column的width属性用于控制每行显示多少列，例如，要想每行显示3列，可以设置为width:33.333333%。

上面的内容在style.css中，另外，需要同时引入normalize.css文件
    
    <link rel="stylesheet" type="text/css" href="tools/waterfall/css/normalize.css" />
    <link rel="stylesheet" type="text/css" href="tools/waterfall/css/styles.css">
 
## 4.启动脚本代码  ##

在页面中启用瀑布流形式的脚本代码
    
    <script type="text/javascript">
     $(function(){
     $('.wall').jaliswall({ item: '.article' });
     });
     </script>