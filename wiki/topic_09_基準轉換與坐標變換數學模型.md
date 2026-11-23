# 主題 09：基準轉換與坐標變換數學模型

> **資料來源標註**：本條目所有定義、矩陣、轉換公式與數值 100% 摘錄自原始文獻 `raw/01.pdf.pdf`（名詞解釋 一-2、公式意義 二、推導 3、5、7、8、計算 6–9、18、申論 比較 10）與 `raw/03.md.md`（第二節 第 4 點）。

---

## 一、三維空間基準轉換模型

依據 `raw/01.pdf.pdf` 與 `raw/03.md.md`：

### 1. 七參數三維相似轉換（Bursa-Wolf 模型 / Helmert 7-Parameter）
用於兩套三維空間坐標系（如參心到地心，或兩代地心框架之間）的嚴格幾何轉換。包含 **3 個平移參數、3 個旋轉參數與 1 個尺度比例因子**：
$$\begin{bmatrix} X \\ Y \\ Z \end{bmatrix}_2 = S \cdot \mathbf{R}(\varepsilon_x, \varepsilon_y, \varepsilon_z) \begin{bmatrix} x \\ y \\ z \end{bmatrix}_1 + \begin{bmatrix} \Delta X \\ \Delta Y \\ \Delta Z \end{bmatrix}$$
- **七參數各項幾何物理意義**：
  - $\Delta X, \Delta Y, \Delta Z$：三軸平移量，用以對齊兩坐標系空間原點。
  - $\varepsilon_x, \varepsilon_y, \varepsilon_z$：繞三個正交軸的微小歐拉旋轉角，用以對齊坐標軸方向。
  - $S = 1 + D$：尺度比率因數（$D$ 為尺度微小偏差量，通常以 $\text{ppm}$ 表示），用以校正兩系統長度基準尺度。

#### 小角度線性化推導（`raw/01.pdf.pdf` 推導 5）
當三維旋轉角 $\varepsilon_x, \varepsilon_y, \varepsilon_z$ 極小時，$\cos\varepsilon \approx 1$，$\sin\varepsilon \approx \varepsilon$（弧度），略去二次小量 $\varepsilon_i \varepsilon_j \approx 0$：
$$\mathbf{R}_1(\varepsilon_x) \approx \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & \varepsilon_x \\ 0 & -\varepsilon_x & 1 \end{bmatrix},\quad
\mathbf{R}_2(\varepsilon_y) \approx \begin{bmatrix} 1 & 0 & -\varepsilon_y \\ 0 & 1 & 0 \\ \varepsilon_y & 0 & 1 \end{bmatrix},\quad
\mathbf{R}_3(\varepsilon_z) \approx \begin{bmatrix} 1 & \varepsilon_z & 0 \\ -\varepsilon_z & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$
三者相乘展開為反對稱矩陣加單位矩陣：
$$\mathbf{R} \approx \mathbf{I} + \begin{bmatrix} 0 & \varepsilon_z & -\varepsilon_y \\ -\varepsilon_z & 0 & \varepsilon_x \\ \varepsilon_y & -\varepsilon_x & 0 \end{bmatrix}$$
令 $S = 1 + D$，代入七參數式得線性化閉合形式：
$$\mathbf{X}_2 \approx \mathbf{X}_1 + \mathbf{T} + D \cdot \mathbf{X}_1 + \mathbf{R}' \cdot \mathbf{X}_1$$
此即 ITRF 框架跨版本轉換所採用的標準計算模型。

### 2. 三參數平移轉換（3-Parameter Shift）
- **數學公式**：
  $$X_b = X_a + \Delta X,\quad Y_b = Y_a + \Delta Y,\quad Z_b = Z_a + \Delta Z$$
- **轉換流程**：
  基準 A 經緯高 $(\phi_a, \lambda_a, h_a) \xrightarrow{\text{正算}} \text{ECEF } (X_a, Y_a, Z_a) \xrightarrow{\text{加平移}} (X_b, Y_b, Z_b) \xrightarrow{\text{迭代反算}} \text{基準 B 經緯高 } (\phi_b, \lambda_b, h_b)$。
- **特徵**：假設兩基準間旋轉與尺度偏差極小，完全由原點偏移吸收所有差異，屬於工程近似轉換。
- **實例（`raw/01.pdf.pdf` 計算 6）**：
  - 美國 NAD27（Clarke 1866 橢球）轉 WGS84：$\Delta X = -8\text{ m}, \Delta Y = +160\text{ m}, \Delta Z = +176\text{ m}$。
  - 測點 $(\phi=30^\circ\text{ N}, \lambda=-100^\circ\text{ E}, h=232\text{ m})$ 經轉換後產生約 $+24.9\text{ m}$（北向）、$-35.6\text{ m}$（西向）的平面位移與 $-37.2\text{ m}$ 的大地高差異。

