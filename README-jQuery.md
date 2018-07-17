# jQuery总结代码
## 1、正则表达式
一、附加参数<br>
/g  进行全局匹配<br>
/i  不区分大小写<br>
/m  可进行多行匹配<br>

二、具体参数<br>
特殊符号要用转义字符实现：<br>
\ .  \ \  \"  \^  \$<br>

\d  表示匹配0-9中任意“一个”数字，等价于 [0-9]<br>
\D  表示匹配一个非数字字符，等价于 [^0-9]<br>
\w  表示匹配任意一个字母、数字、下划线，等价于 [a-zA-Z0-9_]<br>
\W  表示匹配任意一个非字母、数字、下划线，等价于 [^a-zA-Z0-9_]<br>
.   表示除了换行符的任意字符<br>
\s  表示包括空格、制表符、换页等空白字符的其中任意一个<br>
\S  表示包括非空格、制表符、换页等空白字符的其中任意一个<br>

{n} 前面的表达式重复n次<br>
{n,m} 表达式至少重复n次，最多m次<br>
{n,}  表达式至少重复n次<br>

+  表达式至少出现一次，等价于{1,}<br>
*  表达式不出现或出现任意次，等价于{0,}<br>
?  表达式出现0次或1次，等价于{0,1}<br>

^   表示在字符串开始的地方，但它不匹配任何字符<br>
$   表示在字符串结尾的地方，但它不匹配任何字符<br>

[]  可包含一系列字符，能够匹配其中“一个”字符<br>
[^] 匹配其中字符之外的任意一个字符<br>
```bash
<script>
    function fun1(){
        var v1=document.getElementById("id01").value;
        var reg=/abc/gi;
        # var reg=/a\d\dc/gi;  # ga12cf
        # var reg=/\d{5}/gi;  # 多于5个数字，匹配
        # var reg=/^\d{5}/gi;  # 数字连续五个开头
        # var reg=/^\d{5}$/gi;  # 只能输入5个数字
        # var reg=/^a\d{4}b$/gi;

        var reg=/\s/g;
        # 替换
        var v2=v1.replace(reg,",");
        alert(v2);
    }
</script>
<input type="text" id="id01">
<button onclick="fun1()">确定</button>
```

2、加载<br>
```bash
$(function(){
    alert("hello world!");
});  # 文字->提示->图片

(function() {
    alert("hello world!");
})(jQuery);  # 所有页面元素加载之前执行

$(document).ready(function(){
    alert("hello world!");
});  # $(function(){}）是$(document).ready(function(){}的简写，文档结构加载完毕后就执行（不包含图片等非文字媒体文件）

$(function(){
    alert("hello world!");
});  # $(function(){}）是$(document).ready(function(){}的简写，文档结构加载完毕后就执行（不包含图片等非文字媒体文件）

$(window).load(function() {
    alert("hello world!");
});  # 指页面包含图片等文件在内的所有元素都加载完成后执行

<body>
aaaaaaaaaaaaaaaaaa
<img src="images/1.jpg">
</body>
```

3、原生放大<br>
```bash
# 放大
$(function(){
    $("#id01").animate({width:"400px",height:"400px"},2000);
});
# 原生js
var timer;
var n=0;
var m=100;
function fun1(){
    n=n+5;
    m=m+1;
    var v1=document.getElementById("id01");
    v1.style.width=m+"px";
    v1.style.height=m+"px";
    if(n == 2000){
        clearInterval(timer);
    }
}
timer=setInterval(fun1,5);
<div id="id01">sssssssssssss</div>
```

4、鼠标悬停 放大鼠标离开缩小<br>
```bash
$(function(){
    # 鼠标悬停
    $("#id01").mouseover(function(){
        $(this).animate({width:"400px",height:"400px"},2000);
        # css样式
        $(this).css({"background-color":"blue"});
    });
    # 鼠标离开
    $("#id01").mouseout(function(){
        $(this).animate({width:"100px",height:"100px"},2000);
    });
});
<div id="id01">sssssssssssss</div>
```

