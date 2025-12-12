紀錄防禦相關技巧

數據庫方面:
增加terminal白名單。當有dbeaver等可疑 terminal連入數據庫時告警

系統方面:
Linux增加history.sh，錄製所有tty 操作紀錄
非工作時間 ssh登入告警
全時段 非ssh 跳板機登入告警

雲方案:
GCP : elk設置 status error 7 日誌告警

蜜罐方面:
使用hfish全網段覆蓋
