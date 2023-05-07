# README
## Introduction
###### This is a project that can help people feel relex when they struggle in their work and Generate inspirations.

## Usage
###### To use the webpage, tap the button on the home page.

## Description
#### The webpage includes the following components:

###### Three buttons that link to different pages:
###### "Timer" button: A page that displays a timer.
```
<!DOCTYPE html>
<html>
<head>
	<title>Timer</title>
	<style>
		body {
			background-color: #0074D9;
			display: flex;
			align-items: center;
			justify-content: center;
			height: 100vh;
			margin: 0;
			padding: 0;
		}

		.container {
			background-color: #FFFFFF;
			padding: 20px;
			border-radius: 10px;
			box-shadow: 0px 0px 10px #555555;
			text-align: center;
		}

		.timer {
			font-size: 36px;
			margin-bottom: 20px;
		}

		input[type="text"] {
			padding: 10px;
			border-radius: 5px;
			border: none;
			margin-bottom: 10px;
			font-size: 18px;
			width: 100%;
			box-sizing: border-box;
		}

		button {
			background-color: #2ECC40;
			color: #FFFFFF;
			border: none;
			border-radius: 5px;
			padding: 10px 20px;
			font-size: 18px;
			cursor: pointer;
			margin-bottom: 10px;
			transition: all 0.3s ease;
			box-shadow: 0px 2px 5px #555555;
		}

		button:hover {
			transform: translateY(-2px);
			box-shadow: 0px 4px 10px #555555;
		}
		.button-container {
			text-align: center;
			margin-top: 20px;
		}
		.button-container button {
			padding: 10px 20px;
			background-color: #4CAF50;
			color: white;
			border: none;
			border-radius: 4px;
			cursor: pointer;
		}
	</style>
	<script>
		var timer;

		function startTimer() {
			var task = document.getElementById("task").value;
			var minutes = document.getElementById("minutes").value;
			var seconds = minutes * 60;
			var display = document.getElementById("timer");

			if (isNaN(minutes)) {
				alert("please input a number");
				return;
			}

			if (timer) {
				clearInterval(timer);
			}

			timer = setInterval(function() {
				var minutesLeft = parseInt(seconds / 60);
				var secondsLeft = parseInt(seconds % 60);

				display.innerHTML = task + " Time Remaining: " + minutesLeft + " min " + secondsLeft + " sec";

				if (--seconds < 0) {
					clearInterval(timer);
					display.innerHTML = task + " Time's up! ";
					var audio = new Audio('./alert.mp3');
					audio.play();
				}
			}, 1000);
		}

		function stopTimer() {
			clearInterval(timer);
			document.getElementById("timer").innerHTML = "Timer stopped";
		}
	</script>
</head>
<body>
	<div class="container">
		<h1>Timer</h1>
		<p><input type="text" id="task" placeholder="Task"></p>
		<p><input type="text" id="minutes" placeholder="Time (min)"></p>
		<button onclick="startTimer()">Start</button>
		<button onclick="stopTimer()">Stop</button>
		<p class="timer" id="timer"></p>
		<div class="button-container">
			<button onclick="window.location.href='index.html'">Return</button>
		</div>
	</div>
	
</body>
</html>
```
###### "Hints" button: A page that can record inspirations and can store them.
```
<!DOCTYPE html>
<html>
<head>
	<title>Inspiration</title>
	<style>
		.container {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			height: 100vh;
			background-color: #f5f5f5;
		}

		h1 {
			margin-top: 0;
			margin-bottom: 1em;
			color: #333;
		}

		textarea {
			background-color: pink;
			width: 70%;
			height: 200px;
			padding: 10px;
			border-radius: 5px;
			border: none;
			resize: none;
		}

		.btn {
			margin-top: 1em;
			padding: 10px 20px;
			background-color: #4285f4;
			color: #fff;
			border: none;
			border-radius: 5px;
			cursor: pointer;
		}
		
		#scrolling-text {
			position: absolute;
			bottom: 0;
			left: 0;
			width: 100%;
			background-color: #333;
			color: #fff;
			padding: 10px 0;
			font-size: 1.2em;
			text-align: center;
			white-space: nowrap;
			overflow: hidden;
		}
		
		#scrolling-text span {
			display: inline-block;
			padding-left: 100%;
			animation: marquee 10s linear infinite;
		}
		
		@keyframes marquee {
			0% { transform: translate(0, 0); }
			100% { transform: translate(-100%, 0); }
		}
	</style>
</head>
<body>
	<div class="container">
		<h1>Inspiration</h1>
		<textarea id="myText"></textarea>
		<button class="btn" onclick="saveText()">Save</button>
		<button class="btn" onclick="goBack()">Return</button>
	</div>
	
	<div id="scrolling-text">
		<span>"The best way to find out if you can trust somebody is to trust them." - Ernest Hemingway</span>
		<span>"The most important thing is to enjoy your life - to be happy - it's all that matters." - Steve Jobs</span>
		<span>"I'm not a self-made man. I've had a lot of help." - Stan Lee</span>
		<span>"If you can't handle me at my worst, then you sure as hell don't deserve me at my best." - Marilyn Monroe</span>
		<span>"If you can't handle me at my worst, then you sure as hell don't deserve me at my best." - Marilyn Monroe</span>
	</div>

	<script>
		function saveText() {
			var textToSave = document.getElementById("myText").value;
			var textBlob = new Blob([textToSave], {type:"text/plain"});
			var fileName = "mytextfile.txt";
			var downloadLink = document.createElement("a");
			downloadLink.download = fileName;
			downloadLink.innerHTML = "Download File";
			if (window.webkitURL != null) {
				downloadLink.href = window.webkitURL.createObjectURL(textBlob);
			} else {
				downloadLink.href = window.URL.createObjectURL(textBlob);
				downloadLink.onclick = destroyClickedElement;
				downloadLink.style.display = "none";
				document.body.appendChild(downloadLink);
			}
			downloadLink.click();
		}

		function goBack() {
			window.location.href = "index.html";
		}
	</script>
</body>
</html>

```
###### "Relax" button: A page for entertainment and relaxation, and can create a timer page in it.
```
<!DOCTYPE html>
<html>
<head>
	<title>RELAX</title>
	<meta charset="UTF-8">
	<style>
    h1 {
			text-align: center;
			background: linear-gradient(to right, #3B3B98, #6a89cc);
			color: white;
			padding: 20px;
			margin: 0;
		}
    body {
			background: linear-gradient(to right, #3B3B98, #6a89cc);
			animation: backgroundAnimation 20s ease infinite;
		}

		@keyframes backgroundAnimation {
			0% { background-position: 0 0; }
			50% { background-position: 100% 0; }
			100% { background-position: 0 0; }
		}
		iframe {
			display: block;
			margin: 0 auto;
			padding: 0;
			border: none;
		}
		.button-container {
			text-align: center;
			margin-top: 20px;
		}
		.button-container button {
			padding: 10px 20px;
			background-color: #4CAF50;
			color: white;
			border: none;
			border-radius: 4px;
			cursor: pointer;
		}
	</style>
  <script>
		function randomize() {
			var urls = [
				"https://play2048.co/",
				"http://www.sinuousgame.com/",
        "https://ellisonleao.github.io/clumsy-bird/"
			];
			var url = urls[Math.floor(Math.random() * urls.length)];
			document.getElementById("myFrame").src = url;
		}
		function createIframe() {
			var iframeContainer = document.getElementById("iframe-container");
			var iframe = document.createElement("iframe");
			iframe.src = "alert.html";
			iframe.width = "500";
			iframe.height = "500";
			iframe.style.border = "none";
			iframeContainer.appendChild(iframe);
		}
	</script>
</head>
<body onload="randomize()">
	<h1>RELAX</h1>
	<div class="iframe-container">
		<iframe id="myFrame" width="1000" height="1000"></iframe>
	</div>
	<div class="button-container">
		<button onclick="window.location.href='index.html'">Return</button>
	</div>
	<div class ="button-container">
		<button onclick="createIframe()">Alert</button>
		<div id="iframe-container"></div>
	</div>
</body>
</html>

```

## Technologies Used
###### The webpage was created using HTML and CSS.

## User Testmonials
###### The user is writing a draft:
<img width="1277" alt="827a70603f44fbcba5e912b9c6423eb" src="https://user-images.githubusercontent.com/124060188/236702605-fe606394-5337-4889-8a8a-6e4b17f81031.png">

###### Relax after he finish the draft:
<img width="1271" alt="5bdba8d736f18659c10e464b98825f5" src="https://user-images.githubusercontent.com/124060188/236702651-b9ac9af8-35fb-453f-a730-b96da82f1596.png">

###### Set a timer to stop playing and return to write the essay.
<img width="1280" alt="46b78b888d38ccebc138503c6c8840a" src="https://user-images.githubusercontent.com/124060188/236702688-5ab5851c-3123-4e36-8046-aaf9f0cbdfb5.png">


## Credits
###### This webpage was created by Franklin.