5、放大缩小效果<br>
```bash
$(function(){
    $("#id01").click(function(){
        $(this).animate({width:"400px",height:"400px"},2000);
        $("#id02").animate({width:"10px",height:"10px"},2000);
    })
});
<div id="id01">sssssssssssss</div>
<div id="id02"></div>
```


6、多重动画   以及消失  文字变化<br>
```bash
$(function(){
    $("#id01").animate({left:"500px",top:"300px",fontSize:"50px"},1000)
               .animate({left:"100px"},2000)
               .animate({opacity:"0"},1000);
});
<div id="id01">sssssssssssss</div>
```

7、jq选择器<br>
```bash
$(function(){
    $("div").mouseover(function(){
        $(this).css({color:"red"});
        alert($(this).index());  # 获取索引值
    });

    $(".d1").mouseover(function(){
        $(this).css({color:"red"});
    });

    $(".d1 span").mouseover(function(){
        $(this).css({color:"red"});
    });

    $(".d1 span,#id01 span").mouseover(function(){
        $(this).css({color:"red"});
    });

    $(".d1>.s01").mouseover(function(){
        $(this).css({color:"red"});
    });

    $(".d1+div").mouseover(function(){
        $(this).css({color:"red"});
    });

    $(".d1~div").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("span:first").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("span:last").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("span:not").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("div:even").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("div:odd").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("div:eq(2)").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("div:gt(1)").mouseover(function(){
        $(this).css({color:"red"});
    });

    $("div:lt(2)").mouseover(function(){
        $(this).css({color:"red"});
    });
});
<div class="d1">hello
    <span class="s01">bbbb
        <span>gggg</span>
    </span>
    <span class="s02">cccc</span>
</div>
<div id="id01">world
    <span class="s03">aaaa</span>
    <span class="s04">dddd</span>
</div>
<div class="d2">!!!!!
    <span>eeee</span>
    <span>ffff</span>
</div>
```

8、stop() delay()<br>
```bash
# 回调  .stop()选中之后其他停止
# .delay(800)延迟
$(function(){
    $("#d1 div:eq(0)").css({"background":"url('../images/1.jpg')"});
    $("#d1").hover(function(){
        $("#d1 div:eq(0)").stop().animate({width:"60px",height:"60px"},1000)
    },function(){
        $("#d1 div:eq(0)").stop().animate({width:"200px",height:"200px"},1000)
    });
});
<div id="d1">
    <div></div>
    <div>ddddddddddddd</div>
</div>
```

9、find函数定义变量   $v.eq(n)用法<br>
```bash
$(function(){
    $(".img01").hover(function(){
        # $(".img01 .d1 div:eq(0)");
        # $(".img01 .d1 div:eq(1)");
        var $v=$(this).find(".d1 div");
        $v.eq(0).stop().animate({top:"-25px",left:"-25px",width:"250px",height:"250px",opacity: 0},1000);
        $v.eq(1).stop().animate({opacity: 1},1000)
    },function(){
        var $v=$(this).find(".d1 div");
        $v.eq(0).stop().animate({top:"0",left:"0",width:"200px",height:"200px",opacity: 1},1000);
        $v.eq(1).stop().animate({opacity: 0},1000)
    });
});
<div class="img01">
    <div class="d1">
        <div><img src="../images/1.jpg"/></div>
        <div><img src="../images/2.jpg"/></div>
    </div>
</div>
<div class="img01">
    <div class="d1">
        <div><img src="../images/3.jpg"/></div>
        <div><img src="../images/4.jpg"/></div>
    </div>
</div>
```

