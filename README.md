<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>地震學第一章：基本概念與社會連結</title>
<style>
    :root {
        --primary-color: #2c3e50;
        --secondary-color: #3498db;
        --accent-color: #e74c3c;
        --bg-color: #f4f6f8;
        --text-color: #333;
        --sidebar-bg: #1a252f;
        --sidebar-hover: #34495e;
    }

    body { 
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
        display: flex; 
        margin: 0; 
        background-color: var(--bg-color); 
        color: var(--text-color); 
        height: 100vh; 
        overflow: hidden; 
    }

    /* 導覽列設計 */
    .sidebar { 
        width: 300px; 
        background-color: var(--sidebar-bg); 
        color: white; 
        height: 100%; 
        overflow-y: auto; 
        display: flex; 
        flex-direction: column; 
        box-shadow: 2px 0 5px rgba(0,0,0,0.1);
    }
    .sidebar h2 { 
        padding: 20px; 
        text-align: center; 
        background-color: #0f171e; 
        margin: 0; 
        font-size: 1.3rem; 
        letter-spacing: 1px;
    }
    .sidebar ul { list-style: none; padding: 0; margin: 0; flex-grow: 1; }
    .sidebar li { 
        padding: 15px 20px; 
        cursor: pointer; 
        border-bottom: 1px solid #2c3e50; 
        transition: all 0.3s ease; 
        font-size: 0.95rem; 
    }
    .sidebar li:hover:not(.section-title) { background-color: var(--sidebar-hover); padding-left: 25px; }
    .sidebar li.active { background-color: var(--sidebar-hover); border-left: 5px solid var(--secondary-color); font-weight: bold; }
    .sidebar .section-title { 
        background-color: #11181f; 
        font-weight: bold; 
        color: #95a5a6; 
        cursor: default; 
        font-size: 0.85rem;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    /* 主內容區設計 */
    .content-wrapper { 
        flex-grow: 1; 
        overflow-y: auto; 
        padding: 40px; 
        scroll-behavior: smooth; 
    }
    .card { 
        background: white; 
        padding: 40px; 
        border-radius: 12px; 
        box-shadow: 0 5px 15px rgba(0,0,0,0.05); 
        margin-bottom: 40px; 
        display: none; 
        max-width: 900px;
        margin-left: auto;
        margin-right: auto;
    }
    .card.active { display: block; animation: slideUp 0.5s ease; }
    @keyframes slideUp { 
        from { opacity: 0; transform: translateY(20px); } 
        to { opacity: 1; transform: translateY(0); } 
    }

    h1 { color: var(--primary-color); border-bottom: 3px solid var(--secondary-color); padding-bottom: 10px; margin-top: 0; }
    h3 { color: #2980b9; margin-top: 30px; display: flex; align-items: center; gap: 10px; }
    h3::before { content: '💡'; font-size: 1.2rem; }
    p { line-height: 1.8; color: #444; font-size: 1.05rem; }

    /* 引用與解釋區塊 */
    .citation { 
        font-family: 'Georgia', serif;
        color: #555; 
        border-left: 4px solid #bdc3c7; 
        padding: 15px 20px; 
        margin: 20px 0; 
        background: #f8f9fa; 
        border-radius: 0 8px 8px 0; 
        font-size: 0.95rem; 
        line-height: 1.6;
    }
    .citation span.source { display: block; margin-top: 10px; font-size: 0.85rem; color: #7f8c8d; text-align: right; }
    
    .explanation { 
        background: #e1f5fe; 
        padding: 20px; 
        border-radius: 8px; 
        border: 1px solid #b3e5fc; 
        margin-bottom: 25px; 
        font-size: 1.05rem;
        color: #01579b;
    }
    .explanation strong { color: #0277bd; font-size: 1.1rem; }

    /* 互動與動畫區塊 */
    .interactive-area { 
        margin-top: 30px; 
        padding: 25px; 
        border: 2px dashed #90caf9; 
        border-radius: 12px; 
        background: #fafbfc; 
        text-align: center; 
    }
    .anim-box { 
        width: 100%; 
        height: 250px; 
        background: white; 
        border: 1px solid #e0e0e0; 
        border-radius: 8px; 
        position: relative; 
        overflow: hidden; 
        display: flex; 
        align-items: center; 
        justify-content: center; 
        margin-bottom: 20px;
        box-shadow: inset 0 0 10px rgba(0,0,0,0.02);
    }
    
    /* 按鈕與滑桿 */
    .slider-container { display: flex; align-items: center; justify-content: center; gap: 15px; margin-top: 20px; background: #fff; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); }
    input[type=range] { width: 60%; cursor: pointer; }
    .btn { 
        background: var(--secondary-color); 
        color: white; 
        border: none; 
        padding: 10px 20px; 
        border-radius: 6px; 
        cursor: pointer; 
        font-size: 1rem; 
        font-weight: bold;
        transition: background 0.2s, transform 0.1s; 
        margin: 5px; 
    }
    .btn:hover { background: #2980b9; transform: translateY(-2px); }
    .btn:active { transform: translateY(0); }

    /* 測驗區塊 */
    .quiz-section { background: #fff; padding: 40px; border-radius: 12px; border-top: 5px solid #f39c12; }
    .question { margin-bottom: 30px; padding: 25px; background: #fdfbf7; border-radius: 8px; border: 1px solid #f8ecc2; }
    .question p { font-weight: bold; font-size: 1.1rem; color: #2c3e50; }
    .options label { 
        display: block; 
        padding: 12px 15px; 
        margin: 8px 0; 
        background: white; 
        border: 1px solid #ddd; 
        border-radius: 6px; 
        cursor: pointer; 
        transition: all 0.2s; 
    }
    .options label:hover { background: #f0f8ff; border-color: var(--secondary-color); }
    .options input[type="radio"] { margin-right: 12px; transform: scale(1.2); }
    
    .quiz-result { margin-top: 30px; padding: 25px; display: none; border-radius: 8px; background: #f8f9fa; border: 1px solid #ddd; }
    .quiz-result.show { display: block; animation: slideUp 0.5s ease; }
    .feedback-item { padding: 15px; margin-bottom: 15px; border-radius: 6px; }
    .feedback-item.correct { background: #e8f5e9; border-left: 5px solid #4caf50; color: #2e7d32; }
    .feedback-item.incorrect { background: #ffebee; border-left: 5px solid #f44336; color: #c62828; }
    .weak-analysis { margin-top: 20px; padding: 20px; background: #fff3e0; border-radius: 6px; border: 1px solid #ffe0b2; color: #e65100; }

    /* RWD */
    @media (max-width: 768px) {
        body { flex-direction: column; }
        .sidebar { width: 100%; height: auto; max-height: 40vh; }
        .content-wrapper { padding: 20px; }
        .card { padding: 20px; }
    }
</style>
</head>
<body>

<nav class="sidebar">
    <h2>🌍 地震學大師課堂</h2>
    <ul>
        <li class="section-title">一、地震學的基本概念與模型</li>
        <li data-target="ch1-1" class="active">1.1 定義與核心機制</li>
        <li data-target="ch1-2">1.2 探索地球內部的工具</li>
        <li data-target="ch1-3">1.3 地震波傳播特性</li>
        <li data-target="ch1-4">1.4 地震波種類與相位</li>
        <li data-target="ch1-5">1.5 震源機制分析</li>
        <li data-target="ch1-6">1.6 逆問題與模型建構</li>
        <li class="section-title">二、地震學與社會的連結</li>
        <li data-target="ch2-1">2.1 地震危害 vs 風險 & 工程</li>
        <li data-target="ch2-2">2.2 次生災害 & 衰減公式</li>
        <li data-target="ch2-3">2.3 預報、預測與空白區</li>
        <li data-target="ch2-4">2.4 預測方法與核試驗監測</li>
        <li class="section-title">知識評量</li>
        <li data-target="quiz">📝 單元總測驗</li>
    </ul>
</nav>

<main class="content-wrapper">
    
    <section id="ch1-1" class="card active">
        <h1>1. 地震學的定義與核心機制</h1>
        <div class="citation">
            「地震學是研究彈性波（或聲波）在固體地球內傳播的科學。地震波由天然（如地震）或人工（如爆炸）的震源產生，穿過地球內部介質後，由地震儀接收並記錄成地震圖（Seismogram）。」
            <span class="source">[參考來源：2026/3/4 的所有記事, 01_1.1 Introduction.pdf]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            想像地球是一個巨大的果凍。當你在果凍內部引爆一個小鞭炮（震源），震動（地震波）會穿過果凍（介質），最後被貼在果凍表面的感測器（地震儀）記錄下來。地震學家就是透過解讀這張「震動心電圖」，來回推鞭炮在哪裡爆炸、以及果凍內部是什麼材質。
        </div>
        <div class="interactive-area">
            <h3>互動動畫：地震波的產生與紀錄</h3>
            <div class="anim-box" id="anim-flow">
                <svg width="100%" height="100%" viewBox="0 0 600 200">
                    <circle cx="80" cy="100" r="15" fill="#e74c3c" />
                    <text x="65" y="140" font-size="14" font-weight="bold">震源</text>
                    <rect x="150" y="40" width="300" height="120" fill="#ecf0f1" rx="15" stroke="#bdc3c7" stroke-width="2"/>
                    <text x="250" y="105" font-size="16" fill="#7f8c8d" font-weight="bold">地球介質</text>
                    <polygon points="520,100 500,70 540,70" fill="#3498db"/>
                    <rect x="515" y="100" width="10" height="20" fill="#2c3e50"/>
                    <text x="495" y="140" font-size="14" font-weight="bold">地震儀</text>
                    <circle cx="80" cy="100" r="15" fill="none" stroke="#e74c3c" stroke-width="3">
                        <animate attributeName="r" from="15" to="100" dur="2s" repeatCount="indefinite" />
                        <animate attributeName="opacity" from="1" to="0" dur="2s" repeatCount="indefinite" />
                    </circle>
                    <path d="M 150 100 Q 300 100 450 100" stroke="#3498db" stroke-width="3" stroke-dasharray="10,10" fill="none">
                        <animate attributeName="stroke-dashoffset" from="20" to="0" dur="0.5s" repeatCount="indefinite" linear/>
                    </path>
                </svg>
            </div>
            <p>觀察上方流程：能量由震源（紅點）釋放，透過介質傳播，最後由地表的接收器（藍色）記錄。</p>
        </div>
    </section>

    <section id="ch1-2" class="card">
        <h1>2. 探索地球內部的工具</h1>
        <div class="citation">
            「由於人類無法直接觀測地球深處，地震波成為探索地球內部結構（如地殼、地函、液態外核與固態內核）物理與化學性質的最有力工具。此外，地震學也被廣泛用於探勘石油與礦產等天然資源。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            我們無法把地球切開來看，所以地震波就像是醫學上的「X光」或「超音波」。波在堅硬的石頭裡跑得快，在液體裡跑得慢（甚至某些波無法穿透液體）。科學家藉由這些波速變化，描繪出地球有地殼、地函和地核的分層結構。石油公司也用類似原理，在地上製造人工震波來尋找地底下的油礦（地震反射法）。
        </div>
        <div class="interactive-area">
            <h3>互動圖解：點擊地球剖面圖探索分層</h3>
            <div class="anim-box" style="height: 300px; background: #0f171e;">
                <svg width="100%" height="100%" viewBox="0 0 400 300">
                    <g transform="translate(200, 150)">
                        <circle cx="0" cy="0" r="120" fill="#e67e22" style="cursor:pointer;" onclick="showLayer('地函 (Mantle)', '固態岩石，但高溫高壓下具有塑性，會發生緩慢熱對流。波速隨深度逐漸增加。')"/>
                        <circle cx="0" cy="0" r="65" fill="#f1c40f" style="cursor:pointer;" onclick="showLayer('液態外核 (Outer Core)', '液態鐵鎳合金。因為是液體，S波（剪力波）無法穿透此層，造成了S波陰影帶。')"/>
                        <circle cx="0" cy="0" r="25" fill="#ecf0f1" style="cursor:pointer;" onclick="showLayer('固態內核 (Inner Core)', '極高壓狀態下的固態鐵鎳核心，溫度極高。')"/>
                        <circle cx="0" cy="0" r="125" fill="none" stroke="#3498db" stroke-width="5" style="cursor:pointer;" onclick="showLayer('地殼 (Crust)', '最外層的固態岩石薄殼，人類活動與大部分淺層地震都發生在這裡。')"/>
                        <line x1="0" y1="-125" x2="0" y2="-140" stroke="white" stroke-width="1"/>
                        <text x="-15" y="-145" fill="white" font-size="10">地表</text>
                    </g>
                </svg>
            </div>
            <div id="layer-info-box" style="background: #fff9c4; padding: 15px; border-radius: 8px; border-left: 5px solid #fbc02d; font-weight: bold; min-height: 50px;">
                👆 請點擊上方地球的各個分層，查看物理特性說明。
            </div>
            <script>
                function showLayer(title, desc) {
                    document.getElementById('layer-info-box').innerHTML = `<span style="color:#d35400; font-size:1.1rem;">${title}</span><br><span style="color:#333; font-weight:normal;">${desc}</span>`;
                }
            </script>
        </div>
    </section>

    <section id="ch1-3" class="card">
        <h1>3. 地震波的傳播特性</h1>
        <div class="citation">
            「由於地球內部的地震波速通常隨深度增加，波的傳播路徑會產生折射（Refraction）而向下彎曲，最終彎向上方回到地表。就像光波在鏡面上反射一樣，地震波在物理性質改變的介面上也會發生反射（Reflection）與繞射（Diffraction）。」
            <span class="source">[參考來源：2026/3/4 的所有記事, 01_1.1 Introduction.pdf]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            波喜歡走「最快」的路徑。地球越深的地方，壓力越大、岩石越緊密，波速就越快。根據斯涅耳定律（Snell's Law），波在進入高速層時會發生折射，導致地震波在地球內部的路徑不是直線，而是一條「向下彎曲的弧線」。遇到不同岩層的交界面時，一部分能量會彈回來（反射）。
        </div>
        <div class="interactive-area">
            <h3>動畫模擬：波速隨深度增加導致的射線彎曲</h3>
            <div class="anim-box">
                <svg width="100%" height="100%" viewBox="0 0 600 200">
                    <rect x="0" y="0" width="600" height="200" fill="#fdfbf7"/>
                    <defs>
                        <linearGradient id="depthGrad" x1="0" y1="0" x2="0" y2="1">
                            <stop offset="0%" stop-color="#ecf0f1"/>
                            <stop offset="100%" stop-color="#95a5a6"/>
                        </linearGradient>
                    </defs>
                    <rect x="0" y="30" width="600" height="170" fill="url(#depthGrad)"/>
                    <line x1="0" y1="30" x2="600" y2="30" stroke="#2c3e50" stroke-width="3"/>
                    <text x="10" y="20" font-size="14" font-weight="bold">地表 (測站分布)</text>
                    <text x="250" y="180" font-size="14" fill="white">深度越深，波速越快</text>
                    
                    <circle cx="50" cy="30" r="8" fill="#e74c3c"/>
                    
                    <path id="rayPath" d="M 50 30 Q 300 250 550 30" fill="none" stroke="#e67e22" stroke-width="4" stroke-dasharray="15,10">
                        <animate attributeName="stroke-dashoffset" from="100" to="0" dur="1s" repeatCount="indefinite" linear/>
                    </path>
                    
                    <polygon points="550,30 540,15 560,15" fill="#3498db"/>
                </svg>
            </div>
            <p>橘色虛線代表地震波的傳播路徑，因為深部波速快，射線會向下彎曲形成 U 型。</p>
        </div>
    </section>

    <section id="ch1-4" class="card">
        <h1>4. 地震波種類與相位命名</h1>
        <div class="citation">
            「體波（Body waves）：在地球內部傳播，分為質點運動方向與傳播方向平行的 P波（壓縮波），及質點運動方向與傳播方向垂直的 S波（剪力波）。<br>
            表面波（Surface waves）：沿地球表面傳播，例如 Rayleigh waves。<br>
            地震相位（Phases）：依據波傳播路徑命名，例如 P、S、pP、PP，以及在核函邊界反射的 ScS 等。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            <ul>
                <li><strong>P波 (Primary)：</strong> 速度最快，第一個到達。像推擠彈簧一樣「前後」震動。</li>
                <li><strong>S波 (Secondary)：</strong> 速度次之。像甩繩子一樣「上下或左右」震動。破壞力比P波強。</li>
                <li><strong>表面波 (如 Rayleigh 波)：</strong> 只能在地表傳遞，像海浪一樣在原地做「逆時針橢圓形」翻滾，搖晃時間長，是造成建築物倒塌的主因。</li>
                <li><strong>相位密碼：</strong> 大寫字母（P/S）代表在地函走，小寫（p/s）代表往上彈回地表，c代表打到地核反彈。所以 `ScS` 就是 S波一路往下打到地核外殼，再以S波的姿態反彈回地表。</li>
            </ul>
        </div>
        <div class="interactive-area">
            <h3>互動展示：點擊觀察質點運動方式</h3>
            <div style="margin-bottom: 15px;">
                <button class="btn" onclick="document.getElementById('wave-demo-text').innerHTML='<strong>【P波】</strong> 質點平行於傳播方向。 <br> 示意：||| | | ||| | | ||| (疏密波)'">觀察 P 波</button>
                <button class="btn" onclick="document.getElementById('wave-demo-text').innerHTML='<strong>【S波】</strong> 質點垂直於傳播方向。<br> 示意：〰️〰️〰️〰️ (剪力波狀)'">觀察 S 波</button>
                <button class="btn" onclick="document.getElementById('wave-demo-text').innerHTML='<strong>【Rayleigh波】</strong> 質點在垂直面做逆時針橢圓運動。<br> 示意：🔄 (如同海浪翻滾)'">觀察 表面波</button>
            </div>
            <div class="anim-box" style="height: 100px; background: #eef2f5;">
                <div id="wave-demo-text" style="font-size: 1.3rem; color: #2c3e50; text-align: center;">請選擇上方的波型按鈕</div>
            </div>
        </div>
    </section>

    <section id="ch1-5" class="card">
        <h1>5. 震源機制分析</h1>
        <div class="citation">
            「科學家透過分析地震網在各方位記錄到的P波初動方向（First motions，分為壓縮與膨脹象限），可以推斷斷層的走向以及滑動方向。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            當斷層錯動時，會把前方的石頭往前推（產生壓縮，測站測到的第一下波是「往上」的），同時把後方的石頭往後拉（產生膨脹，第一下波是「往下」的）。把全世界測站量到的「上」跟「下」畫在一個球體投影上，就會出現類似「西瓜切四塊」（兩個黑區、兩個白區）的圖案。這就是常在新聞上看到的「沙灘球（Beachball）」，能告訴我們地震是正斷層、逆斷層還是平移斷層造成的。
        </div>
        <div class="interactive-area">
            <h3>沙灘球 (Focal Mechanism) 概念圖</h3>
            <div class="anim-box" style="height: 250px;">
                <svg width="200" height="200" viewBox="0 0 200 200">
                    <circle cx="100" cy="100" r="90" fill="white" stroke="#2c3e50" stroke-width="3"/>
                    <path d="M 100 10 A 90 90 0 0 1 190 100 L 100 100 Z" fill="#2c3e50"/>
                    <path d="M 100 190 A 90 90 0 0 1 10 100 L 100 100 Z" fill="#2c3e50"/>
                    <text x="130" y="60" fill="white" font-weight="bold">初動向上</text>
                    <text x="135" y="75" fill="white" font-size="12">(壓縮)</text>
                    
                    <text x="25" y="150" fill="white" font-weight="bold">初動向上</text>
                    <text x="30" y="165" fill="white" font-size="12">(壓縮)</text>
                    
                    <text x="25" y="60" fill="#2c3e50" font-weight="bold">初動向下</text>
                    <text x="30" y="75" fill="#2c3e50" font-size="12">(膨脹)</text>
                    
                    <text x="130" y="150" fill="#2c3e50" font-weight="bold">初動向下</text>
                    <text x="135" y="165" fill="#2c3e50" font-size="12">(膨脹)</text>
                </svg>
            </div>
            <p>這是一個標準的平移斷層沙灘球示意圖（黑色代表壓縮象限，白色代表膨脹象限）。</p>
        </div>
    </section>

    <section id="ch1-6" class="card">
        <h1>6. 逆問題與模型建構</h1>
        <div class="citation">
            「地震學的特徵是解決「逆問題」，即透過觀測到的地震圖，反過來推導震源的特性與介質的結構。這類問題常面臨數據不足、解的非唯一性，以及觀測上的隨機性（Aleatory）與認知性（Epistemic）不確定性。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            <ul>
                <li><strong>正問題：</strong> 我知道炸彈在哪裡、地質長怎樣 $\rightarrow$ 計算出地震圖會長什麼樣。（由因推果）</li>
                <li><strong>逆問題：</strong> 拿到了地震圖 $\rightarrow$ 像偵探一樣反推炸彈在哪、地質長怎樣。（由果推因，這正是地震學家在做的事）</li>
            </ul>
            因為全世界的地震儀不夠多（像海洋就很少），導致線索永遠不足。有時候兩種完全不同的地質構造，卻會產生一模一樣的地震圖（非唯一解）。加上儀器誤差（隨機性）與人類物理知識的極限（認知性），使得地震模型永遠存在不確定性。
        </div>
    </section>

    <section id="ch2-1" class="card">
        <h1>2.1 地震危害 vs 風險 & 工程地震學</h1>
        <div class="citation">
            「地震危害 (Hazard)：指地震發生與地表震動等自然現象，是無可避免的地質事實。<br>
            地震風險 (Risk)：指危害對人類生命財產造成的威脅。風險高低受人類行為影響。<br>
            建築物在地震中的破壞程度取決於其共振週期（Resonant period）。當地震波主要週期與建築共振週期相近時，會造成嚴重破壞。鬆軟沉積物會產生場地效應（Site effects）放大震動（如1985墨西哥城地震）。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            地震本身是「危害」（天意），但房子倒塌壓死人是「風險」（可透過工程改變）。<br>
            工程地震學最關注「加速度（g）」。每棟房子都有自己的「共振週期」（搖晃一次的時間），通常樓層越高，週期越長。如果地震波的頻率剛好對上房子的週期，就像幫盪鞦韆順勢推一把，房子會越搖越大，這叫「共振效應」。另外，蓋在軟泥土（盆地）上的房子，地震波傳過來會被放大，這就是「場地效應」。
        </div>
        <div class="interactive-area">
            <h3>互動實驗室：建築共振模擬器</h3>
            <p>請拖拉滑桿，改變地震波的週期（頻率），觀察哪一棟建築晃動最劇烈！</p>
            <div class="slider-container">
                <span style="font-weight:bold;">地震波週期：短 (高頻)</span>
                <input type="range" id="waveFreq" min="1" max="3" value="1" step="1">
                <span style="font-weight:bold;">長 (低頻)</span>
            </div>
            <div class="anim-box" style="height: 250px; align-items: flex-end; justify-content: space-evenly; border-bottom: 5px solid #7f8c8d; background: #e8f4f8;">
                <div id="bldg1" style="width: 50px; height: 60px; background: #e74c3c; position: relative; transform-origin: bottom center; transition: 0.3s;">
                    <div style="color:white; text-align:center; font-size:12px; margin-top:5px;">矮房<br>(短週期)</div>
                </div>
                <div id="bldg2" style="width: 50px; height: 120px; background: #f1c40f; position: relative; transform-origin: bottom center; transition: 0.3s;">
                    <div style="text-align:center; font-size:12px; margin-top:5px;">中層<br>(中週期)</div>
                </div>
                <div id="bldg3" style="width: 50px; height: 200px; background: #3498db; position: relative; transform-origin: bottom center; transition: 0.3s;">
                    <div style="color:white; text-align:center; font-size:12px; margin-top:5px;">高樓<br>(長週期)</div>
                </div>
            </div>
            <div id="resonance-msg" style="margin-top: 15px; font-weight: bold; color: #e74c3c; font-size: 1.1rem;">目前高頻短週期波：矮房發生共振！</div>
            
            <script>
                document.getElementById('waveFreq').addEventListener('input', function() {
                    const val = parseInt(this.value);
                    const b1 = document.getElementById('bldg1');
                    const b2 = document.getElementById('bldg2');
                    const b3 = document.getElementById('bldg3');
                    const msg = document.getElementById('resonance-msg');
                    
                    // 重置動畫
                    b1.style.animation = 'none'; b2.style.animation = 'none'; b3.style.animation = 'none';
                    // 強制重繪
                    void b1.offsetWidth; void b2.offsetWidth; void b3.offsetWidth;
                    
                    // 定義搖晃動畫
                    const cssAnim = `
                        @keyframes shakeHigh { 0% {transform: rotate(0deg);} 25% {transform: rotate(20deg);} 50% {transform: rotate(0deg);} 75% {transform: rotate(-20deg);} 100% {transform: rotate(0deg);} }
                        @keyframes shakeMid { 0% {transform: rotate(0deg);} 25% {transform: rotate(15deg);} 50% {transform: rotate(0deg);} 75% {transform: rotate(-15deg);} 100% {transform: rotate(0deg);} }
                        @keyframes shakeLow { 0% {transform: rotate(0deg);} 25% {transform: rotate(10deg);} 50% {transform: rotate(0deg);} 75% {transform: rotate(-10deg);} 100% {transform: rotate(0deg);} }
                    `;
                    let styleSheet = document.getElementById('dynamic-shake');
                    if(!styleSheet) {
                        styleSheet = document.createElement("style");
                        styleSheet.id = "dynamic-shake";
                        document.head.appendChild(styleSheet);
                    }
                    styleSheet.innerText = cssAnim;

                    if(val === 1) {
                        b1.style.animation = 'shakeHigh 0.3s infinite';
                        msg.innerText = "目前高頻短週期波：矮房發生嚴重共振！";
                    } else if(val === 2) {
                        b2.style.animation = 'shakeMid 0.6s infinite';
                        msg.innerText = "目前中頻中週期波：中層建築發生共振！";
                    } else if(val === 3) {
                        b3.style.animation = 'shakeLow 1.2s infinite';
                        msg.innerText = "目前低頻長週期波：高樓層發生劇烈共振！(如墨西哥城案例)";
                    }
                });
                // 初始化
                document.getElementById('bldg1').style.animation = 'shakeHigh 0.3s infinite';
            </script>
        </div>
    </section>

    <section id="ch2-2" class="card">
        <h1>2.2 次生災害 & 地行動力衰減公式</h1>
        <div class="citation">
            「次生災害包括海嘯、火災，以及土壤液化（Soil liquefaction）：強烈震動使富含水分的鬆散沙土失去承載力，變得如同液體一般。<br>
            衰減公式：$a(M,r) = b10^{cM} r^{-d}$。地表加速度 $a$ 會隨地震規模 $M$ 增加而變大，並隨距離 $r$ 增加而衰減。能量衰減原因為幾何擴散與岩石地質特性。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            地震往往伴隨副產物：海底地震會引發海嘯；管線破裂引發大火；在充滿地下水的沙地，搖晃會讓沙粒間的水壓升高撐開沙粒，地表瞬間變成泥漿池（土壤液化），導致房子沉下去。<br>
            公式中的物理意義很直觀：地震越大（$M$大），搖得越厲害（$a$大）；離震央越遠（$r$大），能量散開了（幾何擴散），地層也會吸收能量，所以搖晃就變小。不同地區岩石硬度不同，衰減速度也不同。
        </div>
        <div class="interactive-area">
            <h3>公式計算機：評估地表加速度</h3>
            <p style="font-size:0.9rem; color:#666;">（此為簡化版衰減模型展示，假設 b=1, c=0.5, d=1.2）</p>
            <div style="display:flex; justify-content:center; gap:20px; margin-bottom: 20px;">
                <div>
                    <label>地震規模 $M$：</label>
                    <input type="number" id="calc-m" value="6.5" step="0.1" style="width:70px; padding:5px; border-radius:4px; border:1px solid #ccc;">
                </div>
                <div>
                    <label>距離震源 $r$ (km)：</label>
                    <input type="number" id="calc-r" value="20" step="5" style="width:70px; padding:5px; border-radius:4px; border:1px solid #ccc;">
                </div>
            </div>
            <button class="btn" onclick="calculateAttenuation()">計算相對加速度 $a$</button>
            <div id="calc-result" style="margin-top:20px; font-size:1.5rem; font-weight:bold; color:#d35400;"></div>
            <script>
                function calculateAttenuation() {
                    const m = parseFloat(document.getElementById('calc-m').value);
                    const r = parseFloat(document.getElementById('calc-r').value) || 1; // 避免除以0
                    // a = 1 * 10^(0.5M) * r^(-1.2)
                    const a = Math.pow(10, 0.5 * m) * Math.pow(r, -1.2);
                    document.getElementById('calc-result').innerHTML = `相對加速度 $a$ 約為：${a.toFixed(2)} 單位`;
                }
            </script>
        </div>
    </section>

    <section id="ch2-3" class="card">
        <h1>2.3 地震預報、預測與 Seismic Gap</h1>
        <div class="citation">
            「預報 (Forecasting)：長期評估，基於彈性反彈理論與歷史資料，評估未來（如數十年內）發生大地震的『機率』。<br>
            預測 (Prediction)：短期評估，試圖精準給出『確切時間、地點與規模』。<br>
            Seismic gap (地震空白區)：活躍斷層上長年未發生大地震的區段，因持續累積應力，被認為是未來最可能發生大地震以填補位移的危險區域。」
            <span class="source">[參考來源：2026/3/4 的所有記事]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            <ul>
                <li><strong>預報 (Forecasting) vs 預測 (Prediction)：</strong> 天氣預報可以告訴你明天的降雨機率，這叫 Forecasting（長期機率，有助於制定法規）。但如果有人跟你說「明天下午三點零五分台北車站會發生規模7.0地震」，這叫 Prediction。目前科學界普遍認為，短期的精準預測是無法實現的。</li>
                <li><strong>地震空白區 (Seismic Gap)：</strong> 想像一條拉鍊，上下兩端都拉開了（發生過地震釋放能量），中間卻卡住幾十年沒動。因為板塊還在不斷推擠，這個「卡住的空白區」累積的壓力最大，未來必定會發生大地震來「補齊」這段錯動。</li>
            </ul>
        </div>
    </section>

    <section id="ch2-4" class="card">
        <h1>2.4 預測方法與核試驗監測</h1>
        <div class="citation">
            「地震預測嘗試尋找前兆（Precursors）：前震、地下水/氣體變化（氡氣）、岩石物理性質改變、地表變形、動物異常行為。<br>
            核試驗監測：自然地震是斷層錯動（產生強烈剪力與表面波 $M_s$）；地下核爆是向外膨脹的壓縮爆炸（缺乏剪力，產生異常龐大的 P波/體波 $m_b$）。」
            <span class="source">[參考來源：2026/3/4 的所有記事, 02_1.2 Seismology and society (1).pdf]</span>
        </div>
        <div class="explanation">
            <strong>👨‍🏫 大師白話解析：</strong><br>
            科學家找過很多地震前兆，但沒有一個能 100% 準確預測。有時氡氣增加了卻沒地震，有時大地震前動物毫無反應。<br>
            不過地震學在「抓偷測核彈」上非常精準！這利用了波形特徵：
            <ul>
                <li><strong>天然地震：</strong> 兩塊石頭摩擦錯動 $\rightarrow$ 產生巨大的剪力波（S波與表面波 $M_s$ 大）。</li>
                <li><strong>地下核爆：</strong> 點狀炸藥向四面八方膨脹 $\rightarrow$ 只有強烈的推擠，幾乎沒有剪力（P波體波 $m_b$ 異常巨大，表面波 $M_s$ 極小）。</li>
            </ul>
            比較 $m_b$ 與 $M_s$ 的比例，就能讓秘密核爆無所遁形。
        </div>
    </section>

    <section id="quiz" class="card quiz-section">
        <h1>📝 單元總測驗</h1>
        <p>測試您對本章節核心知識的掌握度！作答完畢請點擊下方按鈕提交。</p>
        
        <form id="quiz-form">
            <div class="question" data-answer="B">
                <p>1. 為什麼科學家能推論出地球具有「液態外核」？</p>
                <div class="options">
                    <label><input type="radio" name="q1" value="A"> A) 深海鑽探船取得了外核的液體樣本</label>
                    <label><input type="radio" name="q1" value="B"> B) 地震波中的S波（剪力波）無法穿透液體，造成觀測上的陰影帶</label>
                    <label><input type="radio" name="q1" value="C"> C) P波抵達地表時的振幅異常龐大</label>
                    <label><input type="radio" name="q1" value="D"> D) 利用石油探勘的地震反射法直接照影</label>
                </div>
            </div>

            <div class="question" data-answer="D">
                <p>2. 下列關於地震波的敘述，何者<strong>錯誤</strong>？</p>
                <div class="options">
                    <label><input type="radio" name="q2" value="A"> A) P波的質點運動方向與傳播方向平行</label>
                    <label><input type="radio" name="q2" value="B"> B) 由於深部波速較快，地震波在地球內部的路徑會向下彎曲</label>
                    <label><input type="radio" name="q2" value="C"> C) 相位命名中，小寫 p 或 s 代表波先向上傳遞到地表再反射</label>
                    <label><input type="radio" name="q2" value="D"> D) Rayleigh波屬於體波的一種，是在地函中傳播的波</label>
                </div>
            </div>

            <div class="question" data-answer="B">
                <p>3. 關於地震與社會的連結，下列敘述何者正確？</p>
                <div class="options">
                    <label><input type="radio" name="q3" value="A"> A) 地震危害（Hazard）可以透過良好的建築工法來消除</label>
                    <label><input type="radio" name="q3" value="B"> B) 當地震波的主要週期與建築物的共振週期相近時，建築破壞最嚴重</label>
                    <label><input type="radio" name="q3" value="C"> C) 「預報（Forecasting）」是指精準預測明天發生的地震時間與地點</label>
                    <label><input type="radio" name="q3" value="D"> D) 土壤液化通常發生在堅硬的岩盤地質上</label>
                </div>
            </div>

            <div class="question" data-answer="C">
                <p>4. 國際監測系統如何利用地震學區分「天然地震」與「地下核試爆」？</p>
                <div class="options">
                    <label><input type="radio" name="q4" value="A"> A) 測量震源的深度，核爆通常發生在地函深處</label>
                    <label><input type="radio" name="q4" value="B"> B) 核試爆會產生強烈的表面波，而缺乏 P 波</label>
                    <label><input type="radio" name="q4" value="C"> C) 核爆缺乏剪力錯動，會產生異常巨大的 P 波（體波 $m_b$）且表面波（$M_s$）微小</label>
                    <label><input type="radio" name="q4" value="D"> D) 天然地震發生前一定會觀測到氡氣外洩，核爆則無</label>
                </div>
            </div>

            <button type="button" class="btn" onclick="gradeQuiz()" style="width: 100%; padding: 15px; font-size: 1.2rem; margin-top: 10px;">送出評分</button>
        </form>

        <div id="quiz-result" class="quiz-result">
            <h2 id="score-text" style="color: var(--primary-color); text-align: center;"></h2>
            <div id="feedback-area"></div>
            <div id="weak-analysis" class="weak-analysis"></div>
        </div>
    </section>

