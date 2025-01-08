<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>生日快乐！</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Ma+Shan+Zheng&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ffd1ff, #ffc3a0, #ffafbd);
            background-size: 400% 400%;
            font-family: Arial, sans-serif;
            overflow: hidden;
            animation: gradientBG 15s ease infinite;
            font-size: calc(14px + 0.4vw);
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            text-align: center;
            position: relative;
            z-index: 1;
            perspective: 1000px;
        }

        .birthday-card {
            background: rgba(255, 255, 255, 0.95);
            padding: clamp(1rem, 3vw, 2rem);
            border-radius: 30px;
            box-shadow: 0 0 30px rgba(255, 182, 193, 0.3);
            animation: float 3s ease-in-out infinite;
            position: relative;
            width: clamp(280px, 85%, 500px);
            margin: clamp(0.5rem, 2vw, 1rem);
            transform-style: preserve-3d;
            transition: transform 0.5s ease;
            max-height: 90vh;
            overflow-y: auto;
            -webkit-overflow-scrolling: touch;
        }

        .birthday-card:hover {
            transform: rotateY(5deg) rotateX(5deg);
            box-shadow: 
                -20px 20px 30px rgba(255, 182, 193, 0.2),
                0 0 50px rgba(255, 182, 193, 0.3);
        }

        .ribbon {
            width: calc(100% + 40px);
            height: calc(100% + 40px);
            position: absolute;
            top: -20px;
            left: -20px;
            border: 3px solid #ff9eb5;
            border-radius: 35px;
            z-index: -1;
            opacity: 0.7;
            animation: borderGlow 2s ease-in-out infinite;
        }

        @keyframes borderGlow {
            0%, 100% { border-color: #ff9eb5; }
            50% { border-color: #ff6b8b; }
        }

        .cake {
            font-size: clamp(1.8rem, 5vw, 2.5rem);
            margin-bottom: 1rem;
            color: #ff6b8b;
            font-family: 'Ma Shan Zheng', cursive;
            text-shadow: 3px 3px 10px rgba(255,107,139,0.3);
            animation: textGlow 2s ease-in-out infinite;
        }

        @keyframes textGlow {
            0%, 100% { text-shadow: 3px 3px 6px rgba(0,0,0,0.1); }
            50% { text-shadow: 0 0 15px rgba(255,107,139,0.5); }
        }

        .balloons {
            font-size: clamp(1.5rem, 4vw, 2rem);
            margin: clamp(0.8rem, 2vw, 1.2rem) 0;
            filter: drop-shadow(2px 2px 4px rgba(0,0,0,0.1));
            animation: swing 3s ease-in-out infinite;
        }

        @keyframes swing {
            0%, 100% { transform: rotate(-3deg); }
            50% { transform: rotate(3deg); }
        }

        .gifts {
            font-size: clamp(1.5rem, 4vw, 2rem);
            margin-top: 1.5rem;
            filter: drop-shadow(2px 2px 4px rgba(0,0,0,0.1));
            animation: bounce 2s ease infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        h1 {
            color: #ff6b8b;
            font-size: clamp(2rem, 6vw, 2.8rem);
            margin: 1rem 0;
            font-family: 'Dancing Script', cursive;
            text-shadow: 3px 3px 8px rgba(255,107,139,0.3);
            animation: colorChange 4s ease-in-out infinite;
        }

        @keyframes colorChange {
            0%, 100% { color: #ff6b8b; }
            50% { color: #ff9eb5; }
        }

        .message {
            color: #777;
            font-size: clamp(1.1rem, 3.5vw, 1.4rem);
            line-height: 1.6;
            margin: clamp(1rem, 3vw, 1.5rem) 0;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.05);
            padding: clamp(12px, 3vw, 20px);
            border-radius: 15px;
            background: rgba(255,255,255,0.9);
            backdrop-filter: blur(5px);
            font-family: 'Ma Shan Zheng', 'STXingkai', 'FZXingKai', cursive;
            letter-spacing: min(0.15em, 1px);
            text-align: center;
            box-shadow: 0 0 40px rgba(255,182,193,0.4);
        }

        .message .greeting {
            font-size: clamp(1.3rem, 4vw, 1.8rem);
            color: #ff6b8b;
            margin-bottom: 1.5rem;
            text-align: center;
            font-weight: bold;
            text-shadow: 3px 3px 8px rgba(255,107,139,0.4);
            letter-spacing: 3px;
            background: linear-gradient(45deg, #ff6b8b, #ff9eb5);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            padding: 10px 0;
        }

        .message .content {
            margin: min(3vw, 1rem) 0;
            text-align: center;
            line-height: 1.8;
            padding: 0 min(3vw, 15px);
            color: #666;
            font-size: min(4vw, 1.6rem);
            text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
        }

        .message .wishes {
            margin: clamp(1rem, 3vw, 1.5rem) 0;
            padding: min(3vw, 15px) min(4vw, 20px);
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: clamp(8px, 2vw, 12px);
            width: fit-content;
            margin-left: auto;
            margin-right: auto;
        }

        .message .wishes li {
            display: flex;
            align-items: center;
            gap: 10px;
            color: #555;
            transition: transform 0.3s ease;
            font-size: clamp(1.1rem, 3.5vw, 1.4rem);
            text-shadow: 1px 1px 3px rgba(0,0,0,0.1);
        }

        .message .wishes li:hover {
            transform: translateX(10px);
            color: #ff6b8b;
            text-shadow: 2px 2px 4px rgba(255,107,139,0.2);
        }

        .message .wishes li span {
            font-size: clamp(1.3rem, 4vw, 1.6rem);
            filter: drop-shadow(2px 2px 4px rgba(0,0,0,0.1));
            transform: scale(1);
            transition: transform 0.3s ease;
        }

        .message .wishes li:hover span {
            transform: scale(1.2);
            filter: drop-shadow(3px 3px 6px rgba(0,0,0,0.15));
        }

        .sparkles {
            font-size: 2rem;
            position: absolute;
            animation: twinkle 1.5s ease-in-out infinite;
        }

        .sparkles:first-of-type {
            top: 10px;
            right: 20px;
        }

        .sparkles:last-of-type {
            bottom: 10px;
            left: 20px;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(1deg); }
            100% { transform: translateY(0) rotate(0deg); }
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(0.8); }
            50% { opacity: 1; transform: scale(1.2); }
        }

        .cherry-blossoms {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .petal {
            position: absolute;
            top: -10%;
            font-size: 1.2rem;
            animation: falling 12s linear infinite;
            opacity: 0.9;
        }

        @keyframes falling {
            0% {
                transform: translate(0, 0) rotate(0deg) scale(0.8);
                opacity: 1;
            }
            25% {
                transform: translate(50px, 25vh) rotate(90deg) scale(1);
            }
            50% {
                transform: translate(100px, 50vh) rotate(180deg) scale(0.9);
            }
            75% {
                transform: translate(150px, 75vh) rotate(270deg) scale(1);
            }
            100% {
                transform: translate(200px, 100vh) rotate(360deg) scale(0.8);
                opacity: 0.3;
            }
        }

        /* 添加爱心样式 */
        .heart {
            position: absolute;
            top: -10%;
            font-size: 1.2rem;
            animation: fallingHeart 15s linear infinite;
            opacity: 0.9;
            z-index: 1;
        }

        @keyframes fallingHeart {
            0% {
                transform: translate(0, 0) rotate(0deg) scale(0.8);
                opacity: 1;
            }
            25% {
                transform: translate(-50px, 25vh) rotate(-45deg) scale(1);
            }
            50% {
                transform: translate(-100px, 50vh) rotate(-90deg) scale(0.9);
            }
            75% {
                transform: translate(-150px, 75vh) rotate(-135deg) scale(1);
            }
            100% {
                transform: translate(-200px, 100vh) rotate(-180deg) scale(0.8);
                opacity: 0.3;
            }
        }

        @media (max-width: 600px) {
            .birthday-card {
                transform: scale(0.95);
                padding: clamp(0.8rem, 3vw, 1.5rem);
                margin: 0.5rem;
                width: clamp(280px, 92%, 450px);
            }
            
            h1 {
                font-size: clamp(2rem, 6vw, 2.8rem);
            }
            
            .message {
                padding: clamp(12px, 3vw, 20px);
            }

            .message .greeting {
                font-size: clamp(1.3rem, 4vw, 1.8rem);
            }

            .message .content,
            .message .wishes li {
                font-size: clamp(1.1rem, 3.5vw, 1.4rem);
                line-height: 1.6;
            }

            .message .wishes li span {
                font-size: clamp(1.3rem, 4vw, 1.6rem);
            }

            .message .wishes {
                gap: clamp(8px, 2vw, 12px);
                margin: clamp(1rem, 3vw, 1.5rem) 0;
            }

            .balloons, .gifts {
                font-size: clamp(1.5rem, 4vw, 2rem);
                margin: clamp(0.8rem, 2vw, 1.2rem) 0;
            }

            .cake {
                font-size: clamp(1.8rem, 5vw, 2.5rem);
            }
        }

        /* 添加打字机效果 */
        .typing-text {
            overflow: hidden;
            white-space: nowrap;
            animation: typing 3.5s steps(40, end);
        }

        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }

        /* 添加照片墙效果 */
        .photo-wall {
            display: flex;
            gap: 15px;
            margin: 20px 0;
            justify-content: center;
            perspective: 1000px;
        }

        .photo-frame {
            width: 80px;
            height: 80px;
            background: white;
            padding: 5px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255,182,193,0.3);
            transform: rotate(var(--rotate));
            transition: transform 0.3s ease;
            animation: frameFloat 3s ease-in-out infinite;
            animation-delay: var(--delay);
        }

        .photo-frame:hover {
            transform: scale(1.1) rotate(0deg);
        }

        .photo-frame span {
            font-size: 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
        }

        @keyframes frameFloat {
            0%, 100% { transform: translateY(0) rotate(var(--rotate)); }
            50% { transform: translateY(-10px) rotate(var(--rotate)); }
        }

        /* 添加闪烁的星星 */
        .stars {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .star {
            position: absolute;
            font-size: 1.2rem;
            animation: starTwinkle var(--duration) ease-in-out infinite;
            opacity: 0;
        }

        @keyframes starTwinkle {
            0% { opacity: 0; transform: scale(0.3); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(0.3); }
        }

        /* 添加彩带效果 */
        .ribbon-decoration {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .ribbon-decoration::before,
        .ribbon-decoration::after {
            content: '🎀';
            position: absolute;
            font-size: 2rem;
            animation: ribbonSway 3s ease-in-out infinite;
        }

        .ribbon-decoration::before {
            top: -20px;
            left: -20px;
        }

        .ribbon-decoration::after {
            bottom: -20px;
            right: -20px;
            animation-delay: -1.5s;
        }

        @keyframes ribbonSway {
            0%, 100% { transform: rotate(-10deg); }
            50% { transform: rotate(10deg); }
        }

        /* 添加开场动画样式 */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #ffd1ff, #ffc3a0);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            animation: fadeOut 1s ease-in-out 6s forwards;
        }

        .loading-text-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }

        .loading-text {
            font-size: clamp(1.8rem, 5vw, 3.5rem);
            color: white;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.2);
            font-family: 'Ma Shan Zheng', cursive;
            opacity: 0;
            animation: none;
            text-align: center;
            padding: 0 1rem;
        }

        .loading-text:nth-child(1) {
            animation: loadingText 1.5s ease-in-out forwards;
        }

        .loading-text:nth-child(2) {
            animation: loadingText 1.5s ease-in-out 1.5s forwards;
        }

        .loading-text:nth-child(3) {
            animation: loadingText 1.5s ease-in-out 3s forwards;
        }

        .loading-text:nth-child(4) {
            animation: loadingText 1.5s ease-in-out 4.5s forwards;
        }

        .container {
            opacity: 0;
            transform: scale(0.8);
            animation: showCard 1s ease-in-out 6.5s forwards;
        }

        @keyframes fadeOut {
            from { opacity: 1; }
            to { 
                opacity: 0; 
                visibility: hidden;
            }
        }

        @keyframes loadingText {
            0% { 
                opacity: 0;
                transform: scale(0.8);
            }
            50% { 
                opacity: 1;
                transform: scale(1.1);
            }
            100% { 
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes showCard {
            from { 
                opacity: 0;
                transform: scale(0.8);
            }
            to { 
                opacity: 1;
                transform: scale(1);
            }
        }

        /* 添加横屏样式 */
        @media (orientation: landscape) and (max-height: 600px) {
            .birthday-card {
                transform: scale(0.85);
                margin: 0.3rem;
                max-height: 85vh;
            }

            .message {
                margin: 1rem 0;
            }
        }

        /* 添加中等屏幕尺寸的优化 */
        @media (min-width: 601px) and (max-width: 1024px) {
            .birthday-card {
                width: 85%;
                padding: 3vw;
            }
        }

        /* 针对特别小的屏幕 */
        @media (max-width: 320px) {
            .birthday-card {
                transform: scale(0.9);
                padding: 0.8rem;
            }

            body {
                font-size: 12px;
            }
        }
    </style>
</head>
<body>
    <!-- 添加加载屏幕 -->
    <div class="loading-screen">
        <div class="loading-text-container">
            <div class="loading-text">亲爱的李响老师 ✨</div>
            <div class="loading-text">愿您生日快乐 🎂</div>
            <div class="loading-text">岁月静好 前程似锦 💝</div>
            <div class="loading-text">永远保持甜美的笑容🌸</div>
        </div>
    </div>

    <div class="cherry-blossoms"></div>
    <div class="container">
        <div class="birthday-card">
            <div class="ribbon"></div>
            <div class="ribbon-decoration"></div>
            <div class="sparkles">✨</div>
            <div class="cake">
                 李响老师
            </div>
            <h1 class="typing-text">生日快乐！</h1>
            
            <div class="balloons">
                🎈🌸🎈🎈
            </div>
            <div class="message">
                <div class="greeting">
                    李响老师：
                </div>
                <div class="content">
                愿你的生日像阳光一样温暖，<br>
                像花儿一样绚丽多彩，<br>
                愿你永远保持甜美的笑容！
                </div>
                <ul class="wishes">
                    <li><span>🌟</span> 前程似锦，未来可期</li>
                    <li><span>✨</span> 梦想成真，心想事成</li>
                    <li><span>💝</span> 平安喜乐，幸福永伴</li>
                </ul>
            </div>
            <div class="gifts">
                🌹 🎁 🦋
            </div>
            <div class="sparkles">✨</div>
        </div>
    </div>

    <!-- 添加动态星星 -->
    <script>
        function createStars() {
            const stars = document.createElement('div');
            stars.className = 'stars';
            document.body.appendChild(stars);

            for (let i = 0; i < 35; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.textContent = '⭐';
                star.style.left = Math.random() * 100 + 'vw';
                star.style.top = Math.random() * 100 + 'vh';
                star.style.setProperty('--duration', 1.5 + Math.random() * 2 + 's');
                stars.appendChild(star);
            }
        }

        createStars();
    </script>

    <!-- 添加新的 JavaScript 代码来生成樱花 -->
    <script>
        function createPetal() {
            const petal = document.createElement('div');
            petal.className = 'petal';
            petal.textContent = '🌸';
            petal.style.left = Math.random() * 100 + '%';
            const duration = 10 + Math.random() * 5;
            petal.style.animation = `falling ${duration}s linear infinite`;
            
            document.querySelector('.cherry-blossoms').appendChild(petal);
            
            // 当樱花飘到底部时移除它
            setTimeout(() => {
                petal.remove();
            }, duration * 1000);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.textContent = '💗';
            heart.style.left = Math.random() * 100 + '%';
            const duration = 12 + Math.random() * 8;
            heart.style.animation = `fallingHeart ${duration}s linear infinite`;
            
            document.querySelector('.cherry-blossoms').appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, duration * 1000);
        }

        // 初始化樱花和爱心
        setTimeout(() => {
            for(let i = 0; i < 40; i++) {
                setTimeout(() => {
                    createPetal();
                    if(i % 2 === 0) {
                        createHeart();
                    }
                }, Math.random() * 3000);
            }

            // 持续创建新的樱花和爱心
            setInterval(() => {
                createPetal();
                if(Math.random() > 0.5) {
                    createHeart();
                }
            }, 500);
        }, 6500); // 等待开场动画结束后再开始生成樱花和爱心
    </script>
</body>
</html> 