10、addClass removeClass toggleClass<br>
```bash
 $(function(){
    var i=0;
    var timer;
    function fun1(){
        $(".v_slider .ul_slider").animate({top:-203*i+"px"},2000);
        # 兄弟清除css
        $(".v_slider .num li")
            .eq(i)
            .addClass("aa")
            .siblings()
            .removeClass("aa");
        i++;
        if(i>4){
            i=0;
        }
    }
    timer=setInterval(fun1,2000);

    $(".v_slider .num li").hover(function(){
        # 加载css属性
        # $(this).addClass("aa");
        # 切换 有减无加
        $(this).toggleClass("aa");
    },function(){
        # 移出css属性
        # $(this).removeClass("aa");
        # 切换 有减无加
        $(this).toggleClass("aa");
    });

    $(".v_slider .num li").hover(function(){
        clearInterval(timer);  # 清除定时器
        var m=$(this).index();  # 获取当前元素索引值
        $(".v_slider .ul_slider").animate({top:-203*m+"px"},2000);
        i=m;
    },function(){
        timer=setInterval(fun1,2000);  # 开启定时器
    });
});
<div class="v_slider">
<ul class="ul_slider">
        <li><img src="../images/lx01.jpg"></li>
        <li><img src="../images/lx02.jpg"></li>
        <li><img src="../images/lx03.jpg"></li>
        <li><img src="../images/lx04.jpg"></li>
        <li><img src="../images/lx11.jpg"></li>
    </ul>
    <ul class="num">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
</div>
```

11、蒙板<br>
```bash
<script>
    # jq中添加图片属性  ==>js添加属性
    # $("img").attr("src","../images/1.jpg")

    $(function(){
        # 蒙板隐藏
        $("#mb").hide();

        # 大图数组
        var big_arr=["../images/1.jpg","../images/2.jpg","../images/3.jpg"];
        var word_arr=["aaaaaa","bbbbbbb","ccccccccc"];

        $("#big img").attr("src",big_arr[0]);
        $("#small li").click(function(){
            # alert($(this).index());
            $("#big img").attr("src",big_arr[$(this).index()]);

            # 显示蒙板
            $("#mb").show();
            $("#mb img").attr("src",big_arr[$(this).index()]);
            document.getElementById("word").innerHTML=word_arr[$(this).index()];

        });
        $("#close").click(function(){
            $("#mb").hide();
        });
    });
</script>
<div id="big">
    <img>
</div>
<ul id="small">
    <li><img src="../images/1.jpg"></li>
    <li><img src="../images/2.jpg"></li>
    <li><img src="../images/3.jpg"></li>
</ul>
<div id="mb">
    <img>
    <a href="#" id="close">×</a>
    <p id="word"></p>
</div>
```

12、 等等（不全）<br>
```bash
$(function(){
            # 1、动态创建元素
#            $("#but01").click(function(){
#               var v1=$("<li>aaaa</li>");
#                v1.attr("title","tttttt");
#                $("#ul01").append(v1);
#            });

            # 2、append：向每个匹配的元素内部追加内容。
#             $("p").append("<b>Hello</b>");

            # 3、appendTo：把所有匹配的元素追加到另一个指定的元素元素集合中。p加到div中
#             $("p").appendTo("div");

            # 4、prepend：向每个匹配的元素内部前置内容。
#             $("p").prepend("<b>Hello</b>");

            # 5、把所有匹配的元素前置到另一个、指定的元素元素集合中。
#             $("p").prependTo("#foo");

#             after:在每个匹配的元素之后插入内容。
#             <p>I would like to say: </p>jQuery
#             $("p").after("<b>Hello</b>");
#             <p>I would like to say: </p><b>Hello</b>

#             before:在每个匹配的元素之前插入内容。
#             <p>I would like to say: </p>
#             $("p").before("<b>Hello</b>");
#             [ <b>Hello</b><p>I would like to say: </p> ]

#             insertAfter:把所有匹配的元素插入到另一个、指定的元素元素集合的后面。
#             <p>I would like to say: </p><div id="foo">Hello</div>
#             $("p").insertAfter("#foo");
#             <div id="foo">Hello</div><p>I would like to say: </p>

#             insertBefore:把所有匹配的元素插入到另一个、指定的元素元素集合的前面。
#             <div id="foo">Hello</div><p>I would like to say: </p>
#             $("p").insertBefore("#foo");
#             <p>I would like to say: </p><div id="foo">Hello</div>

        });

# 1
<ul id="ul01"></ul>
<button id="but01">确定</button>

# 2、4
<p>I would like to say:</p>

# 3
<p>I would like to say: </p>
<div></div>
<div></div>

# 5
<p>I would like to say: </p>
<div id="foo"></div>
```

