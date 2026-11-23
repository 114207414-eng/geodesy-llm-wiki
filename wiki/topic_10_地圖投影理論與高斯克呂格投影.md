# 主題 10：地圖投影理論與高斯克呂格投影

> **資料來源標註**：本條目所有定義、微積分方程、幾何條件與級數展開式 100% 摘錄自原始文獻 `raw/04.md.md`（大地測量學 Ch6 重點整理：橢球面到投影平面 6.1–6.5 節）與 `raw/01.pdf.pdf`。

---

## 一、地圖投影的數學幾何理論

依據 `raw/04.md.md`（6.1 節）：
### 1. 投影目的與數學方程
- **目的**：旋轉橢球面為不可展曲面，在其上進行大地測量幾何計算極為繁複。為了工程放樣與地圖繪製，必須建立橢球大地坐標 $(\phi, \lambda)$ 與平面直角坐標 $(x, y)$ 之間的一對一解析映射：
  $$x = F_1(\phi, \lambda),\quad y = F_2(\phi, \lambda)$$
- **變形根源**：依據高斯微分幾何，旋轉橢球面的高斯曲率 $K > 0$，不可能在不發生幾何形變（撕裂、壓縮或拉伸）的前提下展開為平面。

### 2. 長度比與蒂索變形橢圓（Tissot's Indicatrix）
- **長度比（Scale Factor）**：
  $$m = \frac{ds}{dS}$$
  其中 $dS$ 為橢球面上微分線段長度，$ds$ 為其投影至平面後的相應長度。長度比隨地表點位及線段方位角 $\alpha$ 而變。
- **主方向與變形橢圓**：
  - 橢球面上一點處，必存在互相垂直的兩個特定方向，其長度比分別達到極大值 $a$ 與極小值 $b$，稱為**主方向**。
  - 橢球面上的微小單位圓，投影到平面後變形為半長軸為 $a$、半短軸為 $b$ 的橢圓，此即**蒂索變形橢圓**。

### 3. 各類變形定量公式
1. **長度變形**：
   $$\nu = m - 1,\quad m^2 = a^2\cos^2\alpha + b^2\sin^2\alpha$$
2. **方向角變形**：
   $$\sin(\alpha - \alpha') = \frac{a - b}{a + b}\sin(\alpha + \alpha')$$
3. **最大角度變形（$\Delta u = 2\omega$）**：
   $$\sin\frac{\omega}{2} = \frac{a - b}{a + b}$$
4. **面積比（Area Distortion）**：
   $$P = a \cdot b$$

### 4. 投影分類體系
- **按幾何變形性質**：
  - **正形投影（等角投影，Conformal）**：$a = b \implies m = a = b$。長度比與方向無關，微小圓形投影後仍保持為圓形，角度不變形。
  - **等積投影（Equivalent）**：$P = a \cdot b = 1$。地表幾何面積嚴格無變形。
  - **任意投影（Arbitrary）**：既不等角亦不等積（若 $a=1$ 或 $b=1$ 稱為等距離投影）。
- **按投影面幾何構造**：方位投影（切平面）、圓錐投影（圓錐面）、圓柱投影（圓柱面）。

---

## 二、正形投影的一般條件與柯西－黎曼方程

依據 `raw/04.md.md`（6.3 節）：
### 1. 等量緯度（Isometric Latitude, $q$）
為消除橢球面微分幾何中經向與緯向線元長度的不對稱性，引進等量緯度 $q$：
$$q = \int_0^\phi \frac{M}{N\cos\phi} d\phi$$
使橢球面第一基本形式簡化為等角形式：
$$dS^2 = r^2 (dq^2 + dl^2)$$
其中 $r = N\cos\phi$ 為緯線圈半徑，$l = \lambda - \lambda_0$ 為經差。

### 2. 柯西－黎曼條件（Cauchy-Riemann Conditions）
在正形投影下，長度比 $m$ 必須與微元方位角完全無關。令一階偏導組合形式：
$$E = \left(\frac{\partial x}{\partial q}\right)^2 + \left(\frac{\partial y}{\partial q}\right)^2,\quad
F = \frac{\partial x}{\partial q}\frac{\partial x}{\partial l} + \frac{\partial y}{\partial q}\frac{\partial y}{\partial l},\quad
G = \left(\frac{\partial x}{\partial l}\right)^2 + \left(\frac{\partial y}{\partial l}\right)^2$$
滿足正形條件必須使 $F = 0$ 且 $E = G$，嚴密導出**柯西－黎曼條件**：
$$\frac{\partial x}{\partial q} = \frac{\partial y}{\partial l},\quad \frac{\partial x}{\partial l} = -\frac{\partial y}{\partial q}$$
此時長度比為 $m^2 = \frac{E}{r^2} = \frac{G}{r^2}$。

