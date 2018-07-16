# CSS总结代码
## 1.css引用方式
①内联式
```bash
<style>
    div{
        color:red;
    }
</style>
```
②行内式
```bash
<div style="color:green">
```
③外联式
```bash
<link href="css/css1.css" rel="stylesheet">
```
④@import方式
```bash
<style>
    @import url("css/css1.css");
</style>
```

## 2.路径
```bash
  相对路径：<link href="css/css1.css" rel="stylesheet">
          ../返回上一级目录
  绝对路径：<link href="E:/web Test-43/css/css1.css" rel="stylesheet">
```

## 3.表格
colspan 列合并  rowspan 行合并  cellspacing 单元格间距
```bash
<table cellspacing="0"></table>
<tr>
    <td colspan="2">a1</td> # 行
</tr>
<tr>
    <td rowspan="2">b1</td> # 列
</tr>
```
①固定表格布局
```bash
table{  
    table-layout:fixed;
}
```
②如何让表格边框为1px<br>
方法1：用边框的上下左右调整<br>
方法2：border-collapse:collapse 表格边框合并为单一边框，默认：separate<br>
```bash
<style>
    table{
        border-collapse:collapse;
    }
</style>
```
③列间隔 行间隔:border-spacing
```bash
border-spacing:10px 5px;
```
④文字水平对齐 text-align -- left center right
```bash
table{  text-align:center;  }
```
⑤空单元格 empty-cells:hide隐藏空单元格  show显示空单元格
```bash
table{  empty-cells:hide;  }
```
⑥表格居中
```bash
table{  margin: auto;  }
```
⑦垂直对齐 vertical-align -- top middle bottom
```bash
table tr td{  
    vertical-align:top;  
}
```

## 4.圆角问题
```bash
border-bottom-left-radius: ;
border-bottom-right-radius: ;
border-top-left-radius: ;
border-top-right-radius: ;
border-radius: 10px 0px 0px 10px;
```

## 5.伪类：hover--鼠标悬停
```bash
# 行悬停
table tr:hover{
    background-color: blue;
}
# 每个表格悬停
table tr td:hover{
    background-color: blue;
}
# 表头悬停
table tr th:hover{
    background-color:red;
}
```

## 6.表头
```bash
<tr>
    <th>t1</th>
    <th>t2</th>
    <th>t3</th>
</tr>
```

## 7.表格当中添加表格
```bash
<table class="t1">
    <tr><td>
            <table class="t2">
                <tr>
                    <td></td>
                </tr>
            </table>
    </td></tr>
</table>
```

## 8.透明度：
```bash
.uname:hover{
    background-color: red;
    opacity: 0.2;
}
```

## 9.焦点：
```bash
.pwd:focus{
    background-color: green;
    width: 300px;
}
```

## 10.表单及表单控件
action:提交地址<br>
action=""提交当前页<br>
method:提交方式<br>
get-默认 post-更加安全<br>
```bash
<form action="" method="post"></form>
# （1）文本输入控件
<input type="text" name="uname" value="uname">
# （2）密码输入控件
<input type="password" name="pwd" value="pwd">
# （3）按钮控件
<button>登录</button>
<input type="button" value="登录按钮" name="but01">
# （4）提交按钮 整体刷新      --ajax 局部刷新
<input type="submit" value="登录" name="but02">
# （5）重置按钮
<input type="reset" value="重置" name="but03">
# （6）单选控件 默认选中属性：checked --value="不同" name="相同"
<input type="radio" value="nan" name="r1">男
<input type="radio" value="nv" name="r1">女
# （7）复选控件 默认选中属性：checked --value="不同" name="相同"
爱好：<input type="checkbox" value="xx" name="c1" >学习
      <input type="checkbox" value="yx" name="c1" >游戏
      <input type="checkbox" value="sj" name="c1" >睡觉
# （8）下拉列表   multiple:多选  selected:默认
城市：<select multiple>
         <option class="p01" selected>北京</option>
         <option class="p01">上海</option>
         <option class="p01">哈尔滨</option>
      </select>
# （9）多行文本控件
简介：<textarea rows="20" cols="30"></textarea>
# （10）上传文件控件
上传文件：<input type="file">
# （11）隐藏控件
<input type="hidden">
# （12）html5表单控件
<form action="">
    # email控件
    <input type="email">
    # 网址
    <input type="url">
    # 电话
    <input type="tel">
    # 日期
    <input type="date" value="2016-01-01">
    <input type="time">
    <input type="datetime-local">
    <input type="month">
    <input type="week">
    <input type="datetime">不好使
    # 数值控件
    <input type="number">
    # 范围控件
    <input type="range" value="25" min="0" max="100" step="1">
    # 颜色控件
    <input type="color">
    # 搜索控件
    <input type="search">
</form>
```