13、tab页 选项卡<br>
```bash
$(function(){
   $("#tab_title li").click(function(){
       $(this).addClass("title").siblings().removeClass("title");
       var i=$(this).index();
       $("#tab_content div").eq(i).show().siblings().hide();
   });
});
<ul id="tab_title">
    <li>tab1</li>
    <li>tab2</li>
    <li>tab3</li>
</ul>
<div id="tab_content">
    <div>tab_content111111</div>
    <div>tab_content222222</div>
    <div>tab_content333333</div>
</div>
```

14、手风琴效果<br>
```bash
$(function(){
    # 可视窗口的宽度随着页面拉大拉小 变化
    # window.onresize=function(){
        # 手风琴效果
        # 获得当前可视窗口的宽度  hide() show() 可以加时间
        var v_width=$(window).width();
        var v_height=$(window).height();
        $(".sfq li:odd").hide().css({"background-color":"green"});
        $(".sfq li").css({"height":v_height});
        $(".sfq li:even").click(function(){
            var m=$(this).index();
            $(".sfq li:odd").hide();
            $(".sfq li").eq(m+1).show(1000).animate({"width":(v_width-280)+"px"},200);
         });
    # }
});
<ul class="sfq">
    <li>1</li>
    <li>111content</li>
    <li>2</li>
    <li>222content</li>
    <li>3</li>
    <li>333content</li>
</ul>
```

15、动态转动 缩放 平移 倾斜<br>
```bash
$(function(){
    //JS
    $(".d01").mouseover(function(){
        $(this).css({"transform":"rotate(60deg) scale(2) translate(50px,150px) skew(60deg)"});
    });
    $(".d01").mouseout(function(){
        $(this).css({"transform":"none"});
    });
});
<style>
/*css3*/
/*rotateX() rotateY() rotateZ()*/
.d01{
    width: 150px;
    height: 150px;
    background: url("../images/1.jpg");
    /*过度*/
    transition: transform 3s;
}
</style>
<div class="d01"></div>
```

16、面试题<br>
```bash
<script>
    # 面试题1
    alert(1 + - + + + - + 1);  # 2
    alert(1 + + 1);  # 2
    alert(1 + - 1);  # 0
    alert(1 + - - + 1);  # 2
    alert(1 - + 1);  # 0

    # 面试题2
    # 加号字符串连接  非空字符串为真 'Value is'+ false
    var val = 'smtg';
    alert('Value is ' + (val === 'smtgpp') ? 'Something' : 'Nothing');  # Something

    # 面试题3
    var END = Math.pow(2, 53);
    var START = END - 100;
    var count = 0;
    for (var i = START; i < END; i++) {
        count++;
    }
    alert(count);
    # 一个知识点:Infinity
    # 在 JS 里, Math.pow(2, 53) == 9007199254740992 是可以表示的最大值. 最大值加一还是最大值. 所以循环不会停.
    # 补充:
    # js中可以表示的最大整数不是2的53次方，而是1.7976931348623157e+308。
    # 2的53次方不是js能表示的最大整数而应该是能正确计算且不失精度的最大整数，可以参见js权威指南。9007199254740992 +1还是 9007199254740992 ，这就是因为精度问题，如果9007199254740992 +11或者 9007199254740992 +111的话，值是会发生改变的，只是这时候计算的结果不是正确的值，就是因为精度丢失的问题。

    # 面试题4
    # match 后为正则 .为匹配全部
    if('http://giffadfadafaf.com/picture.jpg'.match('.gif')){
        'a gif file'  # 输出
    }else{
        'not a gif file'
    }

    # 面试题5
    alert(Date(0));  # Tur Jul 12 2016 16:50:14 GMT+0800(中国标准时间)
    alert(new Date());  # Tur Jul 12 2016 16:50:14 GMT+0800(中国标准时间)
    alert(new Date(0));  # 1970

    # 面试题6 
    var a = new Date("2016-07-12");  # 周一是1   月份减一
    var b = new Date(2016, 07, 12);  # 周五是1   正常月份
    alert(a.getDay());  # 2
    alert(b.getDay());  # 5
    alert(a.getMonth());  # 6
    alert(b.getMonth());  # 7
</script>
```

