<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>聖誕禮物爭奪戰</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
            margin: 0;
            padding: 20px;
            background-image: url('https://images.unsplash.com/photo-1512389142860-9c449e58a543?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1169&q=80');
            background-size: cover;
            color: white;
        }
        h1 {
            color: #d42426;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        .game-container {
            max-width: 600px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
            color: #333;
        }
        .gift {
            width: 100px;
            height: 100px;
            background-color: #d42426;
            margin: 10px;
            display: inline-block;
            cursor: pointer;
            border-radius: 5px;
            background-image: url('https://images.unsplash.com/photo-1549465220-1a8b9238cd48?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1160&q=80');
            background-size: cover;
            transition: transform 0.3s;
        }
        .gift:hover {
            transform: scale(1.1);
        }
        button {
            background-color: #d42426;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 20px;
            border-radius: 5px;
        }
        button:hover {
            background-color: #b01e1e;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <h1>聖誕禮物爭奪戰</h1>
        <p>選擇一個禮物盒，看看你能得到什麼！</p>
        
        <div id="gifts-container">
            <div class="gift" onclick="selectGift(1)"></div>
            <div class="gift" onclick="selectGift(2)"></div>
            <div class="gift" onclick="selectGift(3)"></div>
            <div class="gift" onclick="selectGift(4)"></div>
            <div class="gift" onclick="selectGift(5)"></div>
            <div class="gift" onclick="selectGift(6)"></div>
        </div>
        
        <div id="result"></div>
        <button onclick="resetGame()">重新開始</button>
    </div>

    <script>
        const gifts = [
            "聖誕襪子一雙",
            "精美巧克力禮盒",
            "聖誕老人玩偶",
            "限量版聖誕音樂盒",
            "聖誕樹裝飾品",
            "聖誕主題馬克杯",
            "薑餅人餅乾",
            "聖誕節電影票兩張",
            "聖誕節蠟燭",
            "聖誕帽"
        ];
        
        function selectGift(giftNumber) {
            const randomIndex = Math.floor(Math.random() * gifts.length);
            const gift = gifts[randomIndex];
            document.getElementById('result').innerHTML = `恭喜！你獲得了 <span style="color: #d42426;">${gift}</span>！`;
            
            // 禁用所有禮物盒
            const giftElements = document.getElementsByClassName('gift');
            for (let i = 0; i < giftElements.length; i++) {
                giftElements[i].onclick = null;
                giftElements[i].style.cursor = 'default';
                giftElements[i].style.opacity = '0.5';
            }
            
            // 高亮選中的禮物盒
            giftElements[giftNumber - 1].style.opacity = '1';
            giftElements[giftNumber - 1].style.boxShadow = '0 0 20px gold';
        }
        
        function resetGame() {
            // 重置所有禮物盒
            const giftElements = document.getElementsByClassName('gift');
            for (let i = 0; i < giftElements.length; i++) {
                giftElements[i].onclick = function() { selectGift(i + 1); };
                giftElements[i].style.cursor = 'pointer';
                giftElements[i].style.opacity = '1';
                giftElements[i].style.boxShadow = 'none';
            }
            
            // 清除結果
            document.getElementById('result').innerHTML = '';
        }
    </script>
</body>
</html>