## 11.外边距
margin-left margin-right margin-top margin-bottom<br>
1）元素（盒子）垂直排列，margin上下合并，取最大值。<br>
2）元素（盒子）水平排列，margin左右累加<br>

margin允许有负值<br>
margin:20px;       四边<br>
margin:20px 40px;     上下 左右<br>
margin:20px 180px 200px;   上 左右 下<br>
margin:20px 700px 80px 100px; 上 右 下 左<br>

## 12.内边距  
padding-left padding-right padding-top padding-bottom
padding 不允许负值
padding:50px;   四边
padding:30px 40px;    上下 左右
padding:20px 20px 40px;   上 左右 下
padding:20px 40px 20px 40px;    上 右 下 左

## 13.字体加粗
```bash
font-weight: border or 100~900;
简写：
font:italic bolder 20px arial ;   # 简写：20px arial 必写 顺序不能颠倒
```

## 14.背景简写
```bash
background: red url("") no-repeat fixed top;  # 简写 顺序可变
```

## 15.字体单位
px 像素<br>
cm 厘米<br>
pt 磅<br>
in 英寸<br>
百分比  对默认字体缩放（不同浏览器默认字体不同，默认最小字体也不同）<br>
em 字号倍数，相对于默认字体（父元素或浏览器）<br>
//pt cm in 200%原基础上放大 50%原基础上缩小 em成倍数放大//<br>

## 16.label固定大小
```bash
label{
    width: 100px;
    border: 1px solid red;
    display: inline-block;
}
<label>email:</label>
<label>user name:</label>
```

## 17.表示label标签要绑定的HTML元素,你点击这个标签的时候,所绑定的元素将获取焦点
```bash
<label for="inp01">email:</label><input type="text" id="inp01">
```

## 18.颜色的表示方式
1）颜色名 如red<br>
color: red;<br>
2）rgb()  范围0-255 red green blue  黑：rgb(0,0,0) 白：rgb(255,255,255)<br>
color: rgb(255,0,0)<br>
3）十六进制表示，如#fea230<br>
color: #ff0000;<br>
4）十六进制简写：#223344简写为 #234<br>
color: #234;<br>

## 19.背景图片定位
```bash
background-position:top right;
简写：
background:url("images/1.jpg") no-repeat top right;
```

## 20.CSS3 阴影
box-shadow:（inset内阴影，省略为外阴影）水平偏移量，垂直偏移量，阴影模糊度，阴影大小，阴影颜色
```bash
box-shadow: 10px 10px 10px 10px black;         # 外阴影
box-shadow:inset 10px 10px 10px 10px black;    # 内阴影
```

## 21.伪类：被选中（被激活）
```bash
.d01:active{
  background: blue;
}
```

## 22.先隐藏，鼠标悬浮时显示
隐藏的模块必须被包含在悬停的模块里
```bash
.d02{
    display: none;   # 隐藏
}
.d01:hover .d02{
    display: block;  # 显示
}
<div class="d01"> <div class="d02"></div></div>
```

## 23.行高
```bash
line-height:10px;  # 行高，与height所设值相同时，文字垂直居中
```

## 24.元素
块级元素：与同级元素竖直排列，且左右撑满，如：div  ul  li  p  dd  dt  dl<br>