17、在线客服<br>
```bash
$(function(){
    $(".d01 div:first-child").mouseover(function(){
        $(".d01").stop().animate({right:"0px"},1000)
    });
    $(".d01 div:first-child").mouseout(function(){
        $(".d01").stop().animate({right:"-100px"},1000)
    });
    $(".d01 div:last-child").mouseover(function(){
        $(".d01").stop().animate({right:"0px"},1000)
    });
    $(".d01 div:last-child").mouseout(function(){
        $(".d01").stop().animate({right:"-100px"},1000)
    });
});
<div class="d01">
    <div>
        <div class="d02">在线客服</div>
        <ul>
            <li>
                <a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=389520668&site=qq&menu=yes"><img border="0" src="http://wpa.qq.com/pa?p=2::52" alt="点击这里给我发消息" title="点击这里给我发消息"/></a>
            </li>
            <li>777模板</li>
            <li>777模板</li>
            <li>777模板</li>
        </ul>
    </div>
    <div>></div>
</div>
```

18、表格变化<br>
```bash
<script>
    $(function(){
        # 隔行变色
        $("table tr:odd").hover(function(){
            $(this).addClass("tdhover");
        },function(){
            $(this).removeClass("tdhover");
        })

        # 列变色
        $("table th").hover(function(){
            var i=$(this).index();
            # $("table td").eq(i).addClass("td_hover");
            $("table tr td:nth-child("+(i+1)+")").addClass("td_hover");
        },function(){
            $("table tr").children().removeClass("td_hover");
        });
    });
</script>
<style>
    table{
        font-size: 30px;
        background: yellow;
    }
    table .tdhover{
        background: red;
    }
    table .td_hover{
        background: green;
    }
</style>
```

19、面试题<br>
```bash
# 面试题1
var a = 111111111111111110000;
var b = 1111;
alert(a + b);
# 输出 111111111111111110000

var a = 111111110000;
var b = 1111;
alert(a + b);
# 输出 111111111111

var END = Math.pow(2, 53);
var START = END - 3;
var count = 0;
for (var i = START; i <= END; i++) {
    count++;
    alert(i+"  "+count);
}
# Math.pow(2, 53); 2的53次方不是js能表示的最大整数而是能正确计算且不失精度的最大整数

# 面试题2
var two= 0.2;
var one   = 0.1;
var eight = 0.8;
var six   = 0.6;
if[two - one == one, eight - six == two]

alert(0.1+0.2);  # 0.30000000000004
alert(0.2-0.1);  # 0.1
alert(0.8-0.6);  # 0.20000000000007
alert(0.8-0.2);  # 0.60000000000001
alert(0.8-0.1);  # 0.70000000000001

# 面试题3
function showCase(value) {
    switch(value) {
        case 'A':
            alert('Case A');
            break;
        case 'B':
            alert('Case B');
            break;
        case undefined:
            alert('undefined');
            break;
        default:
            alert('Do not know!');  # 输出
    }
}
showCase(new String('A'));  # object

# 面试题4
function isOdd(num) {
    return num % 2 == 1;
}
function isEven(num) {
    return num % 2 == 0;
}
function isSane(num) {
    return isEven(num) || isOdd(num);
}
var values = [7, 4, '13', -9, Infinity];
var v1=values.map(isSane);
alert(v1);//true,true,true,false,false
alert(isEven(3));

# 面试题5
var a = [0];
if ([0]) {
    alert("ttt");  # 输出
    alert(a == true);  # false
} else {
    alert("wut");
}


# 面试题6
alert([]==[]);  # false
alert([0]==[0]);  # false
alert([10]==[10]);  # false
```