---

## 三、高斯－克呂格投影（Gauss-Krüger Projection）

依據 `raw/04.md.md`（6.2、6.4 節）：
**高斯投影**又稱橫軸橢圓柱等角投影。其幾何物理模型為：假想一橢圓柱橫套於地球橢球體外部，並與特定的一條**中央子午線（Central Meridian）** 嚴格相切。

### 1. 高斯投影的三大基本條件
1. **中央子午線投影為平面直角坐標縱軸直線**。
2. **中央子午線長度比恆等於 1（無長度變形，$m_0 = 1$）**。
3. **投影滿足正形條件（角度無變形，$\Delta u = 0$）**。

### 2. 正算公式展開（$\phi, \lambda \to x, y$）
依據柯西－黎曼條件與對稱性，平面坐標展開為經差 $l$ 的泰勒冪級數。由於對稱性，縱軸 $y$ 為經差 $l$ 的偶函數，橫軸 $x$ 為 $l$ 的奇函數：
$$y = Y + \frac{N}{2}\sin\phi\cos\phi \cdot l^2 + \frac{N}{24}\sin\phi\cos^3\phi \left(5 - t^2 + 9\eta^2 + 4\eta^4\right) l^4 + \cdots$$
$$x = N\cos\phi \cdot l + \frac{N}{6}\cos^3\phi \left(1 - t^2 + \eta^2\right) l^3 + \frac{N}{120}\cos^5\phi \left(5 - 18t^2 + t^4 + 14\eta^2 - 58\eta^2 t^2\right) l^5 + \cdots$$
- **式中輔助符號**：
  - $Y$：自赤道沿子午線積分至該緯度 $\phi$ 的子午線弧長實長。
  - $t = \tan\phi$。
  - $\eta^2 = e'^2 \cos^2\phi$（第二偏心率項）。
  - 當要求坐標精度達 $0.001\text{ m}$ 時，級數必須取至 $l^6$ 階項。

### 3. 反算公式（$x, y \to \phi, \lambda$）與底點緯度（Foot Latitude, $\phi_f$）
- **底點緯度 $\phi_f$**：定義為子午線弧長 $Y$ 剛好等於測點縱坐標 $y$ 時所對應的橢球大地緯度。
- **反算流程**：由縱坐標 $y$ 反求底點緯度 $\phi_f$，再將 $(\phi_f - \phi)$ 與經差 $l$ 展開為橫坐標 $x$ 的冪級數，求得大地緯度 $\phi$ 與經度 $\lambda = \lambda_0 + l$。

---

## 四、平面子午線收斂角 $\gamma$（Meridian Convergence）

依據 `raw/04.md.md`（6.5 節）：
### 1. 定義
在投影平面上，過某點的**真子午線投影切線方向**與**平面直角坐標網格北向（縱軸平行線）** 之間的夾角。

### 2. 計算公式
- **由大地坐標 $(\phi, \lambda)$ 計算**：
  $$\gamma = l\sin\phi + \frac{l^3}{3}\sin\phi\cos^2\phi\left(1 + 3\eta^2 + 2\eta^4\right) + \frac{l^5}{15}\sin\phi\cos^4\phi\left(2 - t^2\right) + \cdots$$
- **由平面坐標 $(x, y)$ 計算**：
  $$\gamma \approx \frac{x}{N_f}t_f - \frac{x^3}{3N_f^3}t_f\left(1 + t_f^2 - \eta_f^2\right) + \cdots$$

### 3. 幾何物理性質
1. $\gamma$ 為經差 $l$ 的奇函數：**中央子午線以東為正值，中央子午線以西為負值**；在中央子午線上 $\gamma = 0$。
2. 經差 $l$ 固定時，$\gamma$ 隨緯度 $\phi$ 增高而顯著增大（在兩極處 $\sin 90^\circ = 1$，收斂角等於經差）。

---

## 五、觀測成果之歸算改正

依據 `raw/04.md.md`（6.2 節）：
地面實測角度與長度歸算至高斯投影平面必須經過嚴密改正：
1. **方位角歸算**：
   $$\alpha = A - \gamma + \delta$$
   其中 $A$ 為大地水準面大地方位角，$\gamma$ 為子午線收斂角，$\delta$ 為方向曲率改正（二次微小量）。
2. **距離改正**：
   $$s = S + \Delta s$$
   其中 $S$ 為橢球面大地線長度，$s$ 為投影平面直線長度，$\Delta s$ 為長度投影變形改正數。