行级元素：与同级元素横向排列，且内容自适应，不会左右撑满，如：span  a  img  input<br>
span a：宽高不能改变<br>
img input：宽高能改变（特例）<br>

标准流static：css规定的默认的块级元素与行级元素的排列方式<br>
```bash
display: block;  # 将当前元素转换为块级元素
display: inline;  # 将当前元素转换为行级元素
display: inline-block;  # 行级块元素
```

## 25.display 与 visibility区别
display 不占用空间（后元素补位）<br>
visibility 占用空间（保留原元素空间）<br>
```bash
display: none; # 隐藏
display: block;  # 显示
visibility: hidden;  # 隐藏
visibility: visible;  # 显示
```

## 26.浮动    
float:left;<br>
float:right;<br>
注意：<br>
  1)浮动的元素会脱离标准流<br>
  2)如前面有浮动元素，会依次排在后面<br>
  3)浮动是以标准流所在位置为起始点<br>
  4)同高度元素横向排满后，会被“挤”到下面<br>
  5)不同高度元素横向排满后，挤下后会被其他元素“卡”住<br>
  6)清除浮动：clear:both/left/right;<br>
  7)一个div的范围是由它里面的标准流决定的，与里面浮动的内容无关<br>

## 27.绝对定位
position: absolute;  // left right top bottom<br>
注意：<br>
  1)对定位脱离标准流<br>
  2)绝对定位的元素是以它最近的一个已经定位的祖先元素为基准进行偏移<br>
    如果没有已经定位的祖先元素，则会以浏览器窗口为基准进行偏移<br>
  3)多个元素绝对定位，后面定位的元素的层级会高于前面（覆盖之前的元素）<br>
  4)z-index 设定层级<br>

## 28.相对定位
position: relative;  // left right top bottom<br>
注意：<br>
  1)相对定位不脱离标准流<br>
  2)相对定位元素会相对于它原来的位置进行偏移，不受父元素影响<br>
     //相对定位、绝对定位允许负值<br>
     //相对定位、绝对定位对浮动元素依然有效<br>

## 29.固定定位
position: fixed;  // left right top bottom<br>
注意：<br>
   1)固定定位脱离标准流（只有相对定位不脱离标准流）<br>
   2)固定定位元素是以浏览器窗口或其他显示设备窗口为基准进行偏移<br>
   3)固定定位对浮动元素依然有效<br>

## 30.标准流
position:static; 恢复标准流

## 31.选项卡特效
```bash
<style>
.tab1_content{
    display: none;
}
.tab1:hover .tab1_content{
    display: block;
}
<style>
<div class="tab1">
    tab1
    <div class="tab1_content">11111111111</div>
</div>
```

## 32.列表
```bash
# 列表类型:
list-style-type: circle;  # 空心
list-style-type: disc;  # 实心
list-style-type: square;  # 实心正方形
list-style-type: decimal;  # 数字
list-style-type: decimal-leading-zero；  # 零开头的数字标记
list-style-type: lower-roman;  # 小写罗马
list-style-type: upper-roman;  # 大写罗马

# 列表缩进
list-style-position: inside;

# 列表图片
list-style-image: url("images/1.jpg");

# 简写 顺序不能改变
list-style:circle inside url("images/1.jpg");

# 取消样式
list-style: none;
```
```bash
# 无序列表
<ul>
    <li>a111111111</li>
    <li>a222222222</li>
    <li>a333333333</li>
</ul>

# 有序列表
<ol>
    <li>b111111111</li>
    <li>b222222222</li>
    <li>b333333333</li>
</ol>

# 定义列表
<dl>
    <dt>计算机图书</dt>
        <dd>css计算</dd>
        <dd>java应用</dd>
    <dt>幼儿图书</dt>
        <dd>365故事</dd>
        <dd>唐诗300</dd>
</dl>
```

## 33.盒子模型
一.模式<br>
标准模式（严格模式strictmode）:浏览器按w3c标准解析执行代码<br>
怪异模式（兼容模式quirkmode）:使用浏览器自己的方式解析执行代码，由于不同浏览器解析执行的方式不同，所以称之为怪异模式<br>