### 3. Standard Molodensky 公式
- **原理**：直接將大地坐標變化量 $(\Delta\phi, \Delta\lambda, \Delta h)$ 表達為空間位移 $(\Delta X, \Delta Y, \Delta Z)$ 及橢球幾何差異 $(\Delta a, \Delta f)$ 的解析函數，完全跳過 ECEF 中間直角坐標計算。
- **推導理論（`raw/01.pdf.pdf` 推導 8）**：
  對三維坐標函數 $X(\phi, \lambda, h; a, f)$ 進行全微分，投影至地表測站正交之北、東、天頂方向，分別除以曲率半徑 $M+h$ 與 $(N+h)\cos\phi$。在小範圍與小偏移量下與三參數法數值完全一致。

---

## 二、二維平面坐標轉換模型

依據 `raw/01.pdf.pdf`（名詞解釋 一-2、計算 8）：

| 轉換類型 | 參數個數 | 幾何變換內容 | 最小共同控制點數 | 幾何圖形變化特徵 |
| :--- | :--- | :--- | :--- | :--- |
| **三參數** | 3 (2平移+1旋轉) | $X = x\cos\theta - y\sin\theta + \Delta x$<br>$Y = x\sin\theta + y\cos\theta + \Delta y$ | 1.5 點（3 個坐標分量） | 僅改變位置與朝向，**圖形剛體不變形**。 |
| **四參數（Helmert正形）** | 4 (1尺度+1旋轉+2平移) | $\begin{bmatrix} X \\ Y \end{bmatrix} = S \begin{bmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} + \begin{bmatrix} \Delta x \\ \Delta y \end{bmatrix}$ | 2 個共同點（4 個坐標分量） | 各軸同比例縮放，角度維持不變，**保證幾何正形**。 |
| **六參數（仿射 Affine）** | 6 (2尺度+1旋轉+1剪切+2平移) | 兩軸各具獨立尺度（$S_x \neq S_y$）與軸間非正交偏角 $\varepsilon$ | 3 個共同點（6 個坐標分量） | 容許正方形拉伸扭曲為平行四邊形，**修正各向異性形變**。 |

---

## 三、臺灣 TWD67 與 TWD97 簡易幾何轉換模型

依據 `raw/01.pdf.pdf`（公式意義 二、計算 7、申論 比較 10）：
在臺灣本島 TM2° 平面坐標系下，工程測量常用平均平移量作局部近似轉換：

### 1. 轉換公式
$$E_{67} = E_{97} - 828\text{ m}$$
$$N_{67} = N_{97} + 197\text{ m}$$
- **反求公式**：
  $$E_{97} = E_{67} + 828\text{ m}$$
  $$N_{97} = N_{67} - 197\text{ m}$$

### 2. 幾何物理分析
- **兩系統同一實體點的平面空間向量差**：
  $$\Delta S = \sqrt{(\Delta E)^2 + (\Delta N)^2} = \sqrt{828^2 + 197^2} \approx 851.1\text{ 公尺}$$
  合成方向為東向 828 m、北向 197 m。
- **轉換精度與誤差來源**：
  - 全島平均直接使用該平移量時，平面殘差約在 **5 m 以內**。
  - 若在 TM2° 投影格網下進一步應用**最小曲率法（Minimum Curvature）** 進行網格差值內插，殘差可大幅降至 **30 cm 左右**。
  - **三大誤差來源**：①早期三角測量成果累積誤差；②GRS67 參心與 GRS80 地心橢球本體基準誤差；③地圖投影幾何變形誤差。

---

## 四、跨曆元十四參數轉換（時變坐標外推）

依據 `raw/01.pdf.pdf`（名詞解釋 一-5、公式意義 二、計算 18、19）：
在現代時變大地參考框架（如 ITRF2014 $\to$ ITRF2020）中，因板塊運動各參數均隨時間線性演化：
$$P(t) = P(t_0) + \dot{P} \cdot (t - t_0)$$
包含 7 個基準幾何參數與對應的 7 個年變化率（$\dot{T}_x, \dot{T}_y, \dot{T}_z, \dot{D}, \dot{R}_x, \dot{R}_y, \dot{R}_z$）。轉換時**測站三維坐標與三維速度必須同步進行轉換**：
$$\dot{\mathbf{X}}_2 = \dot{\mathbf{X}}_1 + \dot{\mathbf{T}} + \dot{D}\mathbf{X}_1 + \dot{\mathbf{R}}\mathbf{X}_1$$
若測站具有長期板塊速度（如 $v_N = +3.0\text{ cm/yr}$），在靜態基準下不作動態外推，累積 6 年便會產生 18 cm 的控制點點位系統偏差，此即需要引進動態基準的根本力學原因。