20、按钮事件<br>
```bash
$(function(){
    $("#but01").attr("disabled","disabled");  # 按钮失效

    # 表单获得焦点
    $("#inp01").focus(function(){
        # 取值
        $(this).val("");
    });
    # 表单取消焦点
    $("#inp01").blur(function(){
        var v1=$(this).val();
        if(v1=="" || v1==null){
            alert("用户名不能为空");
            $(this).focus();
        }else{
            $("#but01").removeAttr("disabled","disabled");
        }
    });

    $("#but01").click(function(){
        # 1文本框提取
        var user=$("#inp01").val();
        var pwd=$("#inp02").val();
        $("#result").html();
        $("#result").text("用户名："+user+" 密码："+pwd);

        # 2单选框提取
        # $("input[type='radio']")等价于$(":radio")
        # 得到name值
        alert($(":radio[name='r1']:checked").val());

        # 3复选框提取  i数组下标
        $(":checkbox[name='c1']:checked").each(function(i){
            alert($(this).val()+"  "+i);
        });

    });

    #4全选和反选
    var i=0;
    $("#qx").change(function(){
        i++;
        if(i%2==1){
            $(":checkbox[name='c1']").attr("checked","true");
        }else{
            $(":checkbox[name='c1']").removeAttr("checked","true");
        }
    });
    $("#fx").change(function(){
        $(":checkbox[name='c1']").each(function(){
            $(this).attr("checked",!$(this).attr("checked"));
        });
    });

});
用户名：<input type="text" id="inp01" value="请输入用户名"><br><br>
密码：<input type="password" id="inp02"><br><br>

<input type="radio" name="r1" value="A">A
<input type="radio" name="r1" value="B">B
<input type="radio" name="r1" value="C">C
<input type="radio" name="r1" value="D">D
<br><br>

<input type="checkbox" name="c1" value="A">A
<input type="checkbox" name="c1" value="B">B
<input type="checkbox" name="c1" value="C">C
<input type="checkbox" name="c1" value="D">D
<input type="checkbox" name="c1" value="E">E
<br><br>
<input type="checkbox" id="qx">全选
<input type="checkbox" id="fx">反选


<button id="but01">确定</button>
<div id="result"></div>


# 5自定义下拉列表
$(function(){
    $(".top").click(function(){
        $(".content").css({"opacity":1})
    });
    $(".content").click(function(){
        var a=$(this).text();
        $(".top").text(a);
        $(".content").css({"opacity":0})
    });
});
<div class="top">aaaaa</div>
<div class="content">1111</div>
<div class="content">2222</div>
<div class="content">3333</div>
<div class="content">4444</div>
```

