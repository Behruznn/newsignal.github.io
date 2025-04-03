<!DOCTYPE html>
<html lang="ru">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Gaming portal</title>
		<style>
			 @font-face {
			     font-family: 'Intro';
			     src: url('/static/intro.otf') format('opentype');
			 }
			 body {
			     background: #000;
			     background-size: 600% 600%;
			     animation: Gradient 16s ease infinite;
			     color: #fff;
			     font-family: 'Intro', Arial, sans-serif;
			     margin: 0;
			     padding: 0;
			     display: flex;
			     flex-direction: column;
			     height: 100vh;
			     padding-top: 60px;
			     padding-bottom: 50px;
			     user-select: none;
			     -webkit-tap-highlight-color: transparent;
			     -webkit-touch-callout: none;
			     scroll-behavior: smooth;
			 }
			 @keyframes Gradient {
			     0% { background-position: 0% 50%; }
			     50% { background-position: 100% 50%; }
			     100% { background-position: 0% 50%; }
			 }
			 header {
			     position: fixed;
			     top: 0;
			     z-index: 10;
			     width: 100%;
			     padding: 10px 20px;
			     background-color: #333;
			     color: #fff;
			     display: flex;
			     align-items: center;
			     font-family: 'Intro', Arial, sans-serif;
			     box-sizing: border-box;
			     font-size: 24px;
			 }
			 header img {
			     height: 30px;
			     width: 30px;
			     margin-right: 10px;
			     border-radius: 50%;
			 }
			 .tab {
			     position: fixed;
			     bottom: 0;
			     z-index: 10;
			     width: 100%;
			     display: flex;
			     justify-content: center;
			     background-color: #333;
			     padding: 10px 0;
			     border-radius: 50px;
			 }

			 .tab button {
			     background-color: inherit;
			     flex: 1 0 auto;
			     margin: 0 10px;
			     border: none;
			     outline: none;
			     cursor: pointer;
			     padding: 14px 20px;
			     transition: 0.3s;
			     color: #fff;
			     text-align: center;
			     border-radius: 50px;
			     font-size: 16px;
			     font-family: 'Intro', Arial, sans-serif;
			 }


			 .tab button:hover {
			     background-color: #555;
			     transform: translateY(-2px);
			 }

			 .tab button.active {
			     background-color: #666;
			     box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
			 }

			 .tabcontent {
			     display: none;
			     overflow: auto;
			     flex-direction: column;
			     align-items: center;
			     padding: 20px;
			     border-top: none;
			     overflow: auto;
			     flex-grow: 1;
			     margin-top: 0px;
			     margin-bottom: 50px;
			 }

			 .tabcontent.active {
			     display: flex;
			     opacity: 1;
			     visibility: visible;
			     transition: opacity 0.5s ease, visibility 0.5s ease;
			 }


			 .row {
			     display: flex;
			     flex-wrap: wrap;
			     width: 100%;
			     justify-content: space-around;
			 }
			 .game {
			     flex: 1 1 40%;
			     max-width: 209px;
			     margin: 10px;
			     text-align: center;
			     display: flex;
			     flex-direction: column;
			     align-items: center;
			 }

			 .game img:not(.secretimg) {
			     width: 100%;
			     height: auto;
			     max-height: 200px;
			     max-width: 200px;
			     border-radius: 50px;
			     box-shadow: 0px 0px 20px rgba(255, 255, 255, 0.8),
			                 0px 0px 30px rgba(173, 216, 230, 0.6);
			 }

			 @media (max-width: 400px) {
			 .row {
			     display: flex;
			     flex-wrap: wrap;
			     justify-content: space-around;
			 }

			 .game {
			     flex: 0 1 48%;
			     max-width: 48%;
			     margin: 1% 1%;
			     padding-top: 10px;
			 }

			 .game img:not(.secretimg) {
			     height: 140px !important;
			     width: auto !important;
			     max-width: 100% !important;
			     border-radius: 50px !important;
			     box-shadow: 0px 0px 20px rgba(255, 255, 255, 0.8),
			             0px 0px 30px rgba(173, 216, 230, 0.6);
			 }
			 }
			 .game-info {
			     width: 100%;
			     margin-top: 10px;
			     font-family: 'Intro', Arial, sans-serif;
			 }
			 .game h3 {
			     font-size: 18px;
			     margin: 5px 0;
			 }
			 .game button {
			     font-size: 16px;
			     font-weight: bold;
			     padding: 12px 24px;
			     width: 130px;
			     border-radius: 25px;
			     background: linear-gradient(145deg, #4CAF50 0%, #087f23 100%);
			     box-shadow: 0 6px #065f18, 0 -6px #4CAF50 inset;
			     color: white;
			     cursor: pointer;
			     transition: all 0.2s ease;
			     outline: none;
			     font-family: 'Intro', Arial, sans-serif;
			 }

			 .game button:hover {
			     background: linear-gradient(145deg, #087f23 0%, #4CAF50 100%);
			     box-shadow: 0 8px #065f18, 0 -6px #4CAF50 inset;
			     transform: translateY(-3px);
			 }

			 .game button:active {
			     box-shadow: 0 3px #065f18, 0 -3px #4CAF50 inset;
			     transform: translateY(2px);
			 }
			 canvas#particleCanvas {
			     position: fixed; /* Фиксируем канвас на фоне */
			     top: 0;
			     left: 0;
			     width: 100%;
			     height: 100%;
			     z-index: -1;
			     pointer-events: none;
			 }
			 .about-icon img {
			     width: 28px;
			     height: 28px;
			 }

			 .games-icon img {
			     width: 38px;
			     height: 38px;
			 }

			 .contact-icon img {
			     width: 28px;
			     height: 28px;
			 }
			 .secret-game {
			     margin-top: 50px;
			     margin-bottom: 100px;
			 }

			 .secretimg {
			     width: 100%;
			     height: auto;
			     border-radius: 50px;
			     box-shadow:
			         0 0 20px rgba(255, 0, 0, 0.8),
			         0 0 20px rgba(255, 127, 0, 0.8),
			         0 0 20px rgba(255, 255, 0, 0.8),
			         0 0 20px rgba(127, 255, 0, 0.8),
			         0 0 20px rgba(0, 255, 0, 0.8),
			         0 0 20px rgba(0, 255, 127, 0.8),
			         0 0 20px rgba(0, 255, 255, 0.8),
			         0 0 20px rgba(0, 127, 255, 0.8),
			         0 0 20px rgba(0, 0, 255, 0.8),
			         0 0 20px rgba(127, 0, 255, 0.8),
			         0 0 20px rgba(255, 0, 255, 0.8),
			         0 0 20px rgba(255, 0, 127, 0.8);
			     animation: rainbowGlow 5s linear infinite;
			     filter: hue-rotate(0deg); /* Initial filter state */
			 }

			 @keyframes rainbowGlow {
			     0%, 100% {
			         filter: hue-rotate(0deg);
			     }
			     50% {
			         filter: hue-rotate(360deg);
			     }
			 }

			 .secret-game .game-info h3 {
			     font-family: 'Intro', Arial, sans-serif;
			     text-align: center;
			     color: white;
			     font-size: 24px;
			 }

			 @keyframes Rainbow {
			     0% {background-position: 0% 50%;}
			     50% {background-position: 100% 50%;}
			     100% {background-position: 0% 50%;}
			 }
			 .about-gif {
			     margin-top: 30px;
			     width: 300px;
			     height: auto;
			     border-radius: 15px;
			     box-shadow: 0 0 8px rgba(255, 255, 255, 0.8),
			                 0 0 30px rgba(0, 255, 255, 0.8),
			                 0 0 60px rgba(0, 128, 255, 0.8);
			 }
			 .about-text {
			     position: relative;
			     margin: 20px;
			     padding: 10px;
			     width: 300px;
			     margin-top: 15px;
			     padding: 10px;
			     color: #fff;
			     display: flex;
			     flex-direction: column;
			     align-items: flex-start;
			 }

			 .about-text h2 {
			     font-size: 34px;
			     margin-bottom: 15px;
			 }

			 .typing-text {
			     font-size: 20px;
			     color: white;
			     background: linear-gradient(to right, #6a3093, #a044ff);
			     -webkit-background-clip: text;
			     -webkit-text-fill-color: transparent;
			     margin-top: 0px;
			     display: block;
			     white-space: nowrap;
			     overflow: hidden;
			     width: 100%;
			     margin-bottom: 20px;
			 }
			 .typing-text::after {
			     content: "\00a0";
			     display: inline-block;
			     width: 0;
			     height: 24px;
			 }
			 .about-button {
			     min-height: 25px;
			     display: inline-block;
			     font-size: 16px;
			     font-weight: bold;
			     padding: 12px 24px;
			     width: 300px;
			     border-radius: 25px;
			     background: linear-gradient(145deg, #3a8ccf 0%, #00397a 100%);
			     box-shadow: 0 6px #082d53, 0 -6px #3a8ccf inset;
			     color: white;
			     cursor: pointer;
			     margin-top: 5px;
			     margin-left: 130px;
			     display: block;
			     transition: all 0.2s ease;
			     outline: none;
			     font-family: 'Intro', Arial, sans-serif;
			     left: 50%;
			     transform: translateX(-50%);
			 }

			 .about-button:hover {
			     background: linear-gradient(145deg, #00397a 0%, #3a8ccf 100%);
			     box-shadow: 0 8px #082d53, 0 -6px #3a8ccf inset;
			     transform: translateY(-3px) translateX(-50%);
			 }

			 .about-button:active {
			     box-shadow: 0 3px #082d53, 0 -3px #3a8ccf inset;
			     transform: translateY(2px) translateX(-50%);
			 }
			  .title {
			     margin-top: 100px;
			     margin-left: 18px;
			     font-size: 28px;
			     margin-bottom: 10px;
			     color: #FFF;
			     font-weight: bold;
			 }

			 .image-container img {
			     margin-top: 20px;
			     margin-left: 45px
			     width: 190px;
			     height: 140px;
			     border-radius: 50%;
			     box-shadow: 0px 0px 15px 5px rgba(255, 255, 255, 0.8);
			 }

			 .device-info {
			     margin: 20px 0;
			     font-size: 16px;
			     transition: opacity 0.5s ease, transform 0.5s ease;
			     transform: translateY(-20px);
			     opacity: 0;
			 }

			 .device-info.visible {
			     transform: translateY(0);
			     opacity: 1;
			 }

			 .detect-button, .start-button {
			     font-size: 16px;
			     font-weight: bold;
			     padding: 12px 24px;
			     width: 180px;
			     border-radius: 25px;
			     background: linear-gradient(145deg, #4CAF50 0%, #087f23 100%);
			     box-shadow: 0 6px #065f18, 0 -6px #4CAF50 inset;
			     color: white;
			     cursor: pointer;
			     transition: all 0.2s ease;
			     outline: none;
			     font-family: 'Intro', Arial, sans-serif;
			     display: block;
			     margin: 10px auto;
			 }

			 .detect-button:hover, .start-button:hover {
			     background: linear-gradient(145deg, #087f23 0%, #4CAF50 100%);
			     box-shadow: 0 8px #065f18, 0 -6px #4CAF50 inset;
			     transform: translateY(-3px);
			 }

			 .detect-button:active, .start-button:active {
			     box-shadow: 0 3px #065f18, 0 -3px #4CAF50 inset;
			     transform: translateY(2px);
			 }
			.modal {
			     display: none;
			     position: fixed;
			     z-index: 1000;
			     left: 0;
			     top: 0;
			     width: 100%;
			     height: 100%;
			     overflow: auto;
			     background-color: rgba(0,0,0,0.4);
			     transition: opacity 0.5s ease, transform 0.5s ease;
			     opacity: 0;
			     transform: scale(0.95);
			     visibility: hidden;
			 }

			 .modal.show {
			     display: block;
			     opacity: 1;
			     visibility: visible;
			     transform: scale(1);
			 }

			 .modal-content {
			     background-color: #fefefe;
			     margin: auto;
			     padding: 20px;
			     border: 1px solid #888;
			     width: 70%;
			     height: 30%;
			     position: relative;
			     top: 50%;
			     transform: translateY(-60%);
			     box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
			     border-radius: 25px;
			     text-align: center;
			 }

			 .modal-content h2 {
			     color: black;
			     font-size: 24px;
			     margin: 10px 0;
			 }
			  .close-button {
			     position: absolute;
			     top: 10px;
			     right: 10px;
			     background-color: transparent;
			     border: none;
			     font-size: 24px;
			     cursor: pointer;
			     color: #aaa;
			 }

			 .close-button:hover {
			     color: #f00;
			 }
			  .carousel {
			     position: relative;
			     width: 100%;
			     max-width: 500px;
			     margin: auto;
			 }

			 .slides {
			     display: flex;
			     width: 100%;
			     overflow: hidden;
			     transition: transform 0.5s ease;
			 }

			 .slide img {
			     width: 50%;
			     border-radius: 5px;
			 }

			   .prev, .next {
			     cursor: pointer;
			     position: absolute;
			     top: 50%;
			     width: auto;
			     margin-top: -14px;
			     padding: 16px;
			     color: black;
			     font-weight: bold;
			     font-size: 18px;
			     transition: 0.6s ease;
			     border-radius: 3px;
			     user-select: none;
			     background-color: rgba(0,0,0,0.0);
			 }

			 .prev {
			     left: 10px;
			     border-radius: 3px 0 0 3px;
			 }

			 .next {
			     right: 10px;
			     border-radius: 0 3px 3px 0;
			 }

			 .prev:hover, .next:hover {
			     background-color: rgba(0,0,0,0.0);
			 }

			 .dots-container {
			     text-align: center;
			     padding: 10px;
			     background: #white;
			 }

			 .dot {
			     cursor: pointer;
			     height: 15px;
			     width: 15px;
			     margin: 0 2px;
			     background-color: #bbb;
			     border-radius: 50%;
			     display: inline-block;
			     transition: background-color 0.6s ease;
			 }

			 .dot.active, .dot:hover {
			     background-color: #717171;
			 }
			  .loader {
			     border: 16px solid transparent;
			     border-top: 4px solid #3498db;
			     border-radius: 50%;
			     width: 120px;
			     height: 120px;
			     animation: spin 2s linear infinite, extend 3s forwards;
			     margin-left: 45px;
			 }

			 @keyframes spin {
			     0% { transform: rotate(0deg); }
			     100% { transform: rotate(360deg); }
			 }

			 @keyframes extend {
			     0% { border-top: 4px solid #3498db; }
			     25% { border-top: 16px solid #3498db; border-right: 4px solid #3498db; }
			     50% { border-top: 16px solid #3498db; border-right: 16px solid #3498db; border-bottom: 4px solid #3498db; }
			     75% { border-top: 16px solid #3498db; border-right: 16px solid #3498db; border-bottom: 16px solid #3498db; border-left: 4px solid #3498db; }
			     100% { border: 16px solid #3498db; }
			 }
			 .modal-mini {
			     display: none;
			     position: fixed;
			     z-index: 1000;
			     left: 0;
			     top: 0;
			     width: 100%;
			     height: 100%;
			     background-color: rgba(0, 0, 0, 0.6);
			     align-items: center;
			     justify-content: center;
			     display: flex;
			 }
			 .modal-content-mini {
			     background-color: #fff;
			     padding: 20px;
			     border-radius: 10px;
			     width: 80%;
			     max-width: 500px;
			     text-align: center;
			     box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
			     position: relative;
			 }
			 .close-button-mini {
			     position: absolute;
			     top: 10px;
			     right: 10px;
			     border: none;
			     background: none;
			     font-size: 24px;
			     cursor: pointer;
			 }
			 .close-button-mini:hover {
			     color: #f00; /* Красный цвет при наведении */
			 }
			 .center-row {
			     justify-content: center;
			 }
		</style>
	</head>
	<body>
		
		<div id="Games" class="tabcontent" style="display: block">
			<div class="row">
				<div class="game">
					<img src="./static/1.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Mines</h3>
						<a href="https://onezelenka.github.io/Blume7Games/mines/">
							<button>Open</button>
						</a>
					</div>
				</div>				
				<div class="game">
					<img src="./static/2.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Bombucks</h3>
						<a href="https://onezelenka.github.io/Blume7Games/bombucks/">
							<button>Open</button>
						</a>
					</div>
				</div>
				<div class="game">
					<img src="./static/3.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Lucky Jet</h3>
						<a href="http://behruznn.github.io/luckyjet.github.io/lucky_jet.html">
							<button>Open</button>
						</a>
					</div>
				</div>
				<div class="game">
					<img src="./static/4.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Aviator</h3>
						<a href="https://onezelenka.github.io/Blume7Games/aviator/">
							<button>Open</button>
						</a>
					</div>
				</div>
				<div class="game">
					<img src="./static/5.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Speed-n-Cash</h3>
						<a href="https://onezelenka.github.io/Blume7Games/speed/">
							<button>Open</button>
						</a>
					</div>
				</div>
				<div class="game">
					<img src="./static/6.png" alt="Mines Preview" />
					<div class="game-info">
						<h3>Royal Mines</h3>
						<a href="https://onezelenka.github.io/Blume7Games/royal/">
							<button>Open</button>
						</a>
					</div>
				</div>
				<div class="row center-row">
					<div class="game">
						<img src="./static/7.png" alt="Mines Preview" />
						<div class="game-info">
							<h3>Brawl Pirates</h3>
							<a href="https://onezelenka.github.io/Blume7Games/brawl/">
								<button>Open</button>
							</a>
						</div>
					</div>
				</div>
				
				</div>
			</div>
		</div>
	
		<script>
			document.addEventListener('DOMContentLoaded', function () {
				let gamesButton = document.querySelector('.tablinks.games-icon')
				openTab(new Event('click'), 'Games', gamesButton)
				showSlides(slideIndex)
			})
			function triggerHapticFeedback() {
				if (window.Telegram && window.Telegram.WebApp.HapticFeedback) {
					window.Telegram.WebApp.HapticFeedback.impactOccurred('medium')
				}
			}
			function showSlides(n) {
				var i
				var slides = document.getElementsByClassName('slide')
				var dots = document.getElementsByClassName('dot')
				var slidesContainer = document.querySelector('.slides')

				if (n > slides.length) {
					slideIndex = 1
				}
				if (n < 1) {
					slideIndex = slides.length
				}
				for (i = 0; i < dots.length; i++) {
					dots[i].className = dots[i].className.replace(' active', '')
				}
				slidesContainer.style.transform = `translateX(${
					(-(slideIndex - 1) * 100) / slides.length
				}%)`
				dots[slideIndex - 1].className += ' active'
			}

			function openTab(evt, tabName, button) {
				triggerHapticFeedback()
				var i, tabcontent, tablinks
				var miniModal = document.getElementById('miniModal')
				var aboutGif = document.getElementById('aboutGif')

				// Скрываем все вкладки и удаляем класс 'active'
				tabcontent = document.getElementsByClassName('tabcontent')
				for (i = 0; i < tabcontent.length; i++) {
					tabcontent[i].style.display = 'none'
					tabcontent[i].classList.remove('active')
				}

				// Удаляем класс 'active' у всех кнопок
				tablinks = document.getElementsByClassName('tablinks')
				for (i = 0; i < tablinks.length; i++) {
					tablinks[i].classList.remove('active')
				}

				// Показываем текущую вкладку и добавляем класс 'active'
				document.getElementById(tabName).style.display = 'flex'
				document.getElementById(tabName).classList.add('active')
				button.classList.add('active')

				// Скроллим страницу
				if (tabName === 'Games') {
					window.scrollTo({ top: 45, behavior: 'smooth' })
				} else {
					window.scrollTo({ top: 0, behavior: 'smooth' })
				}

				// Обрабатываем вкладку 'About'
				if (tabName === 'About') {
					var newAboutGif = aboutGif.cloneNode(true)
					aboutGif.parentNode.replaceChild(newAboutGif, aboutGif)
					aboutGif = newAboutGif // обновляем ссылку на новый элемент
					aboutAudio.play()
				} else {
					aboutAudio.pause()
					aboutAudio.currentTime = 0
				}

				// Обрабатываем вкладку 'Contact'
				if (tabName === 'Contact') {
					miniModal.style.display = 'none'
				}
			}

			const canvas = document.getElementById('particleCanvas')
			const ctx = canvas.getContext('2d')
			canvas.width = window.innerWidth
			canvas.height = window.innerHeight
			let particlesArray = []

			class Particle {
				constructor() {
					this.x = Math.random() * canvas.width
					this.y = Math.random() * canvas.height
					this.size = Math.random() * 5 + 1
					this.speedX = Math.random() * 3 - 1.5
					this.speedY = Math.random() * 3 - 1.5
				}
				update() {
					this.x += this.speedX
					this.y += this.speedY
					if (this.size > 0.2) this.size -= 0.1
				}
				draw() {
					ctx.fillStyle = 'rgba(255,255,255,0.8)'
					ctx.beginPath()
					ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2)
					ctx.fill()
				}
			}

			function init() {
				for (let i = 0; i < 100; i++) {
					particlesArray.push(new Particle())
				}
			}

			function animate() {
				ctx.clearRect(0, 0, canvas.width, canvas.height)
				for (let i = 0; i < particlesArray.length; i++) {
					particlesArray[i].update()
					particlesArray[i].draw()
					if (particlesArray[i].size <= 0.3) {
						particlesArray.splice(i, 1)
						i--
						particlesArray.push(new Particle())
					}
				}
				requestAnimationFrame(animate)
			}

			window.addEventListener('resize', () => {
				canvas.width = window.innerWidth
				canvas.height = window.innerHeight
			})

			init()
			animate()
			const typingText = document.querySelector('.typing-text')
			const phrases = [
				'Subscribe to the channel',
				'Don t miss giveaways',
				'Catch vouchers!',
			]
			let phraseIndex = 0
			let letterIndex = 0
			let currentPhrase = []
			let isDeleting = false
			let delay = 60

			function type() {
				if (isDeleting && currentPhrase.length === 0) {
					phraseIndex = (phraseIndex + 1) % phrases.length
					letterIndex = 0
					isDeleting = false
					if (phraseIndex === 0) {
						setTimeout(type, 2000)
						return
					}
				} else if (
					!isDeleting &&
					currentPhrase.length === phrases[phraseIndex].length
				) {
					isDeleting = true
					delay = 2500
				}

				if (isDeleting) {
					currentPhrase.pop()
					delay = 30
				} else {
					currentPhrase.push(phrases[phraseIndex][letterIndex++])
					delay = 120
				}

				typingText.textContent = currentPhrase.join('')
				typingText.style.opacity = isDeleting ? 0.5 : 1
				setTimeout(type, delay)
			}

			document.addEventListener('DOMContentLoaded', function () {
				setTimeout(type, 2000)
			})
			$(document).ready(function () {
				for (i = 0; i < 5; i++) {
					$('.list li').clone().appendTo('.list')
				}
				$('.button').click(function () {
					$('.window').css({
						right: '0',
					})
					$('.list li').css({
						border: '4px solid transparent',
					})
					function selfRandom(min, max) {
						return Math.floor(Math.random() * (max - min + 1)) + min
					}
					var x = selfRandom(50, 100)
					$('.list li:eq(' + x + ')').css({
						border: '4px solid #00ba00',
					})

					var itemWidth = 100
					var itemMargin = 8
					$('.window').animate(
						{
							right: x * itemWidth + x * itemMargin - 119,
						},
						10000
					)
				})
			})
			function detectDevice() {
				triggerHapticFeedback()
				var ua = navigator.userAgent
				var deviceType
				var deviceModel = ''

				if (/android/i.test(ua)) {
					deviceType = 'Android'
					var match = ua.match(/Android.*?; (\w+)\s(\w+)\s/)
					deviceModel = match ? match[1] + ' ' + match[2] : ''
				} else if (/iPhone|iPad|iPod/i.test(ua)) {
					deviceType = 'iOS'
					if (/iPhone/i.test(ua)) {
						deviceModel = 'iPhone'
					} else if (/iPad/i.test(ua)) {
						deviceModel = 'iPad'
					} else if (/iPod/i.test(ua)) {
						deviceModel = 'iPod'
					}
				} else {
					deviceType = 'Desktop'
				}

				var output = deviceModel
					? deviceType + ' (' + deviceModel + ')'
					: deviceType
				var deviceOutput = document.getElementById('device-output')
				deviceOutput.classList.remove('visible')
				setTimeout(function () {
					deviceOutput.textContent = output
					deviceOutput.classList.add('visible')
				}, 10)
			}
			function startGame() {
				triggerHapticFeedback()
				console.log(document.getElementById('device-output').textContent)
				if (
					document.getElementById('device-output').textContent.trim() ===
					'Устройство не определено'
				) {
					showModal()
				} else {
					const now = new Date().getTime()
					const lastGameTime = localStorage.getItem('lastGameTime')
					if (lastGameTime && now - lastGameTime < 600000) {
						showMiniModal()
						return
					}
					var randomNumber = Math.floor(Math.random() * 5) + 1
					var probability = Math.floor(Math.random() * 12) + 85
					localStorage.setItem('lastGameTime', now)
					localStorage.setItem('lastGameImage', randomNumber)
					localStorage.setItem('lastProbability', probability)

					var imgContainer = document.querySelector('.image-container')
					var oldImage = imgContainer.querySelector('img')
					oldImage.style.display = 'none'

					var loaderDiv = document.createElement('div')
					loaderDiv.className = 'loader'
					imgContainer.appendChild(loaderDiv)

					setTimeout(function () {
						loaderDiv.remove()
						oldImage.style.display = 'block'
						oldImage.src = './static/' + randomNumber + '.png' // Корректный путь к изображению
						oldImage.style.marginLeft = '25px'
					}, 3000)
				}
			}

			function showMiniModal() {
				const lastGameImage = localStorage.getItem('lastGameImage')
				const gameName = getGameName(lastGameImage)
				const probability = localStorage.getItem('lastProbability')
				const remainingTime =
					600 -
					Math.floor(
						(new Date().getTime() - localStorage.getItem('lastGameTime')) / 1000
					)

				const modalContent = `
                <div style="
                    background-color: #fff;
                    border-radius: 10px;
                    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
                    padding: 20px;
                    max-width: 290px;
                    margin: 100px auto 0;
                    text-align: center;
                    font-family: 'Intro', Arial, sans-serif;">
                    <h2 style="
                        color: #333;
                        font-size: 24px;">Внимание!</h2>
                    <p style="
                        font-size: 16px;
                        color: #666;
                        line-height: 1.5;
                        margin-top: 10px;">Our team ensures the accuracy of the game provided to you in real-time. In the next 600 seconds, there is a ${probability}% chance that signals for the game ${gameName} will work on your device. The next request can be sent in ${remainingTime} seconds.</p>
                    <p style="
                        font-size: 16px;
                        color: #666;
                        margin-bottom: 20px;">Best regards, BLUME!</p>
                    <button onclick="closeMiniModal()" style="
                        background: linear-gradient(to right, #2196F3, #21CBF3);
                        color: white;
                        padding: 10px 20px;
                        border: none;
                        border-radius: 5px;
                        cursor: pointer;
                        font-size: 16px;
                        transition: all 0.3s ease-out;
                        outline: none;
                        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
                        font-family: 'Intro', Arial, sans-serif;">Закрыть</button>
                </div>
            `

				var miniModal = document.getElementById('miniModal')
				miniModal.innerHTML = modalContent
				miniModal.style.display = 'block'
			}

			function getGameName(imageNumber) {
				switch (imageNumber) {
					case '1':
						return 'Mines'
					case '2':
						return 'Royal Mines'
					case '3':
						return 'Coin Flip'
					case '4':
						return 'Brawl Pirates'
					case '5': // Добавляем Bombucks
						return 'Bombucks'
					default:
						return ''
				}
			}

			function closeMiniModal() {
				triggerHapticFeedback()
				var miniModal = document.getElementById('miniModal')
				miniModal.style.display = 'none'
			}

			function showModal() {
				var modal = document.getElementById('modal')
				modal.style.display = 'block'
				requestAnimationFrame(() => {
					modal.classList.add('show')
				})
			}

			function closeModal() {
				triggerHapticFeedback()
				var modal = document.getElementById('modal')
				modal.classList.remove('show')
				setTimeout(() => {
					modal.style.display = 'none'
				}, 500) // 500ms - время вашей CSS transition
			}

			var slideIndex = 1
			showSlides(slideIndex)

			function plusSlides(n) {
				triggerHapticFeedback()
				showSlides((slideIndex += n))
			}

			function currentSlide(n) {
				showSlides((slideIndex = n))
			}
			function openGame(game) {
				triggerHapticFeedback()
				var ua = navigator.userAgent
				var isIOS = /iPhone|iPad|iPod/i.test(ua)

				var links = {
					mines: {
						ios: '/mines',
						other: '/mines',
					},
					royalMines: {
						ios: '/bombucks',
						other: '/bombucks',
					},
					coinFlip: {
						ios: '/coinflipand',
						other: 'coinflip',
					},
					brawlPirates: {
						ios: '/aviator',
						other: '/aviator',
					},
					penalty: {
						ios: '/brawl',
						other: '/brawl',
					},
					bomBucks: {
						ios: '/royal',
						other: '/royal',
					},
				}

				var url = isIOS ? links[game].ios : links[game].other
				window.location.href = url
			}
			document.addEventListener('DOMContentLoaded', function () {
				// Форсируем пересчет высот
				const gamesContent = document.getElementById('Games')
				gamesContent.style.display = 'none' // Временно скрываем контент
				gamesContent.offsetHeight // Триггерим пересчет
				gamesContent.style.display = 'block' // Снова отображаем контент
			})
		</script>
	</body>
</html>
