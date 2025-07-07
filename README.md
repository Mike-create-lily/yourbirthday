<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<meta property="og:title" content="生日快乐" />
<meta property="og:description" content="🎉 祝你永远开心！" />
<meta property="og:url" content="https://Mike-create-lily.github.io/birthday/" />
<title>生日快乐</title>
<style>
body {
  background-color: #fff8f0;
  text-align: center;
  padding: 50px;
  font-family: sans-serif;
  overflow-x: hidden;
  position: relative;
  height: 100vh;
  margin: 0;
}

h1 {
  font-size: 2.5em;
  color: #ff4081;
  margin: 20px 0;
  position: relative;
  z-index: 10;
}

p {
  font-size: 1.2em;
  color: #555;
  position: relative;
  z-index: 10;
}

/* 花瓣样式 */
.petal {
  position: fixed;
  top: -50px;
  width: 20px;
  height: 20px;
  background: radial-gradient(circle at 50% 50%, #ffb6c1 0%, #ff69b4 70%);
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
  opacity: 0.8;
  animation-name: fall;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  pointer-events: none;
  z-index: 5;
  filter: drop-shadow(0 0 1px #ff69b4);
  transform-origin: center;
}

/* 花瓣飘落动画 */
@keyframes fall {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 0.8;
  }
  100% {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}

/* 流星样式 */
.shooting-star {
  position: fixed;
  top: 0;
  left: 0;
  width: 80px;
  height: 2px;
  background: linear-gradient(90deg, white, rgba(255,255,255,0));
  opacity: 0;
  border-radius: 50%;
  filter: drop-shadow(0 0 4px white);
  animation-timing-function: ease-in-out;
  pointer-events: none;
  z-index: 15;
}

/* 流星划过动画 */
@keyframes shoot {
  0% {
    opacity: 1;
    transform: translate3d(0, 0, 0) rotate(45deg);
  }
  100% {
    opacity: 0;
    transform: translate3d(100vw, 100vh, 0) rotate(45deg);
  }
}
</style>
</head>
<body>
<h1>生日快乐</h1>
<p>愿你每一天都如这蛋糕一样甜美 🍰</p>

<script>
// 创建花瓣函数
function createPetal() {
  const petal = document.createElement('div');
  petal.classList.add('petal');
  petal.style.left = Math.random() * window.innerWidth + 'px';
  petal.style.animationDuration = (5 + Math.random() * 5) + 's'; // 5-10秒飘落
  petal.style.animationDelay = (Math.random() * 10) + 's'; // 随机延迟
  petal.style.transform = `rotate(${Math.random()*360}deg)`;
  document.body.appendChild(petal);

  // 10秒后删除元素，避免DOM过多
  setTimeout(() => {
    petal.remove();
  }, 10000);
}

// 花瓣不断产生
setInterval(createPetal, 300);

// 流星函数
function shootingStar() {
  const star = document.createElement('div');
  star.classList.add('shooting-star');
  // 流星起点随机在屏幕顶部或左侧
  if (Math.random() > 0.5) {
    star.style.top = Math.random() * window.innerHeight * 0.5 + 'px';
    star.style.left = '-100px';
  } else {
    star.style.top = '-10px';
    star.style.left = Math.random() * window.innerWidth * 0.5 + 'px';
  }
  star.style.animationDuration = '1.2s';
  star.style.animationName = 'shoot';
  document.body.appendChild(star);

  star.addEventListener('animationend', () => {
    star.remove();
  });
}

// 每隔5-8秒产生一次流星
setInterval(() => {
  shootingStar();
}, 5000 + Math.random() * 3000);
</script>
</body>
</html>
