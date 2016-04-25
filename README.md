# js-图片文字切换
跟着书上练习了，onclick与html分离这块还不太理解

<!DOCTYPE html>
<head>
	<title>动物展示</title>
	<meta charset="utf-8">
	<script type="text/javascript">
	function showpic(whichpic){
		var placeholder=document.getElementById("placeholder");
		var source=whichpic.getAttribute("href");
		placeholder.setAttribute("src",source);
		var description=document.getElementsByClassName("description")[0];
		var text=whichpic.getAttribute("title");
		description.childNodes[0].nodeValue=text;}//这里是为了实现切换图片和文字的效果
	window.onload=separate;//没有这个效果无法实现，why？因为for函数必须在加载完后才能完成循环吗？
	function separate(){
		var gallery=document.getElementsByClassName("gallery");
		var links=gallery[0].getElementsByTagName("a");//gallery[0]中的0不太理解，这里gallary只有一个，是不是因为用数组来赋值必须指明是数组中的哪一项？
		for (var i=0;i<links.length;i++) {
			links[i].onclick=function(){//这里是新写了一个匿名函数function
				showpic(this);//这里最难理解啊，为什么showpic要写在这个花括号里面呢？哦我懂了，这里showpic代表的是上面的函数，而不是这里的函数，这里的函数的funtion，是没有名字的所以叫匿名函数。这里的function是要执行showpic函数的。
				return false;
			}
		}
	}	//了解了这种将onclick从html中分离出来的方法
	</script>
</head>
<body>
<h1>我的图片库</h1>
<ul class="gallery";>
	<li>
		<a href="dog.jpg" title="可爱的狗狗" >可爱的狗狗</a>
	</li>
	<li>
		<a href="cat.jpg" title="漂亮的猫猫" onclick="showpic(this);return false;">漂亮的猫猫</a>
	</li>
	<li>
		<a href="bird.jpg" title="帅气的鸽子" onclick="showpic(this);return false;">帅气的鸽子</a>
	</li>
</ul>
<img id="placeholder" src="占位图.jpg" alt="my image gallery" height="600px"></img>
<p class="description">请选择图片</p>
</body>
</html>
