# -bear-gift
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>送你一只小熊礼物🎁</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            min-height: 100vh;
            background: #fff5f8;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-family: "Microsoft Yahei", sans-serif;
            overflow: hidden;
        }
        .title {
            font-size: 24px;
            color: #c97892;
            margin-bottom: 30px;
        }
        .bear-box {
            cursor: pointer;
            transition: transform 0.2s;
        }
        .bear-box:hover {
            transform: scale(1.05);
        }
        .bear {
            width: 220px;
            height: 220px;
            position: relative;
        }
        /* 小熊svg绘制 */
        .bear svg {
            width: 100%;
            height: 100%;
        }
        .tip {
            margin-top: 20px;
            color: #b86880;
            font-size: 16px;
        }
        .gift-popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            background: #ffffff;
            padding: 40px 50px;
            border-radius: 20px;
            box-shadow: 0 8px 30px rgba(200, 100, 130, 0.25);
            z-index: 99;
            transition: transform 0.4s ease;
            text-align: center;
        }
        .gift-popup.show {
            transform: translate(-50%, -50%) scale(1);
        }
        .gift-popup h2 {
            color: #c97892;
            margin-bottom: 15px;
        }
        .gift-popup p {
            color: #666;
            line-height: 1.7;
            margin-bottom: 20px;
        }
        .gift-popup button {
            border: none;
            background: #f2b8c8;
            color: white;
            padding: 10px 22px;
            border-radius: 99px;
            font-size: 15px;
            cursor: pointer;
        }
        .gift-popup button:hover {
            background: #e899af;
        }
        /* 爱心飘落 */
        .heart {
            position: fixed;
            color: #ff88a8;
            font-size: 22px;
            animation: fall 3s linear forwards;
            pointer-events: none;
        }
        @keyframes fall {
            0% {
                opacity: 1;
                transform: translateY(0) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(100vh) rotate(360deg);
            }
        }
        .mask {
            position: fixed;
            inset:0;
            background:rgba(0,0,0,0.2);
            z-index:98;
            display:none;
        }
        .mask.show {
            display:block;
        }
    </style>
</head>
<body>
    <div class="title">✨ 点一点小熊，收下礼物 ✨</div>
    <div class="bear-box" id="bearBox">
        <div class="bear">
<svg viewBox="0 0 200 200">
  <!--耳朵-->
  <circle cx="45" cy="45" r="22" fill="#b98b6b"/>
  <circle cx="155" cy="45" r="22" fill="#b98b6b"/>
  <circle cx="45" cy="45" r="12" fill="#e6b8a2"/>
  <circle cx="155" cy="45" r="12" fill="#e6b8a2"/>
  <!--头-->
  <circle cx="100" cy="100" r="70" fill="#b98b6b"/>
  <!--脸-->
  <circle cx="100" cy="110" r="48" fill="#e6b8a2"/>
  <!--眼睛-->
  <circle cx="72" cy="90" r="6" fill="#222"/>
  <circle cx="128" cy="90" r="6" fill="#222"/>
  <!--鼻子嘴巴-->
  <ellipse cx="100" cy="115" rx="8" ry="6" fill="#553828"/>
  <path d="M100 121 Q 94 130 88 126 M100 121 Q 106 130 112 126" stroke="#553828" stroke-width="2" fill="none"/>
  <!--腮红-->
  <circle cx="55" cy="110" r="10" fill="#ffb8b8" opacity="0.5"/>
  <circle cx="145" cy="110" r="10" fill="#ffb8b8" opacity="0.5"/>
</svg>
        </div>
    </div>
    <div class="tip">🐻 小熊带着礼物来找你啦</div>

    <div class="mask" id="mask"></div>
    <div class="gift-popup" id="gift">
        <h2>🎁 你的礼物已送达</h2>
        <p>愿你天天开心，万事顺意<br>所有期待，都有回响</p>
        <button id="closeBtn">收下啦</button>
    </div>

    <script>
        const bearBox = document.getElementById('bearBox');
        const gift = document.getElementById('gift');
        const mask = document.getElementById('mask');
        const closeBtn = document.getElementById('closeBtn');

        // 点击小熊弹出礼物 + 爱心
        bearBox.onclick = () => {
            gift.classList.add('show');
            mask.classList.add('show');
            createHearts();
        }
        // 关闭弹窗
        closeBtn.onclick = () => {
            gift.classList.remove('show');
            mask.classList.remove('show');
        }
        mask.onclick = () => {
            gift.classList.remove('show');
            mask.classList.remove('show');
        }

        // 爱心飘落函数
        function createHearts() {
            for(let i=0; i<25; i++){
                setTimeout(()=>{
                    const h = document.createElement('div');
                    h.className = 'heart';
                    h.innerText = '♥';
                    h.style.left = Math.random()*100 + 'vw';
                    h.style.top = '-20px';
                    document.body.appendChild(h);
                    setTimeout(()=>h.remove(), 3000);
                }, i*80)
            }
        }
    </script>
</body>
</html>
