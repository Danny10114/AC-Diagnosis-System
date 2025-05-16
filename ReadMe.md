# 急性膽囊炎 CT 影像辨識系統

本專案建立一套結合**深度學習模型**與**影像處理技術**的自動化 CT 影像分析系統，能夠快速且準確地辨識腹部 CT 影像中的膽囊位置與輪廓，並進一步判斷是否為**急性膽囊炎（Acute Cholecystitis, AC）**。此系統可大幅減少醫師人工檢視時間，並提供影像輔助資訊作為診斷與手術治療的參考。

---

## 📁 專案架構與模型說明

| 模型名稱        | 說明 |
|----------------|------|
| **GB_Model**   | 使用 VGG16 架構辨識影像中是否存在膽囊器官。 |
| **Segment_Model** | 採用 U-Net 架構，結合影像膨脹與雙邊濾波等前處理，進行膽囊的語意分割，輸出輪廓與大小資訊。 |
| **AC_Model**   | 使用 VGG16 架構進行急性膽囊炎的辨識，輸出高風險區域與預測機率。 |

---

## 🖥️ 系統功能說明

執行 `windows.ipynb` 可進行完整的急性膽囊炎判別流程：

1. 選擇一組腹部 CT 影像。
2. 系統會進行以下流程：
   - 是否包含膽囊（GB_Model）
   - 膽囊分割與輪廓標註（Segment_Model）
   - 急性膽囊炎機率預測與可視化（AC_Model）
3. 輸出包含分割結果與高風險影像的報告。

📦 範例展示影片：`example.mp4`

---

## 🧪 軟體與環境版本

> ✅ 本系統可於 Windows 系統中運行，建議使用 Anaconda 環境進行管理。

| 套件 | 版本 |
|------|------|
| Python | 3.7.16 |
| TensorFlow (GPU) | 2.0.0 |
| NumPy | 1.21.6 |
| OpenCV | 4.6.0 |

---

## 🧠 使用說明（快速上手）

```bash
# 建議使用 conda 建立新環境
conda create -n ac-detection python=3.7
conda activate ac-detection

# 安裝必要套件
pip install tensorflow-gpu==2.0.0 numpy==1.21.6 opencv-python==4.6.0

# 使用 Jupyter Notebook 開啟主執行檔
jupyter notebook windows.ipynb
