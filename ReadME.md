紀錄防禦相關技巧

數據庫方面:
增加terminal白名單。當有dbeaver等可疑 terminal連入數據庫時告警

系統方面:
Linux增加history.sh，錄製所有tty 操作紀錄
非工作時間 ssh登入告警
全時段 非ssh 跳板機登入告警

雲方案:
GCP Audit :
  elk設置 protoPayload.status.code  日誌告警
  Status 16 (Unauthenticated)：你沒登入，或是 Token 失效（「你是誰？」）。
  Status 7 (Permission Denied)：你登入了，但你沒有這項資源的存取權（「你不能動這個資源」）。
  GCP組織project 設置 log router 將所有組織下子項目日誌傳輸到統一個bucket
  GCP組織project 的iam > audit log 全局開啟審計日誌
  
#從GCP console使用指定port 登入vm
protoPayload.serviceName : "iap.googleapis.com"


AWS Audit:
  所有linux 安裝SSM，並在SSM開啟 DHMC 自動管理 跟 自動更新


蜜罐方面:
使用hfish全網段覆蓋

elk方面:
全局DNS收集 紀錄告警
domain: (*.oast.* OR *.dnslog.cn OR webhook.site OR httpbin.org OR canarytokens.com OR interact.sh OR axss.xyz OR ceye.io OR bxss.me)




Linux 溯源
lsof +L1  查詢已被刪除inode但文件還在
文件時間更改過，還是可以根據inode來識別大概是什麼時候建立的檔案
