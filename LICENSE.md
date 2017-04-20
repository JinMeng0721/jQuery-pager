echo "# jQuery-pager" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/JinMeng0721/jQuery-pager.git
git push -u origin master
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../jquery-3.1.1.js"></script>
    <link rel="stylesheet" href="reset.css">
    <style>

        .box{
            width: 500px;
            margin: 0 auto;
            overflow: hidden;
            background: #d1d1d1;
            padding: 50px;
            margin-top: 50px;
        }
        .contentAll{
            width: 8000px;
            overflow: hidden;

        }
        .content{
            width: 500px;
            height: 300px;
            border: 1px solid #000;
            text-align: center;
            float: left;
            margin-right: 50px;
            font-size: 70px;
            color: #1b1b1b;
        }
        .btn{
            width: 500px;
            height: 100px;
            border: 1px solid #000;
            margin-top: 30px;
            overflow: hidden;
        }
        .prev{
            width:50px;
            height: 30px;
            text-align: center;
            vertical-align: center ;
            float: left;
        }
        .pager{
            float: left;
            margin-left: 100px;
            margin-top: 10px;
        }
        .next{
            float: right;
            width:50px;
            height: 30px;
        }
        .selected{
            background: #f0f5b8;
        }
    </style>
</head>
<body>
    <div class="box">
        <ul class="contentAll">
            <li class="content">1</li>
            <li class="content" style="display: none;">2</li>
            <li class="content" style="display: none;">3</li>
            <li class="content" style="display: none;">4</li>
            <li class="content" style="display: none;">5</li>
            <li class="content" style="display: none;">6</li>
            <li class="content" style="display: none;">7</li>
            <li class="content" style="display: none;">8</li>
            <li class="content" style="display: none;">9</li>
        </ul>
        <div class="btn">
            <button class="prev">prev</button>
            <div class="pager">
                <button class="page selected">1</button>
                <button class="page">2</button>
                <button class="page">3</button>
                <button class="page">4</button>
                <button class="page">...</button>
                <button class="page">5</button>
                <button class="page">6</button>
                <button class="page">7</button>
                <button class="page">8</button>
                <button class="page">last</button>
            </div>
            <button class="next">next</button>
        </div>
    </div>
<script>
    $(function () {
        var $page = $('button.page:gt(4):not(":last")');
        var $btn = $("button.page:not(':eq(4)')");
        var $showmore =$("button.page:eq(4)");
        var $li =$(".box ul li");
        $page.hide();

        $btn.click(function () {
            $(this).addClass("selected").siblings().removeClass("selected");
            var index = $btn.index(this);
            $li.eq(index).show()
                    .siblings().hide()
        });
        $showmore.click(function () {
            $page.toggle();
            if($page.is(":visible")){
                $(this).parent("div.pager").css("margin-left","60px")
            }else{
                $(this).parent("div.pager").css("margin-left","100px")
            }
        });
        $(".prev").click(function () {
            var $prevIndex = $li.filter(":visible").index();
            if($prevIndex>0){
                $prevIndex-=1;
                $(".box ul li").eq($prevIndex).show().siblings().hide();
                $btn.eq($prevIndex).addClass("selected")
                        .siblings().removeClass("selected")
            }else{
                return false
            }
        });
        $(".next").click(function () {
            var $prevIndex = $li.filter(":visible").index();
            if($prevIndex<8){
                $prevIndex+=1;
                $(".box ul li").eq($prevIndex).show().siblings().hide();
                $btn.eq($prevIndex).addClass("selected")
                        .siblings().removeClass("selected")
            }else{
                return false
            }
        })
    })
</script>
</body>
</html>
