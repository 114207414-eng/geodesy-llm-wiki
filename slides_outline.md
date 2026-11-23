# 大地測量學（Geodesy）零基礎教學簡報大綱與視覺化設計手稿 (slides_outline.md)

本文件依據 `agent.md` 之 Node 3 規範編寫，並經過 Node 4「嚴格助教」兩輪嚴格審查與迭代修正（詳見 `check_log.md`）。專為「完全零基礎」的初學者設計一份邏輯嚴密、生動直觀、圖文並茂的 29 頁教學簡報大綱。每一頁投影片均包含：
1. **主題與教學目標**：說明該頁的核心教學主旨。
2. **來源出處標註**：嚴格 100% 標註對應之 `wiki/topic_XX`。
3. **初學者白話比喻與生活化解說**：將深奧數學物理名詞轉化為直觀生活經驗。
4. **核心知識點與公式**：依據 `wiki/` 內容條列嚴密重點。
5. **原生內嵌 SVG 原理示意圖**：包含清楚的幾何曲面、軸向箭頭、彩色標註、防呆提示與防重疊文字排版，無外部依賴。

---

## 目錄架構

- **第一單元：地球的真實面貌——從不規則大石塊到旋轉橢球**（第 1～4 頁）
- **第二單元：看不見的隱形手——地球重力場與大地水準面**（第 5～9 頁）
- **第三單元：搖擺的地球與天體坐標——我們在宇宙的哪裡？**（第 10～15 頁）
- **第四單元：空間幾何基準與參考橢球——給地球量身定做坐標**（第 16～22 頁）
- **第五單元：基準轉換與地圖投影——把三維地球攤平在圖紙上**（第 23～29 頁）

---

## 第一單元：地球的真實面貌——從不規則大石塊到旋轉橢球

