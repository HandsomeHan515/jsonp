# jsonp
jsonp实例

```jsonp
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>JSONP</title>
	<style>
		* {
			margin: 0;
			padding: 0;
			list-style: none;
		}
		#wrap {
			width: 500px;
			margin: 100px auto 0;
		}
		#wrap input {
			width: 486px;
			height: 40px; 
			padding-left: 10px;
		}
		#list {
			margin-top: 10px;
			background: #333;
		}
		#list li {
			width: 490px;
			line-height: 40px;
			background: #ccc;
			padding-left: 10px;
			margin-bottom: 3px;
		}
	</style>
</head>
<body>
	<div id="wrap">
		<input type="text" placeholder="请输入内容" id="ipt">
		<ul id="list">
			
		</ul>
	</div>
	<script>
		var ipt = document.getElementById('ipt'),
			list = document.getElementById('list');
		var Script = null;
		ipt.onkeyup = function () {
			if (Script) {
				document.body.removeChild(Script);
			}
			Script = document.createElement('script');
			Script.src = 'http://suggestion.baidu.com/su?wd='+ipt.value+'&cb=mycallback&t='+new Date().getTime();
			document.body.appendChild(Script);
		}
		function mycallback(json) {
			list.innerHTML = '';
			for (var i = 0; i < json.s.length; i++) {
				list.innerHTML += '<li>' + json.s[i] + '</li>';
			}
		}
	</script>
</body>
</html>
```
