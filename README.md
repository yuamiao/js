# js

//图片切换

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<link rel="stylesheet" href="index.css">
</head>
<style>
	*{
	margin: 0;
	padding: 0;
}
	ul{
		list-style: none;
	}
	#container{
		width: 1000px;
		height: 550px; 
		margin: 50px auto;
		overflow: hidden;
		position: relative;
	}
	#content img{
		display: none;
		width: 1000px;
		height: 550px;
	}
	#content img:hover{
		opacity: 0.9;
	}
	#content .selected{
		display: block;
	}
	#tab .selected{
		border: 3px solid #fff;
		margin: 0 5px 0 0 ;
	}
	#tab{
		right: 55px;
		bottom: 15px;
		position: absolute;
		z-index: 1;
	}
	#tab li{
		float: left;
		width: 70px;
		height: 50px;
		margin-right: 5px;
		margin: 3px 5px 3px 3px;
	}
	#tab img{
		width: 70px;
		height: 50px;
	}
	#text span{
		display: none;
	}
	#text .selected{
		display: block;
	}
	#text{
		position: absolute;
		left: 30px;
		bottom: 30px;
		z-index: 1;
		color: #fff;
		font-size: 20px;
	}
	#prev,#next{
		position: absolute;
		color: #ccc;
		font-size: 60px;
		font-weight: bold;
		cursor: pointer;
		bottom: 10px;
	}
	#prev{
		left: 340px;	
	}
	#prev:hover,#next:hover{
		color: #fff;
	}
	#next{
		right: 10px;
	}

	
</style>
<body>
	<div id="container">
		<ul id="tab">
			<li class="selected"><img src="img/1.jpg"></li>
			<li><img src="img/2.jpg"></li>
			<li><img src="img/3.jpg"></li>
			<li><img src="img/4.jpg"></li>
			<li><img src="img/5.jpg"></li>
			<li><img src="img/6.jpg"></li>
			<li><img src="img/7.jpg"></li>
		</ul>
		<div id="content">
			<div id="text"> 
				<span class="selected">啊啊啊啊啊啊啊啊啊啊</span>
			</div>
			<div>
				<img src="img/1.jpg" class="selected" title="啊啊啊啊啊啊啊啊啊啊">
				<img src="img/2.jpg" title="哈哈哈哈哈哈哈哈哈哈">
				<img src="img/3.jpg" title="嘿嘿嘿嘿嘿嘿嘿嘿嘿嘿">
				<img src="img/4.jpg" title="呀呀呀呀呀呀呀呀呀呀">
				<img src="img/5.jpg" title="嘻嘻嘻嘻嘻嘻嘻嘻嘻嘻">
				<img src="img/6.jpg" title="吼吼吼吼吼吼吼吼吼吼">
				<img src="img/7.jpg" title="哼哼哼哼哼哼哼哼哼哼">
			</div>
			<div id="arrow">
			<span id="prev">&lt;</span>
			<span id="next">&gt;</span>
			</div>
		</div>
	</div>
		

	<script type="text/javascript">
	var oTab = document.getElementById('tab');
	var aLi = oTab.getElementsByTagName('li');
	var oContent = document.getElementById('content');
	var aImg = oContent.getElementsByTagName('img');
	var oText = document.getElementById('text');
	var aSpan = oText.getElementsByTagName('span');
	var oPrev = document.getElementById('prev');
	var oNext = document.getElementById('next'); 
	var index = 0;

	for(var i=0; i<aLi.length; i++){
		aLi[i].index = i;
		aLi[i].onmouseover= function(){
			index = this.index;
			switchImg(this.index);
		};
	}
	function switchImg(idx){
		for(var i=0; i<aLi.length; i++){
				aLi[i].className = "";
				aImg[i].className = "";
			}
			aLi[idx].className = 'selected';
			aImg[idx].className = 'selected';
			aSpan[0].innerHTML = aImg[idx].title;//将aSpan中的内容替换成aImg中title的内容。
	}
	oPrev.onclick = function(){
		index--;
		if(index<0){
			index = aLi.length -1
		}
		switchImg(index);
	};

	oNext.onclick = function(){
		index++
		if(index>aLi.length-1){
			index = 0;
		}
		switchImg(index);
	};

	</script>
</body>
</html>