二.如何检测当前执行模式<br>
alert(window.top.document.compatMode);<br>
输出：<br>
css1compat  标准模式<br>
backcompat  怪异模式 (ie盒子模型：实际宽度=width+margin)？<br>

三.标准模式与怪异模式的区别<br>
标准模式：实际宽度=width+border+padding+margin<br>
怪异模式：实际宽度=width+border+margin<br>
    注意：ie6\ie7\ie8在怪异模式下会以此方式显示，其他高级浏览器在怪异模式下依然以标准模式显示，实际宽度=width+border+margin<br>

四.如何区别？<br>
  1.html5：有<!DOCTYPE html>表示为 标准模式<br>
  2.html4：<br>
  (1)<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN  http://www.w3.org/TR/html4/loose.dtd"><br>
  (2)<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN http://www.w3.org/TR/html4/strict.dtd"><br>
  (3)<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN http://www.w3.org/TR/html4/frameset.dtd"><br>

五.边框<br>
border：占用空间<br>
outline:不占用空间<br>
CSS框模型（Box Model）规定了元素框处理元素 内容、内边框、边框、外边框 的方式<br>


## 34.html框架   <!--过时-->
```bash
<frameset cols="20%,80%"> # 列
    <frame>
</frameset>

<frameset rows="20%,80%"> # 行
    <frame>
</frameset>
```
<frame>定义name 使超链接在定义mane的另一个模块中打开

## 35.内联框架
```bash
<a href="images/2.jpg" target="if1name">图片1</a>
<a href="test15.html" target="if1name">网页2</a>
# 内联框架
<iframe src="images/1.jpg" class="if1" name="if1name"></iframe>
```
两个超链接点击后在名为if1name的内联框架中显示

## 36.固定宽度布局
```bash
    <style>
        # 1)浮动法
        .header,.footer,.container{
            margin:0 auto;
        }
        .header,.footer{
            width: 400px;
            height: 50px;
            border: 1px solid #ff0000;
            float: left;
        }
        .container{
            width: 400px;
            height: 250px;
        }
        .content{
            width: 298px;
            height: 248px;
            border: 1px solid #ff0000;
            float: left;
        }
        .side {
            width: 98px;
            height: 248px;
            border: 1px solid #ff0000;
            float: right;
        }

        # 2)定位法
        .header,.footer,.container{
            margin:0 auto;
        }
        .header,.footer,.container{
            width: 400px;
            height: 50px;
            border: 1px solid #ff0000;
            position: relative;
            top:50px;
        }
        .container{
            width: 400px;
            height: 250px;
            position: relative;
            top:50px;
        }
        .content{
            width: 298px;
            height: 248px;
            border: 1px solid #ff0000;
            position: absolute;
            top:0px;
            left:0px;
        }
        .side {
            width: 100px;
            height: 248px;
            border: 1px solid #ff0000;
            position: absolute;
            top:0px;
            left:300px;
        }

        # 3)display法（table法）
        .header,.footer,.container{
            margin:0 auto;
        }
        .header,.footer{
            width: 400px;
            height: 50px;
            border: 1px solid #ff0000;
        }
        .container{
            width: 400px;
            height: 250px;
            border: 1px solid #ff0000;
            display: table;
        }
        .content{
            border: 1px solid #ff0000;
            display: table-cell;
        }
        .side {
            border: 1px solid #ff0000;
            display: table-cell;
        }
    </style>
</head>
<body>
<div class="header"></div>

<div class="container">
    <div class="content"></div>
    <div class="side"></div>
</div>

<div class="footer"></div>
</body>
</html>
```

## 37.变宽变高布局
```bash
# 比例法  宽度百分比
.header,.footer{
    width: 80%;
    height: 100px;
    border: 1px solid #000000;
    margin: 0 auto;
}

# 高度自适应布局
.content{
    width: 80%;
    margin: 0 auto;
    border: 1px solid #000000;
    float: left;
    # 最小高度
    min-height: 300px;
    # 最大高度
    max-height: 500px;
}
```

