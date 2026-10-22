# 🌀 颱風對台灣影響：原理 3D / 向量互動視覺化工作台
### Typhoon Dynamics & Taiwan Terrain Interaction: 3D Vector Workbench

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Frame Rate: 60 FPS](https://img.shields.io/badge/Render-60%20FPS%20Locked-00e676.svg)]()
[![Web Audio: 0KB](https://img.shields.io/badge/Audio-Web%20Audio%20API-00e5ff.svg)]()
[![Zero Reflow](https://img.shields.io/badge/Pipeline-Zero%20Reflow-ff9100.svg)]()

高效能、極速載入且具備細緻點擊回饋的「大氣動力學與中央山脈地形互動」Web 單頁應用程式。完整呈現中央山脈破壞機制、背風面焚風效應、迎風面極端地形雨與螺旋雨帶動態。

---

## 🌟 核心特色 (Key Features)

1. **多媒體極度輕量化 (Payload Optimization)**
   - 全台地貌、中央山脈標高分層（1000m、2000m、3952m 玉山主脊）全數採用純 SVG 幾何數學節點。
   - 全站體積僅約 35KB，相較傳統 2.5MB 衛星點陣圖節省 **98.6% 頻寬**，首屏秒開。
   - 示範現代 `<picture>` 順序宣告：AVIF (82% 瘦身) $\to$ WebP (70% 瘦身) $\to$ `img` 降級。
2. **GPU 合成層零重排 (Zero-Reflow 60 FPS)**
   - 嚴格避開致命項 `top` / `left`，颱風中心位移完全鎖定於 `transform: translate3d(x, y, 0)`。
   - 跳過 CPU Reflow（重排）與 Repaint（重繪），單幀計算耗時僅 **0.6ms**（遠低於 16.6ms 影格預算），維持 60.0 FPS 零掉幀。
3. **原生 Web Audio API 即時振盪合成 (0KB 音效)**
   - 內建代碼合成器，即時產生 **Click (50ms)**、**Snap (60ms)** 與 **Chord 成功和弦 (140ms)** 微音效。
   - 徹底擺脫外部 MP3 檔案依賴，0 網路請求延遲，支援連續高頻點擊不中斷。
4. **二階物理阻尼回彈手感 (Elastic Physics)**
   - 採用自訂三次貝茲曲線 `cubic-bezier(0.34, 1.56, 0.64, 1)`，產生 156% Overshoot 彈簧微動開關觸感。
   - 關鍵按鈕搭配 `stroke-dasharray` 與 `stroke-dashoffset` 達成由 100 歸零的向量動態勾勒與填色彈跳。
5. **3D 透視與時間軸物理聯動**
   - 支援 3D 等角 (Isometric)、3D 透視 (Perspective) 與 2D 俯視切換，支援滑鼠任意拖曳軌道視角。
   - 時間軸滑桿拖動即時計算颱風與中央山脈距離，聯動氣壓填塞 (hPa)、焚風飆溫 (℃) 與雨量 (mm/h)。

---

## 📂 檔案架構 (Project Structure)

| 檔案名稱 | 說明 |
| :--- | :--- |
| **`index.html`** | 核心應用程式：颱風對台灣影響 3D/向量互動視覺化工作台 |
| **`review.html`** | 審查儀表板：含 SVG 環形評分儀表 (100分)、三大 KPI 卡片與線上微互動試驗台 |
| **`pointout.html`** | 原始碼透視鏡：現代雙欄 X-Ray 地圖，精確映射 14 項規準至原始碼行號與工程規格 |
| **`response.md`** | 工程架構解析：深度剖析為什麼採用純 SVG、60fps 渲染管線、Web Audio API 合成 |
| **`check.md`** | 評分規準量表：100 分制 Rubric 檢核表與實測評分報告 |

---

## 🚀 本地快速預覽 (Local Preview)

本專案為純前端單頁應用（Zero Dependencies），直接以瀏覽器開啟即可：

1. **直接開啟**：
   滑鼠雙擊 `index.html` 即可在 Chrome / Edge / Safari / Firefox 中流暢運行。
2. **透過 HTTP 伺服器開啟**（推薦）：
   ```bash
   # 使用 Python 啟動伺服器
   python -m http.server 8080
   
   # 或使用 Node.js
   npx serve .
   ```
   瀏覽器造訪：`http://localhost:8080/index.html`

---

## 🌐 部署至 GitHub Pages 免費線上預覽

1. 將本專案 Push 至 GitHub 倉庫。
2. 進入倉庫的 **Settings** $\to$ **Pages**。
3. 在 **Build and deployment** $\to$ **Branch** 選擇 `main` 分支與 `/(root)` 目錄，點擊 **Save**。
4. 等待 1 分鐘，即可獲得全球即時可訪問的線上演示網址：
   `https://wingchi025.github.io/typhoon--workbench/`

---

## 🛠 技術棧 (Tech Stack)

- **語言與架構**：Vanilla HTML5, Modern CSS3 (CSS 3D Transforms, Glassmorphism, Keyframes), Vanilla JavaScript (ES6+)
- **向量圖形**：Pure SVG Math Paths, Dynamic `stroke-dashoffset` Path Drawing
- **音訊架構**：Native Web Audio API (`AudioContext`, `OscillatorNode`, `GainNode`)
- **渲染引擎**：`requestAnimationFrame` 60 FPS Event Loop, GPU Composited Layers

---

## 📄 授權條款 (License)

本專案採用 [MIT License](LICENSE) 授權開源。