21、jq -- ajax<br>
```bash
用户名：<input type="text" id="uname"><br><br>
密码：<input type="password" id="upwd"><br><br>
<button id="login">登录</button>
<button id="queryall">查询所有</button>
<div id="show"></div>

$(function(){
    # 登录
    $("#login").click(function(){
        var vname=$("#uname").val();
        var vpwd=$("#upwd").val();
        $.ajax({
            type:"GET",
            url:"test16_loginphp.php",
            data:"username="+vname+"&password="+vpwd,
            success:function(msg){
                alert(msg);
            }
        });
    });
    # 查询所有
    $("#queryall").click(function(){
        $.ajax({
            type:"GET",
            url:"test16_cxsy.php",
            success:function(msg){
                var arr=eval(msg);
                $.each(arr,function(i){
                    var str=$("<span>"+arr[i].aname+"</span>");
                    $("#show").append(str);
                });

            }
        })
    })
});

<?php
header("Content-type:text/html;charset=utf-8");
$db_link=mysql_connect("localhost","root","123456") or die("数据库服务器连接失败".mysql.error());
$db=mysql_select_db("db43",$db_link )or die("数据库连接失败".mysql.error());
$v_uname=$_REQUEST["username"];
$v_upwd=$_REQUEST["password"];
$sql="select * from t_test where uname='$v_uname' and pwd='$v_upwd'";
mysql_query("SET NAMES UTF8");
$result=mysql_query($sql,$db_link);
$v_result=mysql_fetch_row($result);
if(!empty($v_result)){
echo "成功";
}else{
echo "失败";
}
?>

<?php
header("Content-type:text/html;charset=utf-8");
$db_link=mysql_connect("localhost","root","123456") or die("数据库服务器连接失败".mysql.error());
$db=mysql_select_db("db43",$db_link )or die("数据库连接失败".mysql.error());
$sql="select * from t_test";
mysql_query("SET NAMES UTF8");
$result=mysql_query($sql,$db_link);
$arr2=array();
while($v1=mysql_fetch_array($result)){
$arr1=array('aid'=>$v1['uid'],'aname'=>$v1['uname'],'apwd'=>$v1['pwd']);
array_push ($arr2,$arr1);
}
echo json_encode($arr2);
?>
```

22、滚轴事件<br>
```bash
$(function(){
    $("#d01 div:eq(1)").click(function(){
        var v1=$("#mk2").offset().top;  # 距离顶部距离
        $("html,body").animate({scrollTop:v1},1000);  # 滚动事件
    });

    # 滚轴事件
    window.onscroll=function(){
        if(document.body.scrollTop>800){
            $("#mk2").animate({width:"300px",height:"200px"},1000);
        }
    }
});
<div id="d01">
    <div>模块1</div>
    <div>模块2</div>
    <div>模块3</div>
    <div>模块4</div>
</div>
<div id="mk1"></div>
<div id="mk2"></div>
<div id="mk3"></div>
<div id="mk4"></div>
```

23、封装<br>
```bash
jQuery.extend({
    jqzoom:function(simg,bimg){
        simg.hover(function(){
            # 元素距离浏览器左上的距离
            var imgleft=$(this).get(0).offsetLeft;  # 8
            var imgtop=$(this).get(0).offsetTop;  # 8
            # 获取元素的宽高
            var imgwidth=$(this).get(0).offsetWidth;  # 300
            var imgheight=$(this).get(0).offsetHeight;  # 398

            # 设置大图的位置
            bimg.css({left:imgleft+imgwidth+10,top:imgtop,display:"block"});
            # 获取大图的宽高
            var b_imgwidth=bimg.get(0).offsetWidth;
            var b_imgheight=bimg.get(0).offsetHeight;
            # 大小图的缩放比
            var scale_x=b_imgwidth/imgwidth;
            var scale_y=b_imgheight/imgheight;
            var v1=$("<div style='width: 50px;height:50px; background:black;opacity:0.2;position:absolute;'></div>");
            $("body").append(v1);
            $(this).mousemove(function(e){
                v1.css({left:e.pageX,top:e.pageY});
                var b_x=(e.pageX-imgleft)*scale_x;
                var b_y=(e.pageY-imgtop)*scale_y;

                bimg.get(0).scrollLeft=b_x;
                bimg.get(0).scrollTop=b_y;
            });
        },function(){
            bimg.css({display:"none"});
        });
    }
});

<script src="../js/jquery-1.8.2.js"></script>
<script src="../js/jqzoom-1.5.js"></script>
<script>
    # 放大镜效果
    $(function(){
        # 插件封装
        Query.jqzoom($(".smallimg"),$(".bigimg"));
    })
</script>
<style>
    .bigimg{
         width: 300px;
         height: 300px;
         border: 1px solid red;
         overflow: hidden;
         position: absolute;
         z-index: -1;
         display: none;
     }
</style>
<div id="show"></div>
<img src="../images/majesty_.jpg" class="smallimg" style="position: absolute;top:100px;left: 100px;">
<div class="bigimg"><img src="../images/majesty.jpg"></div>
```