## 38.变宽布局
```bash
# 单侧变宽布局
# 定位法  --适合高度等高的元素
.header,.footer{
    width: 80%;
    height: 100px;
    border: 1px solid #000000;
    margin: 0 auto;
}
.container{
    width: 80%;
    height: 400px;
    margin: 0 auto;
    position: relative; # 相对定位

}
.content{
    width: 50%;
    height: 400px;
    border: 1px solid #000000;
    margin: 0 300px 0 0;
}
.side{
    width: 300px;
    height: 600px;
    border: 1px solid #000000;
    position: absolute;  # 绝对定位
    top:0;
    right: 0;
}

# 高度不一致---浮动法
.content_wrap{
    width: 100%;
    height: 400px;
    float: left;
    margin-left: -300px;
}
.content{
    height: 400px;
    border: 1px solid #008000;
    margin-left: 300px;
}
.side{
    width: 296px;
    height: 450px;
    border: 1px solid #000000;
    float: right;
}
<div class="content_wrap">
    <div class="content"></div>
</div>
<div class="side"></div>
```

## 39.PS
图片格式：<br>
1）.JPG：有损压缩，压缩方式是去除冗余的图像和彩色数据（不支持透明）<br>
2）.bmp：无压缩格式，比较大（支持透明）<br>
3）.GIF：可以存储背景透明格式，可做多帧动画，但能呈现的色彩为256色，适合较少颜色的图片<br>
4）.png：吸取jpg/gif格式优点，压缩率高，不失真，可透明<br>

快捷键：<br>
1)ctrl+t 变形<br>
2)ctrl+ + 放大<br>
3)ctrl+ - 缩小<br>
4)空格 小手移动<br>
5)ctrl+e 合并图层<br>

## 40.
css 切图：<br>
css sprite也叫css精灵，css雪碧：是一种css图像合并技术，是将小图标合成大图，再利用背景定位技术，显示需要显示的图片部分<br>
background: url("../images/menu_sprite.jpg") no-repeat 0 -30px;<br>

背景图片横向平铺：
```bash
background: url("../images/k3.jpg") repeat-x;
```

## 41.浏览器兼容性：
css Hack（黑客）：不同浏览器对css的解析结果不同，会导致相同的css输出页面效果不同，此时需要csshack技术来解决浏览器局部兼容性问题<br>
css Hack 原理：利用书写顺序和不同浏览器对一些特定书写方法的解析方式不同，而达到不同的效果<br>
```bash
_background    ie6
*background    ie6/ie7
background:#008000!important;  #ie7及其以上版本 !important优先级最高
background: #800080\0;         #ie8及其以上版本
background: #000000\9;         #ie6--ie10
>background-color: #428037;    #ie7 8?
*+background-color: #802611;   #ie7?

/*chrome safari opera*/
@media all and(-webkit-min-device-pixel-ratio:0){
    .d1{
        background: #008000;
        color: #0000ff;
    }
}
/*firefox--ff*/
@-moz-document url-prefix(){
    .d1{
    background: #ff55b3;
    color: #b20000;
    }
}
```
ie条件注释（ie的if条件Hack）<br>
（1）ie10及以上不支持<br>
（2）ie专属，其他浏览器当作普通注释完全忽略<br>
1.if ie 6      等于ie6<br>
2.<br>
[if lt ie 7]      小于ie7       lt----less than<br>
[if lte ie 7]     小于等于ie7   lte---less than equal<br>
[if gt ie 7]      大于ie7       gt---greater than<br>
[if gte ie 7]     大于等于ie7   gte---greater than equal<br>

问题：<br>
1）不同浏览器默认的外边距不一致问题<br>
解决：<br>
```bash
body{
    # css重置（复位）
    margin: 0;
    padding: 0;
}
```

2）图片超链接有边框（ie10及以下）<br>
解决：<br>
```bash
a img{
    border: 0\9;  # border:none
}
```

