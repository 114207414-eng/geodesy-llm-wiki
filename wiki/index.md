# 大地測量學知識庫總目錄與概念索引 (wiki/index.md)

本知識庫遵循 `agent.md` 規範建置，**嚴格遵守「100% 來源無幻覺鐵則」**。知識庫中所有定義、數學物理公式、推導步驟與參數數值，100% 提煉自 `raw/` 資料夾中之五份原始教材與考題解答：
1. `raw/01.pdf.pdf`：〈基準與坐標系統 期末猜題（名詞解釋·公式意義·推導·計算）〉
2. `raw/02.pdf.pdf`：〈地球的運轉·時間系統 猜題與解答〉
3. `raw/03.md.md`：〈大地測量基礎筆記：重力場、基準與座標系統、時間系統〉
4. `raw/04.md.md`：〈大地測量學 Ch6 重點整理：橢球面到投影平面（地圖投影）〉
5. `raw/05.md.md`：〈地球重力場及地球形狀的基本理論｜詳細筆記〉

---

## 一、知識庫條目總覽與摘要目錄

| 條目編號與檔名 | 主題名稱 | 核心內容摘要 | 主要來源依據 |
| :--- | :--- | :--- | :--- |
| [`topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md) | 地球形狀與幾何物理特徵 | 地球尺寸基本數據（表面積、質量、密度）、南北半球不對稱性、梨形地球（20m差）與三軸橢球、大氣垂直五分層及電離層色散延遲、地球自轉角速度與赤道最大線速度（465 m/s）、克卜勒三定律與天體軌道形狀。 | `raw/05.md.md`<br>`raw/03.md.md` |
| [`topic_02`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_02_地球重力場與重力位理論.md) | 地球重力場與重力位理論 | 重力合成公式（$\mathbf{g}=\mathbf{F}+\mathbf{P}$）、引力位 $V$ 與負梯度場（$\mathbf{a}=-\operatorname{grad}V$）、保守力場與路徑無關性、真空引力位調和性（$\Delta V=0$）、離心力位布阿桑算子（$\Delta Q=2\omega^2\neq 0$）、重力位 $W$（非調和）、鉛垂線與水準面性質（$dl=-dW/g$，水準面不平行不相交）、大地水準面定義、重力單位（Gal/mGal）及全球緯度遞增趨勢（極曲率與離心力雙重主因）。 | `raw/05.md.md`<br>`raw/03.md.md` |
| [`topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md) | 正常重力位與水準橢球 | 引力位球諧多極展開（帶球、扇球、田球函數與斯托克斯常數）、正常重力位 $U$ 的三大假設（地心原點、主慣性軸、旋轉對稱）、擾動位 $T$（$W=U+T$）、水準橢球面方程（幾何扁率 $\alpha=\mu+q/2$）、克萊羅定理（$\alpha+\beta=\frac{5}{2}q$）、四階正常重力公式與 $\sin^2 2\phi$ 中緯度修正、WGS84 索米里安納閉合公式、自由空間高程修正（每 3m 減 1 mGal）、正常重力場 4 個獨立定義常數。 | `raw/05.md.md`<br>`raw/03.md.md`<br>`raw/01.pdf.pdf` |
| [`topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md) | 地球運動與空間坐標系 | 歲差（25,800年，春分點西移 50.3″/年）、章動（18.6年，9.21″）、極移（張德勒擺動 435天 6m、周年項 2m、極漂移 3.7 mas/年向格陵蘭，地表晃動約 20m 足球場）、歲差章動 vs 極移本質區別、五層坐標系轉換鏈（瞬時天球 $\to$ CIS $\to$ CTS/ECEF $\to$ 瞬時地球 $\to$ 測站地平）、EOP 五大參數與 IERS、天文坐標 vs 大地坐標、垂線偏差 $(\xi, \eta)$、大地起伏 $N$、拉普拉斯方程式、格林威治子午線 102 米垂線偏差歷史謎題。 | `raw/01.pdf.pdf`<br>`raw/02.pdf.pdf`<br>`raw/03.md.md`<br>`raw/05.md.md` |
| [`topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md) | 大地基準與橢球體 | 大地基準定義三要素（參數、定向雙平行條件、定位）、基準偏移可達 1 公里、參考橢球體 vs 總地球橢球體（$\iint N^2 d\sigma=\min$、7 個幾何物理約束）、四大常用橢球比較（GRS67, GRS80, WGS84, Clarke 1866）、GRS80 與 WGS84 扁率微小差異（0.1毫米）、卯酉圈曲率半徑 $N$ 與子午圈曲率半徑 $M$（幾何物理意義與大小關係）、大地坐標 $(\phi,\lambda,h)$ 與 ECEF $(X,Y,Z)$ 正反算及迭代推導。 | `raw/01.pdf.pdf`<br>`raw/03.md.md`<br>`raw/05.md.md` |
| [`topic_06`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_06_大地測量時間系統.md) | 大地測量時間系統 | 計時三要件、恆星時系統（恆星日 23h56m04s、LST、真/平恆星時）、1 平太陽日 = 1.0027379 恆星日（公轉每天多轉 1° 差 4 分鐘）、真太陽時 vs 平太陽時、世界時系列（UT0, UT1 自轉核心標準, UT2）、國際原子時 TAI（銫-133 9,192,631,770 Hz）、協調世界時 UTC 與閏秒機制（$|UT1-UTC|<0.9\text{s}$）、動力時 TDT/TT、GPST（連續無閏秒，1980/1/6 起算）、時間系統嚴密轉換鏈、儒略日 JD 與 MJD、時鐘誤差光速放大（1 ms $\to$ 300 km）。 | `raw/02.pdf.pdf`<br>`raw/03.md.md` |
| [`topic_07`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_07_國際參考框架與現代動態基準.md) | 國際參考框架與現代動態基準 | 參考系統（理論）$\to$ 參考框架（物理實現）$\to$ 基準（地域參數）層次劃分、ITRS 四大條件（地心、SI公尺、BIH 1984.0、無淨旋轉 NNR）、ITRF 內容與版本、五大空間測地技術（VLBI, SLR, LLR, GNSS, DORIS）、聯合國 GGRF 決議、基準演進（靜態 $\to$ 半動態 $\to$ 動態）、紐西蘭 NZGD2000、澳洲雙框架 GDA2020/ATRF2014、日本 JGD2024、歐洲 ETRS89、臺灣雙框架策略（TWD97 靜態法定義務 ＋ TTRF 即時動態框架 ＋ 地殼變位模型）。 | `raw/01.pdf.pdf`<br>`raw/03.md.md` |
| [`topic_08`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_08_臺灣大地基準與全球系統比較.md) | 臺灣大地基準與全球系統比較 | TWD67 詳細規格（參心、GRS67 橢球、埔里虎子山大地原點、平面與高程分離）、TWD97 詳細規格（地心、GRS80 橢球、8 衛星追蹤站聯測 51 個 IGS 站、GAMIT/GLOBK 解算於 ITRF94@1997.0、TM2° 投影）、TWD97 歷代版本更迭（1997.0, 2010.0, 2020.0）、WGS84 演進（TRANSIT, G730, G873）、臺灣高程系統 TWVD2001（基隆平均海水面）、TWD67/TWD97/WGS84 權威比較矩陣。 | `raw/01.pdf.pdf`<br>`raw/03.md.md` |
| [`topic_09`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_09_基準轉換與坐標變換數學模型.md) | 基準轉換與坐標變換數學模型 | 三維七參數相似轉換（Bursa-Wolf，3 平移 + 3 旋轉 + 1 尺度，小角度反對稱線性化矩陣）、三參數 ECEF 平移近似法（以 NAD27 轉 WGS84 為例）、Standard Molodensky 公式、二維平面轉換（三參數、四參數正形 Helmert、六參數仿射）、臺灣 TWD67 與 TWD97 簡易幾何轉換（$E_{67}=E_{97}-828$, $N_{67}=N_{97}+197$，合向量 851.1 m，殘差 5 m，最小曲率法降至 30 cm）、跨曆元十四參數轉換（位置與速度線性演化）、站心坐標 $(n,e,u)$ 與球面 $(A,\beta,r)$ 互換。 | `raw/01.pdf.pdf`<br>`raw/03.md.md` |
| [`topic_10`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_10_地圖投影理論與高斯克呂格投影.md) | 地圖投影理論與高斯克呂格投影 | 投影本質與不可展曲面、長度比 $m$、主方向與蒂索變形橢圓、變形公式（長度、方向、最大角度變形、面積比）、投影分類（等角、等積、任意；方位、圓錐、圓柱）、正形投影柯西－黎曼條件與等量緯度 $q$、高斯投影三大條件、高斯坐標正算（奇偶冪級數展開）與反算（底點緯度 $\phi_f$）、平面子午線收斂角 $\gamma$ 定義與性質、方位角與距離歸算改正（$\delta, \Delta s$）。 | `raw/04.md.md`<br>`raw/01.pdf.pdf` |
| [`topic_11`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_11_UTM投影與臺灣TM2分帶系統.md) | UTM投影與臺灣TM2分帶系統 | UTM 投影規範（割線圓柱 $k_0=0.9996$、割線無變形）、全球經向 6° 帶號公式（臺灣在 Zone 51，中央經線 123°E）、緯向字母區碼（C–X，略去 I, O）、特殊帶（挪威 32V、斯瓦巴 31X 等）、假東 500,000 m 與南北假北、臺灣 TM2° 投影（中央經線本島 121°E、離島 119°E，$k_0=0.9999$、假東 250,000 m、地面距離與網格距離換算）、臺灣 2°/3°/6° 分帶比較與地籍保障原因、英國 BNG 與美國州平面（SPCS 蘭伯特投影）。 | `raw/04.md.md`<br>`raw/01.pdf.pdf`<br>`raw/03.md.md` |