### 第 1 頁：課程導言——為什麼地球不是完美的球體？
- **來源標註**：[`wiki/topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md)
- **初學者白話比喻**：想像你手裡握著一團軟黏土，當你把它放在陶藝轉盤上飛速旋轉時，黏土的中間會被甩得鼓出來，上下兩端會凹陷下去。地球不是一顆堅硬鋼珠，而是一個旋轉了四十幾億年的彈性巨星！
- **核心知識點**：
  - 地球表面積約 5.1 億 $\text{km}^2$，質量約 $5.976 \times 10^{24}\text{ kg}$。
  - 海洋占 70.8%（均深 3900 m），陸地占 29.2%（均高 840 m），最大地貌落差 19.9 km。
  - 大地測量學三大核心任務：測定地球幾何形狀、外部重力場及其隨時間的微小動態演化。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <!-- 背景網格 -->
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 對比輔助圓（正圓球形） -->
  <circle cx="400" cy="200" r="160" fill="none" stroke="#94a3b8" stroke-dasharray="6,6" stroke-width="2"/>
  <text x="400" y="30" text-anchor="middle" font-size="14" fill="#64748b" font-weight="bold">虛線：幾何正球體 (R = 6371 km)</text>
  <!-- 真實旋轉橢球（赤道隆起、兩極扁平） -->
  <ellipse cx="400" cy="200" rx="180" ry="145" fill="#e0f2fe" stroke="#0284c7" stroke-width="3" opacity="0.8"/>
  <!-- 自轉軸 (顯式箭頭，無依賴) -->
  <line x1="400" y1="35" x2="400" y2="375" stroke="#dc2626" stroke-width="2.5"/>
  <polygon points="400,20 393,35 407,35" fill="#dc2626"/>
  <text x="415" y="370" font-size="13" fill="#dc2626" font-weight="bold">地軸 (自轉軸 Z)</text>
  <!-- 赤道長半軸 a -->
  <line x1="400" y1="200" x2="580" y2="200" stroke="#0f172a" stroke-width="2.5"/>
  <polygon points="580,200 570,194 570,206" fill="#0f172a"/>
  <text x="490" y="190" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">長半軸 a = 6378 km</text>
  <!-- 極短半軸 b -->
  <line x1="400" y1="200" x2="400" y2="55" stroke="#0f172a" stroke-width="2.5"/>
  <polygon points="400,55 394,65 406,65" fill="#0f172a"/>
  <text x="330" y="125" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">短半軸 b = 6357 km</text>
  <!-- 扁率標註看板 -->
  <rect x="520" y="70" width="245" height="85" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="1.5"/>
  <text x="535" y="95" font-size="13" fill="#0369a1" font-weight="bold">幾何扁率 α = (a - b) / a</text>
  <text x="535" y="118" font-size="13" fill="#334155">地球扁率約 1 / 298.25</text>
  <text x="535" y="140" font-size="12" fill="#dc2626" font-weight="bold">赤道半徑比極半徑長約 21 公里！</text>
</svg>
```

---

### 第 2 頁：地球的幾何畸形——三軸橢球與「梨形」地球
- **來源標註**：[`wiki/topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md)
- **初學者白話比喻**：如果你以為地球只是個對稱的壓扁橘子，衛星會跳出來糾正你：地球其實像一顆「微微發胖的洋梨」！北極像梨子把兒稍微頂起，南極則像梨屁股微微下陷，中間赤道切開甚至也不是正圓形。
- **核心知識點**：
  - **三軸橢球**：赤道面本身是橢圓，長軸與短軸差約 211 公尺，長軸方向指向西經 35° 左右。
  - **梨形地球**：透過人造衛星軌道攝動分析（如斯密松天文台 C 系統），北極高出大地水準面約 10 m，南極下凹約 10 m，南北極兩端存在約 **20 公尺** 的非對稱幾何落差。
  - **大洋與陸地不對稱**：陸地 2/3 在北半球，南極為高聳大陸，北極為深邃洋盆。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 對稱橢圓基準 -->
  <ellipse cx="400" cy="200" rx="180" ry="140" fill="none" stroke="#94a3b8" stroke-dasharray="5,5" stroke-width="2"/>
  <text x="400" y="35" text-anchor="middle" font-size="13" fill="#64748b">灰虛線：理論對稱旋轉橢球</text>
  <!-- 梨形地球輪廓 (誇張化示意) -->
  <path d="M 400,45 C 470,45 570,120 580,200 C 590,280 480,355 400,355 C 320,355 210,280 220,200 C 230,120 330,45 400,45 Z" fill="#fef3c7" stroke="#d97706" stroke-width="3" opacity="0.85"/>
  <!-- 北極突起標示 -->
  <line x1="400" y1="45" x2="400" y2="60" stroke="#dc2626" stroke-width="3"/>
  <circle cx="400" cy="45" r="4" fill="#dc2626"/>
  <text x="420" y="55" font-size="13" fill="#b45309" font-weight="bold">北極隆起 (+10 m)</text>
  <!-- 南極凹陷標示 -->
  <line x1="400" y1="340" x2="400" y2="355" stroke="#dc2626" stroke-width="3"/>
  <circle cx="400" cy="355" r="4" fill="#dc2626"/>
  <text x="420" y="355" font-size="13" fill="#b45309" font-weight="bold">南極凹陷 (-10 m)</text>
  <!-- 說明看板 -->
  <rect x="50" y="140" width="190" height="90" rx="8" fill="#ffffff" stroke="#d97706" stroke-width="1.5"/>
  <text x="60" y="165" font-size="13" fill="#b45309" font-weight="bold">「梨形」落差約 20 m</text>
  <text x="60" y="190" font-size="12" fill="#475569">由衛星軌道攝動反求</text>
  <text x="60" y="210" font-size="12" fill="#64748b">工程上仍用旋轉橢球</text>
</svg>
```

---

### 第 3 頁：火箭發射的秘密——地球自轉與線速度
- **來源標註**：[`wiki/topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md)
- **初學者白話比喻**：想像你在玩旋轉木馬，騎在最外圈的小朋友風聲呼呼吹，跑得最快；站在轉盤正中央的人卻原地打轉。地球自轉時，赤道就是最外圈，站在赤道上你每秒鐘就跟著地球狂奔 465 公尺！
- **核心知識點**：
  - 自轉角速度：$\omega \approx 7.292115 \times 10^{-5}\text{ rad/s}$。
  - 任意緯度線速度公式：$V = \frac{2\pi R\cos\phi}{T} = V_{\text{赤道}}\cos\phi$。
  - 赤道線速度高達 **$465\text{ m/s}$**，北京（緯度 40°）降至 $355\text{ m/s}$，南北極點則為 **$0\text{ m/s}$**。
  - **航太意義**：火箭發射場選址盡可能靠近赤道（如法屬圭亞那庫魯發射場），能免費借用地球自轉動能，節省寶貴燃料。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地球半球 -->
  <ellipse cx="360" cy="200" rx="160" ry="140" fill="#e2e8f0" stroke="#475569" stroke-width="2"/>
  <!-- 自轉軸 -->
  <line x1="360" y1="30" x2="360" y2="370" stroke="#dc2626" stroke-width="2"/>
  <text x="370" y="50" font-size="13" fill="#dc2626" font-weight="bold">北極 (線速度 = 0 m/s)</text>
  <!-- 赤道切線箭頭 -->
  <line x1="360" y1="200" x2="520" y2="200" stroke="#0284c7" stroke-width="3"/>
  <line x1="520" y1="200" x2="680" y2="200" stroke="#16a34a" stroke-width="4"/>
  <polygon points="680,193 695,200 680,207" fill="#16a34a"/>
  <text x="540" y="190" font-size="14" fill="#15803d" font-weight="bold">赤道最大線速度 V = 465 m/s</text>
  <!-- 中緯度切線箭頭 -->
  <line x1="360" y1="110" x2="480" y2="110" stroke="#0284c7" stroke-width="2" stroke-dasharray="3,3"/>
  <line x1="480" y1="110" x2="590" y2="110" stroke="#ea580c" stroke-width="3"/>
  <polygon points="590,105 600,110 590,115" fill="#ea580c"/>
  <text x="490" y="100" font-size="13" fill="#c2410c" font-weight="bold">中緯度 (40°N) V = 355 m/s</text>
  <!-- 說明卡片 -->
  <rect x="540" y="270" width="230" height="90" rx="8" fill="#ffffff" stroke="#16a34a" stroke-width="1.5"/>
  <text x="550" y="295" font-size="13" fill="#15803d" font-weight="bold">為什麼發射火箭向東射？</text>
  <text x="550" y="320" font-size="12" fill="#334155">順著地球自轉方向發射，</text>
  <text x="550" y="340" font-size="12" fill="#334155">免費獲取 465 m/s 初始速度！</text>
</svg>
```

---

### 第 4 頁：大氣層的電磁迷霧——電離層色散與雙頻 GPS
- **來源標註**：[`wiki/topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md)
- **初學者白話比喻**：想像衛星訊號是一束光穿透有顏色的玻璃水。水氣主要在對流層（天氣變化），而高空 300 公里有一層帶電微粒（電離層），會把不同頻率的無線電波減慢不同幅度（色散）。測量學家怎麼破解？派兩隻不同頻率的偵察兵（雙頻）一起走，比對時間差就能精確扣除干擾！
- **核心知識點**：
  - 大氣垂直五層：對流層（每升高 1 km 降溫 6.5℃）、平流層、中層、熱層（電離層）、散逸層。
  - **電離層（80–800 km）**：電子密度在 300–400 km 達最高峰，具備顯著**電磁波色散效應**。
  - **GPS 雙頻解算原理**：使用 $L_1$（1.575 GHz）與 $L_2$（1.227 GHz）兩個頻率，利用色散差分直接消除一階電離層延遲誤差。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 大氣分層長條 -->
  <rect x="80" y="40" width="300" height="60" fill="#fed7aa" opacity="0.6"/>
  <text x="90" y="75" font-size="13" fill="#9a3412" font-weight="bold">電離層 (80 - 800 km)</text>
  <rect x="80" y="100" width="300" height="40" fill="#e2e8f0"/>
  <text x="90" y="125" font-size="12" fill="#475569">中層 (50 - 80 km)</text>
  <rect x="80" y="140" width="300" height="40" fill="#bae6fd" opacity="0.6"/>
  <text x="90" y="165" font-size="12" fill="#0369a1">平流層 (臭氧層 10 - 50 km)</text>
  <rect x="80" y="180" width="300" height="50" fill="#bbf7d0" opacity="0.7"/>
  <text x="90" y="210" font-size="13" fill="#15803d" font-weight="bold">對流層 (天氣現象 0 - 10 km)</text>
  <!-- 地表 -->
  <line x1="60" y1="230" x2="400" y2="230" stroke="#334155" stroke-width="3"/>
  <text x="180" y="255" font-size="13" fill="#334155" font-weight="bold">地球表面</text>
  <!-- 雙頻消除圖示 -->
  <circle cx="580" cy="50" r="14" fill="#0284c7"/>
  <text x="610" y="55" font-size="14" fill="#0369a1" font-weight="bold">GPS 衛星</text>
  <!-- 兩道電磁波 -->
  <path d="M 580,65 Q 560,140 540,230" fill="none" stroke="#2563eb" stroke-width="2.5"/>
  <text x="460" y="140" font-size="12" fill="#1d4ed8" font-weight="bold">L1: 1.575 GHz</text>
  <path d="M 580,65 Q 620,140 600,230" fill="none" stroke="#7c3aed" stroke-width="2.5" stroke-dasharray="4,4"/>
  <text x="610" y="140" font-size="12" fill="#6d28d9" font-weight="bold">L2: 1.227 GHz</text>
  <!-- 接收機 -->
  <rect x="520" y="230" width="100" height="40" rx="6" fill="#334155"/>
  <text x="535" y="255" font-size="12" fill="#ffffff" font-weight="bold">雙頻接收機</text>
  <!-- 結論看板 -->
  <rect x="440" y="300" width="320" height="70" rx="8" fill="#ffffff" stroke="#2563eb" stroke-width="1.5"/>
  <text x="450" y="325" font-size="13" fill="#1e40af" font-weight="bold">色散差分消除一階延遲</text>
  <text x="450" y="348" font-size="12" fill="#475569">利用兩頻率延遲差值，直接計算出大氣延遲量</text>
</svg>
```

---

## 第二單元：看不見的隱形手——地球重力場與大地水準面

### 第 5 頁：什麼是重力？萬有引力與離心力的合力
- **來源標註**：[`wiki/topic_02`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_02_地球重力場與重力位理論.md)
- **初學者白話比喻**：你站在磅秤上稱出的體重，其實不是單純的萬有引力！因為地球一直在旋轉，離心力會輕微把你往外甩。所以「重力」是萬有引力與離心力拔河妥協後的合力。在赤道甩得最凶，所以去赤道量體重會稍微變輕！
- **核心知識點**：
  - 向量合成公式：$\mathbf{g} = \mathbf{F} + \mathbf{P}$。
  - **引力 $\mathbf{F}$**：指向地心，由地球質量分布決定。
  - **離心力 $\mathbf{P}$**：垂直背離自轉軸，$P = \omega^2 r\cos\phi$。
  - **赤道重力小（約 978 Gal），兩極重力大（約 983 Gal）**：
    1. 兩極離地心近（極曲率效應）；
    2. 赤道離心力最大（約 3.4 Gal），抵消了部分引力。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地表點 P -->
  <circle cx="360" cy="180" r="7" fill="#0f172a"/>
  <text x="340" y="170" font-size="16" fill="#0f172a" font-weight="bold">測點 P</text>
  <!-- 萬有引力向量 F -->
  <line x1="360" y1="180" x2="240" y2="300" stroke="#2563eb" stroke-width="3.5"/>
  <polygon points="240,300 248,288 256,296" fill="#2563eb"/>
  <text x="210" y="270" font-size="14" fill="#1d4ed8" font-weight="bold">萬有引力 F (向地心)</text>
  <!-- 離心力向量 P -->
  <line x1="360" y1="180" x2="480" y2="180" stroke="#ea580c" stroke-width="3"/>
  <polygon points="480,180 470,174 470,186" fill="#ea580c"/>
  <text x="490" y="185" font-size="14" fill="#c2410c" font-weight="bold">自轉離心力 P (背離地軸)</text>
  <!-- 合力重力向量 g -->
  <line x1="360" y1="180" x2="330" y2="330" stroke="#16a34a" stroke-width="4"/>
  <polygon points="330,330 334,316 345,322" fill="#16a34a"/>
  <text x="340" y="325" font-size="16" fill="#15803d" font-weight="bold">地球重力 g = F + P</text>
  <!-- 鉛垂線說明 -->
  <rect x="520" y="50" width="250" height="95" rx="8" fill="#ffffff" stroke="#16a34a" stroke-width="1.5"/>
  <text x="535" y="75" font-size="14" fill="#15803d" font-weight="bold">鉛垂線的本質</text>
  <text x="535" y="100" font-size="12" fill="#334155">重物懸掛靜止時的方向，</text>
  <text x="535" y="120" font-size="12" fill="#334155">指向合力 g 方向，並非精確指向地心！</text>
</svg>
```

---

### 第 6 頁：什麼是「高度」？大地水準面與不平行的水準面
- **來源標註**：[`wiki/topic_02`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_02_地球重力場與重力位理論.md)
- **初學者白話比喻**：你可能以為「水平面」就像一張平整的桌子，大家彼此平行。但物理學告訴我們：水往低處流是因為「重力位能差」。因為地球各處密度不均勻，地球的等位水準面其實像層層疊疊、彼此歪歪扭扭的洋蔥皮——**它們永遠不會相交，但也絕對不平行**！
- **核心知識點**：
  - **大地水準面（Geoid）**：完全靜止的平均海水面穿過陸地所形成的閉合重力等位面（$W = W_0$）。
  - **水準面微分間距公式**：$dl = -\frac{dW}{g}$。
  - 因為地表各處重力 $g$ 大小不一，相同的位能差 $dW$ 在重力大的地方間距 $dl$ 窄、重力小的地方間距寬，所以水準面彼此**不平行且永不相交**。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 水準面 1 (大地水準面 W1) -->
  <path d="M 80,180 Q 250,150 450,190 T 720,160" fill="none" stroke="#0284c7" stroke-width="3.5"/>
  <text x="730" y="165" font-size="14" fill="#0369a1" font-weight="bold">大地水準面 W1 (海平面)</text>
  <!-- 水準面 2 (高處等位面 W2) -->
  <path d="M 80,90 Q 250,70 450,120 T 720,70" fill="none" stroke="#0ea5e9" stroke-width="2.5" stroke-dasharray="6,4"/>
  <text x="730" y="75" font-size="14" fill="#0284c7" font-weight="bold">重力等位面 W2 (高處)</text>
  <!-- 重力大處 (間距狹窄) -->
  <line x1="220" y1="78" x2="220" y2="155" stroke="#dc2626" stroke-width="2"/>
  <text x="140" y="120" font-size="12" fill="#b91c1c" font-weight="bold">g 較大 → 間距窄</text>
  <!-- 重力小處 (間距較寬) -->
  <line x1="500" y1="115" x2="500" y2="185" stroke="#16a34a" stroke-width="2"/>
  <text x="510" y="150" font-size="12" fill="#15803d" font-weight="bold">g 較小 → 間距寬</text>
  <!-- 公式框 -->
  <rect x="250" y="270" width="300" height="75" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="1.5"/>
  <text x="270" y="300" font-size="15" fill="#0369a1" font-weight="bold">核心公式：dl = - dW / g</text>
  <text x="270" y="325" font-size="12" fill="#475569">水準面彼此既不平行，也絕對不相交！</text>
</svg>
```

---

### 第 7 頁：理想與現實的折衷——正常重力位與擾動位 T
- **來源標註**：[`wiki/topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)
- **初學者白話比喻**：真實地球內部有大山、深溝、岩漿庫，質量亂七八糟，就像一顆凹凸不平的發泡馬鈴薯，重力公式根本寫不出來。聰明的大地測量學家怎麼做？我們先捏一個光溜溜、非常完美的「標準橢球重力場」（吸走 99.9% 效應），剩下的細微凹凸叫「擾動位 T」，研究目標頓時變得超級簡單！
- **核心知識點**：
  - 重力位分解：$W = U + T$（真實重力位 = 正常重力位 + 擾動位）。
  - **正常重力位 $U$**：數學上光滑的標準水準橢球場，吸收了地球 99.9% 以上的引力特徵。
  - **三大簡化假設**：
    1. 坐標原點置於地球質心（消除一階項 $v_1 = 0$）；
    2. 坐標軸對齊主慣性軸；
    3. 假定繞地軸旋轉對稱（東西方向無質量偏差，消除經度項）。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 光滑水準橢球 U -->
  <ellipse cx="400" cy="200" rx="200" ry="120" fill="none" stroke="#2563eb" stroke-width="3"/>
  <text x="610" y="190" font-size="14" fill="#1d4ed8" font-weight="bold">正常水準橢球 U (99.9%)</text>
  <!-- 起伏的大地水準面 W -->
  <path d="M 200,200 Q 250,60 400,75 Q 520,90 600,200 Q 550,330 400,320 Q 260,310 200,200 Z" fill="none" stroke="#d97706" stroke-width="3" stroke-dasharray="6,4"/>
  <text x="400" y="55" text-anchor="middle" font-size="14" fill="#b45309" font-weight="bold">真實大地水準面 W</text>
  <!-- 擾動位 T / 大地起伏 N -->
  <line x1="400" y1="75" x2="400" y2="80" stroke="#dc2626" stroke-width="3"/>
  <text x="415" y="105" font-size="13" fill="#dc2626" font-weight="bold">起伏落差 N (擾動位 T 產生)</text>
  <!-- 公式框 -->
  <rect x="250" y="340" width="300" height="45" rx="6" fill="#ffffff" stroke="#475569" stroke-width="1"/>
  <text x="400" y="368" text-anchor="middle" font-size="15" fill="#0f172a" font-weight="bold">W = U + T （研究轉化為求解 T）</text>
</svg>
```

---

### 第 8 頁：不鑽地心也能算扁率——克萊羅定理與索米里安納公式
- **來源標註**：[`wiki/topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)
- **初學者白話比喻**：你不用鑽入地球內部去量極半徑有多短。十八世紀數學家克萊羅發現了一個神奇橋樑：只要在地表各處量測重力加速度的變化幅度，配合地球自轉速度，就能精確倒推算出地球的幾何扁率！
- **核心知識點**：
  - **克萊羅定理（Clairaut's Theorem）**：
    $$\alpha + \beta = \frac{5}{2}q$$
    - $\alpha = \frac{a - b}{a}$：幾何扁率（約 $1/298.25$）。
    - $\beta = \frac{\gamma_p - \gamma_e}{\gamma_e}$：重力扁率（極點正常重力與赤道正常重力之相對變化率，約 $0.0053$）。
    - $q = \frac{\omega^2 a}{g_e} \approx \frac{1}{289}$：赤道離心力與赤道重力之比。
  - **索米里安納閉合公式（WGS-84 核心）**：
    $$\gamma = \gamma_e \frac{1 + K\sin^2\phi}{\sqrt{1 - e^2\sin^2\phi}}$$
    GPS 晶片內部採用的無截斷誤差閉合解。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 天平兩端對比 -->
  <line x1="200" y1="160" x2="600" y2="160" stroke="#334155" stroke-width="4"/>
  <polygon points="400,160 380,210 420,210" fill="#64748b"/>
  <!-- 左端：幾何形狀 -->
  <circle cx="200" cy="120" r="35" fill="#dbeafe" stroke="#2563eb" stroke-width="2"/>
  <text x="200" y="115" text-anchor="middle" font-size="13" fill="#1e40af" font-weight="bold">幾何扁率</text>
  <text x="200" y="135" text-anchor="middle" font-size="16" fill="#1e40af" font-weight="bold">α = (a-b)/a</text>
  <!-- 右端：物理重力 -->
  <circle cx="600" cy="120" r="35" fill="#dcfce7" stroke="#16a34a" stroke-width="2"/>
  <text x="600" y="115" text-anchor="middle" font-size="13" fill="#166534" font-weight="bold">重力扁率</text>
  <text x="600" y="135" text-anchor="middle" font-size="16" fill="#166534" font-weight="bold">β = Δγ/γe</text>
  <!-- 中間紐帶：克萊羅定理 -->
  <rect x="230" y="235" width="340" height="80" rx="8" fill="#ffffff" stroke="#dc2626" stroke-width="2"/>
  <text x="400" y="265" text-anchor="middle" font-size="17" fill="#b91c1c" font-weight="bold">α + β = (5/2) q</text>
  <text x="400" y="292" text-anchor="middle" font-size="13" fill="#475569">地表量重力差值 → 反求地球幾何扁平度！</text>
</svg>
```

---

### 第 9 頁：爬山量重力會變輕？自由空間高程修正
- **來源標註**：[`wiki/topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)
- **初學者白話比喻**：萬有引力跟距離的平方成反比。當你從海平面爬到 101 大樓頂端或玉山山頂，你離地心變遠了，地心對你的吸力自然下降。大地測量中，這個因為「站得高」而引起的重力自然遞減，稱為自由空間高程修正。
- **核心知識點**：
  - 自由空間高程修正（Free-air Correction）：
    $$\Delta_1 g \approx \frac{2\gamma_0}{R}h \approx 0.3086 h\text{ (mGal)}$$
  - **黃金速算法則**：**每爬升 3 公尺，重力值約減少 1 mGal**。
  - 高度 $h$ 處的正常重力公式：$\gamma = (\gamma_0 - 0.3086h) \times 10^{-3}\text{ Gal}$。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 山丘地形輪廓 -->
  <path d="M 100,320 L 300,320 L 480,120 L 560,180 L 700,320 Z" fill="#e2e8f0" stroke="#475569" stroke-width="2.5"/>
  <!-- 海平面基準 -->
  <line x1="80" y1="320" x2="720" y2="320" stroke="#0284c7" stroke-width="3"/>
  <text x="120" y="345" font-size="14" fill="#0369a1" font-weight="bold">海平面 (h = 0, γ = γ₀)</text>
  <!-- 山頂測點 -->
  <circle cx="480" cy="120" r="6" fill="#dc2626"/>
  <text x="500" y="115" font-size="14" fill="#dc2626" font-weight="bold">山頂高程 h</text>
  <!-- 高度線 h -->
  <line x1="480" y1="120" x2="480" y2="320" stroke="#dc2626" stroke-width="2" stroke-dasharray="4,4"/>
  <text x="490" y="220" font-size="14" fill="#dc2626" font-weight="bold">高差 h</text>
  <!-- 衰減說明卡片 -->
  <rect x="140" y="70" width="260" height="90" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="1.5"/>
  <text x="155" y="95" font-size="14" fill="#0369a1" font-weight="bold">自由空間修正法則</text>
  <text x="155" y="122" font-size="13" fill="#b91c1c" font-weight="bold">每上升 3 公尺，減少 1 mGal</text>
  <text x="155" y="145" font-size="12" fill="#475569">Δg = 0.3086 × h (mGal)</text>
</svg>
```

---

## 第三單元：搖擺的地球與天體坐標——我們在宇宙的哪裡？

### 第 10 頁：晃動的陀螺——歲差、章動與極移
- **來源標註**：[`wiki/topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)
- **初學者白話比喻**：想像你在轉陀螺。當陀螺旋轉變慢時，陀螺的軸會在空中畫出一個優雅的大圈圈（歲差，26,000年一圈）；要是旁邊有人輕輕敲轉軸，軸心還會微微發抖（章動，18.6年一週期）。這兩者是整顆地球連同軸心一起在太空中晃動！而「極移」則是軸心不動，地表的泥土自己像晃動的蛋黃，在地表一個足球場大小（20米）的範圍內畫圈圈！
- **核心知識點**：
  - **歲差**：日、月引力矩作用於赤道隆起，自轉軸繞黃極旋轉，週期約 **25,800 年**，春分點西移 **50.3″/年**。
  - **章動**：白道面傾斜 5° 引發短週期抖動，主週期 **18.6 年**，振幅 **9.21″**。
  - **極移**：地軸相對地殼晃動。包含張德勒擺動（435天約 6m）、周年項（2m）、極漂移（3.7 mas/年向格陵蘭），整體變動範圍約 **20 公尺**（一個足球場大小）。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 歲差圓錐體 -->
  <polygon points="400,260 280,60 520,60" fill="#fed7aa" opacity="0.4"/>
  <ellipse cx="400" cy="60" rx="120" ry="25" fill="none" stroke="#ea580c" stroke-width="2.5" stroke-dasharray="4,4"/>
  <!-- 黃北極軸 -->
  <line x1="400" y1="260" x2="400" y2="25" stroke="#334155" stroke-width="2"/>
  <polygon points="400,20 395,30 405,30" fill="#334155"/>
  <text x="415" y="30" font-size="13" fill="#334155" font-weight="bold">黃北極 (垂直黃道)</text>
  <!-- 自轉瞬時地軸 -->
  <line x1="400" y1="260" x2="510" y2="65" stroke="#dc2626" stroke-width="3"/>
  <polygon points="510,65 500,72 505,80" fill="#dc2626"/>
  <text x="520" y="65" font-size="13" fill="#dc2626" font-weight="bold">自轉軸 (地軸)</text>
  <!-- 章動微幅波浪 -->
  <path d="M 500,55 Q 510,65 520,58 T 530,70" fill="none" stroke="#7c3aed" stroke-width="3"/>
  <text x="535" y="85" font-size="12" fill="#6d28d9" font-weight="bold">章動抖動 (18.6年)</text>
  <!-- 歲差箭頭 -->
  <path d="M 460,40 A 120,25 0 0,1 515,65" fill="none" stroke="#ea580c" stroke-width="3"/>
  <polygon points="515,65 505,58 518,52" fill="#ea580c"/>
  <text x="430" y="20" font-size="13" fill="#c2410c" font-weight="bold">歲差進動 (26,000年)</text>
  <!-- 極移小看板 -->
  <rect x="60" y="80" width="200" height="110" rx="8" fill="#ffffff" stroke="#2563eb" stroke-width="1.5"/>
  <text x="75" y="105" font-size="13" fill="#1d4ed8" font-weight="bold">極移 (Polar Motion)</text>
  <text x="75" y="128" font-size="12" fill="#334155">地軸相對地表滑移</text>
  <text x="75" y="148" font-size="12" fill="#334155">張德勒擺動 (435天)</text>
  <text x="75" y="168" font-size="12" fill="#dc2626" font-weight="bold">晃動範圍約 20 公尺！</text>
</svg>
```

---

### 第 11 頁：空間坐標階梯——從宇宙天球 (CIS) 到腳底測站 (CTS)
- **來源標註**：[`wiki/topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)
- **初學者白話比喻**：GPS 衛星在太空中飛行，遵守牛頓力學，必須釘在遙遠恆星為背景的「太空慣性系」（CIS）裡算軌道；但我們在地面測量，房子和公路是跟著地球轉的，必須用「地心地固系」（CTS/ECEF）。
  - *為什麼叫「協議（Conventional）」？* 因為地球天天在晃動，宇宙中沒有大自然天生寫好的坐標軸，所以是全球頂尖科學家坐下來開會、投票協商（協議）出的一套標準坐標軸！
- **核心知識點**：
  - **CIS（協議天球坐標系）**：原點在質心，指向 J2000.0 平極與平春分點，近似慣性系，用於計算衛星星曆。
  - **CTS / ECEF（協議地球坐標系）**：原點在質心，$Z$ 軸指向 CIO 平北極，$X$ 軸指向 IRM 子午線，隨地球轉動。
  - **地球定向參數（EOP）**：IERS 發布的轉換樞紐（包含 UT1、極坐標 $x, y$、天極偏差）。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 流程方塊階梯 -->
  <rect x="60" y="60" width="180" height="60" rx="8" fill="#e0e7ff" stroke="#4338ca" stroke-width="2"/>
  <text x="150" y="85" text-anchor="middle" font-size="13" fill="#3730a3" font-weight="bold">瞬時天球坐標系</text>
  <text x="150" y="105" text-anchor="middle" font-size="11" fill="#4338ca">真北天極 / 真春分點</text>

  <line x1="240" y1="90" x2="310" y2="90" stroke="#6366f1" stroke-width="3"/>
  <polygon points="310,90 300,84 300,96" fill="#6366f1"/>
  <text x="275" y="80" text-anchor="middle" font-size="11" fill="#4f46e5">歲差章動</text>

  <rect x="310" y="60" width="180" height="60" rx="8" fill="#e0e7ff" stroke="#4338ca" stroke-width="2"/>
  <text x="400" y="85" text-anchor="middle" font-size="13" fill="#3730a3" font-weight="bold">協議天球 (CIS)</text>
  <text x="400" y="105" text-anchor="middle" font-size="11" fill="#4338ca">J2000.0 / 衛星軌道</text>

  <line x1="490" y1="90" x2="560" y2="90" stroke="#6366f1" stroke-width="3"/>
  <polygon points="560,90 550,84 550,96" fill="#6366f1"/>
  <text x="525" y="80" text-anchor="middle" font-size="11" fill="#4f46e5">自轉角 UT1</text>

  <rect x="560" y="60" width="180" height="60" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2"/>
  <text x="650" y="85" text-anchor="middle" font-size="13" fill="#14532d" font-weight="bold">協議地球 (CTS/ECEF)</text>
  <text x="650" y="105" text-anchor="middle" font-size="11" fill="#15803d">CIO平極 / WGS84地固</text>

  <!-- 下層地平站心 -->
  <line x1="650" y1="120" x2="650" y2="200" stroke="#16a34a" stroke-width="3"/>
  <polygon points="650,200 644,190 656,190" fill="#16a34a"/>
  <text x="695" y="160" text-anchor="middle" font-size="12" fill="#15803d">極移改正 (x, y)</text>

  <rect x="560" y="200" width="180" height="60" rx="8" fill="#fef3c7" stroke="#b45309" stroke-width="2"/>
  <text x="650" y="225" text-anchor="middle" font-size="13" fill="#78350f" font-weight="bold">測站地平 (站心)</text>
  <text x="650" y="245" text-anchor="middle" font-size="11" fill="#b45309">東北天 (n, e, u)</text>
</svg>
```

---

### 第 12 頁：鉛垂線與法線的叉路——垂線偏差與拉普拉斯方程
- **來源標註**：[`wiki/topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)
- **初學者白話比喻**：拿一條繩子掛鉛錘，它指的是「真正的重力方向」（鉛垂線）；而在電腦數學模型裡，橢圓球面的垂直線叫「法線」。因為地球各處有山脈吸引，鉛垂線和幾何法線**根本不在同一條直線上**！這兩條線在空中的夾角，就叫「垂線偏差」。
- **核心知識點**：
  - **垂線偏差 $(\xi, \eta)$**：鉛垂線與橢球法線的夾角（$\xi$ 為子午圈分量，$\eta$ 為卯酉圈分量）。
  - **坐標關係**：$\phi_G = \Phi_A - \xi$，$\lambda_G = \Lambda_A - \eta\sec\phi$。
  - **拉普拉斯方程式**：$\alpha_A - \alpha_G = (\Lambda_A - \lambda_G)\sin\phi_A \implies \alpha_G = \alpha_A - \eta\tan\phi$。
  - **大地原點定向**：傳統區域基準在大地原點人為假設 $\xi_0 = \eta_0 = N_0 = 0$。
- **內嵌原生 SVG 幾何圖解（防重疊設計）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地表點 P -->
  <circle cx="400" cy="180" r="7" fill="#0f172a"/>
  <text x="400" y="160" text-anchor="middle" font-size="16" fill="#0f172a" font-weight="bold">測站 P</text>
  <!-- 橢球幾何法線 (綠色) -->
  <line x1="400" y1="180" x2="330" y2="340" stroke="#16a34a" stroke-width="3.5"/>
  <text x="250" y="335" font-size="14" fill="#15803d" font-weight="bold">橢球法線 (幾何基準)</text>
  <!-- 真實鉛垂線 (紅色) -->
  <line x1="400" y1="180" x2="470" y2="340" stroke="#dc2626" stroke-width="3.5"/>
  <text x="480" y="335" font-size="14" fill="#b91c1c" font-weight="bold">鉛垂線 (重力基準)</text>
  <!-- 夾角弧線 (垂線偏差) 與獨立標註防重疊框 -->
  <path d="M 370,240 A 60,60 0 0,0 430,240" fill="none" stroke="#2563eb" stroke-width="2.5"/>
  <rect x="330" y="250" width="140" height="30" rx="4" fill="#ffffff" stroke="#2563eb" stroke-width="1.2"/>
  <text x="400" y="270" text-anchor="middle" font-size="13" fill="#1d4ed8" font-weight="bold">垂線偏差 θ (ξ, η)</text>
  <!-- 說明牌 -->
  <rect x="520" y="50" width="250" height="85" rx="8" fill="#ffffff" stroke="#2563eb" stroke-width="1.5"/>
  <text x="535" y="75" font-size="14" fill="#1e40af" font-weight="bold">拉普拉斯方位角方程式</text>
  <text x="535" y="100" font-size="13" fill="#334155">α_G = α_A - η · tan(φ)</text>
  <text x="535" y="120" font-size="12" fill="#64748b">用以檢核與定向測量方位</text>
</svg>
```

---

### 第 13 頁：格林威治的 102 米之謎——為什麼銅線上 GPS 讀不出 0 度？
- **來源標註**：[`wiki/topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)
- **初學者白話比喻**：你去英國倫敦格林威治皇家天文台旅遊，雙腳跨在地面那條著名歷史銅線上拍照，興奮地掏出智慧手機打開 GPS，卻驚訝發現：手機經度居然顯示「西經 0.0015°」，而不是 0 度！難道天文學家畫錯了嗎？
- **核心知識點**：
  - **歷史基準（1884 年）**：喬治·艾里的「艾里中星儀」以測站鉛垂線為基準（天文局部重力坐標）。
  - **現代基準（IRM / WGS84）**：以全體地球質心為原點、以幾何橢球法線為基準。
  - **偏差本質**：格林威治當地存在約 **5.6″ 的垂線偏差**，導致歷史鉛垂線與地心幾何法線產生夾角，使得現代衛星零度子午線往東偏移了 **102 公尺**！
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地表 -->
  <line x1="100" y1="260" x2="700" y2="260" stroke="#334155" stroke-width="4"/>
  <!-- 歷史天文台銅線 (1884) -->
  <line x1="300" y1="80" x2="300" y2="260" stroke="#d97706" stroke-width="4"/>
  <rect x="292" y="250" width="16" height="20" fill="#d97706"/>
  <text x="300" y="60" text-anchor="middle" font-size="14" fill="#b45309" font-weight="bold">歷史銅線 (艾里中星儀)</text>
  <text x="300" y="295" text-anchor="middle" font-size="12" fill="#b45309">天文經度 0° (重力鉛垂)</text>
  <!-- 現代 IRM 子午線 (WGS84) -->
  <line x1="520" y1="80" x2="520" y2="260" stroke="#0284c7" stroke-width="4"/>
  <circle cx="520" cy="260" r="7" fill="#0284c7"/>
  <text x="520" y="60" text-anchor="middle" font-size="14" fill="#0369a1" font-weight="bold">現代 IRM 子午線 (GPS)</text>
  <text x="520" y="295" text-anchor="middle" font-size="12" fill="#0369a1">大地經度 0° (地心橢球法線)</text>
  <!-- 距離雙向箭頭 102 米 -->
  <line x1="305" y1="180" x2="515" y2="180" stroke="#dc2626" stroke-width="3"/>
  <polygon points="305,180 317,174 317,186" fill="#dc2626"/>
  <polygon points="515,180 503,174 503,186" fill="#dc2626"/>
  <text x="410" y="170" text-anchor="middle" font-size="16" fill="#b91c1c" font-weight="bold">相差約 102 公尺！</text>
  <text x="410" y="205" text-anchor="middle" font-size="13" fill="#475569">在銅線上手機會讀出西經 0.0015°</text>
</svg>
```

---

### 第 14 頁：時間的雙重面貌——恆星時 vs 太陽時
- **來源標註**：[`wiki/topic_06`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_06_大地測量時間系統.md)
- **初學者白話比喻**：你以為「一天」剛好就是地球自轉一圈 360 度嗎？錯了！地球在自轉的同時還在一邊公轉，所以自轉完 360 度後，太陽還沒正對你的頭頂，地球必須再多轉約 1 度才算過完一個太陽日！這多轉的 1 度，剛好就是 **4 分鐘**！
- **核心知識點**：
  - **恆星日**：地球相對於遙遠春分點自轉精確 $360^\circ$ 所需時間，長度為 **23 小時 56 分 04 秒**。
  - **太陽日**：地球自轉約 $361^\circ$（多轉約 $1^\circ$ 才能重新正對太陽），長度為 24 小時。
  - **換算推導**：$1\text{ 平太陽日} = 1.0027379\text{ 恆星日}$。
  - **生活規律**：天上的星座每天提早 4 分鐘升起，一個月提早 2 小時，一年累積 24 小時回到原地。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 太陽 -->
  <circle cx="400" cy="330" r="30" fill="#f59e0b"/>
  <text x="400" y="380" text-anchor="middle" font-size="14" fill="#b45309" font-weight="bold">太陽</text>
  <!-- 第一天位置地球 -->
  <circle cx="250" cy="150" r="45" fill="#bae6fd" stroke="#0284c7" stroke-width="2.5"/>
  <line x1="250" y1="150" x2="250" y2="70" stroke="#dc2626" stroke-width="3"/>
  <text x="250" y="55" text-anchor="middle" font-size="12" fill="#dc2626" font-weight="bold">指向頭頂太陽 (第1天)</text>
  <!-- 第二天公轉後位置地球 -->
  <circle cx="550" cy="150" r="45" fill="#bae6fd" stroke="#0284c7" stroke-width="2.5"/>
  <!-- 恆星日方向 (360°) -->
  <line x1="550" y1="150" x2="550" y2="70" stroke="#16a34a" stroke-width="2.5" stroke-dasharray="4,4"/>
  <text x="550" y="55" text-anchor="middle" font-size="12" fill="#15803d" font-weight="bold">自轉360° (恆星日已滿 23h56m)</text>
  <!-- 太陽日方向 (需再多轉 1°) -->
  <line x1="550" y1="150" x2="440" y2="280" stroke="#dc2626" stroke-width="3"/>
  <text x="420" y="240" font-size="12" fill="#b91c1c" font-weight="bold">多轉1°才能正對太陽 (多花4分鐘)</text>
  <!-- 結論文字 -->
  <text x="400" y="25" text-anchor="middle" font-size="15" fill="#0f172a" font-weight="bold">1 太陽日 (24h) = 1 恆星日 (23h56m04s) + 額外自轉約 1° (4分鐘)</text>
</svg>
```

---

### 第 15 頁：原子時、協調世界時與閏秒——追趕變慢的地球
- **來源標註**：[`wiki/topic_06`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_06_大地測量時間系統.md)
- **初學者白話比喻**：原子鐘是一臺冷酷的機器，數著銫原子的震盪，每 140 萬年才差 1 秒；但地球因為潮汐摩擦像被踩了煞車，自轉一年比一年慢！兩者時間越差越遠怎麼辦？1972 年起人類決定：當原子鐘比地球快接近 1 秒時，我們在跨年那一分鐘偷偷加 1 秒（出現罕見的 23:59:60），叫「閏秒」！
- **核心知識點**：
  - **TAI（國際原子時）**：銫-133 躍遷 9,192,631,770 週期為 1 秒，精度高達 $2.3 \times 10^{-14}$。
  - **UTC（協調世界時）**：秒長採原子時，時刻追隨地球自轉 UT1，維持 $|UT1 - UTC| < 0.9\text{ s}$。
  - **GPST（GPS專用時間）**：1980/1/6 起算，**連續計時絕無閏秒**！
  - **時間換算鏈**：$\text{TAI} = \text{GPST} + 19\text{s} = \text{UTC} + n\text{s}$。
  - **測距衝擊**：光速極快，時鐘誤差 **1 毫秒（ms）** 會造成 **300 公里** 的致命定位偏差！
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 時間軸對比 -->
  <!-- GPST 軸 (無閏秒) -->
  <line x1="100" y1="100" x2="700" y2="100" stroke="#0284c7" stroke-width="4"/>
  <text x="100" y="80" font-size="14" fill="#0369a1" font-weight="bold">GPST (原子鐘連續計時，絕無閏秒)</text>
  <circle cx="200" cy="100" r="6" fill="#0284c7"/>
  <circle cx="450" cy="100" r="6" fill="#0284c7"/>
  <circle cx="650" cy="100" r="6" fill="#0284c7"/>
  <!-- UTC 軸 (有閏秒跳躍) -->
  <line x1="100" y1="200" x2="430" y2="200" stroke="#16a34a" stroke-width="4"/>
  <line x1="450" y1="200" x2="700" y2="200" stroke="#16a34a" stroke-width="4"/>
  <text x="100" y="180" font-size="14" fill="#15803d" font-weight="bold">UTC (協調世界時，追隨地球自轉)</text>
  <!-- 閏秒插入階梯 -->
  <line x1="430" y1="200" x2="430" y2="230" stroke="#dc2626" stroke-width="2.5" stroke-dasharray="3,3"/>
  <line x1="430" y1="230" x2="450" y2="230" stroke="#dc2626" stroke-width="3"/>
  <line x1="450" y1="230" x2="450" y2="200" stroke="#dc2626" stroke-width="2.5" stroke-dasharray="3,3"/>
  <text x="440" y="255" text-anchor="middle" font-size="12" fill="#b91c1c" font-weight="bold">插入 23:59:60 撥慢 1 秒</text>
  <!-- 差距標示 -->
  <rect x="220" y="300" width="360" height="60" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="1.5"/>
  <text x="400" y="325" text-anchor="middle" font-size="14" fill="#0369a1" font-weight="bold">TAI = GPST + 19s = UTC + 累積閏秒</text>
  <text x="400" y="348" text-anchor="middle" font-size="12" fill="#dc2626">1 ms 鐘差 = 300 公里距離誤差！</text>
</svg>
```

---

## 第四單元：空間幾何基準與參考橢球——給地球量身定做坐標

### 第 16 頁：參考橢球體 vs 總地球橢球體——量身西裝 vs 均碼成衣
- **來源標註**：[`wiki/topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md)
- **初學者白話比喻**：傳統上，每個國家都只想讓自己國家的地圖畫得最準，所以把橢球「往自己國家方向推動旋轉」，這叫「參考橢球」（像一套專屬訂做西裝，穿在臺灣身上筆挺，在別國卻卡住）；現代 GPS 出現了，大家需要全球統一坐標，於是讓橢球中心嚴格與地球質心重合，讓全球平均誤差最小，這叫「總地球橢球」（均碼成衣）！
- **核心知識點**：
  - **參考橢球（如 TWD67）**：局部定位，幾何中心不與質心重合，大地原點強制設 $\xi_0=\eta_0=N_0=0$。
  - **總地球橢球（如 GRS80、WGS84）**：地心定位，中心與地球質心嚴格重合，滿足全球水準面起伏平方和最小：$\iint_\sigma N^2 d\sigma = \min$。
  - **七個約束條件**：4 個正常重力場定義常數（$a, J_2, fM, \omega$）+ 3 個幾何對齊約束（質心對齊、地軸對齊、子午面對齊）。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地球質心 -->
  <circle cx="380" cy="210" r="6" fill="#dc2626"/>
  <text x="360" y="235" font-size="13" fill="#dc2626" font-weight="bold">地球質心</text>
  <!-- 總地球橢球 (中心在質心) -->
  <ellipse cx="380" cy="210" rx="190" ry="135" fill="none" stroke="#2563eb" stroke-width="3"/>
  <text x="580" y="195" font-size="14" fill="#1d4ed8" font-weight="bold">總地球橢球 (WGS84/GRS80)</text>
  <text x="580" y="215" font-size="12" fill="#475569">地心定位，全球最密合</text>
  <!-- 參考橢球 (局部偏心，貼近臺灣) -->
  <ellipse cx="430" cy="180" rx="170" ry="120" fill="none" stroke="#d97706" stroke-width="3" stroke-dasharray="6,4"/>
  <circle cx="430" cy="180" r="5" fill="#d97706"/>
  <text x="210" y="85" font-size="14" fill="#b45309" font-weight="bold">參考橢球 (TWD67 參心)</text>
  <text x="210" y="105" font-size="12" fill="#475569">中心偏離質心數百米，僅局部密合</text>
  <!-- 偏心箭頭 -->
  <line x1="380" y1="210" x2="430" y2="180" stroke="#dc2626" stroke-width="2"/>
</svg>
```

---

### 第 17 頁：橢球上的兩大曲率半徑——卯酉圈 N vs 子午圈 M
- **來源標註**：[`wiki/topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md)
- **初學者白話比喻**：在籃球表面，往哪個方向切圓圈都一樣大；但在扁平的橄欖球表面，南北向切出來的密切圓（子午圈 M），跟東西向法線插到旋轉軸的長度（卯酉圈 N）截然不同！記住一個大地測量震撼真相：**卯酉圈半徑 N 的圓心根本不在地心**！
- **核心知識點**：
  - **卯酉圈曲率半徑 $N$**：地表點沿橢球面法線延伸到與自轉軸相交的距離，$N = \frac{a}{\sqrt{1 - e^2\sin^2\phi}}$。
  - **幾何原理解析**：因為橢球扁平，法線與自轉軸 $Z$ 的交點落在赤道面下方，偏離地心 $O$ 的垂直距離為 $N e^2\sin\phi$，絕非以地心為圓心！
  - **子午圈曲率半徑 $M$**：南北向橢圓切線上密切圓半徑，$M = \frac{a(1 - e^2)}{(1 - e^2\sin^2\phi)^{3/2}}$。
  - **大小關係**：同緯度恆有 **$M < N$**。在兩極處兩者相等（$M=N=a^2/b$）。
- **內嵌原生 SVG 幾何圖解（強化赤道面與地心對比）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 橢圓橫切面 -->
  <ellipse cx="400" cy="200" rx="220" ry="150" fill="none" stroke="#475569" stroke-width="2.5"/>
  <!-- 自轉軸 Z -->
  <line x1="400" y1="30" x2="400" y2="370" stroke="#dc2626" stroke-width="2"/>
  <polygon points="400,20 395,30 405,30" fill="#dc2626"/>
  <text x="410" y="45" font-size="13" fill="#dc2626" font-weight="bold">自轉軸 Z</text>
  <!-- 水平赤道面虛線 -->
  <line x1="180" y1="200" x2="620" y2="200" stroke="#94a3b8" stroke-dasharray="4,4" stroke-width="1.5"/>
  <text x="630" y="205" font-size="12" fill="#64748b">赤道面</text>
  <!-- 橢球中心 (地心 O) -->
  <circle cx="400" cy="200" r="5" fill="#334155"/>
  <text x="412" y="195" font-size="13" fill="#334155" font-weight="bold">地心 O (幾何中心)</text>
  <!-- 地表點 P (北緯 30°) -->
  <circle cx="560" cy="115" r="6" fill="#0284c7"/>
  <text x="575" y="115" font-size="14" fill="#0369a1" font-weight="bold">測點 P (φ)</text>
  <!-- 卯酉圈法線延伸 (交於 Z 軸在赤道面下方！) -->
  <line x1="560" y1="115" x2="400" y2="280" stroke="#0284c7" stroke-width="3.5"/>
  <circle cx="400" cy="280" r="6" fill="#dc2626"/>
  <text x="475" y="215" font-size="15" fill="#0284c7" font-weight="bold">卯酉圈半徑 N</text>
  <text x="260" y="285" font-size="13" fill="#dc2626" font-weight="bold">法線交點 (在赤道面下方 Ne²sinφ)</text>
  <!-- 子午圈密切圓示意 M -->
  <path d="M 520,70 A 50,50 0 0,1 600,160" fill="none" stroke="#16a34a" stroke-width="3" stroke-dasharray="4,4"/>
  <text x="610" y="85" font-size="14" fill="#15803d" font-weight="bold">子午圈曲率 M (M &lt; N)</text>
</svg>
```

---

### 第 18 頁：經緯高轉空間直角——坐標互換與神速迭代
- **來源標註**：[`wiki/topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md)
- **初學者白話比喻**：地圖上的經緯度 $(\phi, \lambda)$ 配上高度 $h$，怎麼變成三維空間裡的三維直角坐標 $(X, Y, Z)$？正算只要幾何分解；但要從 $(X, Y, Z)$ 倒算回緯度時，因為橢球扁平，緯度卡在公式兩邊無法直接化簡。測量學家發明了神速迭代法：先猜高度是 0，算一次、代回、重複 3 次，立刻精確到毫米以內！
- **核心知識點**：
  - **正算公式**：
    $$X = (N + h)\cos\phi\cos\lambda,\quad Y = (N + h)\cos\phi\sin\lambda,\quad Z = [N(1 - e^2) + h]\sin\phi$$
  - **反算迭代演算法**：
    $\lambda = \tan^{-1}(Y/X)$，$p = \sqrt{X^2+Y^2}$。
    初值令 $h=0$ 算 $\phi_1 = \tan^{-1}\left(\frac{Z}{p(1-e^2)}\right)$，反求 $N_1, h_1$ 後反覆代回。
    因為第一偏心率平方 $e^2 \approx 0.0067$ 極小，**只需迭代 3～4 次即完全收斂**！
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 雙向互換示意圖 -->
  <rect x="80" y="80" width="220" height="100" rx="8" fill="#e0f2fe" stroke="#0284c7" stroke-width="2"/>
  <text x="190" y="115" text-anchor="middle" font-size="16" fill="#0369a1" font-weight="bold">大地幾何坐標</text>
  <text x="190" y="145" text-anchor="middle" font-size="18" fill="#0f172a" font-weight="bold">(φ, λ, h)</text>
  <text x="190" y="165" text-anchor="middle" font-size="12" fill="#64748b">緯度、經度、橢球高</text>

  <!-- 正算箭頭 -->
  <line x1="310" y1="110" x2="480" y2="110" stroke="#16a34a" stroke-width="3"/>
  <polygon points="480,110 470,104 470,116" fill="#16a34a"/>
  <text x="395" y="100" text-anchor="middle" font-size="13" fill="#15803d" font-weight="bold">正算 (解析幾何)</text>

  <!-- 反算箭頭 (迭代) -->
  <line x1="480" y1="150" x2="310" y2="150" stroke="#dc2626" stroke-width="3"/>
  <polygon points="310,150 320,144 320,156" fill="#dc2626"/>
  <text x="395" y="175" text-anchor="middle" font-size="13" fill="#b91c1c" font-weight="bold">反算 (3~4次迭代收斂)</text>

  <rect x="490" y="80" width="230" height="100" rx="8" fill="#fef3c7" stroke="#d97706" stroke-width="2"/>
  <text x="605" y="115" text-anchor="middle" font-size="16" fill="#b45309" font-weight="bold">地心地固直角坐標</text>
  <text x="605" y="145" text-anchor="middle" font-size="18" fill="#0f172a" font-weight="bold">(X, Y, Z)</text>
  <text x="605" y="165" text-anchor="middle" font-size="12" fill="#64748b">地心為原點，單位公尺</text>

  <!-- 底部公式摘要 -->
  <rect x="180" y="240" width="440" height="70" rx="8" fill="#ffffff" stroke="#475569" stroke-width="1.5"/>
  <text x="400" y="265" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">X = (N+h)cosφcosλ, Y = (N+h)cosφsinλ</text>
  <text x="400" y="290" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">Z = [N(1 - e²) + h]sinφ</text>
</svg>
```

---

### 第 19 頁：現代測地五大天王——VLBI, SLR, LLR, GNSS, DORIS
- **來源標註**：[`wiki/topic_07`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_07_國際參考框架與現代動態基準.md)
- **初學者白話比喻**：要給整顆地球建立毫米級的坐標框架，單靠幾個人拉皮尺或拿經緯儀是不可能的。現代地球測量派出五路神仙：射電望遠鏡看數十億光年外的類星體（VLBI）、雷射打向衛星與月球鏡子（SLR/LLR）、衛星微波導航（GNSS）以及衛星都卜勒測速（DORIS）！
- **核心知識點**：
  - **VLBI**：望遠鏡觀測河外射電源時間差，**唯一能獨立測定全套 EOP**，精度 $\pm 0.2\text{ mas}$。
  - **SLR**：雷射打衛星反射鏡（LAGEOS 高度 5900 km），精度 $<1\text{ cm}$，決定地心質心位置。
  - **LLR**：雷射測距月球表面反射鏡。
  - **GNSS（GPS）**：雙頻加密觀測，全球站點最密，實現區域框架加密。
  - **DORIS**：地面發射、衛星接收的上行都卜勒系統。
  - 五者聯合平差，催生了全球大地測量基準 **ITRF** 與聯合國 **GGRF** 決議。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 五大技術分佈圓環或陣列 -->
  <!-- VLBI -->
  <rect x="50" y="60" width="130" height="90" rx="8" fill="#e0e7ff" stroke="#4338ca" stroke-width="1.5"/>
  <text x="115" y="90" text-anchor="middle" font-size="16" fill="#312e81" font-weight="bold">VLBI</text>
  <text x="115" y="115" text-anchor="middle" font-size="12" fill="#4338ca">射電源時間差</text>
  <text x="115" y="135" text-anchor="middle" font-size="11" fill="#dc2626" font-weight="bold">唯一定全套EOP</text>

  <!-- SLR -->
  <rect x="200" y="60" width="130" height="90" rx="8" fill="#fce7f3" stroke="#be185d" stroke-width="1.5"/>
  <text x="265" y="90" text-anchor="middle" font-size="16" fill="#831843" font-weight="bold">SLR</text>
  <text x="265" y="115" text-anchor="middle" font-size="12" fill="#9d174d">衛星雷射測距</text>
  <text x="265" y="135" text-anchor="middle" font-size="11" fill="#dc2626" font-weight="bold">決定地心質心</text>

  <!-- LLR -->
  <rect x="350" y="60" width="110" height="90" rx="8" fill="#fef3c7" stroke="#b45309" stroke-width="1.5"/>
  <text x="405" y="90" text-anchor="middle" font-size="16" fill="#78350f" font-weight="bold">LLR</text>
  <text x="405" y="115" text-anchor="middle" font-size="12" fill="#b45309">月球雷射測距</text>
  <text x="405" y="135" text-anchor="middle" font-size="11" fill="#475569">黃赤交角/引力</text>

  <!-- GNSS -->
  <rect x="480" y="60" width="130" height="90" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="1.5"/>
  <text x="545" y="90" text-anchor="middle" font-size="16" fill="#14532d" font-weight="bold">GNSS / GPS</text>
  <text x="545" y="115" text-anchor="middle" font-size="12" fill="#15803d">雙頻微波測距</text>
  <text x="545" y="135" text-anchor="middle" font-size="11" fill="#dc2626" font-weight="bold">全臺密布站網</text>

  <!-- DORIS -->
  <rect x="630" y="60" width="120" height="90" rx="8" fill="#ccfbf1" stroke="#0f766e" stroke-width="1.5"/>
  <text x="690" y="90" text-anchor="middle" font-size="16" fill="#134e4a" font-weight="bold">DORIS</text>
  <text x="690" y="115" text-anchor="middle" font-size="12" fill="#0f766e">上行都卜勒</text>
  <text x="690" y="135" text-anchor="middle" font-size="11" fill="#475569">軌道測定/集中式</text>

  <!-- 匯流至 ITRF -->
  <line x1="400" y1="160" x2="400" y2="230" stroke="#0284c7" stroke-width="3"/>
  <polygon points="400,230 393,220 407,220" fill="#0284c7"/>
  <rect x="250" y="240" width="300" height="60" rx="8" fill="#0284c7"/>
  <text x="400" y="275" text-anchor="middle" font-size="16" fill="#ffffff" font-weight="bold">ITRF 國際地球參考框架</text>
</svg>
```

---

### 第 20 頁：板塊飄移與臺灣雙框架策略——TWD97 遇上 TTRF
- **來源標註**：[`wiki/topic_07`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_07_國際參考框架與現代動態基準.md)
- **初學者白話比喻**：臺灣踩在歐亞板塊和菲律賓海板塊激烈撞擊的交界處，地表每年都在往西北移動好幾公分！如果地圖坐標天天變，你家地契產權界址會大亂；如果十年不改，GPS 衛星定位又對不上。內政部怎麼解？**雙框架策略**：法定地籍凍結在固定基準（TWD97），同時讓 CORS 衛星站即時計算時變框架（TTRF），中間靠地殼變位模型隨時轉換！
- **核心知識點**：
  - **板塊運動困境**：臺灣地殼每年數公分位移，TWD97 已被迫發表過三版（1997.0, 2010.0, 2020.0）。
  - **雙框架架構**：
    1. **法定靜態基準 TWD97[2020]**：確保地籍與土地行政法規穩定。
    2. **即時時變框架 TTRF**：由 CORS 站對齊 ITRF2020，捕捉地震同震位移與板塊速度。
    3. **地殼變位模型**：精確連結兩系統，消除外業檢核點殘差。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 板塊擠壓示意圖 -->
  <rect x="80" y="70" width="220" height="110" rx="8" fill="#dbeafe" stroke="#1d4ed8" stroke-width="2"/>
  <text x="190" y="105" text-anchor="middle" font-size="16" fill="#1e40af" font-weight="bold">TWD97 法定基準</text>
  <text x="190" y="130" text-anchor="middle" font-size="13" fill="#334155">【靜態框架・凍結曆元】</text>
  <text x="190" y="155" text-anchor="middle" font-size="12" fill="#64748b">保障產權界址永久不變</text>

  <!-- 雙向橋樑：地殼變形模型 -->
  <line x1="310" y1="125" x2="480" y2="125" stroke="#ea580c" stroke-width="4"/>
  <polygon points="310,125 320,119 320,131" fill="#ea580c"/>
  <polygon points="480,125 470,119 470,131" fill="#ea580c"/>
  <text x="395" y="115" text-anchor="middle" font-size="13" fill="#c2410c" font-weight="bold">地殼變形模型</text>
  <text x="395" y="145" text-anchor="middle" font-size="11" fill="#64748b">消除板塊擠壓位移</text>

  <rect x="490" y="70" width="230" height="110" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2"/>
  <text x="605" y="105" text-anchor="middle" font-size="16" fill="#14532d" font-weight="bold">TTRF 現代框架</text>
  <text x="605" y="130" text-anchor="middle" font-size="13" fill="#334155">【動態時變・連續CORS】</text>
  <text x="605" y="155" text-anchor="middle" font-size="12" fill="#15803d">直接對齊國際 ITRF2020</text>
</svg>
```

---

### 第 21 頁：臺灣大地基準大對決——TWD67, TWD97 與 WGS84
- **來源標註**：[`wiki/topic_08`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_08_臺灣大地基準與全球系統比較.md)
- **初學者白話比喻**：老一輩測量員用 TWD67，跑到南投埔里虎子山頂看星星定坐標；現代無人機與工程測量用 TWD97，仰賴全臺 8 大衛星追蹤站解算；而你手機導航晶片預設吃的是美軍的 WGS84。三者坐標若是搞混，點位在地圖上會直接飛走近一公里！
- **核心知識點**：
  - **TWD67**：參心基準（GRS67 橢球），埔里虎子山原點，傳統三角測量，僅為水平基準。
  - **TWD97**：地心基準（GRS80 橢球），全臺 8 追蹤站聯測 51 個 IGS 站，三維空間一體化。
  - **WGS84**：GPS 專用基準，與 TWD97/GRS80 僅扁率小數點第 9 位極微差異（實務互通）。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 對比三欄看板 -->
  <rect x="60" y="50" width="200" height="260" rx="8" fill="#ffffff" stroke="#94a3b8" stroke-width="1.5"/>
  <text x="160" y="80" text-anchor="middle" font-size="16" fill="#334155" font-weight="bold">TWD67 (舊制)</text>
  <text x="75" y="115" font-size="12" fill="#64748b">類型：參心局部基準</text>
  <text x="75" y="140" font-size="12" fill="#64748b">橢球：GRS67 (a=6378160)</text>
  <text x="75" y="165" font-size="12" fill="#64748b">原點：埔里虎子山三角點</text>
  <text x="75" y="190" font-size="12" fill="#64748b">技術：傳統三角測量</text>
  <text x="75" y="215" font-size="12" fill="#dc2626" font-weight="bold">分量：水平與高程分開</text>

  <rect x="290" y="50" width="220" height="260" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="2.5"/>
  <text x="400" y="80" text-anchor="middle" font-size="16" fill="#0369a1" font-weight="bold">TWD97 (現行國標)</text>
  <text x="305" y="115" font-size="12" fill="#334155">類型：地心地固基準</text>
  <text x="305" y="140" font-size="12" fill="#334155">橢球：GRS80 (a=6378137)</text>
  <text x="305" y="165" font-size="12" fill="#334155">起算：8衛星站+51 IGS站</text>
  <text x="305" y="190" font-size="12" fill="#334155">解算：ITRF94@1997.0</text>
  <text x="305" y="215" font-size="12" fill="#0369a1" font-weight="bold">分量：三維一體 (h)</text>

  <rect x="540" y="50" width="200" height="260" rx="8" fill="#ffffff" stroke="#16a34a" stroke-width="1.5"/>
  <text x="640" y="80" text-anchor="middle" font-size="16" fill="#15803d" font-weight="bold">WGS84 (全球衛星)</text>
  <text x="555" y="115" font-size="12" fill="#64748b">類型：全球地心基準</text>
  <text x="555" y="140" font-size="12" fill="#64748b">橢球：WGS84 橢球</text>
  <text x="555" y="165" font-size="12" fill="#64748b">起算：全球GPS追蹤站網</text>
  <text x="555" y="190" font-size="12" fill="#64748b">版本：G730, G873</text>
  <text x="555" y="215" font-size="12" fill="#15803d" font-weight="bold">與GRS80差0.1mm</text>
</svg>
```

---

### 第 22 頁：大地高與正高的橋樑——h = H + N 與臺灣 TWVD2001
- **來源標註**：[`wiki/topic_08`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_08_臺灣大地基準與全球系統比較.md)
- **初學者白話比喻**：GPS 衛星告訴你的高度是「幾何橢球高 $h$」，但工地的水會往哪流看的是「物理正高 $H$」（海拔高度）。兩者之間差了一個叫「大地起伏 $N$」的空間夾層！
  - *為什麼起算點選在基隆？* 因為基隆港驗潮站自日治時期至今累積了數十年最完整穩定的潮位紀錄，能精確算出排除風浪潮汐的平均海平面（MSL）！
- **核心知識點**：
  - **高度核心公式**：
    $$h = H + N$$
    $h$：大地高（橢球高，沿橢球法線量至橢球面）；$H$：正高（海水面起算海拔）；$N$：大地水準面差距（大地起伏）。
  - **TWVD2001**：臺灣高程基準 2001，以基隆平均海水面為零點，為獨立物理基準。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地表面 -->
  <path d="M 100,100 Q 300,60 500,110 T 700,90" fill="none" stroke="#475569" stroke-width="3"/>
  <circle cx="500" cy="110" r="6" fill="#dc2626"/>
  <text x="520" y="105" font-size="14" fill="#dc2626" font-weight="bold">地表測點 P</text>
  <!-- 大地水準面 (波浪) -->
  <path d="M 100,200 Q 300,180 500,220 T 700,190" fill="none" stroke="#0284c7" stroke-width="3"/>
  <text x="120" y="190" font-size="13" fill="#0369a1" font-weight="bold">大地水準面 (基隆海水面 TWVD2001 正高 H=0)</text>
  <!-- 參考橢球面 -->
  <path d="M 100,290 Q 300,290 500,290 T 700,290" fill="none" stroke="#16a34a" stroke-width="3" stroke-dasharray="6,4"/>
  <text x="120" y="315" font-size="13" fill="#15803d" font-weight="bold">參考橢球面 (TWD97 幾何橢球高 h=0)</text>
  <!-- 高度線箭頭標註 -->
  <!-- 總大地高 h -->
  <line x1="460" y1="110" x2="460" y2="290" stroke="#0f172a" stroke-width="2.5"/>
  <text x="400" y="200" font-size="14" fill="#0f172a" font-weight="bold">大地高 h</text>
  <!-- 正高 H -->
  <line x1="500" y1="110" x2="500" y2="220" stroke="#0284c7" stroke-width="2.5"/>
  <text x="510" y="165" font-size="14" fill="#0369a1" font-weight="bold">正高 H (海拔)</text>
  <!-- 大地起伏 N -->
  <line x1="500" y1="220" x2="500" y2="290" stroke="#16a34a" stroke-width="2.5"/>
  <text x="510" y="260" font-size="14" fill="#15803d" font-weight="bold">大地起伏 N</text>
  <!-- 公式提示框 -->
  <rect x="580" y="220" width="180" height="50" rx="6" fill="#ffffff" stroke="#dc2626" stroke-width="1.5"/>
  <text x="670" y="250" text-anchor="middle" font-size="15" fill="#b91c1c" font-weight="bold">h = H + N</text>
</svg>
```

---

## 第五單元：基準轉換與地圖投影——把三維地球攤平在圖紙上

### 第 23 頁：坐標系轉換魔法——三參數、七參數與 Molodensky
- **來源標註**：[`wiki/topic_09`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_09_基準轉換與坐標變換數學模型.md)
- **初學者白話比喻**：想像有兩個三維空間箱子，箱子中心位置不一樣（3個平移）、擺放朝向偏了幾度（3個旋轉）、而且尺子縮放比例不同（1個尺度）。把坐標從一個箱子準確倒到另一個箱子，這套嚴密的七個密碼，就叫「七參數空間相似轉換」！
- **核心知識點**：
  - **七參數（Bursa-Wolf）**：
    $$\mathbf{X}_2 = S \cdot \mathbf{R} \cdot \mathbf{X}_1 + \mathbf{T}$$
    3平移（原點對齊）+ 3旋轉（軸向對齊）+ 1尺度因子（單位對齊）。小角度反對稱線性化形式：$\mathbf{X}_2 \approx \mathbf{X}_1 + \mathbf{T} + D\mathbf{X}_1 + \mathbf{R}'\mathbf{X}_1$。
  - **三參數平移**：忽略旋轉與尺度，僅作原點平移（工程快速近似）。
  - **Standard Molodensky 公式**：跳過 ECEF 直角坐標，直接由大地坐標經緯高互換。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 坐標系 1 -->
  <line x1="200" y1="260" x2="300" y2="260" stroke="#0284c7" stroke-width="3"/>
  <line x1="200" y1="260" x2="200" y2="160" stroke="#0284c7" stroke-width="3"/>
  <line x1="200" y1="260" x2="140" y2="310" stroke="#0284c7" stroke-width="3"/>
  <text x="180" y="275" font-size="13" fill="#0369a1" font-weight="bold">系 1 (X1,Y1,Z1)</text>

  <!-- 平移向量 T -->
  <line x1="200" y1="260" x2="500" y2="180" stroke="#dc2626" stroke-width="3" stroke-dasharray="6,4"/>
  <polygon points="500,180 488,181 494,192" fill="#dc2626"/>
  <text x="350" y="210" text-anchor="middle" font-size="14" fill="#b91c1c" font-weight="bold">3 平移 (ΔX, ΔY, ΔZ)</text>

  <!-- 坐標系 2 (旋轉帶傾角) -->
  <line x1="500" y1="180" x2="610" y2="160" stroke="#16a34a" stroke-width="3"/>
  <line x1="500" y1="180" x2="480" y2="70" stroke="#16a34a" stroke-width="3"/>
  <line x1="500" y1="180" x2="430" y2="230" stroke="#16a34a" stroke-width="3"/>
  <text x="510" y="195" font-size="13" fill="#15803d" font-weight="bold">系 2 (X2,Y2,Z2)</text>

  <!-- 旋轉與尺度標註 -->
  <text x="560" y="110" font-size="13" fill="#15803d" font-weight="bold">3 旋轉角 (εx, εy, εz)</text>
  <text x="560" y="130" font-size="13" fill="#15803d" font-weight="bold">+ 1 尺度比例 S</text>

  <!-- 總結卡片 -->
  <rect x="220" y="325" width="360" height="50" rx="8" fill="#ffffff" stroke="#475569" stroke-width="1.5"/>
  <text x="400" y="355" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">七參數完整相似轉換：3平移 + 3旋轉 + 1尺度</text>
</svg>
```

---

### 第 24 頁：臺灣實務快速換算——TWD67 轉 TWD97（防呆口訣版）
- **來源標註**：[`wiki/topic_09`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_09_基準轉換與坐標變換數學模型.md)
- **初學者白話比喻**：如果你在工地上拿到一張幾十年前手繪的老地籍圖（TWD67），想套進現在的 Google 衛星地圖（TWD97），要怎麼口算快速換？記住測量界的「江湖秘笈」！
- **核心知識點**：
  - **防呆警示（千萬別背反符號）**：
    - **由舊到新（TWD67 $\to$ TWD97）**：整體點位朝東南方移動，所以是：
      $$E_{97} = E_{67} + 828\text{ m},\quad N_{97} = N_{67} - 197\text{ m}$$
      *【口訣：老變新，往東南，東加八二八、北減一九七！】*
    - **由新查舊（TWD97 $\to$ TWD67）**：反向逆推：
      $$E_{67} = E_{97} - 828\text{ m},\quad N_{67} = N_{97} + 197\text{ m}$$
  - **合成空間偏移向量**：$\sqrt{828^2 + 197^2} \approx 851.1\text{ m}$。
  - **精度階梯**：全島簡易轉換殘差在 **5 m 以內**；若配合 TM2° 網格使用**最小曲率法**內插，殘差可壓制到 **30 cm**。
- **內嵌原生 SVG 幾何圖解（防呆箭頭醒目標記）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- TWD67 點位 -->
  <circle cx="230" cy="240" r="8" fill="#d97706"/>
  <text x="180" y="275" font-size="16" fill="#b45309" font-weight="bold">TWD67 舊點位</text>
  <!-- 東向偏移 +828m -->
  <line x1="230" y1="240" x2="520" y2="240" stroke="#0284c7" stroke-width="3"/>
  <polygon points="520,240 508,234 508,246" fill="#0284c7"/>
  <text x="375" y="230" text-anchor="middle" font-size="15" fill="#0369a1" font-weight="bold">+ 828 公尺 (東向加)</text>
  <!-- 北向偏移 -197m -->
  <line x1="520" y1="240" x2="520" y2="120" stroke="#16a34a" stroke-width="3"/>
  <polygon points="520,120 514,132 526,132" fill="#16a34a"/>
  <text x="585" y="185" font-size="15" fill="#15803d" font-weight="bold">- 197 公尺 (北向減)</text>
  <!-- 合成向量 851.1m (紅色醒目) -->
  <line x1="230" y1="240" x2="520" y2="120" stroke="#dc2626" stroke-width="4"/>
  <polygon points="520,120 506,125 514,135" fill="#dc2626"/>
  <text x="350" y="160" text-anchor="middle" font-size="16" fill="#b91c1c" font-weight="bold">合向量位移 851.1 公尺！</text>
  <!-- TWD97 點位 -->
  <circle cx="520" cy="120" r="8" fill="#dc2626"/>
  <text x="540" y="110" font-size="16" fill="#b91c1c" font-weight="bold">TWD97 新點位</text>
</svg>
```

---

### 第 25 頁：地圖投影的終極矛盾——不可展曲面與蒂索變形橢圓
- **來源標註**：[`wiki/topic_10`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_10_地圖投影理論與高斯克呂格投影.md)
- **初學者白話比喻**：你吃橘子的時候，試著把剝下來的圓形橘子皮平平整整地壓扁在桌上，你會發現邊緣一定會破裂或被擠壓變形！這在數學上叫「不可展曲面」。要把圓球畫在平面紙上，長度、角度或面積至少有一樣會變形，不可能三全其美！
- **核心知識點**：
  - **長度比**：$m = ds / dS$。
  - **蒂索變形橢圓（Tissot's Indicatrix）**：地表微小單位正圓，投影至平面後必然變形為以主方向 $a, b$ 為半軸的橢圓。
  - **三大投影分類**：
    1. **正形（等角）投影**：$a = b$，微小圓投影後仍為圓，保證角度與形狀不變形（測量最愛）；
    2. **等積投影**：$a \cdot b = 1$，面積完全不變形；
    3. **任意投影**：折衷方案。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 橢球面微小圓 (無變形) -->
  <circle cx="220" cy="180" r="50" fill="#dbeafe" stroke="#2563eb" stroke-width="2.5"/>
  <text x="220" y="175" text-anchor="middle" font-size="14" fill="#1e40af" font-weight="bold">橢球面上微元</text>
  <text x="220" y="195" text-anchor="middle" font-size="13" fill="#1e40af">正圓 (dS, r=1)</text>

  <!-- 投影映射箭頭 -->
  <line x1="300" y1="180" x2="440" y2="180" stroke="#64748b" stroke-width="3"/>
  <polygon points="440,180 430,174 430,186" fill="#64748b"/>
  <text x="370" y="165" text-anchor="middle" font-size="13" fill="#475569">地圖投影映射</text>

  <!-- 投影後蒂索變形橢圓 -->
  <ellipse cx="560" cy="180" rx="75" ry="40" fill="#fed7aa" stroke="#ea580c" stroke-width="2.5"/>
  <line x1="560" y1="180" x2="635" y2="180" stroke="#dc2626" stroke-width="2"/>
  <text x="595" y="170" font-size="12" fill="#b91c1c" font-weight="bold">長半軸 a</text>
  <line x1="560" y1="180" x2="560" y2="140" stroke="#dc2626" stroke-width="2"/>
  <text x="565" y="155" font-size="12" fill="#b91c1c" font-weight="bold">短半軸 b</text>
  <text x="560" y="240" text-anchor="middle" font-size="14" fill="#c2410c" font-weight="bold">蒂索變形橢圓 (Tissot)</text>

  <!-- 正形條件標註 -->
  <rect x="250" y="290" width="300" height="50" rx="6" fill="#ffffff" stroke="#2563eb" stroke-width="1.5"/>
  <text x="400" y="320" text-anchor="middle" font-size="14" fill="#1d4ed8" font-weight="bold">若 a = b 則為等角 (正形) 投影！</text>
</svg>
```

---

### 第 26 頁：高斯－克呂格投影——橫軸切圓柱的正形奇蹟
- **來源標註**：[`wiki/topic_10`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_10_地圖投影理論與高斯克呂格投影.md)
- **初學者白話比喻**：既然地球皮撕不平，德國數學高斯想出絕招：拿一個橢圓紙筒「橫著套」在地球腰上，讓紙筒剛好貼緊其中一條經線（中央子午線）。在這條切線上，長度完全沒有拉伸變形（$m_0=1$）；雖然離中央線越遠拉伸越大，但我們只要限定兩側只畫一點點（分帶），就能把誤差限制在極微小的範圍內！
- **核心知識點**：
  - **高斯投影三大條件**：
    1. 中央子午線投影為直線；
    2. 中央子午線無長度變形（$m_0 = 1$）；
    3. 滿足柯西－黎曼條件（正形等角，$\Delta u = 0$）。
  - **子午線收斂角 $\gamma$**：真子午線切線與網格坐標北方向的夾角，東正西負。
  - **底點緯度 $\phi_f$**：子午線弧長剛好等於縱坐標 $y$ 時的緯度，反算由此展開。
- **內嵌原生 SVG 幾何圖解（顯式箭頭，無依賴）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 地球主體 -->
  <circle cx="360" cy="200" r="130" fill="#e2e8f0" stroke="#475569" stroke-width="2"/>
  <!-- 橫套圓柱面 (相切) -->
  <rect x="330" y="40" width="60" height="320" fill="#bae6fd" opacity="0.4" stroke="#0284c7" stroke-width="2"/>
  <!-- 中央子午線 (相切直線) -->
  <line x1="360" y1="40" x2="360" y2="360" stroke="#dc2626" stroke-width="3.5"/>
  <text x="375" y="60" font-size="14" fill="#b91c1c" font-weight="bold">中央子午線 (相切 m₀ = 1.0)</text>
  <text x="375" y="80" font-size="12" fill="#b91c1c">嚴格無長度變形！</text>
  <!-- 兩側向外拉伸示意 (顯式 polygon 箭頭) -->
  <line x1="360" y1="140" x2="465" y2="130" stroke="#ea580c" stroke-width="2.5"/>
  <polygon points="465,130 453,124 455,136" fill="#ea580c"/>
  <text x="475" y="135" font-size="13" fill="#c2410c" font-weight="bold">離中央經線越遠，拉伸變形越大</text>
  <!-- 說明看板 -->
  <rect x="540" y="240" width="220" height="80" rx="8" fill="#ffffff" stroke="#0284c7" stroke-width="1.5"/>
  <text x="555" y="265" font-size="13" fill="#0369a1" font-weight="bold">橫軸橢圓柱等角投影</text>
  <text x="555" y="288" font-size="12" fill="#334155">保持微小圖形角度嚴格不變</text>
  <text x="555" y="308" font-size="12" fill="#64748b">大比例尺測量的首選投影</text>
</svg>
```

---

### 第 27 頁：全球通用橫麥卡托 (UTM)——割線圓柱與 60 分帶
- **來源標註**：[`wiki/topic_11`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_11_UTM投影與臺灣TM2分帶系統.md)
- **初學者白話比喻**：高斯投影在中央線完全不變形，但邊緣拉伸太快；美軍說：我們把圓柱稍微往地球內部「切進去」（割線），讓中央線先微幅壓縮千分之 0.4（$0.9996$），在距中央經線 180 公里處剛剛好不變形，邊緣拉伸也就被縮小了！
  - *為什麼假東要設 500,000 米？* 因為赤道上一個 6 度帶寬約 670 公里（中央線兩側各約 335 公里）。給中央線賦予 500,000 米，最西側邊界的坐標約為 165,000 米，保證絕對不會出現負數！
- **核心知識點**：
  - **割線投影尺度比**：中央子午線 $k_0 = 0.9996$；割線處（約距中央線 180 km）無變形（$k=1.0$）；邊界處 $+0.0010$。
  - **全球 60 分帶**：每帶 6°，臺灣全島完整落在 **Zone 51**（中央經線 $123^\circ\text{E}$）。
  - **偽坐標防負值**：假東 $500,000\text{ m}$，北半球赤道 $N=0$，南半球赤道假北 $10,000,000\text{ m}$。
- **內嵌原生 SVG 幾何圖解（軸線與文字安全間距）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 坐標橫軸整體下移至 y=290，保留充足空白 -->
  <line x1="100" y1="290" x2="700" y2="290" stroke="#334155" stroke-width="2"/>
  <line x1="400" y1="50" x2="400" y2="330" stroke="#334155" stroke-width="2"/>
  <text x="400" y="35" text-anchor="middle" font-size="14" fill="#0f172a" font-weight="bold">尺度比 k (中央子午線)</text>

  <!-- k = 1.0 基準虛線 -->
  <line x1="100" y1="180" x2="700" y2="180" stroke="#94a3b8" stroke-dasharray="4,4" stroke-width="2"/>
  <text x="710" y="185" font-size="13" fill="#64748b" font-weight="bold">k = 1.0 (無變形)</text>

  <!-- U型尺度比曲線 -->
  <path d="M 160,110 Q 400,260 640,110" fill="none" stroke="#2563eb" stroke-width="3.5"/>

  <!-- 中央子午線谷底 k=0.9996 (文字安全置於谷底上方) -->
  <circle cx="400" cy="222" r="5" fill="#dc2626"/>
  <rect x="300" y="235" width="200" height="30" rx="4" fill="#ffffff" stroke="#dc2626" stroke-width="1"/>
  <text x="400" y="255" text-anchor="middle" font-size="13" fill="#dc2626" font-weight="bold">k₀ = 0.9996 (負壓縮變形)</text>

  <!-- 兩側割線相交點 (k=1.0) -->
  <circle cx="270" cy="180" r="5" fill="#16a34a"/>
  <circle cx="530" cy="180" r="5" fill="#16a34a"/>
  <text x="240" y="165" font-size="12" fill="#15803d" font-weight="bold">割線 1 (k=1.0)</text>
  <text x="530" y="165" font-size="12" fill="#15803d" font-weight="bold">割線 2 (k=1.0)</text>

  <!-- 兩側邊緣正變形 -->
  <text x="140" y="95" font-size="12" fill="#1d4ed8" font-weight="bold">邊界 k ≈ 1.001</text>
  <text x="630" y="95" font-size="12" fill="#1d4ed8" font-weight="bold">邊界 k ≈ 1.001</text>
</svg>
```

---

### 第 28 頁：守護人民產權的萬分之一——臺灣橫麥卡托 TM2° 投影
- **來源標註**：[`wiki/topic_11`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_11_UTM投影與臺灣TM2分帶系統.md)
- **初學者白話比喻**：你買了一間 100 坪的豪宅土地，如果地政事務所用軍用 6 度的 UTM 投影來量，邊緣長度變形千分之一，換算面積可能直接縮水或膨脹好幾坪，誰能接受？所以臺灣堅持採用 2 度分帶（TM2°），中央線只縮小萬分之一（$0.9999$），嚴格保護老百姓的地籍私有產權！
- **核心知識點**：
  - **TM2° 核心規格**：
    - **臺灣本島及周邊附屬島嶼**：中央子午線 **$121^\circ\text{ E}$**。
    - **澎湖、金門、馬祖等離島**：中央子午線 **$119^\circ\text{ E}$**。
    - 尺度比 **$0.9999$**，假東偏移 **$250,000\text{ m}$**。
  - **臺灣三大分帶**：
    - **TM2（2°帶）**：地籍測量、1:5000 大比例尺圖，尺度誤差 $1/10000 \sim 1/20000$。
    - **TM3（3°帶）**：1:5000～1:20000 中比例尺，$k_0=1.0$。
    - **UTM（6°帶）**：小比例尺國防地圖，$k_0=0.9996$。
  - **網格距離換算**：地面距離 $\approx$ 網格距離 $/ 0.9999$。
- **內嵌原生 SVG 幾何圖解（包含 121°E 與 119°E 雙子午線）**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 澎金馬離島示意線 119°E -->
  <line x1="240" y1="40" x2="240" y2="350" stroke="#0284c7" stroke-width="2.5" stroke-dasharray="6,3"/>
  <text x="240" y="30" text-anchor="middle" font-size="13" fill="#0369a1" font-weight="bold">離島 119°E (澎金馬)</text>
  <circle cx="240" cy="180" r="5" fill="#0284c7"/>
  <text x="250" y="185" font-size="11" fill="#0369a1">澎湖群島</text>

  <!-- 臺灣島幾何簡圖 -->
  <path d="M 460,80 Q 490,130 480,210 Q 460,290 440,310 Q 420,260 430,180 Z" fill="#dcfce7" stroke="#15803d" stroke-width="2.5"/>

  <!-- 本島中央子午線 121°E -->
  <line x1="460" y1="40" x2="460" y2="350" stroke="#dc2626" stroke-width="3.5"/>
  <text x="460" y="30" text-anchor="middle" font-size="14" fill="#dc2626" font-weight="bold">本島中央子午線 121°E (k₀ = 0.9999)</text>

  <!-- 2度分帶邊界 (120°E - 122°E) -->
  <line x1="390" y1="60" x2="390" y2="330" stroke="#94a3b8" stroke-dasharray="4,4" stroke-width="1.5"/>
  <text x="360" y="345" font-size="12" fill="#64748b">120°E</text>
  <line x1="530" y1="60" x2="530" y2="330" stroke="#94a3b8" stroke-dasharray="4,4" stroke-width="1.5"/>
  <text x="535" y="345" font-size="12" fill="#64748b">122°E</text>

  <!-- 守護產權卡片 -->
  <rect x="550" y="140" width="230" height="90" rx="8" fill="#ffffff" stroke="#16a34a" stroke-width="1.5"/>
  <text x="565" y="165" font-size="14" fill="#15803d" font-weight="bold">為什麼地籍必用 TM2°？</text>
  <text x="565" y="190" font-size="12" fill="#334155">變形極限壓在萬分之一以內，</text>
  <text x="565" y="210" font-size="12" fill="#334155">確保土地權利與面積毫釐不差！</text>
</svg>
```

---

### 第 29 頁：課程全景總結——大地測量學的幾何與物理知識網絡
- **來源標註**：[`wiki/index`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/index.md) 及全體主題條目
- **初學者白話比喻**：恭喜你完成大地測量學的宏偉探索！回頭看看，我們從旋轉橘子般的地球形狀出發，理解了重力場這隻無形之手，學會了在太空晃動的陀螺中用原子鐘定時間，再為地球套上精密的旋轉橢球，最後把曲面完美攤平為地圖。這就是現代所有導航、地圖與太空科技的基石！
- **核心知識點**：
  - 幾何與物理的雙重融合：旋轉橢球（幾何）$+$ 大地水準面（物理重力）。
  - 時間與空間的互鎖：銫原子秒長 $+$ 光速測距 $+$ EOP 地球定向轉換。
  - 傳統到現代動態基準：TWD67 參心 $\to$ TWD97 地心 $\to$ TTRF CORS 即時動態。
  - 理論至工程圖紙：高斯正形條件 $\to$ UTM 6° 帶 $\to$ 臺灣 TM2° 地籍高精度投影。
- **內嵌原生 SVG 幾何圖解**：
```xml
<svg viewBox="0 0 800 400" width="100%" height="260" xmlns="http://www.w3.org/2000/svg">
  <rect width="800" height="400" fill="#f8fafc" rx="12"/>
  <!-- 全課程四大支柱閉合圖 -->
  <rect x="60" y="70" width="140" height="70" rx="8" fill="#dbeafe" stroke="#2563eb" stroke-width="2"/>
  <text x="130" y="100" text-anchor="middle" font-size="14" fill="#1e40af" font-weight="bold">1. 地球幾何形狀</text>
  <text x="130" y="122" text-anchor="middle" font-size="11" fill="#475569">旋轉橢球 / 梨形</text>

  <rect x="60" y="220" width="140" height="70" rx="8" fill="#fef3c7" stroke="#b45309" stroke-width="2"/>
  <text x="130" y="250" text-anchor="middle" font-size="14" fill="#78350f" font-weight="bold">2. 地球重力場</text>
  <text x="130" y="272" text-anchor="middle" font-size="11" fill="#475569">大地水準面 / 正常位</text>

  <rect x="600" y="70" width="140" height="70" rx="8" fill="#fce7f3" stroke="#be185d" stroke-width="2"/>
  <text x="670" y="100" text-anchor="middle" font-size="14" fill="#831843" font-weight="bold">3. 空間運動與時間</text>
  <text x="670" y="122" text-anchor="middle" font-size="11" fill="#475569">歲差章動 / 原子時</text>

  <rect x="600" y="220" width="140" height="70" rx="8" fill="#dcfce7" stroke="#15803d" stroke-width="2"/>
  <text x="670" y="250" text-anchor="middle" font-size="14" fill="#14532d" font-weight="bold">4. 基準與地圖投影</text>
  <text x="670" y="272" text-anchor="middle" font-size="11" fill="#475569">TWD97 / TM2°</text>

  <!-- 中央樞紐核心 -->
  <circle cx="400" cy="180" r="60" fill="#0284c7" stroke="#0369a1" stroke-width="3"/>
  <text x="400" y="175" text-anchor="middle" font-size="15" fill="#ffffff" font-weight="bold">大地測量學</text>
  <text x="400" y="195" text-anchor="middle" font-size="13" fill="#ffffff">現代時空基底</text>

  <!-- 連接箭頭 -->
  <line x1="200" y1="105" x2="340" y2="150" stroke="#0284c7" stroke-width="2"/>
  <line x1="200" y1="255" x2="340" y2="210" stroke="#0284c7" stroke-width="2"/>
  <line x1="600" y1="105" x2="460" y2="150" stroke="#0284c7" stroke-width="2"/>
  <line x1="600" y1="255" x2="460" y2="210" stroke="#0284c7" stroke-width="2"/>
</svg>
```