3）ie6\7浮动问题<br>
解决：<br>
```bash
（1）*position:absolute;
     *left: 0px;
     *top:0;
     *z-index:-1;
（2）clear:both;  # 统一格式
```

4）ie6  3像素bug问题<br>
一个元素浮动，另一个元素不浮动，中间会产生3px空隙<br>
解决：<br>
```bash
# （1）_margin-right:-3px;
# （2）另一个元素也浮动
```

5）letter-spacing兼容性问题<br>
解决：<br>
```bash
*margin-right: 4px;
```

6）ie6 伪类问题<br>
首字符设置样式<br>
```bash
.d2:first-letter {
    color: #ff0000;
}
```
ie6在处理伪类时，如伪类名称中包含“-”，则伪类名后必须跟一个“空格”，否则无效<br>

7）ie6 1光标高度问题<br>
解决：<br>
```bash
height: 1px;
_overflow: hidden;  # 溢出:隐藏 overflow:scroll 滚动条
```

8）透明度问题<br>
```bash
opacity: 0.5;   # 高级浏览器支持   0-1
filter:alpha(opacity=50);  # 针对ie低版本  0-100
```

9）ie6不支持png图片格式<br>
background:url("images/a1.png");<br>
解决：<br>
```bash
1._background:url("images/a1.gif");
2._background:none;
_filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(sizingMethod=crop,src='images/a1.png');   # 滤镜
```

10）ie6 不支持最小高度 min-height max-height<br>
解决：<br>
最小高度：<br>
min-height: 300px;<br>
_height: 300px;<br>
最大高度：<br>
max-height: 500px;<br>
_height: 500px;<br>
overflow: hidden;<br>

## 42.首字符设置样式
```bash
.d2:first-letter {
    color: #ff0000;
}
```

## 43.选择器：
一、基本选择器<br>
1、标签（元素）选择器<br>
```bash
div{
    color:red;
}
```
2、类选择器：由class定义<br>
```bash
.d1{
    color:red;
}
```
（1）允许重名<br>
（2）允许组合 class="d1 d2 d3"<br>
3、id选择器：由id定义，#引用<br>
```bash
#id01{
    color: #008000;
}
```
（1）不允许重名,名字唯一（高级浏览器容错，可显示）<br>
（2）id主要用于脚本中<br>

二、复合选择器<br>
1、并集选择器：风格完全或部分相同，可用并集选择器声明，多个选择器间，用“，”分开，例：.d1,#id01{}<br>
2、后代（层级）选择器：外层标记在前，内侧标记在后，例：.d1 span{}<br>
3、交集选择器：第一个必须是标签选择器，第二个必须是类或id选择器，选择器之间必须连续书写<br>
```bash
div.d1{
    color: #ff0000;
}
```
4、E>F:子元素选择器，匹配所有E元素的第一层子元素F<br>
5、E+F：毗邻选择器，匹配所有紧随E元素之后的同级元素F（只对下面的元素有效）<br>

三、属性选择器<br>
1、E[attr]：匹配所有具有attr属性的E元素<br>
多个属性<br>
```bash
div[title][class]{
    color: #ff0000;
}
```
2、E[attr=val]：匹配所有attr属性等于val的E元素，/*div[class="d1"] 等价于 div.d1*/<br>
3、E[attr~=val]：匹配所有attr属性具有多个空格分隔的值，其中一个值等于val的E元素<br>
```bash
div[title~='bb']{
      color: #ff0000;
 }
<div title="aa bb" class="d1 d2 d3">hello11_11111</div>
<div title="cc" class="d2">hello11_22222</div>
<div title="bb ss">hello11_33333</div>
```
4、E[attr|=val]：匹配所有attr属性具有多个连字号（中划线）分隔的值，其中一个值以val开头的E元素<br>
```bash
div[title|='aa']{
     color:#008000;
}
div title="aa-bb" class="d1 d2 d3">hello11_11111</div>
div title="cc" class="d2">hello11_22222</div>
div title="aa-ss">hello11_33333</div>
```
四、伪类<br>
:focus 焦点<br>
:hover 鼠标悬停<br>
:active 被激活（被选中）<br>
:link 未被访问的链接样式<br>
:visited 被访问过的链接样式<br>
:empty 当元素为空时显示的样式<br>
:first-child<br>
注意：<br>
1、:hover要在:visited之后（部分浏览器hover在visited之前也好用）<br>
2、:active必须在:hover之后，顺序：link>visited>hover>active<br>