---

## 二、雙向概念關聯矩陣（Concept Cross-Reference Matrix）

本矩陣標示各條目間的核心交叉概念，便於查閱前後相繼的幾何與物理知識傳承：

| 核心概念 | 主定義條目 | 高度關聯引用條目 | 物理／幾何交互關聯說明 |
| :--- | :--- | :--- | :--- |
| **旋轉橢球幾何參數** | `topic_05` | `topic_01`, `topic_03`, `topic_08`, `topic_10` | 地球自轉離心力造就旋轉橢球（01）；正常重力位以此為幾何水準面（03）；國家基準（TWD67/97）與國際系統之選型（08）；投影歸算幾何基礎（10）。 |
| **大地水準面與大地起伏** | `topic_02` | `topic_03`, `topic_04`, `topic_05`, `topic_08` | 水準面由重力等位面定義（02）；擾動位 $T$ 與水準橢球之幾何分離（03）；垂線偏差與正高/大地高關係 $h=H+N$（04）；總地球橢球最小二乘擬合（05）；臺灣 TWVD2001 正高與 TWD97 橢球高之橋樑（08）。 |
| **地球自轉與地球運動** | `topic_04` | `topic_01`, `topic_02`, `topic_06`, `topic_07` | 赤道自轉線速度最大（01）；自轉離心力削弱重力（02）；自轉角度直接定義世界時 UT1 與恆星時（06）；EOP 參數修正 ITRS 與 ICRS 之時變轉換（07）。 |
| **地心地固坐標（ECEF）** | `topic_04` | `topic_05`, `topic_08`, `topic_09` | 協議地球坐標 CTS 定義（04）；大地坐標 $(\phi,\lambda,h)$ 轉換與迭代演算法（05）；TWD97 與 WGS84 地心坐標實現（08）；空間七參數與三參數基準平移之數學載體（09）。 |
| **基準轉換模型** | `topic_09` | `topic_05`, `topic_07`, `topic_08`, `topic_11` | 基準偏移幾何成因（05）；時變動態基準之十四參數跨曆元演化（07）；TWD67 與 TWD97 實務轉換向量與精度分析（08）；平面轉換與 TM2 投影網格平移之對接（11）。 |
| **地圖投影與中央經線** | `topic_10` | `topic_04`, `topic_08`, `topic_11` | 高斯正形柯西－黎曼條件與子午線收斂角（10）；大地方位角與收斂角歸算（04）；臺灣 TWD97 TM2° 投影中央子午線 121°E 與 0.9999 尺度規範（08, 11）。 |
| **原子時與衛星導航時間** | `topic_06` | `topic_01`, `topic_04`, `topic_07` | 電離層雙頻測距消除延遲（01）；時間延遲對應空間距離之光速極端敏感性（06）；時角轉換與 EOP 時間標註（04）；GNSS 與 SLR 測距時間同步基礎（07）。 |