</main>

<script>
    // 側邊欄導航邏輯
    const navItems = document.querySelectorAll('.sidebar li[data-target]');
    const cards = document.querySelectorAll('.card');

    navItems.forEach(item => {
        item.addEventListener('click', () => {
            // 移除所有 active 狀態
            navItems.forEach(nav => nav.classList.remove('active'));
            cards.forEach(card => card.classList.remove('active'));
            
            // 添加當前 active 狀態
            item.classList.add('active');
            const targetId = item.getAttribute('data-target');
            document.getElementById(targetId).classList.add('active');
            
            // 滾動回頂部
            document.querySelector('.content-wrapper').scrollTo(0, 0);
        });
    });

    // 測驗評分邏輯
    function gradeQuiz() {
        const questions = document.querySelectorAll('.question');
        let score = 0;
        let feedbackHTML = '';
        let weakPoints = [];

        // 定義教科書詳解
        const explanations = [
            "詳解：S波（剪力波）無法在液體中傳播。科學家觀測到 S波無法穿透地球深處某個邊界，產生了S波陰影帶，從而證實了液態外核的存在。[參見 1.2 探索地球內部的工具]",
            "詳解：Rayleigh波屬於「表面波（Surface waves）」，只沿著地球表面傳播，並非在地球內部傳遞的體波（Body waves）。[參見 1.4 地震波種類]",
            "詳解：建築破壞程度取決於「共振週期」。當波的頻率吻合建築本身週期時會產生共振放大。危害(Hazard)是天災無法消除；預報(Forecasting)是長期機率評估；土壤液化發生在含水鬆散沙土。[參見 2.1 與 2.2]",
            "詳解：核爆是向外膨脹的爆炸力，沒有斷層滑動的剪力，因此會輻射出巨大的體波（$m_b$），而表面波（$M_s$）非常小。比較兩者比例即可鑑別。[參見 2.4 核試驗監測]"
        ];

        const topicLinks = [
            { name: "地球內部構造模型", target: "ch1-2" },
            { name: "地震波的種類與定義", target: "ch1-4" },
            { name: "工程地震學與次生災害", target: "ch2-1" },
            { name: "逆問題與核試爆監測", target: "ch2-4" }
        ];

        questions.forEach((q, index) => {
            const correctAns = q.getAttribute('data-answer');
            const selected = q.querySelector(`input[name="q${index+1}"]:checked`);
            
            if (selected) {
                if (selected.value === correctAns) {
                    score++;
                    feedbackHTML += `<div class="feedback-item correct"><strong>✅ 第 ${index+1} 題：答對！</strong><br>${explanations[index]}</div>`;
                } else {
                    feedbackHTML += `<div class="feedback-item incorrect"><strong>❌ 第 ${index+1} 題：答錯（您的答案：${selected.value}，正確為：${correctAns}）</strong><br>${explanations[index]}</div>`;
                    weakPoints.push(topicLinks[index]);
                }
            } else {
                feedbackHTML += `<div class="feedback-item incorrect"><strong>⚠️ 第 ${index+1} 題：未作答（正確為：${correctAns}）</strong><br>${explanations[index]}</div>`;
                weakPoints.push(topicLinks[index]);
            }
        });

        // 顯示分數
        const resultDiv = document.getElementById('quiz-result');
        document.getElementById('score-text').innerText = `總分：${score * 25} / 100 (${score}題答對 / ${4-score}題答錯)`;
        document.getElementById('feedback-area').innerHTML = feedbackHTML;

        // 弱點分析
        const analysisDiv = document.getElementById('weak-analysis');
        if (score === 4) {
            analysisDiv.innerHTML = "<strong>🎓 學習分析：</strong> 表現完美！您已徹底掌握第一章「地震學的基本概念與社會連結」的核心知識點。";
            analysisDiv.style.background = "#e8f5e9";
            analysisDiv.style.borderColor = "#c8e6c9";
            analysisDiv.style.color = "#2e7d32";
        } else {
            let suggestHTML = "<strong>🔍 弱點分析與改進建議：</strong><br>您在以下主題仍需加強，建議點擊返回對應章節重新複習教科書原文：<ul>";
            weakPoints.forEach(pt => {
                suggestHTML += `<li style="margin:5px 0;"><a href="javascript:void(0)" onclick="goToSection('${pt.target}')" style="color:#d35400; font-weight:bold; text-decoration:underline;">▶ 複習：${pt.name}</a></li>`;
            });
            suggestHTML += "</ul>";
            analysisDiv.innerHTML = suggestHTML;
            analysisDiv.style.background = "#fff3e0";
            analysisDiv.style.borderColor = "#ffe0b2";
            analysisDiv.style.color = "#e65100";
        }

        resultDiv.classList.add('show');
    }

    // 弱點跳轉輔助函數
    function goToSection(targetId) {
        document.querySelector(`.sidebar li[data-target="${targetId}"]`).click();
    }
</script>

</body>
</html>