## 44.选择器的优先级
1)!important 优先级最高（ie7及以上）<br>
2)行内优先级高于外联和内联<br>
  如果只有外联与内联，则与他们的排列顺序有关<br>
  即采用“最近优先”原则<br>
3)行内 > id > class > 标签<br>
4)class="d3 d2 d1" 与class中的顺序无关，与在css中定义的顺序有关，最近优先原则<br>

css权重<br>
______________a（行内）______b（id）______c (类、伪类、属性)______d（标签）<br>
_______img_____0______________0______________0__________________1<br>
_____a img_____0______________0______________0__________________2<br>
 a img:hover___0______________0______________1__________________2<br>
 #img:hover____0______________1______________1__________________0<br>
 a[title][class="d1"] img：0022<br>
 a[title] img.d1：0022<br>
 a[title][href] img#img01:hover：0132<br>
 a#a01 img[src][title][class]:active：0142<br>

## 45.小技巧：
一、display: inline  block  inline-block  table  table-cel  none  run-in<br>
run-in:根据上下文作为内联或块级元素显示<br>
1)如果 设置display: run-in;的元素 后面是块级元素 则该元素（设置display: run-in;的元素）<br>
会变成inline属性（行级元素） 且它的内容会嵌入到block块级元素中<br>
2)如果 设置display: run-in;的元素 后面不是块级元素 则该元素（设置display: run-in;的元素）<br>
维持本身block属性<br>

二、word-wrap white-space word-beak text-overflow<br>
1)word-wrap 属性允许长单词或 URL 地址换行到下一行。(内容在边界内换行，针对连续书写的字母)<br>
值：<br>
normal   只在允许的断字点换行。<br>
break-word 在长单词或 URL 地址内部进行换行。<br>
2)white-space 属性设置如何处理元素内的空白。（只在一行内显示）<br>
值：<br>
normal   默认。空白会被浏览器忽略。<br>
pre    空白会被浏览器保留。其行为方式类似 HTML 中的 < pre > 标签。<br>
nowrap 文本不会换行，文本会在在同一行上继续，直到遇到 < br > 标签为止。<br>
pre-wrap   保留空白符序列，但是正常地进行换行。<br>
pre-line   合并空白符序列，但是保留换行符。<br>
inherit    规定应该从父元素继承 white-space 属性的值。<br>
3)word-break 属性规定自动换行的处理方法。（处理单词折行）<br>
值：<br>
normal   使用浏览器默认的换行规则。<br>
break-all  允许在单词内换行。（强制换行）<br>
keep-all   只能在半角空格或连字符处换行。<br>
4)text-overflow 属性规定当文本溢出包含元素时发生的事情。（css3的文本属性，与overflow:hidden一起用）<br>
值：<br>
clip 修剪文本。<br>
ellipsis   显示省略符号来代表被修剪的文本。（超出部分显示省略号）<br>
string 使用给定的字符串来代表被修剪的文本。<br>

三、伪类<br>
:before<br>
:after<br>
```bash
.d1:before,.d1:after{
    position: absolute;
}
.d1:hover:before{
    content: "\5B";
    left: 0px;
}
.d1:hover:after{
    content: "\5D";
}
#悬停出现方括号
```

四、元素分组
```bash
<fieldset>
    <legend>用户登录</legend>
    <label for="v1">用户名：</label><input type="text" id="v1"><br><br>
    <label for="v2">密码：</label><input type="password" id="v2">
</fieldset>
```