---

## 三、大地測量核心公式速查索引

- **地表線速度**：$V = \frac{2\pi(R\cos\phi + h)}{T} = \omega(R\cos\phi + h)$（[`topic_01`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_01_地球形狀與幾何物理特徵.md)）
- **外部引力場調和性**：$\Delta V = 0$；**離心力位布阿桑算子**：$\Delta Q = 2\omega^2$；**重力位**：$\Delta W = 2\omega^2$（[`topic_02`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_02_地球重力場與重力位理論.md)）
- **等位面間距公式**：$dl = -\frac{dW}{g}$（[`topic_02`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_02_地球重力場與重力位理論.md)）
- **克萊羅定理**：$\alpha + \beta = \frac{5}{2}q$（[`topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)）
- **索米里安納閉合重力公式**：$\gamma = \gamma_e \frac{1 + K\sin^2\phi}{\sqrt{1 - e^2\sin^2\phi}}$（[`topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)）
- **自由空間重力高程修正**：$\Delta_1 g \approx 0.3086 h\text{ (mGal)}$（每升 3m 減 1 mGal）（[`topic_03`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_03_正常重力位與水準橢球.md)）
- **天文轉大地坐標**：$\phi_G = \Phi_A - \xi$，$\lambda_G = \Lambda_A - \eta\sec\phi$，$h = H + N$（[`topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)）
- **大地拉普拉斯方程式**：$\alpha_G = \alpha_A - \eta\tan\phi$（[`topic_04`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_04_地球運動與空間坐標系.md)）
- **曲率半徑公式**：卯酉圈 $N = \frac{a}{\sqrt{1 - e^2\sin^2\phi}}$，子午圈 $M = \frac{a(1-e^2)}{(1 - e^2\sin^2\phi)^{3/2}}$（[`topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md)）
- **大地坐標轉 ECEF**：$X=(N+h)\cos\phi\cos\lambda,\; Y=(N+h)\cos\phi\sin\lambda,\; Z=[N(1-e^2)+h]\sin\phi$（[`topic_05`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_05_大地基準與橢球體.md)）
- **恆星日與平太陽日轉換**：$1\text{ 平太陽日} = 1.0027379\text{ 恆星日}$，$1\text{ 恆星日} = 23\text{h } 56\text{m } 04\text{s}$（[`topic_06`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_06_大地測量時間系統.md)）
- **時間系統換算鏈**：$\text{TAI} = \text{GPST} + 19\text{s} = \text{UTC} + n\text{s} = \text{TDT} - 32.184\text{s}$（[`topic_06`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_06_大地測量時間系統.md)）
- **七參數轉換式**：$\mathbf{X}_2 \approx \mathbf{X}_1 + \mathbf{T} + D\mathbf{X}_1 + \mathbf{R}'\mathbf{X}_1$（[`topic_09`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_09_基準轉換與坐標變換數學模型.md)）
- **臺灣 TWD67 與 TWD97 簡易幾何平移**：$E_{67} = E_{97} - 828\text{ m},\; N_{67} = N_{97} + 197\text{ m}$（合向量 $851.1\text{ m}$）（[`topic_09`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_09_基準轉換與坐標變換數學模型.md)）
- **正形柯西－黎曼條件**：$\frac{\partial x}{\partial q} = \frac{\partial y}{\partial l},\; \frac{\partial x}{\partial l} = -\frac{\partial y}{\partial q}$（[`topic_10`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_10_地圖投影理論與高斯克呂格投影.md)）
- **UTM 分帶號**：$\text{帶號} = \lfloor(\lambda + 180^\circ)/6^\circ\rfloor + 1$；中央經線 $\lambda_0 = 6^\circ \times \text{帶號} - 183^\circ$（[`topic_11`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/topic_11_UTM投影與臺灣TM2分帶系統.md)）
