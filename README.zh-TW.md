# 工程作品集

這個作品庫展示 Python 後端、部署診斷及多 Agent 流程架構。英文主頁適合提供給接案客戶；本頁供中文走讀。

## 先看哪裡

1. [Operations Health API](projects/operations-health-api/)：可執行的 FastAPI 示範，使用模擬設備事件，包含 SQLite、事件去重、驗證、健康檢查與測試。
2. [4-Agent 架構案例](case-studies/server-assembly-inspection/)：進行中的伺服器組裝檢驗設計，說明本人主導的架構、分工、雲端與 Edge 邊界及回饋流程。
3. [驗證紀錄](projects/operations-health-api/evidence/verification.json)：確認哪些檢查實際執行過。
4. [GitHub Actions 工作流程](.github/workflows/verify.yml)：分開驗證 Python 測試與 Docker 容器建置、HTTP 操作。

## 已確認的範圍

API 的原始本機紀錄為 15 項整合測試與 11 個 HTTP 情境通過。原始環境無法連線 Docker daemon，因此不把 Compose 設定檢查當作容器已運行的證據。發布後的容器驗證結果，應以對應 commit 的 Actions 紀錄為準。

API 是這次準備作品集時以 AI 協助製作的獨立示範，並非先前公司或客戶的交付。架構案例則是進行中的設計工作，尚未宣稱完成四個 Agent、實測檢驗準確率或設備防撞驗證。

## 可重現的走讀重點

- 同一事件重送，如何避免新增重複紀錄？相同 key 搭配不同內容會如何處理？
- 資料庫故障時，為何 liveness 仍成功而 readiness 失敗？
- 過期資料、未知狀態、設備異常與時鐘偏移如何區分？
- Serverless invocation 可以無狀態，但整個檢驗流程仍需保存哪些狀態？
- 為何 VLM 的光學診斷交回 Planner，而不是直接繞過 Edge 控制？

每週可合作 10–20 小時；實際里程碑、會議與交付範圍依專案約定。