五、热点    rect矩形   circle圆形  poly不规则图形
```bash
<img src="images/1.jpg" usemap="#map1">
<map name="map1">
   <area shape="rect" coords="1,2,100,50" href="test24.html"> #左 上 宽 高
   <area shape="circle" coords="100,100,30" href="test24.html"> #左 上 半径
   <area shape="poly" coords="102,204,304,50,200,299" href="test24.html"> #两个两个 第一点坐标 第二点坐标 第三点坐标
</map>
```

六、水平居中
1)文本居中 text-align:center<br>

2)inline-block;方式实现<br>
```bash
<div class="d1">
   <div class="d2">hello</div>
</div>
.d1{
    text-align: center;
}
.d2{
    width: 200px;
    height: 100px;
    border: 1px solid #000000;
    display: inline-block;
    *display: inline;
}
```

3)margin:0 auto;<br>

4)定位实现--宽度固定 水平居中<br>
```bash
.d1{
    text-align: center;
}
.d2{
    width: 200px;
    height: 100px;
    border: 1px solid #000000;
    position: absolute;
    left: 50%;
    margin-left: -100px;
}
```

5)定位实现--宽度不固定 水平居中<br>
```bash
<div class="d0">
   <div class="d1">
       <div class="d2">ddddddddddddddddddd</div>
   </div>
</div>
.d0{
    border: 1px solid red;
    float: left ;
    width: 100%;
    position: relative ;
}
.d1{
    border: 1px solid blue ;
    float: left ;
    position: relative ;
    left: 50%;
    text-align: center ;
}
.d2 {
    border: 1px solid green ;
    float: left ;
    position: relative ;
    right: 50%;
}
```

6)css3实现水平居中 flex<br>
```bash
<div class="d0">
    <div class="d1">ddddddddddddddddddd</div>
</div>
.d0{
    border: 1px solid green ;
    display: -webkit-box;
    -webkit-box-orient: horizontal;
    -webkit-box-pack: center;
}
.d1{
    border: 1px solid red;
    float: left;
}
```

7)css3 fit-content<br>
```bash
<div class="d0">
    <div class="d1">ddddddddddddddddddd</div>
</div>
.d0{
    border: 1px solid green ;
    width: -webkit-fit-content;
    margin-left: auto;
    margin-right: auto;
}
.d1{
    border: 1px solid red;
    float: left;
}
```

## 46.垂直居中
1)行高  --单行<br>
height: 100px;<br>
line-height: 100px;<br>
2)padding 实现  --单行<br>
padding-top: 40px;<br>
padding-bottom: 40px;<br>
3)display 表格发（table-cell） --多行<br>
display: table-cell;<br>
vertical-align: middle;<br>
4)定位法  --高度定位<br>
position: absolute;<br>
top:50%;<br>
margin-top: -50px;<br>
5)css3-- transform--未知高度<br>
position: absolute;<br>
top:50%;<br>
/*利用transform将元素的中心与父容器的中心融合*/<br>
transform:translateY(-50%);<br>
6)css3-- flex<br>
display: flex;<br>
flex-direction:column;<br>
justify-content: center;<br>

## 47.水平垂直居中
1)宽高固定--定位法<br>
position: absolute;<br>
top:50%;<br>
left:50%;<br>
margin: -150px 0 0 -100px;<br>
2)宽高不固定--translate平移<br>
position: absolute;<br>
top:50%;<br>
left:50%;<br>
transform: translate(-50%,-50%);<br>
3)css3-- flex（宽高固定）--内容水平垂直居中<br>
display: flex;<br>
justify-content: center;<br>
align-items: center;<br>

## 48.布局头尾固定，中间高度自适应
```bash
<style>
    body{
        margin: 0;
        padding: 0
    }
    .head,.footer{
        width: 100%;
        height: 100px;
        border: 5px solid #ff0000;
    }
    .head{
        position: absolute;
        top:0;
     }
    .footer{
        position: absolute;
        bottom:0;
    }
    .content{
        width: 100%;
        border: 5px solid #008000;
        position: absolute;
        top:100px;
        bottom:100px;
        overflow: auto;
    }
</style>
<div class="head"></div>
<div class="content">
    abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>
    abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>abcdefghigk<br>
</div>
<div class="footer"></div>
```
